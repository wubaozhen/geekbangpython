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
    
# 主程序中已有一个排好序的列表，请编写函数insertList，将从键盘接收的整数按原来从小到大的顺序规律插入到该列表中
def insertList(L1,x):
    '''
    思路：首先想到的二分法，用列表居中的元素跟这个值比，这样就把目标缩小了一半。然后对新的列表再二分，直到最后的列表
    元素个数为2个或1个
    :param L1:
    :param x:
    :return:
    '''
    L2 = L1[:]  # 复制一个L1
    lenth = len(L2)
    # 条件设置大于2是因为，当L2只有2个元素时，就得到了临界元素
    while lenth > 2:
        if lenth%2 == 0:
            mid = int(len(L2) / 2) -1
        else:
            mid = int(len(L2) / 2)
        if L2[mid] < x:
            L2 = L2[mid+1:]
        else:
            L2 = L2[:mid]

        lenth = len(L2)
    # 找出临界元素在元列表的索引位置，再用insert()
    inx = L1.index(L2[0])
    if L2[0] < x:
       L1.insert(inx+1,x)
    else:
       L1.insert(inx,x)


L1 = [1, 4, 6, 9, 16, 28, 40, 100]
x = int(input('请输入一个要插入的整数：'))
insertList(L1,x)
print(L1)

# 参考答案：
def insertList(L1,x):
    lenth = len(L1)
    if x > L1[lenth -1]:
        L1.append(x)
        return  # return 相当于退出函数

    for i in range(lenth):
        if x < L1[i]:
            L1.insert(i,x)
            break
    return
备注：
1.明显比我的代码简洁很多
2.要善于利用题目本身的优势：a,已经是一个排好序的列表，所以可以先跟最大一个比；b,因为已经是一个排好序的列表，所以找到小的那个就可以退出循环了

    for i in L1:
        if x < i:
            index = L1.index(i)
            L1.insert(index,x)
            break
    return

# 编写函数，生成包含20个随机数的列表，然后将前10个元素升序排列，后10个元素降序排列，并输出结果

# 参考答案：
import random
def l():
    L = [random.randint(1,100) for _ in range(20)]

    for i in range(10):
        for j in range(9,i,-1):
            if L[j-1] > L[j]:
                L[j-1],L[j] = L[j],L[j-1]

    for i in range(10,20):
        for j in range(19,i,-1):
            if L[j-1] < L[j]:
                L[j-1], L[j] = L[j], L[j-1]

    return L

print(l())

#我的答案： sorted()
import random
def l():
    L = [random.randint(1,100) for _ in range(20)]

    L1 = L[:10]
    L2 = L[10:20]
    L = sorted(L1) + sorted(L2,reverse=True)

    return L

print(l())

# 编写程序，生成一个包含20个随机整数的列表，然后对其中偶数下标的元素进行降序排列，奇数下标的元素不变

# 我的答案：
import random

L = [random.randint(1,100) for _ in range(20)]
print(L)
for i in range(0,20,2):
    for j in range(18,i,-2):  # 这里开始定18是因为最后一个偶数下标为18
        if L[j-2] < L[j]:
            L[j-2],L[j] = L[j],L[j-2]

print(L)

# 参考答案
import random

L = [random.randint(1,100) for _ in range(20)]

L1 = L[::2]
L1.sort(reverse=True)
L[::2] = L1
print(L)

# 编写函数，模拟内置函数sum()

def fsum(L):
    ret = 0
    for i in L:
        ret += i
    return ret

L = [1,2,3,4,5,6,7,8,9]
ret = fsum(L)
print(ret)

# 编写函数，模拟内置函数sorted()

思路：利用比较相邻两元素的大小
def fsorted(L):
    newL = L[:]
    lenth = len(L)
    for i in range(lenth):
       for j in range(lenth-1,i,-1):
           if newL[j-1] > newL[j]:
               newL[j-1],newL[j] = newL[j],newL[j-1]

    return newL

L = [9,8,7,6,5,4,3,2,1]
ret = fsorted(L)
print(ret)

# 参考答案：
思路：利用min()函数找到最小的，然后append到另外一个列表，当前列表再删掉这个最小的
def fsorted(v):
    t = v[::]
    r = []
    while t:
        tt = min(t)
        r.append(tt)
        t.remove(tt)
    return r

v = [9,8,7,6,5,4,3,2,1]
ret = fsorted(v)
print(ret)

# 假设有一个英文文本文件，编写程序读取其内容，并将其中的大写字母变为小写字母，小写字母变成大写字母
# 参考答案：
with open('res.txt','r') as f:
    s = f.readlines()

r = [i.swapcase() for i in s]

with open('res.txt','w') as f:
    f.writelines(r)
    
# 我的答案：
with open('res.txt','r') as f:
    text = f.read()

print(text.swapcase())

# 编写程序，生成一个包含50个随机整数的列表，然后删除其中所有奇数

# 我的答案：
import random

L = [random.randint(1,500) for _ in range(50)]
for i in L:
    if i%2:
        L.remove(i)
print(L)

# 参考答案：从后往前删
import random

L = [random.randint(1,500) for _ in range(50)]

i = len(L) -1
while i>=0:
    if L[i]%2:
        del L[i]
    i -= 1

print(L)

# 编写程序，将包含学生成绩的字典保存为二进制文件，然后再读取内容并显示

import pickle

# 保存为二进制文件
data = {'张三':89,'李四':56,'王五':70}
with open('res.pk','wb') as f:
    pickle.dump(data,f)


#读取出来
with open('res.pk','rb') as f:
    data1 = pickle.load(f)
print(data1)

# 编写程序，问题描述：
求这样的一组数据和，s=a+aa+aaa+aaaa+aa...a的值，其中a是一个数字；
例如：2+22+222+2222+22222(此时共有5个数相加)，这里具体是由几个数相加，由键盘控制

#我的答案：
n = int(input('请输入数字：'))
c = int(input('请输入数字最大的重复次数：'))

l = []
l.append(n)
n1 = n
for i in range(c-1):
    temp = n1*10 + n
    l.append(temp)
    n1 = temp

print(sum(l))

#参考答案：
from functools import reduce
Tn = 0
Sn = []
n = int(input('n = : '))  # n为次数
a = int(input('a = : '))  # a为数字
for count in range(n):
    Tn = Tn + a
    a = a * 10
    Sn.append(Tn)

# print(Sn)
Sn = reduce(lambda x,y:x+y,Sn)
print(Sn)

注：
1.reduce在python3非内建函数，需要从functools导入
2.参考答案能包含第一个，而我的答案还要先加进去
3.参考答案看着舒服，我的太丑了。。。
4.参考答案很高级的用了reduce(func,iterable)函数，

```

