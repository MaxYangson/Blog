## 数据类型

python数据类型分为：可变数据类型、不可变数据类型

- ** 不可变数据（3 个）：**Number（数字）、bool类型、String（字符串）、Tuple（元组）；
- ** 可变数据（3 个）：**List（列表）、Dictionary（字典）、Set（集合）

可变不可变：在不改变变量引用的前提下，能否改变变量引用的数据

```python
age = 10
name = 'yang'  # 引号引起来的内容就是字符串，单引号和双引号是没有区别的
print(name)
print(age)

age = 18  # 修改变量
print(age)
print(type(age))  # type()函数获取数据类型
print(type(name))

res = 12.232
print(type(res))

c = True   # bool类型值需要首字母大写
print(c)
print(type(c))
```

    yang
    10
    18
    <class 'int'>
    <class 'str'>
    <class 'float'>
    True
    <class 'bool'>

## 输入输出

```
# 输出测试
print("hello")  # 基本输出

print('hello', 123)  # 一次输出两个内容，用逗号隔开
age = 20
print("我的年龄为：", age, "岁")

print()  # 可以不写内容，表示回车
print(1+232)  # 可以书写表达式

# 格式化输出，使用百分号%
name = "yang"
print("我是%s, 我很快乐" % name)  
a = 15
print('我的年龄是：%d岁' % a)
print('我的年龄是：%d岁' % a)
height = 170.5
print("我的身高：%fcm" % height)
print("我的身高：%.2fcm" % height)  # 保留两位小数

print("及格人数占比%d%%" % 50)   # 想要输出一个%，需要两个%

# 连续输出多个，百分号%()
print("我的名字叫%s, 年龄为%d" % (name, age))

# python3.6 支持f-string，占位符统一用{}，填充数据直接写在里面
print(f"我的名字叫{name}, 身高为{height}")

# print()函数默认换行，如果不想换行，可以使用end参数将其换为其他字符
print("hello", end="_*_")
# print("hello", end=" ")
print("world")

print("hello\nworld", end="  ") # 可以直接使用\n来换行
```

```
hello
hello 123
我的年龄为： 20 岁
233
我是yang, 我很快乐
我的年龄是：15岁
我的身高：170.500000cm
我的身高：170.50cm
及格人数占比50%
我的名字叫yang, 年龄为18
我的名字叫yang, 身高为170.5
hello_*_world
hello
world  
```

```
# 输入测试——从键盘获取内容，存入计算机程序中，使用input函数
# input("用于给用户的提示信息")， 得到用户输入内容，遇到回车表示结束，得到的数据都是字符串类型
# input() 里面可以不写内容，但是不够友好
password = input("请输入用户密码：")
print(f"密码为：{password}")
print(type(password))

# 可以输入一个整数/浮点数，使用eval()函数转化为整数/浮点数类型，或者使用强制转化
a = input("请输入一个整数：")
b = input("再输入一个整数：")
# print(f"输入的整数为：{eval(a) + eval(b)}")
print(f"输入的整数为：{int(a) + int(b)}")
```

```
请输入用户密码：yans12
密码为：yans12
<class 'str'>
请输入一个整数：12
再输入一个整数：23
输入的整数为：35
```

## 数据类型转换[掌握]

```
# 数据类型转换
# 1. 浮点型/整数类型字符串转化为整数类型，使用强制转换
pi = 3.14
num = int(pi)
print("num =", num)
print(type(num))

str1 = '10'
num2 = int(str1)
print(type(num2))

# 2. 整数/浮点型字符串转化为浮点型，使用强制转换
num3 = float(10)
print(type(num3))

num4 = float("3.14")
print("num4 =", num4)
print(type(num4))

# eval() 还原原来的数据类型，去掉引号，常用来将字符串转为其他类型
print(type(eval("2.1")))
print(type(eval("10")))
print("2.1 + 3.56 =", eval("2.1") + eval("3.56"))# 数据类型转换

# str()将整形、浮点型转化为字符串型
s = str(123)
print(type(s))
```

```
num = 3
<class 'int'>
<class 'int'>
<class 'float'>
num4 = 3.14
<class 'float'>
<class 'float'>
<class 'int'>
2.1 + 3.56 = 5.66
<class 'str'>
```

## 运算符

### 算术运算符

```
+ - * / 
// 整除(求商)
% 取余数
** 指数,幂运算
() 可以改变优先级
```

### 赋值运算符

```python
= 将等号右边的结果赋值给等号左边的变量
等号左边,必须是变量,不能是具体的数字
```

### 复合赋值运算符

```python
+=  
c += a  ===> c = c + a
```

### 比较运算符

> 比较运算符的结果是 bool 类型, 即 True,或者是 False

```python
== 判断是否相等, 相等是 True. 不相等是 False
!= 判断是否不相等, 不相等是 True, 相等 False
>
<
>=
<=
```

### 逻辑运算符

> 逻辑运算符可以连接连个表达式, 两个表达式共同的结果决定最终的结果是 True,还是 False

```python
and  逻辑与, 连接的两个条件都必须为 True,结果为 True,  一假为假
    如果第一个条件为 False,就不会再判断第二个条件
or   逻辑或, 连接的两个条件都为 False,结果为 False,    一真为真
    如果第一个条件为 True,第二个条件就不会再判断了
not  逻辑非, 取反,原来是 True,变为 False,原来是 False,变为 True
```

PEP 8 规范（非强制）

1. 单行注释#后边应该有一个空格
2. 代码文件的最后一行是空行

## 判断和循环

```
if 判断条件:
    判断条件为 True,会执行的代码
    判断条件为 True,会执行的代码
    ...

顶格书写的代码,代表和 if 判断没有关系
在 python 中使用缩进,代替代码的层级关系,
在 if 语句的缩进内,属于 if 语句的代码块(多行代码的意思)

if else 结构
if 判断条件:
    判断条件为 True,会执行的代码
    判断条件为 True,会执行的代码
    ...
else:
    判断条件为 False, 会执行的代码
    判断条件为 False, 会执行的代码

if elif 结构
if     判断条件1:
    判断条件1成立,执行的代码
elif 判断条件2:
    判断条件1不成立,判断条件2 成立,会执行的代码
else:
    判断条件1和判断条件2都不成立,执行的代码

--------
if 判断条件1:
    判断条件1成立执行的代码

if 判断条件2:
    判断条件2 成立执行的代码
```

```python
#2.条件判断if
if 1 == 2: # 如果 if 跟随的条件为 假 那么不执行属于if 的语句,然后寻找 else
    print("假的")
else: # 寻找到 else 之后 执行属于else中的语句
    print("1==2是假的")
```

    1==2是假的

三目运算——if else 结构变形

```
if 判断条件1:
    表达式1
else:
    表达式2

判断条件成立,执行表达式 1, 条件不成立,执行表达式 2

变量 = 表达式1 if 判断条件 else 表达式2  # 推荐用于扁平化代码

变量最终存储的结构是: 
    判断条件成立,表达式1的值, 
    条件不成立,表达式2的值
```

```
# 三目运算
a = int(input("请输入一个整数："))
b = int(input("在输入一个整数："))
res = a-b if a > b else b-a
# res = (a-b) if a > b else (b-a)  # 一般用括号括起来，条理清楚
print("绝对值为：", res)
```

for循环

```python
for 变量x in 字符串/列表/元组/range():
    代码
for 循环也称为 for 遍历,会将字符串/列表中的元素全部取到，复制到变量x中   
```

    # for循环
    for c in "hello":
        print(c, end=" ")  # 一次循环输出字符串中的一个字符
    print()
    for i in range(5):  # 生成[0, 5)的序列
        print(i, end=" ")
    print()
    for i in range(2, 5):    # 生成[2, 5)的序列
        print(i, end=" ")
    print()
    for i in range(1, 10, 2): # 生成[1， 10)，且步长为2的序列
        print(i, end=" ")
    print()
    list = [2, -1, 23, 90, -233]
    for x in list:
        print(x, end=" ")   # 遍历列表中的元素
    print()

```
h e l l o 
0 1 2 3 4 
2 3 4 
1 3 5 7 9 
2 -1 23 90 -233 
```

循环else结构

```
for x in xx:
    if xxx:
        xx  # if 判断条件成立会执行
    else:
        xxx  # if 判断条件不成立,会执行
else:
    xxx  # for 循环代码运行结束,但是不是被 break 终止的时候会执行

需求:
    有一个字符串 'hello python', 想要判断这个字符串中有没有包含 p 这个字符,如果包含,就输出, 包含 p, 如果没有 p ,就输出,不包含
```

```
str = "hello python"
for c in str:
    if c == 'p':
        print("包含p字符")
        break
else:
    print("str中不包含p字符")
```

```
包含p字符
```

while循环

```
while 判断条件:
    判断条件成立,执行的代码
    判断条件成立,执行的代码

不在 while 的缩进内,代表和循环没有关系 

while True:  # 无限循环
    代码
```

```python
sum = 0
n = 99
while n > 0:
    sum = sum + n
    n = n - 1  # 没有n++或者n--等语法
print(sum)
```

    4950

break、continue、pass

```python
#break语句可以跳出 for 和 while 的循环体
n = 1
while n <= 100:
    if n > 10:
        break
    print(n)
    n += 1
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
    10

```python
#continue语句跳过当前循环，直接进行下一轮循环
n = 1
while n < 10:
    n = n + 1
    if n % 2 == 0:
        continue
    print(n)
```

    3
    5
    7
    9

```python
 #pass是空语句，一般用做占位语句，不做任何事情
 for letter in 'Room':  #也可以把字符串看成一个数组，使用for循环
    if letter == 'o':
        pass  #常用作定义函数的时候，不知道写啥，写个pass
        print('pass')
    print(letter)
```

    R
    pass
    o
    pass
    o
    m

# Python进阶

* **深度学习**离不开数学分析（高等数学）、线性代数、概率论等知识，**更离不开以编程为核心的动手实践。**
* 无论是在机器学习还是深度学习中，**Python** 已经成为主导性的编程语言。而且，现在许多主流的深度学习框架都提供Python接口，Python被用于数据预处理、定义网络模型、执行训练过程、数据可视化等
* **熟悉 Python 的基础语法，并掌握 NumPy，Pandas 及其他基础工具模块的使用对深度学习实践是非常重要的！**

## Python数据结构

数字、字符串、列表、元组、字典

### 数字

Python Number 数据类型用于存储数值。

Python Number 数据类型用于存储数值，包括整型int、长整型long、浮点型float、复数complex。

```python
#5.数据类型---Number(数字)
#Python支持int, float, complex三种不同的数字类型
a = 3
b = 3.14
c = 3 + 4j  #j也可以用于变量命名，也可以用于复数中的虚部
print(type(a), type(b), type(c))  #type函数输出变量类型
```

    <class 'int'> <class 'float'> <class 'complex'>

**（1）Python math 模块**：Python 中数学运算常用的函数基本都在 math 模块

```python
import math

print(math.ceil(4.1))   #返回数字的上入整数

print(math.floor(4.9))  #返回数字的下舍整数

print(math.fabs(-10))   #返回数字的绝对值

print(math.sqrt(9))     #返回数字的平方根

print(math.exp(1))      #返回e的x次幂
```

    5
    4
    10.0
    3.0
    2.718281828459045

**（2）Python随机数**

首先import random，使用random()方法即可随机生成一个[0,1)范围内的实数

```python
import random
ran = random.random()
print(ran)
```

    0.9693881604049188

调用 random.random() 生成随机数时，每一次生成的数都是随机的。但是，当预先使用 random.seed(x) 设定好种子之后，其中的 x 可以是任意数字，此时使用 random() 生成的随机数将会是同一个。

```python
print ("------- 设置种子 seed -------")
random.seed(10)
print ("Random number with seed 10 : ", random.random())

