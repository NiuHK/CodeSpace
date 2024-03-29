---
title: 从C++到python
toc: true
date: 2023-07-01 08:41:25
tags: [cpp,python]
top: 0
---

>python的优点是简单易学，库安装简单配置丰富，写法简洁，本文目的即初步认识python的规则化写法。


<!-- more -->

# 环境安装
1. 进入'https://www.jetbrains.com/pycharm/' 下载pycharm并安装。
2. 根据引导安装应用并登录，创建你的第一段python代码。


# 差异
- 毋庸置疑，py比cpp更简单，写代码形式上亦是如此，大体上差别如下：
    - 1. 不需要头文件
    - 2. 主函数没有函数名
    - 3. 不需要{}
    - 4. 不需要;

接下来，从最简单的输出开始；

# 基本知识
## 输入输出

输出函数print()语法就是：
```python
print()
```

输入函数是 input()，功能是接收用户输入的内容，语法是：
```python
input（输出的内容）
```
举例：接收用户输入的密码并打印:
```python
n = input("请输入密码：")	#把输入内容赋给n，用 n 接收一下
print(n)	#打印n
```
在Python里，“#” 表示注释，“#”后面的东西不会被执行。
```
提示信息
请输入密码：123
123
```
## 变量
- 合法的标识符:大小写字母，数字(不能开头),下划线。
- 没有长度限制。
>建议望文生义，函数名、变量名等命名方法各有区分：
```eg:
  1. 包名：全小写，例如 time ;
  2. 类名：每个单词的首字母大写，其他的小写，简称大驼峰命名，例如 HelloWorld ；
  3. 变量名/函数名:第一个单词的首字母小写，后面的单词的首字母大写，简称小驼峰命名，例如 helloWorld ；
  4. 常量：全大写，例如 HELLO 。
  5. 其他命名方式，比如 hello_world 。
```

## 数据类型

与c++不同，python不需要类型说明符，在设置时会自行分配。**（不是没有!!!）**

1. 整型
2. 浮点型
3. 字符串
4. bool类型
5. None 是一个单独的数据类型
6. 列表、元组、字典、集合也是常见的数据类型
- 类型转换：
```python
int() #被转换的必须为全数字的字符串
str()
float() #被转换的必须为全数字的字符串
```
- 获取类型信息
```python
type() #返回的是对象的类型
type().__name__

sinstance(,)  #常用来判断数据类型,返回bool
```
例子：
```python
f = 30
print(type(f))
print(type(f).__name__) 
print(isinstance(f,int))
```
输出：
```python
f = 30
print(type(f))
print(type(f).__name__)
print(isinstance(f,float))
```

## 运算符
运算符可以分为很多4类

1. 一般运算符
>+，-，*，/（真除法）,//（地板除，舍去小数部分）,%（取余数）,**（幂运算）

2. 赋值运算符
>=,+=，-=，*=，/=,%=,**=<br>
连续赋值：a=b=c=d=10

3. 布尔运算符
>== （等于），！=（不等于）, >= ,<= ,>, <

4.逻辑运算符
>主要有not、and和or三类，又称非、与和或
>>and：前后都为真则为真
or：有一个为真则为真
not:非真，非假

例子：
```python
a = 10
b = 20
c = 30
d = 40
n1 = a > b and a < c    #a>b为假，a<c为真，假与真为假
n2 = not a < c   #a<c为真，非真则为假
n3 = a > b or a < c     #a>b为假，a<c为真，假或真为真
print(n1,n2,n3)
```
输出;
```python
False False True
```
# 流程控制
## 条件分支 (if  elif  else)
例子：
```python
s = int(input("请输入分数:"))
if 80 >= s >= 60:
    print("及格")
elif 80 < s <= 90:
    print("优秀")
elif 90 < s <= 100:
    print("非常优秀")
else:
    print("不及格")
    if s > 50:
        print("你的分数在60分左右")
    else:
        print("你的分数低于50分")
```
输出：
```
请输入分数:55
不及格
你的分数在60分左右
```
## 循环流程
1. while循环

语法：
```
while 布尔表达式: 
	代码块
```
只要条件(布尔表达式)为真就执行里面的代码块。

