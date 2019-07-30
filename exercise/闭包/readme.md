```
# 函数嵌套格式：

def f1():
    print('hello')
    def f2():
        print('world')
    f2()

f1()

输出：
hello
world

# 在函数嵌套的基础上给外层函数加个参数，此参数在内层函数能访问，就成闭包了，格式如下：
def f1(x):
    print('hello')
    def f2():
        print('world'*x)
    f2()

f1(2)

输出：
hello
worldworld

注：闭包的目的是增加数据的安全性，放在内层函数里，只有外层函数能调用

# 在闭包的基础上继续衍生出装饰器，即外层函数的参数是一个函数，返回的也是一个函数




# 变量作用域

x = 1
def foo():
    print(x) ----> 会报UnboundLocalError: local variable 'x' referenced before assignment
    x = 10
foo()
-----------------------------------------------------
x = 1
def foo():
    print(x) 
foo()
没报错，打印1
------------------------------------------------------
x = 1
def foo():
    global x
    print(x)
    x = 10
foo()
print(x)
也不会报错，打印1 10

同理，如果是在内部函数想访问外部函数的变量，就用nonlocal 关键字









```
