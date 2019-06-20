# 练习一 字符串


```python
# 1. 定义一个字符串Hello Python 并使用print( )输出
string1 = 'Hello Python'
print(string1)


# 2. 定义第二个字符串Let‘s go并使用print( )输出

# 字符串内容包括单引号可以使用双引号将字符串括起来
string2 = "Let's go"
print(string2)


# 3. 定义第三个字符串"The Zen of Python" -- by Tim Peters 并使用print( )输出

string3 = '"The Zen of Python" -- by Tim Peters'
print(string3)

```

# 练习二 字符串基本操作

```python
# 1. 定义两个字符串分别为 xyz 、abc
string1 = 'xyz'
string2 = 'abc'

# 2. 对两个字符串进行连接
# 字符串属于序列，序列连接操作符为“+”
print(string1 + string2)

# 3. 取出xyz字符串的第二个和第三个元素
# 序列的切片操作使用“[ ]”
print(string1[1])
print(string1[2])

# 4. 对abc输出10次
# 序列的重复操作
print(string2 * 10)

# 5. 判断a字符（串）在 xyz 和 abc 两个字符串中是否存在，并进行输出
# 判断字符是否存在于序列当中， 返回布尔值类型，如果存在返回True，不存在返回False
print('a' in string1)
print('a' in string2)

# 6.将'hello world' 转换为首字母大写'Hello World'
arr = 'hello world'.split()
new_arr = f'{arr[0].capitalize(),arr[1].capitalize()}'
print(new_arr)

# 7.如何检测字符串中只含有数字？
s1 = '12223'.isdigit()
print(s1)
s2 = 'q22u3eu'.isdigit()
print(s2)

结果如下：
# True
# False

# 8. 将字符串'ilovechina'进行反转
s1 = 'ilovechina'[::-1]
print(s1)

# 9.Python中的字符串格式化方式你知道哪些？
答： %s , format ，fstring(python3.6 开始才主持，现在推荐的写法）

# 10. 有一个字符串开头和末尾都有空格，比如' adabdw ',要求写一个函数把这个字符串的前后空格都去掉
答：因为题目是要写一个函数，所以我们不能直接使用strip,不过我们可以把它封装到函数啊

  def strip_function(s):
       return s.strip()
   s1 = ' adabdw '
   print(strip_function(s1))
   
# 11. 获取字符串'123456'最后的两个字符
a = '123456'
print(a[-2:])  或者 print(a[-2::]) 

# 12. 一个编码为GBK的字符串S，要将其转成UTF-8编码的字符串，应如何操作？
 a = 'S'.encode('gbk').decode('utf-8')
 print(a)
 
# 13. (1) s= 'info: xiaoZhang 33 shandong' ，用正则切分字符串输出['info','xiaoZhang','33','shandong']
     （2） a = '你好     中国',去除多余空格只留一个空格
 答：    
     （1）我们需要根据冒号或者空格切分
     import re
     s= 'info: xiaoZhang 33 shandong'
     res = re.split(r':| ',s)
     print(res）
     
     （2）
     a = '你好     中国'
     print(' '.join(a.split()))

```


# 练习三 列表的基本操作

```python
# 1. 定义一个含有5个数字的列表
list1 = [5, 6, 7, 8, 9]
# 使用type( )可以查看变量的类型
print(type(list1))

# 2. 为列表增加一个元素 100
# 列表自带的方法很丰富，参考官方文档
# https://docs.python.org/3.5/library/stdtypes.html#sequence-types-list-tuple-range
list1.append(100)
print(list1)

# 3. 使用remove()删除一个元素后观察列表的变化
list1.remove(7)
print(list1)

# 4. 使用切片操作分别取出列表的前三个元素，取出列表的最后一个元素
print(list1[0:3])
# 注意取出最后一个元素的类型为整型
print(list1[-1])

# 5. 如何打乱列表的元素
import random
a = [1,2,3,4,5]
random.shuffle(a)
print(a)

# 6. 已知AList = [1,2,3,1,2],对 AList 列表去重
list(set(AList))

# 7. 如何实现'1,2,3' 变成['1','2','3']
'1,2,3'.split(',')

# 8.给定两个list ,A 和 B，找出相同元素和不同元素
相同元素： print(set(A) & set(B))
不同元素： print(set(A) ^ set(B))

# 9. [[1,2],[3,4],[5,6]] 一行代码展开该列表，得出[1,2,3,4,5,6]
l = [[1,2],[3,4],[5,6]]
l1 = [II for I in l for II in I]

# 10. 合并列表[1,5,7,9] 和 [2,2,6,8]
c = [1,5,7,9].extend([2,2,6,8])
或者c = [1,5,7,9] + [2,2,6,8]

```