举例：比如说输入一个整数并计算各个位和，例如输入321，那么各个位之和则为6。
```python
# 请输入一个整数，并计算各个位和 如：321=6

n = int(input("请输入一个整数:"))  # 将字符串转为整型

# sums累加器：m=10 m=10+5

sums = 0

while n != 0:  # 32 #3
    sums = sums + n % 10  # sums=1+2=3+3=6
    n = n // 10  # 32
print(sums)

```
输出：
```
请输入一个整数:2345
14
```
2. for循环

语法：
```
for 变量 in 可迭代对象:
	代码块
```
例子：
```python
l=[3,2,1]
for n in l:
	print("1")
```
输出：
```
1
1
1
```

3. range

for循环经常会搭配range来使用，range是一个可迭代对象，range的语法如下：
```python
range(start=0,stop,step=1)
```
 Range对象返回一个对象，该对象按步生成从开始(包含)到结束(排除)的整数序列。Range (i, j)产生i, i+1, i+2，…j - 1。Start默认为0,stop省略!<br>
 Range(4)产生0,1,2,3。这些正是包含4个元素的列表的有效索引。<br>
 当给出step时，它指定增量(或减量)。

4. continue  break

continue跳过本次循环，后面的循环继续执行<br>
break终止循环

# 列表(List)
列表是可以**同时**存放任何数据，包括整型，浮点型，字符串，布尔型等等，是常用的数据类型之一。
##  列表的创建
```
列表也是一个可迭代对象
1. 普通形式
        l = [1,2,3,4,5] ---整型列表
        l = ["a","b","c"] ---字符串列表
        l = [True,False,1>2,5<6]---布尔列表
2. 混合列表
		l = [1,2.5,"a",True]
3. 空列表
		l = []
```
## 从列表中获取数据
列表是有下标的，并且下标从0开始，获取方法类似数组<br>
**但是列表的下标正序从0开始，倒叙从-1开始**<br>
>print(List)顺序输出整个列表
## 列表中数据交换
例子：
```python
l = [1, 2, 3, 4, 5]  # 下标/索引：0开始
l[2], l[3] = l[3], l[2]
print(l)
```
Output:
```python
[1, 2, 4, 3, 5]
```
## 向列表添加元素
```python
append(project) #列表尾插对象（作为整体）
extend(project) #列表尾插可迭代对象 eg：两列表相连接
insert(num,project) #指定下标位置添加对象（作为整体）
```

## 列表删除元素
```python
clear()#清空列表（列表还在，没被删除）
pop()#删除下标指定的元素，如果不加下标则删除最后一个元素
remove()#删除（正序第一个）指定的对象
del()#删除变量(整个列表)或列表指定下标元素的值（补位）
```
例子:
```python
l = [1, 2, 3, 4, 5]
l2=[6, 7, 8, 9, 10]
l.extend(l2)
print(l)
l.append(l2)
print(l)
l.insert(3,l2)
print(l)
l.pop(1)
print(l)
l.remove(l2)
print(l)
del l[-1]
print(l)
del l

print(l2)
l2.clear()
print(l2)
```
Output
```python
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, [6, 7, 8, 9, 10]]
[1, 2, 3, [6, 7, 8, 9, 10], 4, 5, 6, 7, 8, 9, 10, [6, 7, 8, 9, 10]]
[1, 3, [6, 7, 8, 9, 10], 4, 5, 6, 7, 8, 9, 10, [6, 7, 8, 9, 10]]
[1, 3, 4, 5, 6, 7, 8, 9, 10, [6, 7, 8, 9, 10]]
[1, 3, 4, 5, 6, 7, 8, 9, 10]
[6, 7, 8, 9, 10]
[]
```

## 修改元素
同数组。

## 列表高级特性
### 切片操作
切片，顾名思义就是把1个列表切分为多个列表，语法如下：
```
变量[起始下标:结束下标] 	#结束下标取不到
```
做切片操作时要注意以下几个点：

