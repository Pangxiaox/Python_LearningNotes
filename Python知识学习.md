# Python知识学习

**注：本笔记版本为Python3**



### 1. Python简介

Python是一个高层次的结合了解释性、编译性、互动性和面向对象的脚本语言

解释性：开发过程中没有编译这环节

交互式：在一个Python提示符>>>后直接执行代码



### 2. 条件语句

- if语句块关键字为：if-elif-else

```python
a = int(input("输入一个整数："))


if a == 0:
    print("0")


elif a > 0:
    print("正整数")

else:
    print("负整数")
```

🔺 1. 每个条件后面用冒号：，表示接下来是满足条件后要执行的语句块

2. 用缩进划分语句块，相同缩进数的语句组成一个语句块

3. 没有switch-case语句

- if嵌套

```python
a = float(input("输入一个数"))
if a < 7:
    if a < 4:
        print(a, "小于4")
    else:
        print(a, "大于等于4且小于7")
elif a == 7:
    print(a, "等于7")
else:
    print(a, "大于7")
```



### 3. 循环语句

- while语句

```python
n = int(input("输入一个正整数"))
sum = 0
a = 1
while a <= n:
    sum += a
    a += 1
print("1到%d的总和为:%d" % (n, sum))
```

🔺注意冒号和缩进，没有do...while循环

- while循环使用else语句：条件语句为false时候执行else语句块

```python
a = 3
while a < 6:
    print(a)
    a += 1
else:
    print("oops:%d" % a)
```

- for语句

```python
list = ['1', '2', 'a', 'b']
for item in list:
    print(item)
```

- for语句+range()函数

例子1：遍历数字序列

```python
for i in range(3):
    print(i) # 输出 0 1 2（有换行）
```

例子2：指定区间值

```python
for i in range(3, 6):
    print(i) # 输出 3 4 5（有换行）
```

例子3：指定数字区间并指定不同增量（步长），步长为负数也可以

```python
for i in range(20, 14, -2):
    print(i) # 输出 20 18 16（有换行）
```

- break语句

```python
n = 5
while n > 0:
    n -= 1
    if n == 2:
        break
    print(n)
print('循环结束。')
```

- continue语句

```python
n = 5
while n > 0:
    n -= 1
    if n == 2:
        continue
    print(n)
print('循环结束。')
```

🔺循环语句可以有else子句，在穷尽列表（for循环）或条件变为false（while循环）导致循环终止时被执行，但循环被break终止时不执行。

```python
#  查询质数
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print(n, '等于', x, '*', n//x)
            break
    else:
        # 循环中没有找到元素
        print(n, ' 是质数')
```

- pass语句

pass一般用作占位语句，不做任何事情

⭐while循环语句和for循环语句使用else的区别：

else和while循环一起用，当条件变为False时执行else语句

else和for循环一起用，else语句块只在for循环正常终止时执行



### 4. Python运算符

##### 4.1 算术运算符

/：除，x除以y（a=21 b=10 a/b结果为2.1）

//：取整除，向下取接近除数的整数（9//2等于4，-9//2等于-5）

##### 4.2 比较运算符

**4.3 赋值运算符**

**= ：幂赋值运算符

//= ：取整除赋值运算符

:=   ：海象运算符，可在表达式内部为变量赋值。Python 3.8版本新增。

**4.4 位运算符**

&、|、^（按位异或）、~（按位取反）

<<：左移运算符，高位丢弃，低位补0

＞＞：右移运算符，低位丢弃，高位补0

**4.5 逻辑运算符**

and：布尔 与、or：布尔 或、not：布尔 非

**4.6 成员运算符**

in、not in：是否在序列中（字符串/列表/元组）

**4.7 身份运算符**

is、is not：判断两个标识符是否引用自一个对象

🔺id()函数用于获取对象内存地址

⭐is与==区别：is判断两个变量引用对象是否为同一个，==判断引用变量的值是否相等

**运算符优先级**

从高到低：

| 运算符                   | 描述                               |
| ------------------------ | ---------------------------------- |
| **                       | 指数                               |
| ~ + -                    | 按位翻转，一元加号和减号（+@、-@） |
| * / % //                 | 乘除，取模，取整除                 |
| + -                      | 加减                               |
| ＞>   <<                 | 右移、左移运算                     |
| &                        | 位运算AND                          |
| ^ \|                     | 位运算符                           |
| <= < > >=                | 比较运算符                         |
| <> == !=                 | 等于运算符                         |
| = %= /= //= -= += *= **= | 赋值运算符                         |
| is is not                | 身份运算符                         |
| in not in                | 成员运算符                         |
| not and or（and高于or）  | 逻辑运算符                         |



### 5. Python 数字（Number）

Python数字类型用于存储数值。数据类型不允许改变，如果改变数字数据类型的值，将重新分配内存空间。

```python
var1 = 0x12
var2 = 0o12
var3 = complex(1, 2)
var4 = complex(5)
var5 = int(2.35)
var6 = float(5)
print(var1) # 18
print(var2)	# 10
print(var3) # (1+2j)
print(var4)	# (5+0j)
print(var5)	# 2
print(var6)	# 5.0
del var1, var2, var3, var4
print(8/3) # 2.6666666666666665（总是返回一个浮点数）
print(8//3)	# 2
print(8.0//3) # 2.0
print(8//3.0) # 2.0
```

🔺del语句删除数字对象的引用

Python支持三种不同的数值类型：整型（Int）、浮点型（float）、复数（complex）：复数的实部和虚部都是浮点型

**常用数学函数**

abs()：返回数字绝对值、pow(x,y)：x**y运算后的值

**常用随机数函数**

choice(seq)：从序列的元素中随机挑选一个元素

random()；随机生成下一个实数，它在[0,1)范围内

random.randint(x,y)：随机生成一个int类型整数，指定范围

