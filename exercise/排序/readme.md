```
# 已知有一个已经排好序的数组。要求是，有一个新数据项，要求按原来的规律将它插入数组中。

我的答案：
L = [1,3,4,6,8,12,45,77,98]
n = int(input('pls input a num'))

if n > L[-1]:
    L.append(n)

if n < L[0]:
    L.insert(0,n)

# 复制原列表
L1 = L[:]

# 循环均分列表，直到最后元素少于2
while len(L1) > 2:
    temp = int(len(L1)/2)  # n为4，居中元素的索引
    if n > L1[temp]:
        L1 = L1[temp:]
    else:
        L1 = L1[0:temp]

# 以上跑完后，L1要么是2个元素要么是一个元素
if len(L1) == 2:
    if n > L1[1]:
        inx = L.index(L1[1])
        L.insert(inx+1,n)
    elif n > L1[0]:
        inx = L.index(L1[0])
        L.insert(inx+1,n)
else:
    if n > L1[0]:
        inx = L.index(L1[0])
        L.insert(inx+1,n)

print(L)

# 参考答案：
if __name__ == '__main__':
    a = [1,4,6,9,13,16,19,28,40,100]
    print('original list is:')
    for i in range(len(a)):
        print a[i]
    number = int(raw_input("insert a new number:\n"))
    end = a[9]
    if number > end:
        a[10] = number
    else:
        for i in range(10):
            if a[i] > number:
                temp1 = a[i]
                a[i] = number
                for j in range(i + 1,11):
                    temp2 = a[j]
                    a[j] = temp1
                    temp1 = temp2
                break
    for i in range(11):
        print a[i]


















```