>1. 如果下标从0开始可以省略不写，例如 n = l[:4]。
>2. 如果结束下标取的是最后一个元素，可以省略不写，例如 n = l[3:]。
>3. 如果列表中的元素都要，开始和结束下标都可以省略，例如 n = l[:]。
>4. n = l[:-1] 表示从0开始 - 到数二个元素。
例子：
```python
l = [1, 2, 3, 4, 5]
print(l[0:4])
```
Output
```
[1, 2, 3, 4]
```
### 等距抽取
方法是 n = l[开始:结束:步长] ，这个方法既可以正向去操作列表，也可以反向去操作列表,例如:
```python
l = [1, 2, 3, 4, 5]
n = l[-1:-3:-1]
print(n)
```
Output
```
[5, 4]
```
## 列表的一些操作符

### 比较运算符
列表之间进行比较，以相同下标进行比较，从小到大进行比较，如果值相同则比较下一组元素，如果不同直接出结果，例如：
```python
l = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]  # 下标/索引：0开始
l2 = [2, 3, 4, 6]
print(l < l2)  # True
```
Output
```
True
```

### 逻辑运算符
逻辑运算符and not or 跟比较运算符相似，返回结果都是布尔值（True/False）
### 拼接运算符
拼接运算符是 + ，常用来进行两个列表拼接
```python
l = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]  # 下标/索引：0开始
l2 = [2, 3, 4, 6]
print(l + l2)
```
### 重复操作符
重复操作符为 * ，后面常跟数字，表示将列表里面的元素重复复制几遍
```python
l2 = [2, 3, 4, 6]
print(l2*2)
```
### 成员关系操作符
成员关系操作符主要有 in和not in，用来判断元素是否在列表中，返回结果是布尔值
```python
l = [2, 3, 4, 6]
print(5 not in l)	#输出“5不在列表l中”这句话的真假
```
执行结果
```
True
```


## 列表的其他方法
```python
copy()#浅拷贝
count(project)#返回对象在列表中出现的次数
index(value,开始下标,结束下标)#元素出现的第一次下标位置，也可自定义范围
reverse()#原地翻转
sort (key=None reverse=False)#快速排序，默认从小到大排序，key:算法
len()#获取列表长度
```
### 二维列表
```python 
#变量[外层列表下标][内层列表的下标]
l = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
for i in l:
    for j in i:
        print(j)
```
Output
```
1
2
3
4
5
6
7
8
9
```
# 元组（tuple）
## 元组的创建及访问
>元组用（）的形式，是可迭代对象，是有序的，下标操作,支持切面操作 [:]<br>
同列表，不再赘述。
## 修改和删除
元组是不可变类型，不能修改，但是可以通过将元组转换成列表的形式进行修改和删除等操作，最后再将列表转换成元组，完成元组的修改和删除。<br>
例如：修改元组中的元素:
```python
t = (1, 2, 3, 4, 5)
l = list(t) #将元组转换成列表
print(l)    #输出列表
l[2] = 6    #列表指定元素的修改
print(l)    #输出新列表
t = tuple(l)    #列表转换成元组
print(t)
```
Output
```
[1, 2, 3, 4, 5]
[1, 2, 6, 4, 5]
(1, 2, 6, 4, 5)
```
## 元组的操作符
元组同样也有着操作符，方法跟列表的操作符是一样的,不再赘述。
## 元组的方法
对其操作先转换成列表再行操作，不再赘述。<br>
另外有两种方法新增：
```python
1. count(value)
#统计某个值出现的次数，value是指定的值

2. index(value,[start],[stop])
#返回value在元组中(start到stop间)出现的下标位置（第一次出现的下标）
```