# 生成同一个随机数
random.seed(10)
print ("Random number with seed 10 : ", random.random())
```

    ------- 设置种子 seed -------
    Random number with seed 10 :  0.5714025946899135
    Random number with seed 10 :  0.5714025946899135

randint()生成一个随机整数

```python
ran = random.randint(1,20)  # 生成一个随机数
print(ran)
```

    14

### 字符串

```python
#5.数据类型---String（字符串）
#支持字符串拼接、截取等多种运算
a = "Hello"
b = "Python"
print("a + b 输出结果：", a + b)  # 字符串拼接
print("a[1:4] 输出结果：", a[1:4])   #支持切片截取，左闭右开
```

获取字符串长度：len(str)

```
print(len(my_str))
```

字符串连接：+

```python
a = "Hello "
b = "World "
print(a + b)
```

    Hello World 

重复输出字符串：*

```python
print(a * 3)
```

    Hello Hello Hello 

通过索引获取字符串中字符[]

```python
print(a[0])
```

    H

字符串截取[:]  牢记：左闭右开

```python
print(a[1:4])
```

    ell

判断字符串中是否包含给定的字符或者字符串: **in, not in**

```python
a = 'hello'
print('e' in a)
print('e' not in a)
print('he' in a)
```

    True
    False
    True

查找方法find、rfind、index、rindex

```
# find, rfind
# 使用：my_str.find(sub_str, start, end)

my_str = "hello world itcast and itcastcpp"
print(my_str.find("hello"))  # 0

# 从下标为3的位置开始查找
print(my_str.find("hello", 3)) # 没有找到，返回-1
print(my_str.find("itcast", 3))  # 12
print(my_str.find("itcast", 20))  # 23 , 从下标20位置开始查找

# rfind()  right find() 从右边位置开始查找
print(my_str.find("itcast"))   # 23

#index、rindex和find, rfind使用方法几乎一样，只是如果没有查到，不会返回-1，会直接报错
# 使用：my_str.index(sub_str, start, end)
```

统计出现次数count()

```
my_str = "hello world itcast and itcastcpp"
print(my_str.count("aaaa"))  # 0
print(my_str.count("hello"))  # 1
print(my_str.count("itcast"))  # 2
```

字符串替换方法 replace

```
# my_str.replace(old_str, new_str, count)
# count 是替换次数，默认全部替换
# 返回值是替换后的字符串， 得到一个新的字符串，不会改变原来的字符串
my_str = "hello world itcast and itcastcpp"
my_str1 = my_str.replace("itcast", "itheima")
print(my_str1)
print(my_str.replace("itcast", "itheima", 1))  # 只替换一次
```

字符串分隔 split()

```
# my_str.split(sub_str, count)
# sub_str 表示按照什么切割字符串， 不写默认按照空格切割
# count 表示切割的次数， 默认全部切割
# 返回值是一个字符串列表
my_str = "hello world itcast and itcastcpp"
res = my_str.split()
print(res)
res2 = my_str.split("it")
print(res2)
```

```
['hello', 'world', 'itcast', 'and', 'itcastcpp']
['hello world ', 'cast and ', 'castcpp']
```

字符串连接 join():以字符作为分隔符，将字符串中所有的元素合并为一个新的字符串

```python
new_str = '-'.join('Hello')
print(new_str)
```

    H-e-l-l-o

字符串单引号、双引号、三引号

```python
print('Hello World!')
print("Hello World!")
```

    Hello World!
    Hello World!

转义字符 \

```python
print("The \t is a tab")
print('I\'m going to the movies')
```

    The      is a tab
    I'm going to the movies

三引号让程序员从引号和特殊字符串的泥潭里面解脱出来，自始至终保持一小块字符串的格式是所谓的WYSIWYG（**所见即所得**）格式的。

```python
print('''I'm going to the movies''')

html = '''
<HTML><HEAD><TITLE>
Friends CGI Demo</TITLE></HEAD>
<BODY><H3>ERROR</H3>
<B>%s</B><P>
<FORM><INPUT TYPE=button VALUE=Back
ONCLICK="window.history.back()"></FORM>
</BODY></HTML>
'''
print(html)
```

    I'm going to the movies
    
    <HTML><HEAD><TITLE>
    Friends CGI Demo</TITLE></HEAD>
    <BODY><H3>ERROR</H3>
    <B>%s</B><P>
    <FORM><INPUT TYPE=button VALUE=Back
    ONCLICK="window.history.back()"></FORM>
    </BODY></HTML>

### 列表

作用：类似其他语言中的数组

声明一个列表，并通过下标或索引获取元素

![](https://ai-studio-static-online.cdn.bcebos.com/41840090b1c14c4daa704f9565fd5ba663d08a7d383444fa98c5c3d31f7e4c1d)

```python
#数据类型---List（列表），也就是可变数组
#列表是写在方括号 [] 之间、用逗号分隔开的元素列表。元素可以不同类型
#声明一个列表
names = ['jack','tom','tonney','superman','jay']

#通过下标或索引获取元素
#列表索引值以 0 为开始值，-1 为从末尾的开始位置。-1，-2，... 表示从后往前遍历
print(names[0])
print(names[1])
#获取最后一个元素
print(names[-1])
print(names[len(names)-1])
#获取第一个元素
print(names[-5])
```

```python
#遍历列表，获取元素
for name in names:
    print(name)
```

    jack
    tom
    tonney
    superman
    jay

```python
#查询names里面有没有superman
for name in names:
    if name == 'superman':
        print('有超人')
        break
else:
    print('没有超人')

#更简单的方法,来查询names里有没有superman，列表中也可以使用in， not in
if 'superman' in names:
    print('有超人')
else:
    print('有超人')
```

    有超人
    有超人

列表元素添加

```python
#声明一个空列表
girls = []

#append(),末尾追加
girls.append('杨超越')
print(girls)
```

    ['杨超越']

```python
#extend(),一次添加多个。把一个列表添加到另一个列表 ，列表合并。
models = ['刘雯','奚梦瑶']
girls.extend(models)
# girls = girls + models  也可以使用加号+实现列表的拼接
print(girls)
```

    ['杨超越', '刘雯', '奚梦瑶']

```python
#insert():指定位置添加
girls.insert(1,'虞书欣')
print(girls)
```

    ['杨超越', '虞书欣', '刘雯', '奚梦瑶']

列表元素修改,通过下标找到元素，然后用=赋值

```python
fruits = ['apple','pear','香蕉','pineapple','草莓']
print(fruits)

fruits[-1] = 'strawberry'
print(fruits)
```

    ['apple', 'pear', '香蕉', 'pineapple', '草莓']
    ['apple', 'pear', '香蕉', 'pineapple', 'strawberry']

```python
'''
将fruits列表中的‘香蕉’替换为‘banana’
'''

for fruit in fruits:  
    if '香蕉' in fruit:
        fruit = 'banana'  #能够实现修改效果，因为变量复制得到的是引用地址
print(fruits)

for i in range(len(fruits)):
    if '香蕉' in fruits[i]:
        fruits[i] = 'banana'
        break
print(fruits)
```

    ['apple', 'pear', '香蕉', 'pineapple', 'strawberry']
    ['apple', 'pear', 'banana', 'pineapple', 'strawberry']

列表元素删除——del、remove、pop

```python
words = ['cat','hello','pen','pencil','ruler']
del words[1]
print(words)
```

    ['cat', 'pen', 'pencil', 'ruler']

```python
words = ['cat','hello','pen','pencil','ruler']
words.remove('cat')
print(words)
```

    ['hello', 'pen', 'pencil', 'ruler']

```python
words = ['cat','hello','pen','pencil','ruler']
words.pop(1)
print(words)
```

    ['cat', 'pen', 'pencil', 'ruler']

列表切片

* 在Python中处理列表的部分元素，称之为切片。

* 创建切片，可指定要使用的第一个元素和最后一个元素的索引。注意：左闭右开

* 将截取的结果再次存放在一个列表中，所以还是返回列表

![](https://ai-studio-static-online.cdn.bcebos.com/3e1286d72f144f378afd29d8fc720e1430919c5b0c0d413b9ca1539f3ae087a0)

```python
animals = ['cat','dog','tiger','snake','mouse','bird']

print(animals[2:5])

print(animals[-1:])

print(animals[-3:-1])

print(animals[-5:-1:2])  #最后一个2表示步长为2

print(animals[::2])
```

    ['tiger', 'snake', 'mouse']
    ['bird']
    ['snake', 'mouse']
    ['dog', 'snake']
    ['cat', 'tiger', 'mouse']

列表排序、逆置

```python
# 使用sort成员函数，直接在原列表中排序
my_list = [16, 11, 3, 8, 12, 2, 14, 5, 20, 13]
my_list.sort()  # 默认升序
print(my_list)
my_list.sort(reverse=True)  # 降序
print(my_list)

my_list = [16, 11, 3, 8, 12, 2, 14, 5, 20, 13]
# 使用公有函数sorted(列表)， 不会在原列表中排序，而是生成一个新列表
#默认升序
new_list = sorted(random_list)
print(new_list)
#降序
new_list = sorted(random_list,reverse =True)
print(new_list)

# 逆置
# 使用切片方式，得到一个新的列表
my_list = ['a', 'b', 'c', 'd', 'e']
my_list2 = my_list[::-1]
print(my_list)
print(my_list2)
# 使用成员函数reverse, 在原列表中直接逆置
my_list.reverse()
print(my_list)
```

    [2, 3, 5, 8, 11, 12, 13, 14, 16, 20]
    [20, 16, 14, 13, 12, 11, 8, 5, 3, 2]
    ['a', 'b', 'c', 'd', 'e']
    ['e', 'd', 'c', 'b', 'a']
    ['e', 'd', 'c', 'b', 'a']

 列表嵌套——形成多维数组

```
city_schools = [
    ["北京大学", "清华大学"],
    ["南开大学", "天津大学", "天津财经大学"],
    ["山东大学", "中国海洋大学"]
]
print(city_schools[1])   # ["南开大学", "天津大学", "天津财经大学"]
print(city_schools[1][0])  # 南开大学
print(city_schools[1][0][1])  # 开

# 遍历
for schools in city_schools:
    for name in schools:
        print(name, end=" ")
    print()
```

列表推导式

列表推导式，为了快速生成一个列表

```python
1， 变量 = [生成数据的规则 for 临时变量 in xxx]

my_list = [i for i in range(5)]
print(my_list)  # [0, 1, 2, 3, 4]

my_list = ['hello' for i in range(5)]
print(my_list)  # ['hello', 'hello', 'hello', 'hello', 'hello']

my_list1 = [f'num:{i}' for i in my_list]
print(my_list1)  # ['num:hello', 'num:hello', 'num:hello', 'num:hello', 'num:hello']

my_list2 = [i+i for i in range(5)]
print(my_list2)  # [0, 2, 4, 6, 8]

2, 变量 = [生成数据的规则 for 临时变量 in xxx if xxx]
# 每循环一次并且if条件为True，生成一个数据
my_list2 = [i for i in range(5) if i%2 == 0]
print(my_list2)  # [0, 2, 4]

3, 变量 = [生成数据的规则 for 临时变量 in xxx for 另一个临时变量 in xxx]
# 第二个for循环，循环一次生成一个数据，相当于两重循环
my_list2 = [(i, j) for i in range(3) for j in range(3)]
print(my_list2)  
# [(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2), (2, 0), (2, 1), (2, 2)]
```

### 元组

与列表类似，但是元组中的内容不可修改

```python
#5.数据类型---Tuple（元组）
#tuple与list类似，不同之处在于tuple的元素不能修改。tuple写在小括号里，元素之间用逗号隔开。
#元组的元素不可变，但如果包含可变对象，如list，则列表中的元素可以变
t1 = ('abcd', 786 , 2.23, 'runoob', 70.2)   #使用小括号进行初始化赋值
t2 = (1, )
t3 = ('a', 'b', ['A', 'B'])  #Turple中的数组元素可以修改内容，但是普通元素内容不让修改
t3[2][0] = 'X'
print(t3)
# t3[1] = 'x'   # err! 不支持修改
```

    ('a', 'b', ['X', 'B'])

```python
tuple1 = ()  # 定义空元组，没有意义
print(type(tuple1))
```

    <class 'tuple'>

注意：元组中只有一个元素时，需要在后面加逗号！， 否则为里面的类型

```python
tuple2 = ('hello')
print(type(tuple2))
```

    <class 'str'>

```python
tuple3 = ('hello',)
print(type(tuple3))
```

    <class 'tuple'>

元组不能修改，所以不存在往元组里加入元素。

——可以使用列表来初始化

```python
import random

