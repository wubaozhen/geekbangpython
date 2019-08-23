# 练习一 异常
```python
# 1. 在Python程序中，分别使用未定义变量、访问列表不存在的索引、访问字典不存在的关键字观察系统提示的错误信息

# 使用未定义变量
a + 1

# 访问列表不存在的索引
b = ['a', 'b', 'c']
b[3]

# 访问字典不存在的key
c = {'x': 1}
c['y']


# 2. 通过Python程序产生IndexError，并用try捕获异常处理
try:
    b = ['a', 'b', 'c']
    b[3]
except IndexError:
    print('访问列表不存在的索引')

```
# 练习二 try...except  while ... break
```
while True:
    try:
        age = int(input('你今年几岁了？'))
        break
    except ValueError:
        print('你输入的不是数字！')

if age < 18:
    print('不可以喝酒噢')

```
