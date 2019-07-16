```
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

# 编写程序：问题简述：假设一支皮球从100米高度自由落下。条件，每次落地后反跳回原高度的一半后，再落下。

要求：算出这支皮球，在它在第10次落地时，共经过多少米？第10次反弹多高？

# 我的答案：
n = 100
t = 10
l = []  # 初始化
while t > 0:
   temp = round(n/2,1)  # 保留一位小数
   l.append(temp)
   n = temp
   t -= 1

for i,v in enumerate(l,1): # 1表示索引从1开始
    if i == 10:
        print('第10次反弹%f' % v)

print(sum(l)) # 第10次落地，共经过的米数

# 参考答案：
Sn = 100.0
Hn = Sn/2

for n in range(2,11):  # 循环9次
    Sn += 2*Hn  # 这里乘2代表反弹掉落
    Hn /= 2

print('Total of road is %f' %Sn)
print('The tenth is %f meter' % Hn)


# 注：
1 用range()限定循环次数，都省了判断if i == 10:,得到结论，知道循环几次的情况下就用range

# 问题简述：一只小猴子吃桃子的问题。
话说，一只小猴子第一天摘下若干个桃子，并吃了一半。感觉到吃的还不瘾，于是又多吃了一个；
第二天早上，又将剩下的桃子吃掉一半，又多吃了一个。
以后每天早上,都吃了前一天剩下的一半零一个。

# 参考答案：
x2 = 1
for day in range(9,0,-1):
    x1 = (x2+1) *2
    x2 = x1

print(x1)