random_list = []
for i in range(10):
    ran = random.randint(1,20)
    random_list.append(ran)
print(random_list)

random_tuple = tuple(random_list)   #使用列表初始化，强制转化
print(random_tuple)
```

    [14, 10, 9, 15, 6, 10, 12, 5, 15, 8]
    (14, 10, 9, 15, 6, 10, 12, 5, 15, 8)

<br/>

元组访问——使用下标访问、切片截取

```python
print(random_tuple)
print(random_tuple[0])
print(random_tuple[-1])
print(random_tuple[1:-3])
print(random_tuple[::-1])  #步长为-1表示，从后往前取值
```

    (14, 10, 9, 15, 6, 10, 12, 5, 15, 8)
    14
    8
    (10, 9, 15, 6, 10, 12)
    (8, 15, 5, 12, 10, 6, 15, 9, 10, 14)

元组的修改：

```python
t1 = (1,2,3)+(4,5)  # 元组拼接，得到新元组
print(t1)
```

    (1, 2, 3, 4, 5)

```python
t2 = (1,2) * 2  # 元组可以使用乘法*
print(t2)
```

    (1, 2, 1, 2)

元组的一些函数：

```python
print(max(random_tuple))  # 最大值
print(min(random_tuple))  # 最小值
print(sum(random_tuple))  # 求和
print(len(random_tuple))  # 元组长度
#统计元组中4的个数
print(random_tuple.count(4))
#元组中4所对应的下标，如果不存在，则会报错
print(random_tuple.index(4))
#判断元组中是否存在1这个元素
print(4 in random_tuple)
#返回元组中4所对应的下标,不会报错
if(4 in random_tuple):
    print(random_tuple.index(4))
```

元组的拆包与装包

```python
# 装包：多个元素装包为一个元组
a = 1, 2, 3  
print(type(a))   # <class 'tuple'>
print(a)

# 拆包：将容器（字符串、列表、元组、字典）中的数据分别给到多个变量，注意变量个数和容器中元素个数相同
b = [23,  2, -1]
st = "hel"
x, y, z = b
print(x, y, z)
c1, c2, c3 = st
print(c1, c2, c3)
my_dict = {"name": "yang", "age": 23}
e, f = my_dict  # key值赋给e， f
print(e, f)

# 拆包、装包实现快速交换
a = 12
b = 34
a, b = b, a
print(a, b)
```

```python
#当元组中元素个数与变量个数不一致时

#定义一个元组，包含5个元素
t4 = (1,2,3,4,5)

#将t4[0],t4[1]分别赋值给a,b;其余的元素装包后变成一个列表list赋值给c
a,b,*c = t4

print(a,b,c)
print(c)
print(*c)
```

    1 2 [3, 4, 5]
    [3, 4, 5]
    3 4 5

### 字典

```python
#5.数据类型---dict（字典）
#字典是无序的对象集合，使用键-值（key-value）存储，具有极快的查找速度。
#键(key)必须使用不可变类型。
#同一个字典中，键(key)必须是唯一的。
```

```python
#定义一个空字典
dict1 = {}
d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}   #使用大括号赋值初始化
print(d['Michael'])   # 95
dict2 = {'name':'杨超越','weight':45,'age':25}
```

```python
#成员是元组的list可以转成字典，但前提是列表中元素都要成对出现
dict3 = dict([('name','杨超越'),('weight',45)])  # 使用字典构造函数
print(dict3)
```

```python
dict4 = {}
dict4['name'] = '虞书欣'
dict4['weight'] = 43
print(dict4)
```

```python
dict4['weight'] = 44
print(dict4)
```

```python
#字典里的函数 items()  keys() values()

dict5 = {'杨超越':165,'虞书欣':166,'上官喜爱':164}
print(dict5.items())

#遍历
for key,value in dict5.items():
    if value > 165:
        print(key)

for item in  dict5.items():
    print(item[0], item[1])

for key in dict5.keys():
    print(dict5[key])
```

```python
#values() 取出字典中所有的值,保存到列表中
results = dict5.values()
print(results)

#求小姐姐的平均身高
heights = dict5.values()
print(heights)
total = sum(heights)
avg = total/len(heights)
print(avg)
```

```python
#keys()取出字典中所有的key，保存在列表中
names = dict5.keys()
print(names)
```

```python
#使用key下标访问，get函数访问
print(dict5['赵小棠'])       

print(dict5.get('赵小棠'))

print(dict5.get('赵小棠',170)) #如果能够取到值，则返回字典中的值，否则返回默认值170
```

```python
# 删除元素——del， pop
dict6 = {'杨超越':165,'虞书欣':166,'上官喜爱':164}
del dict6['杨超越']
print(dict6)

result = dict6.pop('虞书欣')
print(result)
print(dict6)
```

### 集合

```python
#5.数据类型---set（集合）
# set是可变类型，可以添加、删除操作
# set是无序的，重复元素在set中自动被过滤。
# set不支持下标操作

s = {1, 2}  # set的初始化使用大括号{}包起来，表示字典dict中没有value，全是key
print(type(s))  # <class 'set'>
s1 = set([1, 1, 2, 2, 3, 3])   # 也可以使用set构造函数，把列表转为集合set
print(type(s1))  # <class 'set'>
s = {}  #定义空字典，而不是集合，这里需要注意
print(type(s))  # <class 'dict'>
```

```
# 常用函数：添加add、删除remove/pop、清空clear
s = {1, 'yang'}
print(s)
# 添加
s.add(100)
s.add(34.73)
print(s)

# 删除
s.remove(100)
print(s)
# s.pop()  #这里的pop调用，实际上是随机删除，不常用
# print(s)

# 修改——实际上就是删除，再添加
s.remove("yang")
s.add("yangshun")
print(s)

# 清空
s.clear()
print(s)
```

```
{'yang', 1}
{'yang', 1, 34.73, 100}
{'yang', 1, 34.73}
{1, 34.73, 'yangshun'}
set()
```

```
# 集合、列表、元组三者可以相互转化
my_list = [12, "xyz", 900, 3.14]
new_tup = tuple(set(my_list))
print(new_tup, type(new_tup)) 

# (900, 3.14, 12, 'xyz') <class 'tuple'>
```

## 公共方法总结

- `+`  支持 字符串、列表、元组进行操作， 得到一个新的容器

- `* 整数`  复制， 支持 字符串、列表、元组进行操作， 得到一个新的容器

- `in/not in`  判断存在或者是不存在，支持 字符串、列表、元组、字典进行操作， 注意： ==如果是字典的话，判断的是 key 值是否存在或不存在==

- `max/min` 对于字典来说，得到字典的 key值的最大值，最小值（按照字典序）

## 函数

定义和调用

```python
# def 函数名(参数1， 参数2，。。)： # 函数名要遵循标志符的规则，见名知意
#    函数代码

def add(a, b):
    return a + b

print("函数调用前：")
res = add(23, 90)
print(res)
print("函数调用结束：")
```

函数返回值——不需要在函数中定义，直接使用return返回即可

```python
def add(a, b):
    c = a + b
    return c
    print(f"求和的结果为{c}")  # 遇到return就已经返回了，这段代码不会执行

res = add(100, 200)
print(f"求和的结果为{res}")

# 返回多个数据值—默认组成元组进行返回的
def func(a, b):
    c = a + b
    d = a - b
    return c, d

res = func(10, 20)
print(f"a+b结果是{res[0]}， a-b结果是{res[1]}")

# 不写return/return后面不写数据，默认返回None
1. return 关键字后边可以不写数据值， 默认返回 None
def func():
    xxx
    return   # 返回 None，终止函数的运行的

2. 函数可以不写 return，返回值默认是 None
def func():
    xxx
    pass
```

函数传参的两种形式[掌握]

```
def func(a, b, c):
    print(f"a: {a}")
    print(f"a: {b}")
    print(f"a: {c}")
# 位置传参， 按照形参位置顺序将实参值传递给行参
func(1, 2, 3)
# 关键字传参，指定实参给到哪个形参，注意：关键字必须是函数的形参名
func(a=10, b=20, c=30)
func(c=10, a=20, b=30)
# 混合使用，必须先写位置传参，再写关键字传参
func(10, b=20, c=30)
func(a=10, 20, 30) # 报错
```

缺省参数：

```
def func(a, b, c=10):
    print(f"a: {a}")
    print(f"a: {b}")
    print(f"a: {c}")

func(1, 2) # 默认c=10
func(1, 2, 3) # 将3传递给c形参
```

不定长参数：

```python
注意点: 函数定义中的 args 和 kwargs可以是任意的形参变量,不过习惯使用 args 和 kwargs.
def func(*args, **kwargs):
    print(args)
    print(kwargs)
# 形参前面加上一个*，该形参为不定长元组形参，可以接受所有的位置实参，类型是元组
# 形参前面加上两个*，该形参为不定长字典形参，可以接受所有的关键字实参，类型是字典
func(1, 2, 3, 4, 5)
func(a=1, b=2, c=3, d=4)
func(1, 2, 3, a=4, b=5, c=6)
```

函数形参的完整格式

```python
# 顺序：普通形参  缺省形参  不定长元组形参  不定长字典形参
def func3(a, *args, b=1, **kwargs):  # 或者不定长元组形参放在缺省形参前面也行
    pass
```

## 匿名函数

使用 `lambda` 关键字定义的函数就是匿名函数

一般就只有一条语句

```python
lambda 参数列表：表达式
```

1. 无参数无返回值
   
   ```python
   def 函数名()：
     函数代码
   
   lambda:函数代码
   ```

2. 无参数有返回值
   
   ```python
   def 函数名()：
       return 1 + 2
   
   lambda: 1 + 2
   ```

3. 有参数无返回值
   
   ```python
   def 函数名(a, b):
     print(a, b)
   
   lambda a, b: print(a, b)
   ```

4. 有参数有返回值
   
   ```python
   def 函数名(a, b):
     return a + b
   
   lambda a, b: a + b
   ```

```
匿名函数的应用场景 

```python
# -- 作为函数的参数使用
def my_calc(a, b, func):
 print("其他函数代码")
 num = func(a, b)
 print(num)
def add(a, b):
 return a+b

my_calc(10, 20, add)
my_calc(10, 20, lambda a, b: a-b)
my_calc(10, 20, lambda a, b: a*b)
my_calc(10, 20, lambda a, b: a/b)

-- 列表/字典中自定义排序
list1 = [{'name': 'd', 'age': 19}, {'name': 'b', 'age': 16}, {'name': 'a', 'age': 16}, {'name': 'c', 'age': 20}]
list1.sort() # 没有传入参数，程序报错
## sort(self, key, reverse)   这里的key形参需要传递一个函数指定排序规则，列表中的数据根据什么排序

# 匿名函数的形参是列表中每一个元素
list1.sort(lambda x: x['name'])  # 根据name大小进行排序
list1.sort(lambda x: x['age'])   # 根据age大小进行排序

# list1.sort(lambda x: len(x))   # 可以根据字符串长度进行排序（列表如果是一个字符串列表的话）
```

## 局部变量和全局变量

```
局部变量的作用域（作用范围）： 当前函数的内部
局部变量的生存周期：在函数调用的时候被创建，函数调用结束之后，被销毁（删除）
局部变量只能在当前函数的内部使用，不能在函数的外部使用。

全局变量： 就是在函数外部定义的变量。
在函数内部可以访问全局变量的值，如果想要修改全局变量的值，需要使用 global 关键字声明

g_num = 100  #定义全局变量
def func1():  # 能在函数内部直接访问全局变量
    print(g_num) 

def func2():   # 不能在函数内部直接修改全局变量的值，需要使用global关键字声明这个变量为全局变量
    # g_num = 200  # 这里不是修改全局变量的值，而是定义了一个同名的局部变量
    global g_num
    g_num = 300  # 这里才是修改了全局变量的值

func1()
func2()
```

## 拆包组包

```python
注意点: 容器中元素数据的个数需要和变量的个数保持一致.

# 组包，将多个数据值组成元组，给到一个变量
a = 1, 2, 3
print(a) # (1, 2, 3)

# 拆包：将容器的数据分别给到多个变量，注意：数据的个数要和变量的个数保持一致
b, c, d = a
print(b, c, d)

# 组包拆包实现变量交换
a, b = b, a
print(a, b)
```

