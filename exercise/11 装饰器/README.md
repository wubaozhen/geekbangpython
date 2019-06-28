# 练习一 定义装饰器，用于打印函数执行的时间
1. 统计函数开始执行和结束执行的时间
2. 扩展练习：为装饰器传入超时时间，函数执行超过指定时间后退出




# 练习二 定义装饰器，实现不同颜色显示执行结果的功能
1. 向装饰器传递参数，通过传递的参数获取到输出的颜色
2. 被装饰函数的print( )输出根据装饰器得到的颜色进行输出


# 我对装饰器的理解
```
def register(fn):
    print('in register')
    def wrap(*args,**kwargs):
        ret = fn(*args,**kwargs)
        return ret
        print('in wrap')
    return wrap

@register
def add(x,y):
    print('in add')
    return x + y

@register
def multi(x,y):
    print('in multi ')
    return x * y

```
如上：脚本执行会打印2行 in register,说明程序走到@register，会执行register函数

如果在脚本最后加上add(),且把ret = fn(*args,**kwargs) 和 print ret注调，那么程序会打印2行in register 和 in wrap,说明此时执行的是wrap函数
如果在脚本最后加上add(1,2),且把注掉的打开，则会打印5
