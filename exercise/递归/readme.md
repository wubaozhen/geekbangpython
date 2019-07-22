```
# 问题：要求利用递归函数调用的方式，将获取到所输入的5个字符，以相反顺序分别输出来。

def output(s,l):
    if l == 0:
        return
    print(s[l-1])
    output(s,l-1)

s = input('Input a string：')
l = len(s)
output(s,l)

# s = 'hello'
print(s[::-1]) -->逆向输出

















```