## 引用【理解】

```python
# 可以使用id()查看变量的引用，可以将id值认为是内存地址的别名
# python中数据值的传递的是引用
# 赋值运算符可以改变变量的引用

a = 10 # 本质是将数据10所在的内存的引用地址保存到变量a中
b = a  #将变量a中保存的引用地址给到b
print(a, b)      # 10 10
print(id(a), id(b)) # 140732963607872 140732963607872

a = 20   # 变量a保存的引用地址发生变化
print(id(a), id(b))  # 140732963608192 140732963607872

# 列表的引用
my_list = [1, 2, 3]  # 将列表的引用地址保存到my_list中，内部：列表中各个元素保存的也是1,2,3数据所在的引用地址
my_list1 = my_list   # 将my_list中保存的引用地址赋值给my_list1
print(my_list, id(my_list))
print(my_list1, id(my_list1))

my_list.append(4)    # 将数据4的引用地址保存在列表中
print(my_list, id(my_list))
print(my_list1, id(my_list1))

my_list[2] = 5    # 修改列表中下标为2的元素，使其保存数据5的引用
print(my_list, id(my_list))
print(my_list1, id(my_list1))

# 引用用作函数参数
# 函数传参传递的也是引用地址
my_list = [1, 2, 3]  # 全局变量
def func1(a):
    a.append(4)
def func2():
    my_list.append(5)  # 为啥不加global,因为没有修改my_list中存的引用值
def func3():
    global my_list
    my_list = [1, 2, 5]   # 修改全局变量的值
def func4(a):
    # += 对于列表来说，类似于列表的extend方法，不会修改变量的引用地址
    a += a  # 对于不可变类型来说，修改了变量a的引用

func1(my_list)  # my_list = [1, 2, 3, 4]
func2()      #  my_list = [1, 2, 3, 4, 5]
func3()     #   my_list = [1, 2, 5]
print(my_list)   # my_list = [1, 2, 5]

b = 10   # 不可变类型
func4(b)  # 相当于值传递
print(b)  # 10

func4(my_list)  # 可变类型
print(my_list)  # my_list = [1, 2, 5, 1, 2, 5]
```

## 文件操作

文件在硬盘中存储的格式永远是二进制，但是有可能是以不同的编码格式存储的二进制数据

### 打开文件open

```
# 打开文件，把文件从硬盘加载到内存
# open(file, mode, encoding)
# file 要操作的文件路径和名字，类型为string，默认在项目根路径下
# mode 文件打开的方式， r表示只读，w表示只写，a表示追加，类型为string
# encoding 表示文件的编码格式，常见两种：gbk和utf-8
# 返回值为文件对象，后续所有文件操作都通过这个对象进行操作

# "w"模式打开文件时，文件不存在会自动创建文件，文件存在会自动覆盖清空原文件
f = open("1.txt", "r")  # 1，打开文件, 推荐每次都写上编码格式
buf = f.read()  # 2. 读取文件内容到buf缓存中，默认是读取所有数据
print(buf)
f.close()  # 3. 读取完需要关闭文件
```

### 读文件-read/readline/readlines

```
# 按行读取
f = open("3.txt", "r", encoding="utf-8")
# buf = f.readline()  # 一次读取一行的内容，返回值是读取到的内容字符串+尾部的换行\n（str)
# print(buf)
# buf = f.readline()  # 下次读取，接着上次的读取位置
# print(buf)
buf = f.readlines()  # 按行读取，一次读取所有行，返回值是包含所有行字符串的列表
print(buf)
```

```
['hello\n', 'world\n', "i'm yang shun\n", 'are u ok?']
```

模拟读取大文件

```
read()  一次读取全部的内容
read() 读到文件末尾会返回空
```

```
# 模拟读取大文件
f = open("4.txt", "r", encoding="utf-8")
while True:
    # buf = f.read(5)  # 每次5个字符地读取
    buf = f.readline()  # 每次读取一行的内容
    if buf:  # if len(buf) > 0:
        print(buf)
    else:
        break
f.close()
```

### 写文件write

```
# 写文件测试
# f = open("a.txt", "w")  # 不指定编码格式，windows下默认是gbk，而pycharm打开文件默认的编码是utf-8，所以如果文件有中文，会出现乱码
f = open("a.txt", "w", encoding="utf-8")  # 解决方案：1， 打开/创建文件设置编码为utf-8； 2，或者再打开文件时设置gbk格式打开
f.write("hello world\n")
f.write("hello python\n")
f.write("hello 中国\n")

f.close()
```

### 追加文件

```
# 追加文件
# a方式打开文件，用于追加文件内容，在文件末尾写入内容
# 文件不存在，自动创建文件
# a方式和w方式写入内容，都是用write函数
f = open("b.txt", "a", encoding="utf-8")  # 需要设置打开/创建文件编码格式为utf-8
# f.write("hello")
f.write(" world")
f.close()
```

### 文件打开模式

```python
文本文件: txt, .py .md  能够使用记事本打开的文件
二进制文件: 具有特殊格式的文件, mp3 mp4 rmvb avi png jpg 等

文本文件可以使用 文本方式打开文件,也可以使用二进制的方式打开文件

二进制文件,只能使用二进制的方式打开文件
二进制打开方式如下: 不管读取,还是书写,都需要使用二进制的数据
rb wb  ab
注意点: 不能指定 encoding 参数
```

```
f = open("c.txt", "wb")  # 以二进制格式打开文件用于只写，“wb"、”rb"等二进制模式不能设定encoding参数
# f.write("你好")   # err错误，必须是二进制字节对象，不能是字符串
f.write("你好".encode())  # encode()将str转化为二进制格式的字符串，也就是字节类型
f.close()  

f = open("c.txt", "rb")  # 以二进制格式打开文件用于只读
buf = f.read()
print(type(buf))  # buf类型是字节<class 'bytes'>
print(buf)  # 乱码， 需要转码才能解析出来
print(buf.decode())
```

```
<class 'bytes'>
b'\xe4\xbd\xa0\xe5\xa5\xbd'
你好
```

| 访问模式 | 说明                                                                                |
|:---- |:--------------------------------------------------------------------------------- |
| r    | 以只读方式打开文件。文件的指针将会放在文件的开头。这是默认模式。                                                  |
| w    | 打开一个文件只用于写入。如果该文件已存在则将其覆盖。如果该文件不存在，创建新文件。                                         |
| a    | 打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。       |
| rb   | 以二进制格式打开一个文件用于只读。文件指针将会放在文件的开头。这是默认模式。                                            |
| wb   | 以二进制格式打开一个文件只用于写入。如果该文件已存在则将其覆盖。如果该文件不存在，创建新文件。                                   |
| ab   | 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。 |
| r+   | 打开一个文件用于读写。文件指针将会放在文件的开头。                                                         |
| w+   | 打开一个文件用于读写。如果该文件已存在则将其覆盖。如果该文件不存在，创建新文件。                                          |
| a+   | 打开一个文件用于读写。如果该文件已存在，文件指针将会放在文件的结尾。文件打开时会是追加模式。如果该文件不存在，创建新文件用于读写。                 |
| rb+  | 以二进制格式打开一个文件用于读写。文件指针将会放在文件的开头。                                                   |
| wb+  | 以二进制格式打开一个文件用于读写。如果该文件已存在则将其覆盖。如果该文件不存在，创建新文件。                                    |
| ab+  | 以二进制格式打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。如果该文件不存在，创建新文件用于读写。                       |

### 应用-文件备份

```
1. 用只读的方式,打开文件
2. 读取文件内容
3. 关闭文件
4. 只写的方式,打开新文件
5. 将 第 2 步读取的内容写入新文件
6. 关闭新文件

思考:
    1. 如果文件比较大,循环读取文件
    2. 复制备份的文件可能是 txt 文件,可能是 二进制文件,  ---> 使用二进制方式打开文件
```

```
# 文件备份
file_name = input("请输入要备份的文件名：")   # 01-今日内容.mp4
f = open(file_name, "rb")
buf = f.read()
f.close()

pos = file_name.find(".")
# file_name[:pos] 文件前缀名 file_name[pos:] 文件后缀名
newfile_name = file_name[:pos] + "[备份]" + file_name[pos:]
print(newfile_name)   # 01-今日内容[备份].mp4

f = open(newfile_name, "wb")
f.write(buf)
f.close()
```

### 文件和文件夹的操作

```python
# 文件和文件夹操作
# 对文件和目录操作，需要导入os模块
import os
# 文件重命名 os.rename(原文件路径名，新文件路径名)
os.rename("a.txt", "aa.txt")
# 删除文件 os.remove(文件路径名）
os.remove("aa.txt")
# 创建目录 os.mkdir(目录路径名)
os.mkdir("test")
os.mkdir("test/aa")
# 删除空目录 os.rmdir(目录路径名)
os.rmdir("test/aa")
# 获取当前所在的目录 os.getcwd()
buf = os.getcwd()
print(buf)
# 修改当前的目录为目标目录 os.chdir(目标目录名）
os.chdir("test")
print(os.getcwd())
# 获取指定目录中的内容，os.listdir(目录)，不写参数默认是获取当前目录内容
# 返回值是列表，列表每一项是文件名
# os.chdir("D:\CodingSpace\PyCode\Project0")
os.chdir("../")  # 返回上一级目录
buf = os.listdir()
print(buf)
```

### 应用-批量新建/修改文件名

```python
def create_files1():
    os.mkdir("test1")
    for i in range(10):
        file_name = "test1/file_" + str(i) + ".txt"
        print(file_name)
        f = open(file_name, "w")
        f.close()


def create_files2():
    os.mkdir("test2")
    os.chdir("test2")  # 进入目标目录
    for i in range(10):
        file_name = "file_" + str(i) + ".txt"
        print(file_name)
        f = open(file_name, "w")
        f.close()
    os.chdir("../")  # 返回上一级目录


# 修改文件名为：py12_原来的文件名
def modify_files1():
    os.chdir("test1")
    filename_list = os.listdir()
    for filename in filename_list:
        new_filename = 'py12_' + filename
        os.rename(filename, new_filename)
    os.chdir("../")


# 修改文件名为：py12代替原文件名的前4个字符
def modify_files2():
    os.chdir("test2")
    filename_list = os.listdir()
    for filename in filename_list:
        pos = len("py12")
        new_filename = "py12" + filename[pos:]
        os.rename(filename, new_filename)
    os.chdir("../")
```

## 面向对象

定义一个类Animals:

(1)`__init__`()定义构造函数，与其他面向对象语言不同的是，Python语言中，会明确地把代表自身实例的self作为第一个参数传入

(2)创建一个实例化对象 cat，`__init__`()方法接收参数

(3)使用点号 . 来访问对象的属性。

```python
# 三种定义方式
class Dog(object):  # 默认继承object类
    pass
class Dog():  # 括号内容可以不写
    pass 
class Dog:  # 括号可以不写
    pass 


class Animal:
    def __init__(self, name):
        self.name = name
        print('动物名称实例化')
    def eat(self):
        print(self.name +'要吃东西啦！')
    def drink(self):
        print(self.name +'要喝水啦！')

cat =  Animal('miaomiao')
print(cat.name)
cat.eat()
cat.drink()
```

### 魔法方法

```bash
在 python 的类中,有一类方法,这类方法以 `两个下划线开头` 和`两个下划线结尾`, 并且在`满足某个特定条件的情况下,会自动调用`. 这类方法,称为魔法方法
如何学习魔法方法:
1. 魔法方法在什么情况下会自动调用
2. 这个魔法方法有什么作用
3. 这个魔法方法有哪些注意事项
```

#### `__init__()` [掌握]

```bash
调用时机: 在创建对象之后,会立即调用.
作用: 
    1. 用来给对象添加属性,给对象属性一个初始值(构造函数)
    2. 代码的业务需求,每创建一个对象,都需要执行的代码可以写在 `__init__ `中
    3. 只能有一个
```

注意点: 如果 `__init__` 方法中,有除了 self 之外的形参,那么在创建的对象的时候,需要给额外的形参传递实参值 `类名(实参)`

