V 1.0
```
class Person:
    def __init__(self,name):
        self.name = name
        print('大家注意了！')
        
    def show(self):
        print('一个叫"%s"的人来了' % self.name)


# 子类的继承和定制
class Man(Person):
    def show(self):
        print('一个叫"%s"的男人来了' % self.name)
       
    def leave(self):
        print('那个叫"%s"的男人留下了他的背影'% self.name)
        

author1 = Person('吉多')
author1.show()
author2 = Man('范罗苏姆')
author2.show()
author3 = Man('范罗苏姆')
author3.leave()
```
V2.0
```
class Person:
    def __init__(self, name):
        self.name = name
        print('大家注意了！')

    def show(self):
        print('一个叫“%s”的人来了。' % self.name)


class Man(Person):
    def __init__(self):
        Person.__init__(self, name='范罗苏姆')  # 继承的基础上做一些改变
        # 上面的括号里也可以写成(self,'范罗苏姆')，但加上参数后清晰一些，代码看起来更清晰。

    def show(self):
        Person.show(self)  # 完全继承父类的方法

    def leave(self):  # 子类定制新方法
        print('那个叫“%s”的男人留下了他的背影。' % self.name)


author1 = Person('吉多')
author1.show()
author2 = Man()
author2.show()
author3 = Man()
author3.leave()

```
备注： 注意看V2.0的class Man(Person):def __init__(self)