# 列表推导式
```
1.将字符串以空格区分，转换成列表
常规方法
s = '51 5000 10000'
li = []
for item in s.split():
    li.append(int(item))
k,a,b = li
print(k,a,b)
列表推导式
k,a,b = [int(item) for item in s.split()]
print(k,a,b)

输出
51 5000 10000
51 5000 10000

2.生成一个列表，列表元素分别为[1**2,2**2,3**2,4**2,...,n**2]
常规方法
li = []
for i in range(1,10):
    li.append(i ** 2)

print(li)
列表推导式
li = [i**2 for i in range(1,10)]
print(li)
输出
[1, 4, 9, 16, 25, 36, 49, 64, 81]
[1, 4, 9, 16, 25, 36, 49, 64, 81]

3.找出1~8之间的所有偶数，并且返回一个列表
常规方法
li = []
for i in range(1,9):
    if not i%2:
        li.append(i)
print(li)
列表推导式
li = [i for i in range(1,9) if not i % 2]
print(li)
输出
[2, 4, 6, 8]
[2, 4, 6, 8]

4.找出1~8之间的所有偶数，并且返回一个列表(元素为以这个偶数为半径的圆的面积)
常规方法
import math
li = []
for i in range(1,9,2):
    li.append(math.pi * i * i)
print(li)
列表推导式
li = [math.pi * i * i for i in range(1,9,2) ]
print(li)
注：
>>>import math
>>>math.pi
>>>3.141592653589793

5.找出1~10之间的所有奇数，并且返回一个列表(所有基数转换为字符串)
## 常规方法
l = []
for i in range(1,11,2):
    l.append(str(i))
print(l)
## 列表推导式
l = [str(i) for i in range(1,11,2)]
print(l)
## 输出
['1', '3', '5', '7', '9']
['1', '3', '5', '7', '9']

6.找出1~num之间的所有质数
思路：对正整数n,如果用2到根号n之前的所有整数去除，均无法整除，则n为质数
常规方法
import math
def prime(num):
    for n in range(2,num+1):
        for i in range(2,int(math.sqrt(n)) + 1):
            if not n % i:
                break
        else:
            print(n)

prime(51)

列表推导式
def isPrime(num):
    for i in range(2,num):
        if num % i == 0:
            return False
    else:
        return  True

print([i for i in range(2,51) if isPrime(i)])
```
# 练习四 元组的基本操作

```python
# 1. 定义一个任意元组，对元组使用append() 查看错误信息
tuple1 = ('x', 'y', 3, 4, 5)
# 元组定义完成一般不可变，也没有append方法，会报错
# AttributeError: 'tuple' object has no attribute 'append'
# tuple1.append()

# 2. 访问元组中的倒数第二个元素
# 元组也是序列，因此可以使用序列操作
print(tuple1[-2])

# 3. 定义一个新的元组，和 1. 的元组连接成一个新的元组
tuple2 = ('a', 'b', 'c')
print(tuple1 + tuple2)
# 组成新的元组之后会新申请一块内存存放元组，操作的两个元组不变
print(tuple1)
print(tuple2)

# 4. 计算元组元素个数
# 可以使用len( )方法计算，也可以使用自带的__len__( )方法得到元组元素的个数，
# 元组元素的个数和总长度是一样的
print(len(tuple1))
print(tuple1.__len__())
```