```
class Dog:
    def __init__(self):
        print("__init__方法被调用了")
        self.name = "小狗"


dog = Dog()
print(dog.name)
```

#### `__str__()`[掌握]

```bash
调用时机:
    1. `print(对象)`, 会自动调用 `__str__` 方法, 打印输出的结果是 `__str__` 方法的返回值
    2. `str(对象)`  类型转换,将自定义对象转换为字符串的时候, 会自动调用
应用:
    1. 打印对象的时候,输出一些属性信息
    2. 需要将对象转换为字符串类型的时候
注意点:
    `方法必须返回一个字符串`,只有 self 一个参数
```

```
class Dog:
    def __init__(self):
        print("__init__方法被调用了")
        self.name = "小狗"

    def __str__(self):
        print("__str__方法被调用了")
        return f"小狗名字叫{self.name}"


dog = Dog()
print(dog.name)
print(dog)
```

#### `__del__()`[理解]

```bash
析构函数
调用时机:
    对象在内存中被销毁删除的时候(引用计数为 0)会自动调用 __del__ 方法
    1. 程序代码运行结束,在程序运行过程中,创建的所有对象和变量都会被删除销毁
    2. 使用 `del 变量` , 将这个对象的引用计数变为 0.会自动调用 __del__ 方法
应用场景:
    对象被删除销毁的时候,要书写的代码可以写在 `__del__`中.一般很少使用, 因为python可以自动内存回收

引用计数: 是 python 内存管理的一种机制, 是指一块内存,有多少个变量在引用,
1. 当一个变量,引用一块内存的时候,引用计数加 1
2. 当删除一个变量,或者这个变量不再引用这块内存.引用计数减 1
3. 当内存的引用计数变为 0 的时候,这块内存被删除,内存中的数据被销毁

my_list = [1, 2]  # 1
my_list1 = my_list # 2
del my_list  # 1
del my_list1 # 0 
```

### 继承

```
继承实现

class Person:        
    def __init__(self,name):
        self.name = name
        print ('调用父类构造函数')

    def eat(self):
        print('调用父类方法')

class Student(Person):  # 定义子类，把父类放到子类名中
   def __init__(self):
      print ('调用子类构造方法')

   def study(self):
      print('调用子类方法')

s = Student()          # 实例化子类
s.study()              # 调用子类的方法
s.eat()                # 调用父类方法
```

```
继承说明：
1. 支持多层继承，也支持像C++那样的继承多个父类——多继承  Class Student(父类1， 父类2)：
2. 子类可以重写父类的同名方法[掌握]
3. 子类调用父类的同名方法[掌握]  —— super().bark()
```

### 私有权限[理解]

```bash
访问权限控制: 在什么地方可以使用和操作.
私有权限: 
    定义: 在方法和属性前加上两个下划线, 就变为私有.
    1. 不能在类外部通过对象直接访问和使用, 只能在类内部访问和使用
    2. 不能被子类继承,
公有: 不是私有的,就是公有的.
```

```
class Dog:
    def __init__(self):
        print("__init__方法被调用了")
        self.name = "小狗"
        self.__age = 3

    def get_age(self):
        return self.__age

    def set_age(self, age):
        self.__age = age

    def __sleep(self):
        print("小狗正在睡觉。。。")

    def __str__(self):
        print("__str__方法被调用了")
        return f"小狗名字叫{self.name}"


dog = Dog()
print(dog.name)
print(dog)

print(dog.__age)  # err! 不支持访问
dog.__sleep()   # err! 不支持访问
```

### 类属性[理解]

<img src="C:\Users\ys\AppData\Roaming\Typora\typora-user-images\image-20211026152057886.png" alt="image-20211026152057886" style="zoom:80%;" />

<img src="C:\Users\ys\AppData\Roaming\Typora\typora-user-images\image-20211026152126854.png" alt="image-20211026152126854" style="zoom:67%;" />

### 类方法

<img src="C:\Users\ys\AppData\Roaming\Typora\typora-user-images\image-20211026152203852.png" alt="image-20211026152203852" style="zoom:80%;" />

### 静态方法[掌握]

<img src="C:\Users\ys\AppData\Roaming\Typora\typora-user-images\image-20211026152226930.png" alt="image-20211026152226930" style="zoom:80%;" />

### 多态[理解]

<img src="C:\Users\ys\AppData\Roaming\Typora\typora-user-images\image-20211026152249072.png" alt="image-20211026152249072" style="zoom:80%;" />

## Python JSON模块

JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式，易于人阅读和编写。

```json
JSON 语法:
    数据在键/值对中
    数据由逗号分隔
    大括号 {} 保存对象
    中括号 [] 保存数组，数组可以包含多个对象

eg.
{
    "sites": [
        { "name":"菜鸟教程" , "url":"www.runoob.com" }, 
        { "name":"google" , "url":"www.google.com" }, 
        { "name":"微博" , "url":"www.weibo.com" }
    ]
}
对象 sites 是包含三个对象的数组。每个对象代表一条关于某个网站（name、url）的记录
```

python中 json.dumps 用于将 Python 对象编码成 JSON 字符串。

```
import json
data = [ { 'b' : 2, 'd' : 4, 'a' : 1, 'c' : 3, 'e' : 5 } ]  # data是一个列表list对象
json = json.dumps(data)   # 转变成了json字符串
print(json)   # [{"b": 2, "d": 4, "a": 1, "c": 3, "e": 5}]
```

```python
为了提高可读性，dumps方法提供了一些可选的参数：
    sort_keys=True表示按照字典排序(a到z)输出。
    indent参数，代表缩进的位数
    separators参数的作用是去掉,和:后面的空格，传输过程中数据越精简越好

import json
data = [ { 'b' : 2, 'd' : 4, 'a' : 1, 'c' : 3, 'e' : 5 } ]
json = json.dumps(data, sort_keys=True, indent=4,separators=(',', ':'))
print(json)
```

json.loads 用于**解码 JSON 数据**。该函数返回 Python 字段的数据类型。

```python
import json
jsonData = '{"a":1,"b":2,"c":3,"d":4,"e":5}'   # json字符串
text = json.loads(jsonData)  #将json字符串转换为dict对象
print(text)
print(type(text))  #类型是一个字典
```

    {'a': 1, 'b': 2, 'c': 3, 'd': 4, 'e': 5}
    <class 'dict'>

## Python异常处理

当Python脚本发生异常时我们需要捕获处理它，否则程序会终止执行。

捕捉异常可以使用try/except语句。

try/except语句用来检测try语句块中的错误，从而让except语句捕获异常信息并处理。

```python
try:
    fh = open("/home/aistudio1/data/testfile01.txt", "w")
    fh.write("这是一个测试文件，用于测试异常!!")
except IOError:
    print('Error: 没有找到文件或读取文件失败')
else:
    print ('内容写入文件成功')
    fh.close()
```

finally中的内容，退出try时总会执行

```python
try:
    f = open("/home/aistudio/data/testfile02.txt", "w")
    f.write("这是一个测试文件，用于测试异常!!")
finally:
    print('关闭文件')
    f.close()
```

# 常见的Python库

Python被大量应用在数据挖掘和深度学习领域，其中使用极其广泛的是Numpy、pandas、Matplotlib、PIL等库。

<img src='https://ai-studio-static-online.cdn.bcebos.com/d2ab7dc4c05c42fe85c557a5ed084038822806b23ed544b5bab62517994f5383' height='400' width='400'>

**numpy**是Python科学计算库的基础。包含了强大的N维数组对象和向量运算。

**pandas**是建立在numpy基础上的高效数据分析处理库，是Python的重要数据分析库。

**Matplotlib**是一个主要用于绘制二维图形的Python库。用途：绘图、可视化

**PIL**库是一个具有强大图像处理能力的第三方库。用途：图像处理

## Numpy库

NumPy是使用Python进行科学计算的基础软件包。

更多学习，可参考**numpy中文网**：https://www.numpy.org.cn/

### 1.数组创建

创建数组——使用array函数。它接受一切序列型的对象（包括列表、元组或者其他数组），然后产生一个新的含有传入数据的numpy数组。

嵌套序列（比如由一组**等长列表**组成的列表）将会被转换为一个多维数组

```python
语法：
numpy.array(object, dtype = None, copy = True, order = None, subok = False, ndmin = 0)
    object    数组或嵌套的数列
    dtype    数组元素的数据类型，可选
    copy    对象是否需要复制，可选
    order    创建数组的样式，C为行方向，F为列方向，A为任意方向（默认）
    subok    默认返回一个与基类类型一致的数组
    ndmin    指定生成数组的最小维度


import numpy as np  #将numpy导进来，并且给与别名np
#将列表转换为数组
array = np.array([[1,2,3],
                 [4,5,6]])
print(array)

#将元组转换为数组
array = np.array(((1,2,3),
                 (4,5,6)))
print(array)

# 表示一维数组
a = np.array([1,2,3,4])  # 表示一维数组
print(a)
```

    [[1 2 3]
     [4 5 6]]
    
    [[1 2 3]
     [4 5 6]]
    
    [1,2,3,4]

通常，数组的元素最初是未知的，但它的大小是已知的。因此，NumPy提供了几个函数来创建具有初始占位符内容的数组。

* zeros():可以创建指定长度或者形状的全0数组

* ones():可以创建指定长度或者形状的全1数组

* empty():创建一个数组，其初始内容是随机的,取决于内存的状态

```python
zeroarray = np.zeros((2,3)) 
print(zeroarray)

onearray = np.ones((3,4),dtype='int64')
print(onearray)

emptyarray = np.empty((3,4))
print(emptyarray)
```

    [[0. 0. 0.]  # 默认元素都是浮点型float64
     [0. 0. 0.]]
    
     [[1 1 1 1]
     [1 1 1 1]
     [1 1 1 1]]
    
     [[6.94528877e-310 6.94528877e-310 0.00000000e+000 0.00000000e+000]
     [0.00000000e+000 0.00000000e+000 0.00000000e+000 0.00000000e+000]
     [0.00000000e+000 0.00000000e+000 0.00000000e+000 0.00000000e+000]]

从数值范围创建数组

```python
1，numpy.arange(start, stop, step, dtype)
    start    起始值，默认为0
    stop    终止值（不包含）
    step    步长，默认为1
    dtype    返回ndarray的数据类型，如果没有提供，则会使用输入数据的类型。
x = np.arange(5)  # 默认从0开始，间隔为1
print (x)
array = np.arange( 10, 31, 5)  # 10到30之间，间隔5
print(array)

2，np.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None)   # 创建一个一维数组，数组是一个等差数列构成的
    start    序列的起始值
    stop    序列的终止值，如果endpoint为true，该值包含于数列中
    num    要生成的等步长的样本数量，默认为50
    endpoint    该值为 true 时，数列中包含stop值，反之不包含，默认是True。
    retstep    如果为 True 时，生成的数组中会显示间距，反之不显示。
    dtype    默认数据类型为float

import numpy as np
a = np.linspace(1,10,10)
print(a)

3，np.logspace(start, stop, num=50, endpoint=True, base=10.0, dtype=None)  # 用于创建一个等比数列
    start    序列的起始值为：base ** start
    stop    序列的终止值为：base ** stop。如果endpoint为true，该值包含于数列中
    num    要生成的等步长的样本数量，默认为50
    endpoint    该值为 true 时，数列中中包含stop值，反之不包含，默认是True。
    base    底数。
    dtype    默认数据类型为float

# 默认底数是 10
a = np.logspace(0,9,10,base=2)
print (a)   # [  1.   2.   4.   8.  16.  32.  64. 128. 256. 512.]
```

从已有的数组创建数组

```python
语法：numpy.asarray(a, dtype = None, order = None)
    a    任意形式的输入参数，可以是，列表, 列表的元组, 元组, 元组的元组, 元组的列表，多维数组
    dtype    数据类型，可选
    order    可选，有"C"和"F"两个选项,分别代表，行优先和列优先，在计算机内存中的存储元素的顺序。

# 列表转化数组
x =  [1,2,3] 
a = np.asarray(x)  
print (a)  # [1  2  3]
# 元组转化数组
x =  (1,2,3) 
a = np.asarray(x)  
print (a)  # [1  2  3]
# 元组列表转化数组（还是一维数组，数组中元素为元组）
x =  [(1,2,3),(4,5)] 
a = np.asarray(x)  
print (a)  # [(1, 2, 3) (4, 5)]
```

