---
title: c++ STL 库 （未完成）
date: 2024-03-07 19:56:48
tags:
toc: true
cover: https://picstorage.danielniu.me/imgs/cppstl12687.jpg
---

c++ STL 库包含基本的图，列表，栈等数据结构以及基本操作，方便使用。

<!-- more -->

## 结构图

![结构图](https://picstorage.danielniu.me/imgs/2.png)

## set（集合）

> **内部自动有序 不含重复元素** **容器**

```cpp
#include <set>
set<int> name;
set<double> name;
set<char> name;
set<struct node> name;
set<set<int> > name;//注意：> >之间要加空格
set<int> arr[10];
```

### set容器内元素的访问

**set只能通过迭代器(iterator)访问(除了vector和string之外的STL容器都不支持\*(it+i)的访问方式)** ：

```cpp
set<int>::iterator it;
set<char>::iterator it;
```

```cpp
    for (set<int>::iterator it = st.begin(); it != st.end(); it++)
    {
        cout << *it << endl;
    }
```

### 常用函数

#### insert(value)

```cpp
    st.insert('C');
```

#### find(value)

**find(value)返回的是set中value所对应的迭代器，也就是value的指针（地址）**

```cpp
cout << *(st.find(2)) << endl;
```

#### **erase(it)**

```cpp
st.erase(st.find(100)); //利用find()函数找到100,然后用erase删除它
```

#### **erase(iteratorBegin , iteratorEnd)**

**左闭右开**

```cpp
    st.erase(it, st.end());
```

#### size()

```cpp
    cout << st.size() << endl;
```

## vector（矢量）

> **变长数组**

```cpp
#include <vector>

vector<int> name;
vector<double> name;
vector<char> name;
vector<struct node> name;
vector<vector<int> > name;//注意：> >之间要加空格

vector<int> array[SZIE]; //二维变长数组
```

**二维数组中，它的一维形式就是地址。例如：**

```cpp
    int arr[3][2];//定义一个3行2列的地址
    cout<<arr[0]<<endl; //输出arr第1行的地址
```

output:

```cpp
0x61fe00 //arr第1行的地址
```

### vector容器内元素的访问

**（1）通过下标访问**

```cpp
    cout<<vi[0]<<endl;
```

**（2）通过迭代器访问**

> 迭代器（iterator）可以理解为指针

```cpp
vector<类型名>::iterator 变量名;

vector<int>::iterator it;
vector<double>::iterator it;

    vector<int>::iterator it=v.begin();
    for (int i = 0; i < v.size(); i++)
    {
       cout<<it[i]<<" ";
    }

    vector<int>::iterator it=v.begin();
    for (int i = 0; i < v.size(); i++)
    {
       cout<<*(it+i)<<" ";
    }

    //vector的迭代器不支持it<v.end()的写法，因此循环条件只能it!=v.end()
    for (vector<int>::iterator it=v.begin(); it!=v.end();it++)
    {
        cout<<*it<<" ";
    }


```

### vector常用函数实例解析

#### **（1）push_back(item)**

```cpp
        v.push_back(i);
```

#### **（2）void pop_back()**

```cpp
        v.push_back(i);
```

#### **（3）size()**

```cpp
    cout<<v.size()<<endl;
```

#### **（4）clear()**

```cpp
    v.clear();
```

#### **（5）insert()**

```cpp
insert(__position,__x);

v.insert(v.begin()+2,-1); //将-1插入v[2]的位置
```

#### **（6）erase()    左闭右开**

```cpp
erase(__position); //删除一个元素
   v.erase(v.begin()+3);

erase(__positionBegin,__positionEnd);//删除一个区间内的元素
    v.erase(v.begin()+1,v.begin()+4);
```