**数学常量**

pi：圆周率、e：自然常数



### 6. Python 注释

- 单行注释：以#开头
- 多行注释：用三个单引号'''或三个双引号“”“将注释括起来

```python
#  打印出注释内容
def a():
    '''
    注释
    文本1
    '''
print(a.__doc__)
```



### 7. Python字符串

```python
a = 'abc'
b = "abcdefg"
print(a+b)	# abcabcdefg
print(a*3)	# abcabcabc	
print(b[1:4])	# bcd
print(a[1])	# b
if 'b' in a:
    print("yes")	# yes
if 'h' not in b:
    print("yes")	# yes
print(r'\n')	# \n
print(R'\n')	# \n
print("我叫 %s ，年龄为 %d" % ('ming', 24)) # 我叫 ming，年龄为 24
```

用单引号 ' 或双引号 “ 创建字符串

Python不支持单字符类型，单字符也是作为字符串使用

**Python 三引号**

三引号允许一个字符串跨多行，字符串中可包含换行符、制表符及其他特殊字符

**f-string**

字面量格式化字符串。字符串以f开头，后面跟着字符串，字符串中表达式用大括号包起来，会将变量及表达式计算后的值替换进去。

```python
w = 'ab'
str = f'a{w}'
print(str) # aab
```

Python 3.8之后，可使用 = 符号拼接运算表达式和结果：

```python
x = 1
print(f'{x+1=}')  # x+1=2
```

**Unicode字符串**

Python3中，所有字符串都是Unicode字符串

**部分字符串内建函数**

| 函数             | 描述                         |
| ---------------- | ---------------------------- |
| capitalize()     | 将字符串第一个字符转换为大写 |
| len(string)      | 字符串长度                   |
| upper()、lower() | 转换大小写字母               |



### 8. Python列表

列表数据项不需要具有相同的类型，索引从0开始。

```python
list1 = [1, 2, 3, 4]
list2 = ['a', 'b', 'c']
# 访问列表中的值
print(list1[1])	# 2
print(list1[1:3])	# [2,3]
# 更新列表
list1[0] = 0
print(list1[0])	# 0
# 删除列表元素
del list1[0]
print(list1)	# [2,3,4]
print(len(list2)) # 3
# 列表脚本操作符，+：组合列表，*：重复列表
print(list1+list2)	# [2,3,4,'a','b','c']
print(list1*2)	# [2,3,4,2,3,4]
# 列表截取
print(list1[-1])	# 4
print(list2[1:])	# ['b','c']
# 列表拼接
list1 += [1, 2, 3]
print(list1)	# [2,3,4,1,2,3]
# 嵌套列表
list3 = [list1, list2]
print(list3[1])	# ['a','b','c']
print(list3[1][1])	# b
```

**部分列表函数和方法**

| 函数/方法            | 描述                           |
| -------------------- | ------------------------------ |
| list(seq)            | 元组转换为列表                 |
| list.append(obj)     | 在列表末尾添加新对象           |
| list.reverse()       | 反向列表的元素                 |
| list.remove(obj)     | 移除列表中某个值的第一个匹配项 |
| list.clear()         | 清空列表                       |
| max(list)、min(list) | 返回列表元素的最大值/最小值    |



### 9. Python元组

元组使用小括号，元组的元素不能修改，索引从0开始。

元组的不可变指元组所指向的内存中的内容不可变。

```python
tup1 = (1, 2, 3, 4)
print(type(tup1)) # <class 'tuple'>
print(id(tup1))	# 3246458952584
# 空元组
tup2 = ()
# 元组中只含一个元素时，要在元素后面加逗号否则括号会被当作运算符使用
tup3 = (20)
print(type(tup3))	# <class 'int'>
tup4 = (20,)	
print(type(tup4))	# <class 'tuple'>
# 访问元组的值，元组截取
print(tup1[1:3])	# (2,3)
# 元组拼接和元组运算符
tup5 = tup1+tup4
print(tup5)	# (1,2,3,4,20)
print(tup4*3)	# (20,20,20)
# 元组中元素值不允许修改，下面操作非法
# tup1[0] = 5
# 这样更改元组中的元素值，但已经绑定到新对象上
tup1 = (2, 4, 6, 8)
print(id(tup1)) # 3246459038120
# 删除元组
del tup1, tup2, tup3, tup4
```

**部分元组函数**

| 函数                   | 描述                    |
| ---------------------- | ----------------------- |
| len(tuple)             | 元组元素个数            |
| max(tuple)、min(tuple) | 元组中元素最大值/最小值 |
| tuple(iterable)        | 将可迭代序列转换为元组  |



### 10. Python字典

字典是可变容器类型，可存储任意类型对象。

字典元素以键值对表示，键必须唯一，必须不可变，如字符串、数字或元组，但不能是列表；值不一定唯一，可以取任何数据类型。

```python
dict1 = {'name': "Ann", 1: 2, ('1',): 3}
# 访问字典里的值
print(dict1[1])	# 2
print(dict1['name'])	# Ann
print(dict1[('1',)])	# 3
# 修改字典（也可以新增新的键值对）
dict1[1] = 10
print(dict1[1])	# 10
dict1[2] = 20
print(dict1)	# {'name': 'Ann', 1: 10, ('1',): 3, 2: 20}
# 删除字典元素
del dict1[2]	
print(dict1)	# {'name': 'Ann', 1: 10, ('1',): 3}
# 不允许同一个键出现两次。创建时如果同一个键被赋值两次，后一个值会被记住
dict2 = {1: 2, 1: 3}
print(dict2[1])	# 3
```

**部分字典函数**

| 函数          | 描述                                 |
| ------------- | ------------------------------------ |
| len(dict)     | 计算字典元素个数，即键的总数         |
| str(dict)     | 输出字典，以可打印的字符串表示       |
| dict.values() | 以列表返回字典中所有值               |
| dict.keys()   | 以列表返回一个字典所有键             |
| dict.items()  | 以列表返回可遍历的（键，值）元组数组 |
| dict.pop(key) | 删除键为key的键值对                  |



### 11. Python集合

集合是无序的不重复元素序列

可用大括号{ }或者set()函数创建集合。创建空集合时必须用set()而不是{ }，因为{ }是用来创建一个空字典。

```python
set1 = {1, 2, 1, 3, 4}
print(set1) # {1,2,3,4}
set2 = set((1, 2, 3))
print(set2)	# {1,2,3}
# 空集合创建
set0 = set()
set3 = {1, 4, 5}
#集合a中包含而集合b中不包含的元素
print(set3 - set1) # {5}
#集合a或集合b包含的所有元素
print(set1 | set3)	# {1,2,3,4,5}
#集合a和集合b中都包含的元素
print(set1 & set3)	# {1,4}
#不同时包含于集合a和集合b的元素
print(set1 ^ set3)	# {2,3,5}
# 类似列表，支持集合推到式
a = {x for x in 'abcrabcrabc' if x not in 'abc'}
print(a)	# {'r'}
# 添加元素，如果元素已存在就不进行任何操作
set1.add(6)
print(set1)	# {1,2,3,4,6}
set1.add(1)
print(set1)	# {1,2,3,4,6}
# 添加元素另一方法，参数可以为列表、元组、字典等
set1.update({1, 7})
print(set1)	# {1,2,3,4,6,7}
set1.update([1, 2], [7, 8])
# 移除元素，如果元素不存在，会发生错误
set1.remove(3)
print(set1)	# {1,2,4,6,7,8}
# set1.remove(10)
# 移除元素，如果元素不存在，不会发生错误
set1.discard(1)
print(set1)	# {2,4,6,7,8}
set1.discard(11)
print(set1)	# {2,4,6,7,8}
# 随机删除集合中一个元素
print(set1.pop())	# 2
# 计算集合中元素个数
print(len(set1))	# 4
```

**部分集合函数**

| 函数           | 描述             |
| -------------- | ---------------- |
| clear()        | 清空集合         |
| difference()   | 返回多个集合差集 |
| union()        | 返回两个集合并集 |
| intersection() | 返回集合的交集   |



### 12. Python基本数据类型与编程基础

变量不需要声明，每个变量使用前必须赋值，变量赋值后该变量才会被创建。

**多个变量赋值**

```python
a = b = 1
print(a)	# 1
print(b)	# 1
c, d = 'a', 5
print(c)	# a
print(d)	# 5
```

**标准数据类型**

- 不可变数据：Number（数字）、String（字符串）、Tuple（元组）
- 可变数据：List（列表）、Dictionary（字典）、Set（集合）

**判断类型：type()和isinstance()**

```python
class A:
    pass


class B(A):
    pass


print(type(A()) == A) 	# True
print(type(B()) == A)	# False
print(isinstance(A(), A))	# True
print(isinstance(B(), A))	# True
```

type()不会认为子类是一种父类类型

isinstance()会认为子类是一种父类类型

**Python数据类型转换**

| 函数      | 描述                                         |
| --------- | -------------------------------------------- |
| ord(x)    | 将一个字符转换为它的整数值                   |
| eval(str) | 计算字符串中有效Python表达式，并返回一个对象 |

**等待用户输入**

```python
input("\n\n按下enter键退出。")
```

**end关键字**

用于将结果输出到同一行，或在输出末尾添加不同字符

```python
for i in range(0, 4):
    print(i, end=',') #	0,1,2,3,
```

*args、**kwargs用法

```python
def foo(*args, **kwargs):
    print ('args = ', args)
    print ('kwargs = ', kwargs)
    print ('---')

if __name__ == '__main__':
    foo(1,2,3,4)
    foo(a=1,b=2,c=3)
    foo(1,2,3,4, a=1,b=2,c=3)
    foo('a', 1, None, a=1, b='2', c=3)
    
'''
args =  (1, 2, 3, 4)
kwargs =  {}
---
args =  ()
kwargs =  {'a': 1, 'b': 2, 'c': 3}
---
args =  (1, 2, 3, 4)
kwargs =  {'a': 1, 'b': 2, 'c': 3}
---
args =  ('a', 1, None)
kwargs =  {'a': 1, 'b': '2', 'c': 3}
---
'''
```

- `*args`表示任何多个无名参数，是一个元组
- `**kwargs`表示关键字参数，是一个字典
- 同时使用 `*args`和 `**kwargs`时，必须 `*args`参数列要在 `**kwargs`前



### 13. Python迭代器与生成器

**13.1 迭代器**

迭代器是访问集合元素的一种方式。迭代器是一个可以记住遍历的位置的对象。迭代器对象从集合的第一个元素开始访问，直到所有元素被访问完结束。迭代器只能往前不能后退。字符串、元组或列表都可创建迭代器。

```python
import sys
list = [1,2,3]
it = iter(list)

while True:
    try:
        print(next(it))
    except StopIteration:
        sys.exit()
```

iter()创建迭代器对象、next()输出迭代器下一元素

**创建一个迭代器**

```python
class A:
    def __iter__(self):
        self.a = 1
        return self

    def __next__(self):
        x = self.a
        self.a += 2
        return x

myA = A()
myiter = iter(myA)
print(next(myiter))	# 1
print(next(myiter))	# 3
print(next(myiter))	# 5
```

**StopIteration**

用于表示迭代的完成，防止出现无限循环情况。

```python
class A:
    def __iter__(self):
        self.a = 1
        return self

    def __next__(self):
        if self.a <= 7:
            x = self.a
            self.a += 2
            return x
        else:
            raise  StopIteration


myA = A()
myiter = iter(myA)
for x in myiter:
    print(x, end=" ")	# 1 3 5 7
```

**13.2 生成器**

使用了yield的函数被称为生成器。生成器是一个返回迭代器的哈数，只能用于迭代操作。

在调用生成器运行的过程中，每次遇到yield时函数会暂停并保存当前所有的运行信息，返回yield的值，并在下一次执行next()方法时从当前位置继续运行。

```python
import sys


def fibonacci(n):  # 生成器函数 - 斐波那契
    a, b, counter = 0, 1, 0
    while True:
        if (counter > n):
            return
        yield a
        a, b = b, a + b
        counter += 1


f = fibonacci(5)  # f 是一个迭代器，由生成器返回生成

while True:
    try:
        print(next(f), end=" ")	# 0 1 1 2 3 5
    except StopIteration:
        sys.exit()
```



### 14. Python 模块

模块是一个包含所有你定义的函数和变量的文件，后缀名是.py。模块可以被别的程序引入，以使用该模块中的函数等功能。这也是使用Python标准库的方法。

**import语句**

**from...import语句**：从模块中导入一个只当的部分到命名空间中

**from...import * 语句**：把一个模块所有内容全部导入到当前命名空间

**dir()函数**

找到模块内定义的所有名称。以一个字符串列表形式返回

如果没有给定参数，dir()函数罗列出当前定义的所有名称

```python
a = [1,2,3]
import sys
# ['__annotations__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'a', 'sys']
print(dir())
# omit
print(dir(sys))
```

**包、从一个包中导入 ***

包是一种管理Python模块命名空间的形式，采用“点模块名称”。

如一个模块名称是A.B，表示一个包A中的子模块B



### 15. Python File（文件）

open()函数打开一个文件，并返回文件对象。如果该文件无法被打开，会抛出OSError。

⭐open()方法一定要保证关闭文件对象，即调用close()方法。

常用形式为：`open(file,mode='r')`

mode参数：

| 模式 | 描述                                                         |
| ---- | ------------------------------------------------------------ |
| t    | 文本模式（默认）                                             |
| x    | 写模式，新建一个文件，如果该文件已存在会报错                 |
| b    | 二进制模式                                                   |
| r    | 以只读方式打开文件。文件的指针会放在文件开头，是默认模式     |
| w    | 打开一个文件只用于写入。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。 |
| w+   | 打开一个文件用于读写。如果该文件已存在则打开文件，并从开头开始编辑，即原有内容会被删除。如果该文件不存在，创建新文件。 |
| a    | 打开一个文件用于追加。如果该文件已存在，文件指针将会放在文件的结尾。也就是说，新的内容将会被写入到已有内容之后。如果该文件不存在，创建新文件进行写入。 |
| r+   | 打开一个文件用于读写。文件指针将会放在文件的开头。           |

file对象：

使用open函数创建

| 方法                       | 描述                                                         |
| -------------------------- | ------------------------------------------------------------ |
| file.close()               | 关闭文件。关闭后文件不能再进行读写                           |
| file.flush()               | 刷新文件内部缓冲，直接把内部缓冲区的数据立刻写入文件，而不是被动地等待输出缓冲区写入 |
| file.write(str)            | 将字符串写入文件，返回的是写入的字符长度                     |
| file.read([size])          | 从文件读取指定的字节数，如果未给定或为负则读取所有           |
| file.seek(offset[,whence]) | 移动文件读取指针到指定位置                                   |

```python
f = open('a.txt', mode='w+')
f.write("abcd")
f.seek(0)
print(f.read())	# abcd
```



### 16. Python OS

os模块提供了很多方法来处理文件和目录：

| 方法                 | 描述             |
| -------------------- | ---------------- |
| os.access(path.mode) | 检验权限模式     |
| os.chdir(path)       | 改变当前工作目录 |
| os.getcwd()          | 返回当前工作目录 |
| os.chmod(path,mode)  | 更改权限         |



### ⭐17. Python 内存管理

python内存管理是由私有堆空间管理的，所有的python对象和数据结构都存储在私有堆空间中。程序员没有访问堆的权限，只有解释器才能操作。为python的堆空间分配内存的是python的内存管理模块进行的，核心api会提供一些访问该模块的方法供程序员使用。python自有的垃圾回收机制回收并释放没有被使用的内存供别的程序使用。

**17.1 对象的内存使用**

```python
a = 2
b = 2
print(a is b)	# True

a = "ab"
b = "ab"
print(a is b)	# True

a = []
b = []
print(a is b)	# False
```

python缓存了整数和短字符串，因此每个对象只存有一份，使用赋值语句只是创造了新的引用而不是对象本身。

**17.2 引用计数**

```python
from sys import getrefcount
a = [1, 2, 3]
print(getrefcount(a))   # 2
b = a
print(getrefcount(b))   # 3
```

python每个对象都存有指向该对象的引用总数。

当使用某个引用作为参数，传递给getrefcount()时会创建一个临时引用，所以结果比预期多1.

**对象引用对象**

```python
class from_obj():
    def __init__(self, to_obj):
        self.to_obj = to_obj


b = [1, 2, 3]
a = from_obj(b)
print(a.to_obj is b) # True
```

容器对象中包含的并不是对象本身，而是指向各个元素对象的引用

```python
from sys import getrefcount
a = [1, 2, 3]
print(getrefcount(a))	# 2
b = [a, a]	
print(getrefcount(a))	# 4
```

对象b引用了a两次，a引用计数加2

🔺两个对象可能互相引用，构成**引用环**。即使是一个对象，只需自己引用自己，也能构成引用环。引用环给垃圾回收机制带来很大麻烦。

```python
a = []
b = [a]
a.append(b)
print(a) # [[[...]]]
```

```python
from sys import getrefcount
a = []
a.append(a)
print(getrefcount(a))	# 3
```

**引用减少**

del关键字删除某个引用

```python
from sys import getrefcount
a = [1,2,3]
b = a
print(getrefcount(b))	# 3
del a
print(getrefcount(b))	# 2
```

如果某个引用指向对象a，当这个引用被重新定向到其他对象b时，对象a引用计数会减少

```python
from sys import getrefcount
a = [1,2,3]
b = a
print(getrefcount(b))	# 3
a = 1
print(getrefcount(b))	# 2
```

**17.3 垃圾回收**

python会在适当时候启动垃圾回收机制，将没用的对象清除。

**原理**：当一个对象的引用计数降为0时说明没有任何引用指向对象，这时该对象成为需要被清除的垃圾。

垃圾回收的时候，python不能进行其他任务；频繁的垃圾回收会大大降低python工作效率。如果内存中对象不多，没必要总启动垃圾回收。python只在特定条件下自动垃圾回收。

**python运行时，记录其中分配对象和取消分配对象的次数，两者差值高于某个阈值时，垃圾回收才会启动**

```python
import gc
print(gc.get_threshold()) # (700,10,10)
```

返回值中后面两个10，是与分代回收相关的阈值，700是垃圾回收的启动阈值。可通过gc中的 `set_threshold()`来重新设定。也可手动使用 `gc.collect()`启动垃圾回收机制

**17.4 分代回收**

**基本假设**：存活时间越久的对象，越不可能在后面的程序中变成垃圾。我们的程序往往会产生大量的对象，许多对象很快产生和消失，但也有长期存在被使用的对象，出于信任和效率，对于这样一些对象，我们相信他的用处，所以减少在垃圾回收中扫描他们的频率。

python将所有的对象分为0,1,2三代，所有新建的对象都是0代对象，当某一代对象经历过垃圾回收之后，依然存活，那就归入到下一代中，垃圾回收启动时，一定会扫描所有的0代对象。如果0代对象经历过一定次数的垃圾回收，那么就启动对0代和1代的扫描清理，当1代也经历了一定数量的垃圾回收，那就启动对0,1,2代即所有的对象进行扫描。

上述 `gc.get_threshold()`返回的（700，10，10）表示：**每经过10次对0代的垃圾回收，就会配合启动一次对1代的扫描；每经过10次对1代的扫描，才启动一次对2代的垃圾回收**

**17.5 孤立的引用环**

引用环可能构成无法使用，但是引用计数不为0的对象

为了回收这样的引用环，**python复制每个对象的引用计数，记为gc_ref。假设对于每个对象i，计数为gc_ref_i。python会遍历所有对象i，对于每个对象i引用的对象j，将相应gc_ref_j减1**。结束遍历后，gc_ref不为0的对象和这些对象引用的对象以及继续更下游引用的对象需要被保留，其他对象则被垃圾回收。



### ⭐18. Python装饰器

**18.1 本质和功能**

本质：一个闭包函数（高阶函数+嵌套函数）

功能：在不修改原函数以及其调用方式情况下对原函数功能进行扩展

**18.2 闭包原理**

```python
def print_msg():
    msg = "is a closure"

    def printer():
        print(msg)

    return printer

closure = print_msg()
closure()	# 输出 is a closure
```

闭包就是引用了自有变量的函数，这个函数保存了执行的上下文，可以脱离原本作用域独立存在。

**18.3 装饰器**

```python
import functools


def log(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        print('call %s():' % func.__name__)
        print('args = {}'.format(*args))
        return func(*args, **kwargs)

    return wrapper


@log
def test(p):
    print(test.__name__ + " param: " + p)


test("I'm a param")

'''
call test():
args = I'm a param
test param: I'm a param
'''
```

上面的@语法只是将函数传入装饰器函数，下面这个写法结果一样：

```python
def test(p):
    print(test.__name__ + " param: " + p)


wrapper = log(test)
wrapper("I'm a param")
```

🔺 `@functions.wraps(func)`是python提供的装饰器，可以把原函数的元信息拷贝到装饰器里面的func函数中。函数元信息包括docstring、name、参数列表等。

**18.4 带参数的装饰器**

```python
import functools


def log_with_param(text):
    def decorator(func):
        @functools.wraps(func)
        def wrapper(*args, **kwargs):
            print('call %s():' % func.__name__)
            print('args = {}'.format(*args))
            print('log_param = {}'.format(text))
            return func(*args, **kwargs)

        return wrapper

    return decorator


def test_with_param(p):
    print(test_with_param.__name__)
    
# 传入装饰器的参数，并接收返回的decorator函数
decorator = log_with_param("param")
# 传入test_with_param函数
wrapper = decorator(test_with_param)
# 调用装饰器函数
wrapper("I'm a param")

'''
call test_with_param():
args = I'm a param
log_param = param
test_with_param
'''
```

一个携带了参数的装饰器将有三层函数

**18.5 类装饰器**

```python
class DecorateDemo(object):
    def  __init__(self, func):
        self.__func = func
    def  __call__(self):
        print("before class decorator")
        self.__func()
        print("after class decorator")
        return self.__func

@DecorateDemo
def test():
    print("this is what I want")

test()

'''
before class decorator
this is what I want
after class decorator
'''
```

用法：让类的构造函数 `__init__()`接收一个参数 👉 重载 `__call__()`并返回一个函数 👉 使用 `@类`形式将装饰器附加到业务函数上

**18.6 多个装饰器**

```python
def log(func):
    def wrapper():
        print("call test()")
        result = func()
        print("end test()")
        return result 
    return wrapper

def hello(func):
    def wrapper():
        print("hello test()")
        result = func()
        print("goodbye test()")
        return result 
    return wrapper

@log
@hello
def test():
    print("this is what I want")

test()

'''
call test()
hello test()
this is what I want
goodbye test()
end test()
'''
```

先调用最里层装饰器，最后调用最外层装饰器



### ⭐19. Python多线程

参考自： [https://www.cnblogs.com/luyuze95/p/11289143.html#%E4%B8%89gilglobal-interpreter-lock%E5%85%A8%E5%B1%80%E8%A7%A3%E9%87%8A%E5%99%A8%E9%94%81](https://www.cnblogs.com/luyuze95/p/11289143.html#三gilglobal-interpreter-lock全局解释器锁)

**19.1 多线程实现**

**threading模块**

```python
import threading
import time

def run(n):
    print("task", n)
    time.sleep(1)
    print('2s')
    time.sleep(1)
    print('1s')
    time.sleep(1)
    print('0s')
    time.sleep(1)


if __name__ == '__main__':
    t1 = threading.Thread(target=run, args=("t1",))
    t2 = threading.Thread(target=run, args=("t2",))
    t1.start()
    t2.start()
    
'''
task t1
task t2
2s
2s
1s
1s
0s
0s
'''
```

**自定义线程**

```python
import threading
import time


class MyThread(threading.Thread):
    def __init__(self, n):
        super(MyThread, self).__init__()  # 重构run函数必须要写
        self.n = n

    def run(self):
        print("task", self.n)
        time.sleep(1)
        print('2s')
        time.sleep(1)
        print('1s')
        time.sleep(1)
        print('0s')
        time.sleep(1)

if __name__ == "__main__":
    t1 = MyThread("t1")
    t2 = MyThread("t2")
    t1.start()
    t2.start()
    
'''
task t1
task t2
2s
2s
1s
1s
0s
0s
'''
```

**守护线程**

把所有子线程变成了主线程的守护线程，因此当主线程结束之后子线程也会随之结束。所以当主线程结束之后，整个程序就退出了。

```python
import threading
import time

def run(n):
    print("task", n)
    time.sleep(1)       #此时子线程停1s
    print('3')
    time.sleep(1)
    print('2')
    time.sleep(1)
    print('1')

if __name__ == '__main__':
    t = threading.Thread(target=run, args=("t1",))
    t.setDaemon(True)   #把子进程设置为守护线程，必须在start()之前设置
    t.start()
    print("end")
    
'''
task t1
end
'''
```

**主线程等待子线程结束**

使用join方法，让主线程等待子线程执行，这样守护线程执行结束之后主线程再结束

```python
import threading
import time

def run(n):
    print("task", n)
    time.sleep(1)       #此时子线程停1s
    print('3')
    time.sleep(1)
    print('2')
    time.sleep(1)
    print('1')

if __name__ == '__main__':
    t = threading.Thread(target=run, args=("t1",))
    t.setDaemon(True)   #把子进程设置为守护线程，必须在start()之前设置
    t.start()
    t.join() # 设置主线程等待子线程结束
    print("end")
```

**多线程共享全局变量**

同一个进程中的多线程共享资源

```python
import threading
import time

g_num = 100

def work1():
    global g_num
    for i in range(3):
        g_num += 1
    print("in work1 g_num is : %d" % g_num)

def work2():
    global g_num
    print("in work2 g_num is : %d" % g_num)

if __name__ == '__main__':
    t1 = threading.Thread(target=work1)
    t1.start()
    time.sleep(1)
    t2 = threading.Thread(target=work2)
    t2.start()
    
'''
in work1 g_num is : 103
in work2 g_num is : 103
'''
```

**互斥锁**

由于线程之间随即调度，如果多个线程同时操作一个对象，如果没有很好地保护该对象，会造成程序结果的不可预期，**称为线程不安全**

```python
from threading import Thread,Lock
import os, time


def work():
    global n
    lock.acquire()
    temp=n
    time.sleep(0.1)
    n=temp-1
    lock.release()


if __name__ == '__main__':
    lock=Lock()
    n=100
    l=[]
    for i in range(100):
        p=Thread(target=work)
        l.append(p)
        p.start()
    for p in l:
        p.join()
```

**递归锁**

RLock类支持嵌套，在多个锁没有释放时一般使用RLock类

```python
import threading
import time

def Func(lock):
    global gl_num
    lock.acquire()
    gl_num += 1
    time.sleep(1)
    print(gl_num)
    lock.release()

if __name__ == '__main__':
    gl_num = 0
    lock = threading.RLock()
    for i in range(10):
        t = threading.Thread(target=Func, args=(lock,))
        t.start()

'''
// 分10行输出 1 2 3 ... 9  10
'''
```

**信号量BoundedSemaphore**

互斥锁同时只允许一个线程更改数据，信号量同时允许一定数量线程更改数据

```python
import threading
import time

def run(n, semaphore):
    semaphore.acquire()   #加锁
    time.sleep(1)
    print("run the thread:%s\n" % n)
    semaphore.release()     #释放

if __name__ == '__main__':
    num = 0
    semaphore = threading.BoundedSemaphore(5)  # 最多允许5个线程同时运行
    for i in range(12):
        t = threading.Thread(target=run, args=("t-%s" % i, semaphore))
        t.start()
    while threading.active_count() != 1:
        pass  # print threading.active_count()
    else:
        print('-----all threads done-----')
        
'''
run the thread:t-0
run the thread:t-1
run the thread:t-4
run the thread:t-2
run the thread:t-3