数组属性：

```python
array = np.array([[1,2,3],[4,5,6],[7,8,9],[10,11,12]])
print(array)
#数组维度
print(array.ndim)
#数组形状，返回的是一个元组
print(array.shape)
#数组元素个数
print(array.size)
#数组元素类型
print(array.dtype)
```

    [[ 1  2  3]
     [ 4  5  6]
     [ 7  8  9]
     [10 11 12]]
    2
    (4, 3)
    12
    int64

切片操作：

ndarray对象的内容可以通过索引或切片来访问和修改，与 Python 中 list 的切片操作一样

```python
1, ndarray 数组可以基于 0 - n 的下标进行索引，切片对象可以通过内置的 slice 函数，并设置 start, stop 及 step 参数进行，从原数组中切割出一个新数组。
a = np.arange(10)
s = slice(2,7,2)   # 从索引 2 开始到索引 7 停止，间隔为2
print (a[s])    # [2  4  6]


2，冒号分隔切片参数 start:stop:step 来进行切片操作
a = np.arange(10)  
b = a[2:7:2]   # 从索引 2 开始到索引 7 停止，间隔为 2
print(b)

# 冒号 : 的解释：
只有一个冒号:，如[:]，表示返回所有元素
只放置一个参数，如 [2]，将返回与该索引相对应的单个元素。
如果为 [2:]，表示从该索引开始以后的所有项都将被提取。
使用了两个参数，如 [2:7]，那么则提取两个索引(不包括停止索引)之间的项。
使用了三个参数，如 [2:7:2]，最后一个参数为步长2。

# 多维数组同样适用上述索引提取方法：
a = np.array([[1,2,3],[3,4,5],[4,5,6]])
print(a)
# 从某个索引处开始切割
print(a[1:])    # [[3 4 5] [4 5 6]]

a = np.array([[1,2,3],[3,4,5],[4,5,6]])  
print (a[..., 1])   # 第2列元素，或者使用a[:,1]，冒号取代省略号
print (a[1, ...])   # 第2行元素
print (a[..., 1:])  # 第2列除了第一个其他所有元素

# 索引下标访问
arr5 = np.arange(0,6).reshape([2,3])
print(arr5)
print(arr5[1])
print(arr5[1][2])
print(arr5[1,2])   #这种写法和上面的效果一样

#下面的是数组切片操作
print(arr5[1,:])   #取第二行所有元素，返回的是一维数组
print(arr5[:,1])  #取第二列的所有元素
print(arr5[1,0:2]) #取第二行0—1的所有元素
```

numpy广播

```python
如果两个数组 a 和 b 形状相同，即满足 a.shape == b.shape，那么 a*b 的结果就是 a 与 b 数组对应位相乘
a = np.array([1,2,3,4]) 
b = np.array([10,20,30,40]) 
c = a * b 
print (c)  # [ 10  40  90 160]

# 当两个数组的形状并不相同的时候，我们可以通过扩展数组的方法来实现相加、相减、相乘等操作，这种机制叫做广播（broadcasting）

广播的原则：如果两个数组的后缘维度（trailing dimension，即从末尾开始算起的维度）的轴长度相符，或其中的一方的长度为1，则认为它们是广播兼容的
1, 数组维度不同，后缘维度的轴长相符

arr1 = np.array([[0, 0, 0],[1, 1, 1],[2, 2, 2], [3, 3, 3]])  #arr1.shape = (4,3)
arr2 = np.array([1, 2, 3])    #arr2.shape = (3,)
arr_sum = arr1 + arr2
print(arr_sum)

输入结果如下:
'''
[[1 2 3]
 [2 3 4]
[3 4 5]
[4 5 6]]
'''

2, 数组维度相同，其中有个轴为1
arr1 = np.array([[0, 0, 0],[1, 1, 1],[2, 2, 2], [3, 3, 3]])  #arr1.shape = (4,3)
arr2 = np.array([[1],[2],[3],[4]])    #arr2.shape = (4, 1)

arr_sum = arr1 + arr2
print(arr_sum)

输出结果如下：
[[1 1 1]
 [3 3 3]
 [5 5 5]
 [7 7 7]]
```

### 2.数组操作

```
Numpy 中包含了一些函数用于处理数组，大概可分为以下几类：
    修改数组形状
    翻转数组
    连接数组
    分割数组
    数组元素的添加与删除

修改数组形状
reshape    不改变数据的条件下修改形状   
    numpy.reshape(arr, newshape, order='C')或者arr.reshape([4, 2])
flat    对数组中每个元素都进行处理，可以使用flat属性，该属性是一个数组元素迭代器：
    print ('迭代后的数组：')
    for element in a.flat:
        print (element)
flatten    返回一份展开数组的拷贝，对拷贝所做的修改不会影响原始数组
    print ('展开的数组：')
    print (a.flatten())   # [0 1 2 3 4 5 6 7]
ravel    返回展开数组，修改会影响原始数组
    print ('调用 ravel 函数之后：')
    print (a.ravel())

翻转数组-转置
transpose    转置
    numpy.transpose(arr, axes)或者arr.transpose()
ndarray.T    和 self.transpose() 相同，转置
    print ('转置数组：')
    print (a.T)

连接数组
concatenate    连接沿现有轴的数组序列
stack    沿着新的轴加入一系列数组。
hstack    水平堆叠序列中的数组（列方向）
vstack    竖直堆叠序列中的数组（行方向）

分割数组
split    将一个数组分割为多个子数组
hsplit    将一个数组水平分割为多个子数组（按列）
vsplit    将一个数组垂直分割为多个子数组（按行）

数组元素的添加与删除
resize    返回指定形状的新数组
append    将值添加到数组末尾
insert    沿指定轴将值插入到指定下标之前
delete    删掉某个轴的子数组，并返回删除后的新数组
unique    查找数组内的唯一元素
```

### 3.数组字符串函数

| 函数             | 描述                    |
|:-------------- |:--------------------- |
| `add()`        | 对两个数组的逐个字符串元素进行连接     |
| multiply()     | 返回按元素多重连接后的字符串        |
| `center()`     | 居中字符串                 |
| `capitalize()` | 将字符串第一个字母转换为大写        |
| `title()`      | 将字符串的每个单词的第一个字母转换为大写  |
| `lower()`      | 数组元素转换为小写             |
| `upper()`      | 数组元素转换为大写             |
| `split()`      | 指定分隔符对字符串进行分割，并返回数组列表 |
| `splitlines()` | 返回元素中的行列表，以换行符分割      |
| `strip()`      | 移除元素开头或者结尾处的特定字符      |
| `join()`       | 通过指定分隔符来连接数组中的元素      |
| `replace()`    | 使用新字符串替换字符串中的所有子字符串   |
| `decode()`     | 数组元素依次调用`str.decode`  |
| `encode()`     | 数组元素依次调用`str.encode`  |

### 4.数学函数、算术函数、统计函数

```
数学函数
1.标准的三角函数：sin()、cos()、tan()
    a = np.array([0,30,45,60,90])
    print ('不同角度的正弦值：')
    # 通过乘 pi/180 转化为弧度  
    print (np.sin(a*np.pi/180))  # [0.         0.5        0.70710678 0.8660254  1.        ]

2.反三角函数：arcsin，arccos，和 arctan 函数 
    np.arcsin(sin) 

3.其他函数：
numpy.around() 函数返回指定数字的四舍五入值。
numpy.floor() 返回小于或者等于指定表达式的最大整数，即向下取整
numpy.ceil() 返回大于或者等于指定表达式的最小整数，即向上取整

算术函数
1.简单的加减乘除: add()，subtract()，multiply() 和 divide()，注意：数组必须具有相同的形状或符合数组广播规则，对应位置进行加减乘除
    a = np.arange(9, dtype = np.float_).reshape(3,3)  
    b = np.array([10,10,10])  
    print ('两个数组相加：')
    print (np.add(a,b))
直接使用加减乘除号
    print(arr1 + arr2)
    print(arr1 - arr2)
    print(arr1 * arr2)   #这里的乘除是对应元素进行乘除，和下面的矩阵乘法不一样
    print(arr1 / arr2)
    print(arr1 ** 2)

其他函数：    
numpy.reciprocal() 函数返回参数逐元素的倒数
    print (np.reciprocal(a))
numpy.power() 函数将第一个输入数组中的元素作为底数
    print (np.power(a,2))
numpy.mod() 计算输入数组中相应元素的相除后的余数。 函数 numpy.remainder() 也产生相同的结果
    print (np.mod(a,b))/print (np.remainder(a,b))


统计函数
numpy.amin() 用于计算数组中的元素沿指定轴的最小值。
numpy.amax() 用于计算数组中的元素沿指定轴的最大值。
    a = np.array([[3,7,5],[8,4,3],[2,4,9]]) 
    print (np.amin(a,1))  # 寻找行最小值  [3 3 2]
    print (np.amin(a,0))  # 寻找列最小值  [2 4 3]

numpy.ptp()函数计算数组中元素最大值与最小值的差（最大值 - 最小值）。
numpy.median() 函数用于计算数组 a 中元素的中位数（中值）
numpy.mean() 函数返回数组中元素的算术平均值。算术平均值是沿轴的元素的总和除以元素的数量
numpy.average() 函数根据在另一个数组中给出的各自的权重计算数组中元素的加权平均值，加权平均值即将各数值乘以相应的权数，然后加总求和得到总体值，再除以总的单位数
    print (np.average(a))  # 不指定权重时相当于 mean 函数
    print (np.average(a,weights = wts))

numpy.np.std() 函数返回数组中元素的标准差，标准差是方差的算术平方根。
    print (np.std([1,2,3,4]))  # 1.1180339887498949

numpy.np.var() 标准差是方差的平方根
    print (np.var([1,2,3,4]))  # 1.25
```

### 5.排序、条件筛选函数

```python
1.numpy.sort() 函数返回输入数组的排序副本   numpy.sort(a, axis, kind, order)
    a: 要排序的数组
    axis: 沿着它排序数组的轴，默认按照行排序， axis=0 按列排序，axis=1 按行排序
    kind: 默认为'quicksort'（快速排序）
    order: 如果数组包含字段，则是要排序的字段
print (np.sort(a))
print (np.sort(a, axis =  0))
print (np.sort(a, order =  'name'))

2.numpy.argsort() 函数返回的是数组值从小到大的索引值。
    x = np.array([3,  1,  2])  
    y = np.argsort(x)   # [1 2 0]
    print ('以排序后的顺序重构原数组：')
    print (x[y])
3.numpy.lexsort() 用于对多个序列进行排序。排序时优先照顾靠后的列
    nm =  ('raju','anil','ravi','amar') 
    dv =  ('f.y.',  's.y.',  's.y.',  'f.y.') 
    ind = np.lexsort((dv,nm))  #返回的是索引位置 [3 1 0 2]

4.numpy.argmax() 和 numpy.argmin()函数分别沿给定轴返回最大和最小元素的索引。这里的索引是将数组平铺后的索引
5.numpy.nonzero() 函数返回输入数组中非零元素的索引。
6.numpy.where() 函数返回输入数组中满足给定条件的元素的索引。
    y = np.where(x >  3)  # 大于 3 的元素的索引
7.numpy.extract() 函数根据某个条件从数组中抽取元素，返回满条件的元素。
```

### 6.线性代数

```python
dot    两个数组的点积，即元素对应相乘。
    两个一维的数组，计算的是这两个数组对应下标元素的乘积和(数学上称之为内积)；
    对于二维数组，计算的是两个数组的矩阵乘积

vdot    返回两个向量的点积，如果参数是多维数组，它会被展开
    a = np.array([[1,2],[3,4]]) 
    b = np.array([[11,12],[13,14]]) 
    # vdot 将数组展开计算内积
    print (np.vdot(a,b))  # 1*11 + 2*12 + 3*13 + 4*14 = 130

inner    返回两个一维数组的向量内积

matmul    返回两个数组的矩阵乘积（矩阵乘法）。 如果任一参数是一维数组，则通过在其维度上附加 1 来将其提升为矩阵，并在乘法之后被去除

determinant    数组的行列式
solve    求解线性矩阵方程
inv    计算矩阵的乘法逆矩阵

numpy.linalg.det() 函数计算输入矩阵的行列式
    a = np.array([[1,2], [3,4]]) 
    print (np.linalg.det(a))  # -2.0

numpy.linalg.inv() 函数计算矩阵的乘法逆矩阵
    x = np.array([[1,2],[3,4]]) 
    y = np.linalg.inv(x) 
```

