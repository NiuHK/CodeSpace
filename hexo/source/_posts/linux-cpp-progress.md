---
title: c++ & Linux 操作系统进程相关操作
toc: true
top: 0
date: 2024-03-22 11:42:28
tags:
---
实现进程管理协同


<!-- more -->



# fork()

# pipe() 实现进程通信

> 每个进程各自有不同的用户地址空间,任何一个进程的全局变量在另一个进程中都看不到，所以进程之间要交换数据必须通过内核,在内核中开辟一块缓冲区,进程A把数据从用户空间拷到内核缓冲区,进程B再从内核缓冲区把数据读走,内核提供的这种机制称为进程间通信。

## API函数的使用以及注意点

```c++
 #include <unistd.h>
 int pipe(int pipefd[2]);
```

**参数说明：**

* fd为文件描述符数组，其中fd[0]表示读端，fd[1] 表示写端

**返回值：**

* 成功返回0，失败返回-1，并且设置errno。

**注意点：**

1. 管道内 `没有数据`时，`读端（read）`发生 `阻塞`，等待有效数据进行读取
2. 管道容量被 `数据填满`时，`写端（write）发生阻塞`，等待进程将数据读走再进行写入
3. 如果所有管道 `写端对应的文件描述符被关闭`，`read返回0`，但会将之前管道里的数据读完
4. 如果所有管道的 `读端对应的文件描述符被关闭`，`write操作会产生信号，SIGPIPE`,进而导致write进程退出
5. 当要写入的数据量不大于管道的容量（PIPE_BUF）时，linux将保证写入的原子性
6. 当要写入的数据量大于管道容量(PIPE_BUF)时，linux将不再保证写入的原子性



## fork子进程并使用pipe通信

{% codeblock lang:cpp >folded %}

#include <unistd.h>
#include <sys/types.h>
#include <iostream>
#include <string>
#include <cstring>
#include <sys/wait.h>
using namespace std;
int main() {
    int pipe_fd[2]; // 0 for reading, 1 for writing
    pid_t cpid;
    char buf;

    // 创建管道
    if (pipe(pipe_fd) == -1) {
        perror("pipe");
    }

    for (int i = 0; i < 4; ++i) {
        cpid = fork();
        if (cpid == -1) {
            perror("fork");
        }

        if (cpid == 0) { // 子进程
            close(pipe_fd[0]); // 关闭读端

            // 发送消息
            string message = "Child " + to_string(getpid()) + " is sending a message to parent!\n";
            write(pipe_fd[1], message.c_str(), message.length());

            close(pipe_fd[1]); // 发送完毕，关闭写端
        } else {
            // 父进程不立即关闭管道，等待所有子进程发送完毕
        }
    }
    // 父进程读取数据
    close(pipe_fd[1]); // 关闭写端

    while (read(pipe_fd[0], &buf, 1) > 0) {
        write(STDOUT_FILENO, &buf, 1);
    }

    close(pipe_fd[0]); // 关闭读端

    // 等待所有子进程退出
    for (int i = 0; i < 4; ++i) {
        wait(NULL);
    }

    return 0;
}

{% endcodeblock %}

## shmget() shmat() shmdt() shmctl() 实现进程间数据同步
>int shmget(key_t key, size_t size, int shmflg);

目的：用于创建新的共享内存段或访问一个已存在的共享内存段。

>void *shmat(int shmid, const void *shmaddr, int shmflg);

目的：将共享内存段附加到调用进程的地址空间。

>int shmdt(const void *shmaddr);

目的：将共享内存段从当前进程的地址空间分离。

>int shmctl(int shmid, int cmd, struct shmid_ds *buf);

目的：对共享内存段执行各种控制操作。

### 示例程序

./2.cpp:

{% codeblock lang:cpp >folded %}

#include <iostream>
#include <sys/ipc.h>
#include <sys/shm.h>
#include <cstring>
#include <unistd.h>

#define SHM_SIZE 512  // 定义共享内存的大小

int main() {
    key_t key = ftok("shmfile",65);  // 生成唯一键
    int shmid = shmget(key, SHM_SIZE, 0666|IPC_CREAT);  // 创建共享内存
    if (shmid == -1) {
        perror("shmget");
        exit(1);
    }

    // 将共享内存附加到进程的地址空间
    char *data = (char*) shmat(shmid, (void*)0, 0);
    if (data == (char*)(-1)) {
        perror("shmat");
        exit(1);
    }

    // 等待进程B写入数据
    std::cout << "Waiting for process B to write data...\n";
    sleep(5);  // 简单的同步机制，等待几秒

    // 显示共享内存中的数据
    std::cout << "Data read from shared memory: " << data << std::endl;

    // 分离共享内存
    if (shmdt(data) == -1) {
        perror("shmdt");
        exit(1);
    }

    // 删除共享内存
    shmctl(shmid, IPC_RMID, NULL);

    return 0;
}

{% endcodeblock %}

./2.1.cpp:

{% codeblock lang:cpp >folded %}

#include <iostream>
#include <sys/ipc.h>
#include <sys/shm.h>
#include <cstring>

#define SHM_SIZE 512  // 定义共享内存的大小

int main() {
    key_t key = ftok("shmfile",65);  // 生成唯一键
    int shmid = shmget(key, SHM_SIZE, 0666);  // 访问共享内存
    if (shmid == -1) {
        perror("shmget");
        exit(1);
    }

    // 将共享内存附加到进程的地址空间
    char *data = (char*) shmat(shmid, (void*)0, 0);
    if (data == (char*)(-1)) {
        perror("shmat");
        exit(1);
    }

    // 向共享内存写入数据
    std::cout << "Writing to shared memory\n";
    std::strncpy(data, "Hello from process B!", SHM_SIZE);

    // 分离共享内存
    if (shmdt(data) == -1) {
        perror("shmdt");
        exit(1);
    }

    return 0;
}

{% endcodeblock %}