run the thread:t-7
run the thread:t-6

run the thread:t-9

run the thread:t-5
run the thread:t-8



run the thread:t-11
run the thread:t-10


-----all threads done-----
'''
```

**事件（Event类）**

python线程的事件用于主线程控制其他线程执行，事件是一个简单的线程同步对象，主要有以下方法：

- clear()：将flag设置为“False”
- set()：将flag设置为“True”
- is_set()：判断是否设置了flag
- wait()：一直监听flag，如果没有检测到flag就一直处于阻塞状态

事件处理机制：全局定义了一个“Flag”，当flag值为“False”，event.wait()会阻塞；当flag值为“True”，event.wait()不再阻塞

```python
#利用Event类模拟红绿灯
import threading
import time

event = threading.Event()


def lighter():
    count = 0
    event.set()     #初始值为绿灯
    while True:
        if 5 < count <=10 :
            event.clear()  # 红灯，清除标志位
            print("\33[41;1mred light is on...\033[0m")
        elif count > 10:
            event.set()  # 绿灯，设置标志位
            count = 0
        else:
            print("\33[42;1mgreen light is on...\033[0m")

        time.sleep(1)
        count += 1

def car(name):
    while True:
        if event.is_set():      #判断是否设置了标志位
            print("[%s] running..."%name)
            time.sleep(1)
        else:
            print("[%s] sees red light,waiting..."%name)
            event.wait()
            print("[%s] green light is on,start going..."%name)

light = threading.Thread(target=lighter,)
light.start()

car = threading.Thread(target=car, args=("MINI",))
car.start()
```

**19.2 GIL（Global Interpreter Lock）全局解释器锁**

**GIL介绍和背景**

在非python环境中，单核情况下，同时只能有一个任务执行。多核时可以支持多个线程同时执行。但是在python中，无论有多少核，同时只能执行一个线程。究其原因，这就是由于GIL的存在导致的。

GIL的全称是Global Interpreter Lock(全局解释器锁)，来源是python设计之初的考虑，为了数据安全所做的决定。某个线程想要执行，必须先拿到GIL，我们可以把GIL看作是“通行证”，并且在一个python进程中，GIL只有一个。拿不到通行证的线程，就不允许进入CPU执行。GIL只在cpython中才有，因为cpython调用的是c语言的原生线程，所以他不能直接操作cpu，只能利用GIL保证同一时间只能有一个线程拿到数据。而在pypy和jpython中是没有GIL的。

**python多线程工作过程**

python在使用多线程的时候，调用的是c语言的原生线程。

- 拿到公共数据
- 申请GIL
- python解释器调用os原生线程
- os操作cpu执行运算
- 当该线程执行时间到后，无论运算是否已经执行完，GIL都被要求释放
- 进而由其他进程重复上面的过程
- 等其他进程执行完后，又会切换到之前的线程（从他记录的上下文继续执行），整个过程是每个线程执行自己的运算，当执行时间到就进行切换（context switch）。

**python针对不同类型的代码执行效率不同**

- **CPU密集型代码** (各种循环处理、计算等等)，在这种情况下，由于计算工作多，ticks计数很快就会达到阈值，然后触发GIL的释放与再竞争（多个线程来回切换当然是需要消耗资源的），所以**python下的多线程对CPU密集型代码并不友好**。
- **IO密集型代码** (文件处理、网络爬虫等涉及文件读写的操作)，多线程能够有效提升效率(单线程下有IO操作会进行IO等待，造成不必要的时间浪费，而开启多线程能在线程A等待时，自动切换到线程B，可以不浪费CPU的资源，从而能提升程序执行效率)。所以**python的多线程对IO密集型代码比较友好**。

**实际使用建议**

python下想要充分利用多核CPU，就用多进程。因为每个进程有各自独立的GIL，互不干扰，这样就可以真正意义上的并行执行，在python中，多进程的执行效率优于多线程(仅仅针对多核CPU而言)。

**GIL在python中版本差异**

- 在python2.x里，GIL的释放逻辑是当前线程遇见IO操作或者ticks计数达到100时进行释放。（ticks可以看作是python自身的一个计数器，专门做用于GIL，每次释放后归零，这个计数可以通过sys.setcheckinterval 来调整）。而每次释放GIL锁，线程进行锁竞争、切换线程，会消耗资源。并且由于GIL锁存在，python里一个进程永远只能同时执行一个线程(拿到GIL的线程才能执行)，这就是为什么在多核CPU上，python的多线程效率并不高。
- 在python3.x中，GIL不使用ticks计数，改为使用计时器（执行时间达到阈值后，当前线程释放GIL），这样对CPU密集型程序更加友好，但依然没有解决GIL导致的同一时间只能执行一个线程的问题，所以效率依然不尽如人意。



### 20. Python封装、继承与多态

**20.1 封装**

将数据与具体操作的实现代码放在某个对象内部，外界只能通过接口使用该对象而不能通过任何形式修改对象内部实现。

```python
    class Student:
        def __init__(self,name, age):
            self.name = name
            self.age = age
        def printInfo(self):
            print("name:{}".format(self.name), "age:{}".format(self.age))
    # 下面的操作都是错误的！原因：类将它内部的变量和方法封装起来，阻止外部的直接访问
    print(name)
    print(age)
    printInfo()
```

**20.2 继承**

```python
# 父类定义
class people:
    def __init__(self, name, age, weight):
        self.name = name
        self.age = age
        self.__weight = weight

    def speak(self):
        print("%s 说: 我 %d 岁。" % (self.name, self.age))


# 单继承示例
class student(people):

    def __init__(self, name, age, weight, grade):
        # 调用父类的实例化方法
        people.__init__(self, name, age, weight)
        self.grade = grade

    # 重写父类的speak方法
    def speak(self):
        print("%s 说: 我 %d 岁了，我在读 %d 年级" % (self.name, self.age, self.grade))


s = student('ken', 10, 30, 3)
s.speak()

'''
ken 说: 我 10 岁了，我在读 3 年级
'''
```

**继承原则**

- 子类在调用某个方法或变量时，首先在自己内部查找，如果没有找到，则开始根据继承机制在父类查找

```python
class D:
    pass


class C(D):
    pass


class B(C):
    def show(self):
        print("i am B")

    pass


class G:
    pass


class F(G):
    pass


class E(F):
    def show(self):
        print("i am E")

    pass


class A(B, E):
    pass


a = A()
a.show()

'''
i am B
'''
```

继承参数书写有先后顺序，写在前面被优先继承

- 根据父类定义中的顺序，以DFS方式逐一查找父类

```python
class D:
    def show(self):
        print("i am D")

    pass


class C(D):
    pass


class B(C):
    pass


class G:
    pass


class F(G):
    pass


class E(F):
    def show(self):
        print("i am E")

    pass


class A(B, E):
    pass


a = A()
a.show()

'''
i am D
'''
```

🔺当类D和类G同时继承了类H：

```python
class H:
    def show(self):
        print("i am H")

    pass


class D(H):
    pass


class C(D):
    pass


class B(C):
    pass


class G(H):
    pass


class F(G):
    pass


class E(F):
    def show(self):
        print("i am E")

    pass


class A(B, E):
    pass


a = A()
a.show()

'''
i am E
'''
```

🔺其他更复杂继承情况

```python
class D():
    pass


class G():
    def show(self):
        print("i am G")

    pass


class F(G):
    pass


class C(D):
    pass


class B(C, F):
    pass


class E(F):
    def show(self):
        print("i am E")

    pass


class A(B, E):
    pass

a = A()
print(a.show())

'''
i am E
'''
```

**super()函数**

在子类中如果有与父类同名的成员，会覆盖掉父类里的成员。如果想强制调用父类的成员则需要使用super()函数。传入子类名和self，调用父类的方法，按父类的方法需要传入参数

```python
class A:
    def __init__(self, name):
        self.name = name
        print("父类的__init__方法被执行了！")

    def show(self):
        print("父类的show方法被执行了！")


class B(A):
    def __init__(self, name, age):
        super(B, self).__init__(name=name)
        self.age = age

    def show(self):
        super(B, self).show()


obj = B("jack", 18)
obj.show()

'''
父类的__init__方法被执行了！
父类的show方法被执行了！
'''
```

**类型判断**

继承关系中，如果一个实例的数据类型是某个子类，那它的数据类型也可以被看做父类，但反过来不行。

```python
class Animal:
    pass


class Dog(Animal):
    pass


dog = Dog()
b = Animal()
print(isinstance(b, Dog))	# False
print(isinstance(dog, Dog))	# True
print(isinstance(b, Animal))	# True
print(isinstance(dog, Animal))	# True
```

**多重继承**

```python
class Runnable(object):
    def run(self):
        print('Running...')


class Flyable(object):
    def fly(self):
        print('Flying...')


class Dog(Runnable, Flyable):
    pass


d = Dog()
d.fly()
d.run()

'''
Flying...
Running...
'''
```

**20.3 多态**

```python
class Animal:

    def kind(self):
        print("i am animal")


class Dog(Animal):

    def kind(self):
        print("i am a dog")


class Cat(Animal):

    def kind(self):
        print("i am a cat")


class Pig(Animal):

    def kind(self):
        print("i am a pig")


# 这个函数接收一个animal参数，并调用它的kind方法
def show_kind(animal):
    animal.kind()


d = Dog()
c = Cat()
p = Pig()

show_kind(d)
show_kind(c)
show_kind(p)

'''
i am a dog
i am a cat
i am a pig
'''
```

⭐Python语言的动态语言特性，传递给函数show_kind()的参数animal可以是任何类型，只要它有一个kind()方法即可。动态语言调用实例方法不检查类型，只要方法存在，参数正确，就可以调用



### 21. Python浅拷贝和深拷贝

①浅拷贝：没有拷贝子对象，原始数据改变，子对象会改变

```python
import copy
list1 = [1, 2, [1, 3, 4], 7]
list2 = copy.copy(list1)
print(list1,list2)
list1.append(4)
print(list1,list2)
list1[2].append(6)
print(list1,list2)

'''
[1, 2, [1, 3, 4], 7] [1, 2, [1, 3, 4], 7]
[1, 2, [1, 3, 4], 7, 4] [1, 2, [1, 3, 4], 7]
[1, 2, [1, 3, 4, 6], 7, 4] [1, 2, [1, 3, 4, 6], 7]
'''
```

②深拷贝：包含对象里子对象的拷贝，原始数据改变不会造成深拷贝里任何子元素的改变

```python
import copy
list1 = [1, 2, [1, 3, 4], 7]
list2 = copy.deepcopy(list1)
print(list1,list2)
list1.append(4)
print(list1,list2)
list1[2].append(6)
print(list1,list2)

'''
[1, 2, [1, 3, 4], 7] [1, 2, [1, 3, 4], 7]
[1, 2, [1, 3, 4], 7, 4] [1, 2, [1, 3, 4], 7]
[1, 2, [1, 3, 4, 6], 7, 4] [1, 2, [1, 3, 4], 7]
'''
```

③列表和元组的深拷贝和浅拷贝

列表可变，元组不可变

```python
import copy
tuple1 = (1, 2, 3)
tuple2 = copy.copy(tuple1)
tuple3 = copy.deepcopy(tuple1)
print(tuple1 is tuple2)	#True
print(tuple1 is tuple3)	#True
print(tuple2 is tuple3)	#True

list1 = [1, 2, 3]
list2 = copy.copy(list1)
list3 = copy.deepcopy(list1)
print(list1 is list2)	#False
print(list2 is list3)	#False
print(list2 is list3)	#False
```



### 22. 排序 sort与sorted

Python list内置sort()方法用来排序，Python内置全局的sorted()方法来对可迭代序列排序生成新的序列。对dict的排序默认会按照key值排序，通过指定key参数可对value排序

**对字典的value排序**

```python
dict = {'a': 5, 'c': 2, 'b': 6}
res1 = sorted(dict)
print(res1)	#['a','b','c']
res2 = sorted(dict, key=lambda x: dict[x])
print(res2)	#['c','a','b']
```