## pandas库

pandas是python第三方库，提供高性能易用数据类型和分析工具。

pandas基于numpy实现，常与numpy和matplotlib一同使用

更多学习，请参考**pandas中文网**：https://www.pypandas.cn/

**Pandas核心数据结构：**

<img src="https://ai-studio-static-online.cdn.bcebos.com/a8c80653f39b479dab9f6867a638b64c405e79d6540c4307a22f43c4b0e228bc" width='300' height='200'>

<img src="https://ai-studio-static-online.cdn.bcebos.com/c8f06f423acc488fb391bca5dcf8f2b02d7444ef526f41599b6b430ae24659c1" width='500' height='200'>

### 1.Series-相当于excel中的一列

Series是一种类似于**一维数组**的对象，它由一维数组（各种numpy数据类型）以及一组与之相关的数据标签（即索引）组成.

可理解为**带标签的一维数组**，可存储整数、浮点数、字符串、Python 对象等类型的数据。

```python
# 初始化使用
import pandas as pd
import numpy as np
# 可以使用列表初始化
s = pd.Series(['a','b','c','d','e'])
print(s)
# 可以用字典实例化
d = {'b': 1, 'a': 0, 'c': 2}
pd.Series(d)  # 索引就是'b''a''c'
# 可以使用np.array初始化，可以使用index设置索引列表
s = pd.Series(np.array([1,2,3,4,5]), index=['a', 'b', 'c', 'd', 'e'])
print(s)

#与字典不同的是：Series允许索引重复
s = pd.Series(['a','b','c','d','e'],index=[100,200,100,400,500])
print(s)
```

    0    a
    1    b
    2    c
    3    d
    4    e
    dtype: object

常用函数：

```python
# 可以通过Series的values和index属性获取其数组表示形式和索引对象
print(s)
print(s.values)
print(s.index)
print(s.keys())  # 和index效果一样
```

    100    a
    200    b
    100    c
    400    d
    500    e
    dtype: object
    ['a' 'b' 'c' 'd' 'e']
    Int64Index([100, 200, 100, 400, 500], dtype='int64')
    Int64Index([100, 200, 100, 400, 500], dtype='int64')

```python
#与普通numpy数组相比，可以通过索引的方式选取Series中的单个或一组值
print(s[100])  
print(s[[400, 500]])  #获取索引为400和500的值
```

    100    a
    100    c
    dtype: object
    400    d
    500    e
    dtype: object

```python
#对应位置的元素求和
print(s+s)
#对应位置的元素乘
print(s*3)

#算数运算，Series会在算术运算中自动对齐不同索引的数据
obj1 = pd.Series({"Ohio": 35000, "Oregon": 16000, "Texas": 71000, "Utah": 5000})
print(obj1)
obj2 = pd.Series({"California": np.nan, "Ohio": 35000, "Oregon": 16000, "Texas": 71000}) 
# np.nan 表示未定义或不可表示的值 NaN
print(obj2)
print(obj1 + obj2)   #求和结果，索引相同进行求和，索引不同进行合并，有一方没有的则为NaN值
```

    a     2
    b     4
    c     6
    d     8
    e    10
    dtype: int64
    a     3
    b     6
    c     9
    d    12
    e    15
    dtype: int64
    
    Ohio      35000
    Oregon    16000
    Texas     71000
    Utah       5000
    dtype: int64
    California        NaN
    Ohio          35000.0
    Oregon        16000.0
    Texas         71000.0
    dtype: float64
    California         NaN
    Ohio           70000.0
    Oregon         32000.0
    Texas         142000.0
    Utah               NaN
    dtype: float64

```python
# 切片操作，操作类似于数组
s = pd.Series(np.array([1,2,3,4,5]), index=['a', 'b', 'c', 'd', 'e'])
print(s[1:])  # 以原来的索引下标看待
print(s[:-1])
print(s[1:] + s[:-1])
```

    b    2
    c    3
    d    4
    e    5
    dtype: int64
    a    1
    b    2
    c    3
    d    4
    dtype: int64
    a    NaN
    b    4.0
    c    6.0
    d    8.0
    e    NaN
    dtype: float64

### 2.DataFrame-类似于excel中的表格

<img src="https://ai-studio-static-online.cdn.bcebos.com/c8f06f423acc488fb391bca5dcf8f2b02d7444ef526f41599b6b430ae24659c1" width='500' height='200'>

DataFrame可以被看做由多个Series组成的字典（共用同一个索引）

```python
DataFrame 构造方法如下：
pandas.DataFrame( data, index, columns, dtype, copy)
    data：一组数据(ndarray、series, map, lists, dict 等类型)，所有列的长度必须相同
    index：索引值，或者可以称为行标签。
    columns：列标签，默认为 RangeIndex (0, 1, 2, …, n) 。
    dtype：数据类型。
    copy：拷贝数据，默认为 False。

# 列表字典生成 DataFrame，用来初始化
data = {'state': ['Ohio', 'Ohio', 'Ohio', 'Nevada', 'Nevada'], 'year': [2000, 2001, 2002, 2001, 2002], 'pop': [1.5, 1.7, 3.6, 2.4, 2.9]}
frame = pd.DataFrame(data)
print(frame)

# 使用二维列表创建DataFrame
data = [['Google',10],['Runoob',12],['Wiki',13]]
df = pd.DataFrame(data,columns=['Site','Age'],dtype=float)

# 使用字典创建
data = [{'a': 1, 'b': 2},{'a': 5, 'b': 10, 'c': 20}]
df = pd.DataFrame(data)

# 用 Series 字典或字典生成 DataFrame
d = {'one': pd.Series([1., 2., 3.], index=['a', 'b', 'c']),
     'two': pd.Series([1., 2., 3., 4.], index=['a', 'b', 'c', 'd'])}
print(pd.DataFrame(d))

#如果指定了列顺序，则DataFrame的列就会按照指定顺序进行排列
frame1 = pd.DataFrame(data, columns=['year', 'state', 'pop'])
print(frame1)

# 可以用index设置索引列表
# 跟原Series一样，如果传入的列在数据中找不到，就会产生NAN值
frame2 = pd.DataFrame(data, columns=['year', 'state', 'pop', 'debt'], index=['one', 'two', 'three', 'four', 'five'])
print(frame2)
```

        state  year  pop
    0    Ohio  2000  1.5
    1    Ohio  2001  1.7
    2    Ohio  2002  3.6
    3  Nevada  2001  2.4
    4  Nevada  2002  2.9
    
        Site  Age
    0    Google 10
    1    Runoob 12
    2    Wiki   13
    
       a   b     c
    0  1   2   NaN
    1  5  10  20.0
    
       one  two
    a  1.0  1.0
    b  2.0  2.0
    c  3.0  3.0
    d  NaN  4.0
    
       year   state  pop
    0  2000    Ohio  1.5
    1  2001    Ohio  1.7
    2  2002    Ohio  3.6
    3  2001  Nevada  2.4
    4  2002  Nevada  2.9
    
           year   state  pop debt
    one    2000    Ohio  1.5  NaN
    two    2001    Ohio  1.7  NaN
    three  2002    Ohio  3.6  NaN
    four   2001  Nevada  2.4  NaN
    five   2002  Nevada  2.9  NaN

常见用法：

```python
#查：通过类似字典标记的方式或属性的方式，可以将DataFrame的列获取为一个Series,返回的Series拥有原DataFrame相同的索引
print(frame2['state'])  # 返回特定的列'state'
print(frame2['state', 'year'])  # 返回特定的列'state'  'year'

# 抽取数据——loc和iloc，都可以进行切片操作，返回结果其实就是一个 Pandas Series 数据
.loc[]：是location，以index（行名）、columns（列名）作为参数。当只有一个参数时，默认是行名（即抽取整行），所有列都选中。
.iloc[]：是index location，以二维矩阵的位置指标（即0,1,2……）作为参数。# 可以用来返回特定的行和列

# Pandas 可以使用 loc 属性返回指定行的数据（Pandas Series 数据），如果没有设置索引，第一行索引为 0，第二行索引为 1，以此类推：
    data = {
      "calories": [420, 380, 390],
      "duration": [50, 40, 45]
    }
    df = pd.DataFrame(data)     # 数据载入到 DataFrame 对象
    print(df.loc[0])      # 返回第一行
    print(df.loc[1])     # 返回第二行
# 返回多行数据（返回结果其实就是一个 Pandas DataFrame 数据）
print(df.loc[[0, 1]])  # 返回第一行和第二行
# 指定索引
print(df.loc["day2"])

#赋值：列可以通过赋值的方式进行修改
frame2['debt'] = 16.5  #给那个空的“delt”列赋上一个标量值或一组值
print(frame2)
# 可以使用np.array来赋值
frame2['debt'] = np.arange(5.)  #赋值一个数组
print(frame2)

#运算：对应位置运算
frame2['new'] = frame2['debt' ]* frame2['pop']  # 对应位置相乘运算，然后赋值给‘new’
print(frame2)

#插入：插入一列
data.insert(0, 'Ones', 1) #在位置0处插入一个“Ones"的Series，值为1
```

    one        Ohio
    two        Ohio
    three      Ohio
    four     Nevada
    five     Nevada
    Name: state, dtype: object
    
    calories    420
    duration     50
    Name: 0, dtype: int64
    calories    380
    duration     40
    Name: 1, dtype: int64
    
           year   state  pop  debt
    one    2000    Ohio  1.5  16.5
    two    2001    Ohio  1.7  16.5
    three  2002    Ohio  3.6  16.5
    four   2001  Nevada  2.4  16.5
    five   2002  Nevada  2.9  16.5
    
           year   state  pop  debt    new
    one    2000    Ohio  1.5   0.0  24.75
    two    2001    Ohio  1.7   1.0  28.05
    three  2002    Ohio  3.6   2.0  59.40
    four   2001  Nevada  2.4   3.0  39.60
    five   2002  Nevada  2.9   4.0  47.85
    
           year   state  pop  debt    new
    one    2000    Ohio  1.5  16.5  24.75
    two    2001    Ohio  1.7  16.5  28.05
    three  2002    Ohio  3.6  16.5  59.40
    four   2001  Nevada  2.4  16.5  39.60
    five   2002  Nevada  2.9  16.5  47.85

### 3.Pandas CSV

常用函数

```
CSV（Comma-Separated Values，逗号分隔值，有时也称为字符分隔值，因为分隔字符也可以不是逗号），其文件以纯文本形式存储表格数据（数字和文本）。

1. read_csv(参数...)  将csv文件打开，并返回DataFrame 类型的数据。这里是pd来调用，后面的都是用df来调用
df = pd.read_csv('nba.csv')
data = pd.read_csv(path, header=None, names=['Population', 'Profit']) 
#如果原文件中没有列标题，加“header=None”，告诉函数，我们读取的原始文件数据没有列索引，然后加上另外的标题names

2. to_string() 用于返回 DataFrame 类型的数据，如果不使用该函数，则输出结果为数据的前面 5 行和末尾 5 行，中间部分以 ... 代替
print(df.to_string())

3. to_csv() 将 DataFrame 存储为 csv 文件
# 字典
dict = {'name': nme, 'site': st, 'age': ag} 
df = pd.DataFrame(dict)
# 保存 dataframe
df.to_csv('site.csv')


4. head(n) 用于读取前面的 n 行，如果不填参数 n ，默认返回 5 行
df = pd.read_csv('nba.csv')
print(df.head())

5. tail(n) 方法用于读取尾部的 n 行，如果不填参数 n ，默认返回 5 行，空行各个字段的值返回 NaN

6. info() 方法返回表格的一些基本信息:行数、列数、数据类型等

7. describe()  显示DataFrame的部分参数：count/mean/max/min/4分位数等

8. plot() 是DataFrame的绘图函数，使用如下：
data.plot(kind='scatter', x='Population', y='Profit', figsize=(12,8))
plt.show()  # 显示图形
```

