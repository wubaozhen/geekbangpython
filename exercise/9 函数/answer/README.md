# 练习一 函数
```python
# 1. 创建一个函数，用于接收用户输入的数字，并计算用户输入数字的和
def func1():
    two_num = input('请输入两个数字，用空格做分隔：')
    # 检查用户输入是否合法
    func2(two_num)
    num1, *_, num2 = list(two_num)
    print(int(num1) + int(num2))


def func2(check_number):
    pass


func1()

#我的答案：
def Fsum():
    # 转换成列表，类似['1','2']
    args = input('请输入数字并用，分隔：').split(',')
    # 因字符串类型不能用于求和，于是转成int()
    args = [int(i) for i in args]
    ret = sum(args)
    print(ret)

Fsum()


# 2. 创建一个函数，传入n个整数，返回其中最大的数和最小的数


def func3(*nums):
    print(max(list(nums)))
    print(min(list(nums)))


func3(1, 5, 8, 32, 654, 765, 4, 6, 7)

#我的答案：
def Fun():
    num = input('传入整数用，分隔:').split(',')
    maxN = max(num)
    minN = min(num)

    return maxN,minN

maxN , minN = Fun()
print('最大的数为%s,最小的数为%s' % (maxN,minN))

注：对比参考答案，貌似我误解意思了，题目是要求函数传入参数



# 3. 创建一个函数，传入一个参数n，返回n的阶乘


def fact(num3):
    if num3 == 0 or num3 == 1:
        return 1
    else:
        return (num3 * fact(num3 - 1))


print(fact(10))


# 使用高阶函数
from functools import reduce
num4 = 10
print(reduce(lambda x, y: x * y, range(1, num4 + 1)))

# 我的答案：
def Fun(n):
    ret = 1
    for i in range(n,0,-1):
        ret *= i
    print(ret)

Fun(5)

# 4. 如果当前的日期为20190530，要求写一个函数输出N天后的日期，（比如N为2，则输出20190601）
import datetime
def Fun(n:int):
    now = datetime.datetime.now() # 获取当前时间
    delta = datetime.timedelta(days=n) # 获取指定天数后的新日期
    n_days = now + delta
    return n_days

if __name__ ==  '__main__':
    print(Fun(2))
    
# 5. 写一个函数，接收整数参数n,返回一个函数，函数的功能是把函数的参数和n相乘并把结果返回
此题考查的是闭包，闭包返回函数对象，在内部函数调用外部函数的变量
def OutFun(n):
    def InFun(i):
        return i * n
    return InFun

F = OutFun(8)
print(F(5))

# 6. 下面代码会存在什么问题，如何改进？

def strappend(num):
    str='first'
    for i in range(num):
        str+=str(i)
    return str

改进后：
def str_append(num):
    s = 'first'
    for i in range(num):
        s += str(i)
        yield s
if __name__ == '__main__':
    for i in str_append(3):
        print(i)

1.函数名用_连接单词
2.不要用内置函数名作为变量名
3.str是不可变对象，每次迭代都会生成新的内存空间，num越大，创建的str对象就会越多，内存消耗越大，使用yield改成生成器即可

# 7.一行代码输出1-100之间的所有偶数

print([i for i in range(2,101,2)])
print([i for i in range(2,101) if not i%2])
print([i for i in range(2,101) if i & 0x1 == 0])  # 这是新方法，&不好理解

# 8. 请写一个Python逻辑，计算一个文件中的大写字母数量
# 我的答案：
with open('1.txt','r') as f:
    txt = f.read()

count = 0
for i in txt:
    if i.isupper():
        count += 1
print(count)

# 参考答案
with open('1.txt') as fs:
    count = 0
    for i in fs.read():
        if i.isupper():
            count += 1
print(count)

注：可以省txt变量，其次把for写在with里面

# 9. 编写程序，生成包含1000个0到100之间的随机整数，并统计每个元素出现次数
import random
L = []
for i in range(1000):
     L.append(random.randint(0, 100))  # randint(上限，下限)

print(L)

# 字典，键为元素：值为次数
d = {}
for i in L:
    if i in d:
        d[i] += 1
    else:
        d[i] = 1

print(d)

# d的值加起来应该为1000
d_values = [v for v in d.values()] # 获取字典的值，形成一个列表
print(sum(d_values))

d_keys = [k for k in d.keys()]
print(sorted(d_keys))  # 将列表的键排序

# 参考答案：集合
import random
x = [random.randint(0,100) for i in range(1000)]  # 列表推导式

d = set(x)
for v in d:
    print(v,':',x.count(v))
    
参考答案：字典
import random
x = [random.randint(0,100) for i in range(1000)]

d = dict()
for i in x:
    d[i] = d.get(i,0) + 1  # d.get(key,[default)]:如果key存在，则返回key对应的值，如不存在，则返回default
    
# 写一个函数，实现列表的切片功能,例如用户输入[1,2,3,4,5,6]和2,5，程序输出[3,4,5,6]

#我的答案：
def slice():
    l = [int(i) for i in input('请输入一个列表:').split(',')]  # 得到一个整数列表
    n1,n2 = [int(i) for i in input('请输入2个整数作为起始和结束下标:').split(',')]  # 得到2个整数下标
    for i in range(len(l)):
        if  n1 <= i <= n2:
            print(l[i],end='')

slice()

# 参考答案： eval
x = input('Please input a list:')
x = eval(x)
start,end = eval(input('Please input the start position and the end position:'))
print(x[start:end+1])

# 写一判素数的函数，在主函数中输入一个整数，调用该函数进行判断并输出结果
import math
def isPrime(n):
    for i in range(2,int(math.sqrt(n))+1):
        if not n%i:
            print('%d 不是素数' % n)
            break
    else: # else代表for循环走完了
        print('%d 是素数' % n)

if __name__ == '__main__':
    n = 5
    isPrime(n)

# 另一个例子  for ... else ...
for i in range(5):
    print(i)
else:
    print('in else')

```