# 字符串
在Python中，字符和字符串没有区别。可用\'    \'也可以是" "
## 字符串的特点
```python
1. 字符串不可变类型
2. 字符串是可迭代对象
3. 字符串支持索引和切片操作
4. 支持操作符;
		拼接：+
		重复操作符：*
		比较运算符： > < <= >= == !=
		逻辑运算符：not and or
		成员关系： in    not in		
```
## 字符串的方法
```python
capitalize()#把字符串的第一个字符改为大写，后面的小写
casefold()#把整个字符串都小写
encode()#编码 str--bytes (二进制字符串)
decode()#解码
count(sub,start, stop)#返回字符(sub)出现的次数，star: 开始下标，stop:结束下标
find(sub,start,stop)# 返回sub第一次出现的下标,查不到返回-1
index(sub, start, stop)#返回sub第一次出现的下标，查不到报错
upper()#将字符串转为大写
1ower()#将字符串转为小写
```
## 格式化输出
1. format 语法1：用数字占位（下标）
```python
"{0} 嘿嘿".format("Python")
a = 100
s = "{0}{1}{2} 嘿嘿"
s2 = s.format(a, "JAVA", "C++")
print(s2)
```
2.format 语法2：{} 占位
```python
a = 100
s = "{}{}{} 嘿嘿"
s2 = s.format(a, "JAVA", "C++", "C# ")
print(s2)
#Output
100JAVAC++ 嘿嘿
```
3.format 语法3：{} 占位用字母占位
```python
s = "{a}{b}{c} 嘿嘿"
s2 = s.format(b="JAVA", a="C++", c="C# ")
print(s2)
#Output:
C++JAVAC#  嘿嘿
```
s.format(s2)可理解为使用s格式化s2

4.%s

语法为 “%s”%（值） ，最常用的参数可以是任意值。
例子：
```python
for i in range(1, 10):
    for j in range(1, i + 1):
        print("%s * %s = %s" % (i, j, i * j), end="\t")
    print()

#Output:
1 * 1 = 1	
2 * 1 = 2	2 * 2 = 4	
3 * 1 = 3	3 * 2 = 6	3 * 3 = 9	
4 * 1 = 4	4 * 2 = 8	4 * 3 = 12	4 * 4 = 16	
5 * 1 = 5	5 * 2 = 10	5 * 3 = 15	5 * 4 = 20	5 * 5 = 25	
6 * 1 = 6	6 * 2 = 12	6 * 3 = 18	6 * 4 = 24	6 * 5 = 30	6 * 6 = 36	
7 * 1 = 7	7 * 2 = 14	7 * 3 = 21	7 * 4 = 28	7 * 5 = 35	7 * 6 = 42	7 * 7 = 49	
8 * 1 = 8	8 * 2 = 16	8 * 3 = 24	8 * 4 = 32	8 * 5 = 40	8 * 6 = 48	8 * 7 = 56	8 * 8 = 64	
9 * 1 = 9	9 * 2 = 18	9 * 3 = 27	9 * 4 = 36	9 * 5 = 45	9 * 6 = 54	9 * 7 = 63	9 * 8 = 72	9 * 9 = 81	
```

## 转义字符
```
1. “\n” ：换行符
2. “\'”:单引号
3. “\“”:双引号
4. "\\" : \
```
在这里值得注意的是 \ ，它有很多比较巧的运用，**比如可以实现代码换行**
```python
a = "sxsxsxsxsxsxsxs\
        xsxsxsxs\
        xsx"
print(a)

a = 1 + 2 + 3 \
    + 4
print(a)

#Output:
sxsxsxsxsxsxsxs        xsxsxsxs        xsx
10

```
# 字典（dict）
字典是用来存储数据的，字典中的数据以映射关系存储。
## 字典的特点
>1. 字典是Python中唯一的映射类型
    2. 字典是无序的
    3. 字典是可迭代对象
    4. 字典的构成:<br>
	    键：key
	    值：value
	    映射：键映射值
	    键-值：键值对，又叫 项 
## 创建字典
```
1. 直接创建
		语法： d = {} 	#空字典
		例如： d = {"name":"不良人","apple":"苹果"}
2. dict()
		例如：d = dict()	#空字典
3. dict(可迭代对象)
```
例子：
```python
d3 = dict([("one",1),("two",2)])
print(d3)
#Output：
{'one': 1, 'two': 2}
```
这就是一个元组，one是键，1是值， ‘one’ : 1 是键值对。
```
4. dict(**kwargs)
```
例子：
```python
d4 = dict(a=3, b=4)
print(d4)
#Output:
{'a': 3, 'b': 4}    
```
## 字典访问
1. 基本形式：<br>
    变量名[键名] #键所对应的值
2. 添加一个键值对<br>
		变量名[键名]=值
3. 修改一个键值对的值<br>
		变量名[键名]=值

Example
```python
d = {"name": "小黑"}
print(d["name"])
#Output:
小黑
```

## 字典的方法