### 4.DataFrame和 Json转换

```python
1.读取json文件，返回DataFrame对象
sites.json文件:
[
   {
   "id": "A001",
   "name": "菜鸟教程",
   "url": "www.runoob.com",
   "likes": 61
   },
   {
   "id": "A002",
   "name": "Google",
   "url": "www.google.com",
   "likes": 124
   },
   {
   "id": "A003",
   "name": "淘宝",
   "url": "www.taobao.com",
   "likes": 45
   }
]

import pandas as pd
df = pd.read_json('sites.json')   
print(df.to_string())

2.JSON 对象与 Python 字典具有相同的格式，所以我们可以直接将 Python 字典转化为 DataFrame 数据
# 字典格式的 JSON                                                                                            
s = {
    "col1":{"row1":1,"row2":2,"row3":3},
    "col2":{"row1":"x","row2":"y","row3":"z"}
}
# 读取 JSON 转为 DataFrame                                                                                   
df = pd.DataFrame(s)
print(df)

3.从 URL 中读取 JSON 数据：
URL = 'https://static.runoob.com/download/sites.json'
df = pd.read_json(URL)
print(df)

4.读取内嵌的 JSON 数据  ——  json_normalize() 方法
# 使用 Python JSON 模块载入数据
with open('nested_list.json','r') as f:
    data = json.loads(f.read())
# 展平数据
df_nested_list = pd.json_normalize(data, record_path =['students'])
print(df_nested_list)
# data = json.loads(f.read()) 使用 Python JSON 模块载入数据。
# json_normalize() 使用了参数 record_path 并设置为 ['students'] 用于展开内嵌的 JSON 数据 students。
```

### 5.Pandas数据清洗

```python
数据清洗是对一些没有用的数据进行处理的过程。
很多数据集存在数据缺失、数据格式错误、错误数据或重复数据的情况，如果要对使数据分析更加准确，就需要对这些没有用的数据进行处理
上表包含来四种空数据：n/a、NA、—、na

1. 删除包含空字段的行，可以使用 dropna() 方法
DataFrame.dropna(axis=0, how='any', thresh=None, subset=None, inplace=False)
    axis：默认为 0，表示逢空值剔除整行，如果设置参数 axis＝1 表示逢空值去掉整列。
    how：默认为 'any' 如果一行（或一列）里任何一个数据有出现 NA 就去掉整行，如果设置 how='all' 一行（或列）都是 NA 才去掉这整行。
    thresh：设置需要多少非空值的数据才可以保留下来的。
    subset：设置想要检查的列。如果是多个列，可以使用列名的 list 作为参数。
    inplace：如果设置 True，将计算得到的值直接覆盖之前的值并返回 None，修改的是源数据。

isnull() 判断各个单元格是否为空
    df = pd.read_csv('property-data.csv')
    print (df['NUM_BEDROOMS'])
    print (df['NUM_BEDROOMS'].isnull())

Pandas 把 n/a 和 NA 当作空数据，na 不是空数据，不符合我们要求，我们可以指定空数据类型
    missing_values = ["n/a", "na", "--"]
    df = pd.read_csv('property-data.csv', na_values = missing_values)
    print (df['NUM_BEDROOMS'])
    print (df['NUM_BEDROOMS'].isnull())

删除包含空数据的行，默认情况下，dropna() 方法返回一个新的 DataFrame，不会修改源数据。如果你要修改源数据 DataFrame, 可以使用 inplace = True 参数
    df = pd.read_csv('property-data.csv')
    new_df = df.dropna()
    print(new_df.to_string())

移除指定列有空值的行
    df = pd.read_csv('property-data.csv')
    df.dropna(subset=['ST_NUM'], inplace = True)  # 移除 ST_NUM 列中字段值为空的行
    print(df.to_string())

可以用 fillna() 方法来替换一些空字段
    df = pd.read_csv('property-data.csv')
    df.fillna(12345, inplace = True)  # 使用12345替换空字段
    # df['PID'].fillna(12345, inplace = True)   # 指定某一个列来替换数据
    print(df.to_string())

替换空单元格的常用方法是计算列的均值、中位数值或众数
使用 mean()、median() 和 mode() 方法均值（所有值加起来的平均值）、中位数值（排序后排在中间的数）和众数（出现频率最高的数）
    df = pd.read_csv('property-data.csv')
    x = df["ST_NUM"].mean()
    df["ST_NUM"].fillna(x, inplace = True)
    print(df.to_string())

清洗格式错误数据
    # 第三个日期格式错误
    data = {
      "Date": ['2020/12/01', '2020/12/02' , '20201226'],
      "duration": [50, 40, 45]
    }
    df = pd.DataFrame(data, index = ["day1", "day2", "day3"])
    df['Date'] = pd.to_datetime(df['Date'])

清洗错误数据
person = {
  "name": ['Google', 'Runoob' , 'Taobao'],
  "age": [50, 200, 12345]    
}
df = pd.DataFrame(person)
for x in df.index:
  if df.loc[x, "age"] > 120:  
    df.loc[x, "age"] = 120    # 将 age 大于 120 的设置为 120
    # df.drop(x, inplace = True)  # 可以将错误数据的行删除

print(df.to_string())

清洗重复数据，可以使用 duplicated() 和 drop_duplicates() 方法
如果对应的数据是重复的，duplicated() 会返回 True，否则返回 False
删除重复数据，可以直接使用drop_duplicates() 方法
    persons = {
      "name": ['Google', 'Runoob', 'Runoob', 'Taobao'],
      "age": [50, 40, 40, 23]  
    }
    df = pd.DataFrame(persons)
    df.drop_duplicates(inplace = True)
    print(df)
```

## PIL库

PIL库是一个具有**强大图像处理能力**的第三方库。

图像的组成：由RGB三原色组成,RGB图像中，一种彩色由R、G、B三原色按照比例混合而成。0-255区分不同亮度的颜色。

图像的数组表示：图像是一个由像素组成的矩阵，每个元素是一个RGB值

![](https://ai-studio-static-online.cdn.bcebos.com/66ad941c87c5459ea2aade30e26fad8ccf65312d850c49e3bc3581b9afc8fd23)

Image 是 PIL 库中代表一个图像的类（对象）

```python
#安装pillow
#!pip install pillow
```

展示图片，并获取图像的模式，长宽，

```python
from PIL import Image   #导入Image模块
import matplotlib.pyplot as plt
#显示matplotlib生成的图形
%matplotlib inline

#读取图片
img = Image.open('/home/aistudio/work/yushuxin.jpg') 

#显示图片
#img.show() #自动调用计算机上显示图片的工具

plt.imshow(img)  
plt.show(img)   

#获得图像的模式/格式
img_mode = img.mode  
print(img_mode)

width,height = img.size
print(width,height)
```

![png](D:\YS-学习总结\python\2381206\output_61_0.png)

    RGB
    533 300

图片旋转

```python
from PIL import Image
import matplotlib.pyplot as plt
#显示matplotlib生成的图形
%matplotlib inline

#读取图片
img = Image.open('/home/aistudio/work/yushuxin.jpg') 
#显示图片
plt.imshow(img)  
plt.show(img)  

#将图片旋转45度
img_rotate = img.rotate(45) 
#显示旋转后的图片
plt.imshow(img_rotate)  
plt.show(img_rotate)   
```

图片剪切

```python
from PIL import Image

#打开图片
img1 = Image.open('/home/aistudio/work/yushuxin.jpg') 

#剪切 crop()四个参数分别是：(左上角点的x坐标，左上角点的y坐标，右下角点的x坐标，右下角点的y坐标)
img1_crop_result = img1.crop((126,0,381,249))

#保存图片
img1_crop_result.save('/home/aistudio/work/yushuxin_crop_result.jpg')

#展示图片
plt.imshow(img1_crop_result)  
plt.show(img1_crop_result)   
```

图片缩放

```python
from PIL import Image

#打开图片
img2 = Image.open('/home/aistudio/work/yushuxin.jpg') 

width,height = img2.size

#缩放
img2_resize_result = img2.resize((int(width*0.6),int(height*0.6)),Image.ANTIALIAS)

print(img2_resize_result.size)

#保存图片
img2_resize_result.save('/home/aistudio/work/yushuxin_resize_result.jpg')

#展示图片
plt.imshow(img2_resize_result)  
plt.show(img2_resize_result)   
```

镜像效果：左右旋转、上下旋转

```python
from PIL import Image

#打开图片
img3 = Image.open('/home/aistudio/work/yushuxin.jpg') 

#左右镜像
img3_lr = img3.transpose(Image.FLIP_LEFT_RIGHT)

#展示左右镜像图片
plt.imshow(img3_lr)  
plt.show(img3_lr)   

#上下镜像
img3_bt = img3.transpose(Image.FLIP_TOP_BOTTOM)

#展示上下镜像图片
plt.imshow(img3_bt)  
plt.show(img3_bt)  
```

## Matplotlib库

Matplotlib库由各种可视化类构成，内部结构复杂。

matplotlib.pylot是**绘制各类可视化图形**的命令字库

更多学习，可参考**Matplotlib中文网**：https://www.matplotlib.org.cn

### 生成折线图-plt.plot

```python
import matplotlib.pyplot as plt
import numpy as np 

x = np.linspace(-1,1,50) #等差数列，生成的是数组类型np.array
y = 2*x + 1

#传入x,y,通过plot()绘制出折线图 
plt.plot(x,y)
#显示图形
plt.show()

# 设置显示大小
x = np.linspace(-1,1,50) #等差数列
y1 = 2*x + 1
y2 = x**2

plt.figure()  # 表示设置大小为默认大小
plt.plot(x,y1)

plt.figure(figsize=(7,5))  # 表示设置图片大小。figure 的大小为宽、长（单位为inch）
plt.plot(x,y2)

plt.show()

# 设置x,y字体大小
plt.figure(figsize=(7,5))
plt.plot(x,y1,color='red',linewidth=1)   # 设置绘制线条颜色和粗细
plt.plot(x,y2,color='blue',linewidth=5)  # 使用同一个x变量的两个图会被画在同一个图中
plt.xlabel('x',fontsize=20)  # fontsize设置x和y的字体大小
plt.ylabel('y',fontsize=20)  
plt.show()

#
l1, = plt.plot(x,y1,color='red',linewidth=1)
l2, = plt.plot(x,y2,color='blue',linewidth=5)
plt.legend(handles=[l1,l2],labels=['aa','bb'],loc='best')  # 设置左上角图标
plt.xlabel('x')
plt.ylabel('y')
# plt.xlim((0,1))  #x轴只截取一段进行显示
# plt.ylim((0,1))  #y轴只截取一段进行显示
plt.show()
```

<img src="C:\Users\ys\AppData\Roaming\Typora\typora-user-images\image-20211029105712731.png" alt="image-20211029105712731" style="zoom:67%;" />

### 生成点图-plt.scatter

```python
dots1 = np.array([2,3,4,5,6])
dots2 = np.array([2,3,4,5,6])
# dots1 =np.random.rand(50)
# dots2 =np.random.rand(50)
plt.scatter(dots1,dots2,c='red',alpha=0.5) #dots1表示横坐标，dots2表示纵坐标，c表示颜色，alpha表示透明度
plt.show()
```

![png](D:\YS-学习总结\python\2381206\output_76_0.png)

### 生成柱状图plt.bar

```python
x = np.arange(10)
y = 2**x+10
plt.bar(x,y,facecolor='#9999ff',edgecolor='white')  #facecolor表示柱子颜色，edgecolor表示框的颜色
plt.show()
```

![png](D:\YS-学习总结\python\2381206\output_77_0.png)

```python
x = np.arange(10)
y = 2**x+10
plt.bar(x,y,facecolor='#9999ff',edgecolor='white')
for ax,ay in zip(x,y):
    plt.text(ax,ay,'%.1f' % ay,ha='center',va='bottom')
plt.show()
```

![png](D:\YS-学习总结\python\2381206\output_78_0.png)
