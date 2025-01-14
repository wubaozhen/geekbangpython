# 练习一 字典的使用

```python
# 1. 定义一个字典，分别使用a、b、c、d作为字典的关键字，值为任意内容
dict1 = {'a': 'aa', 'b': 'xyz', 'c': 'Helo', 'd': 123}

# 2. 为该字典增加一个元素‘c':'cake'后，将字典输出到屏幕
# 字典的key不能重复，否则会覆盖掉相同key的值
dict1['c'] = 'cake'
print(dict1)

# 3. 取出字典中关键字为d的值
print(dict1['d'])

# 4.字典操作中del 和 pop 有什么区别
d = {'a':1,'b':2}
del d['a']
print(d) --> {'b':2}

d = {'a':1,'b':2}
d.pop('a')
print(d) --> {'b':2}

del 是语句，没有返回值 ;pop是方法，弹出键所对应的值，然后可以接收它的返回值，都是用字典的键

# 5.按照字典内的年龄排序
d1 = [
    {'name':'aloce','age':38},
    {'name':'bob','age':18},
    {'name':'carl','age':28},
]

d2 = sorted(d1,key=lambda x : x['age'])
print(d2)
[{'name': 'bob', 'age': 18}, {'name': 'carl', 'age': 28}, {'name': 'aloce', 'age': 38}]

# 6.合并2个字典，a= {'A':1,'B':2}   b = {'C':3,'D':4}
a.update(b)
print(a)
{'A': 1, 'B': 2, 'C': 3, 'D': 4}
也可以用字典解包的方式   
a= {'A':1,'B':2}
b = {'C':3,'D':4}
print({**a,**b})
{'A': 1, 'B': 2, 'C': 3, 'D': 4}

# 7. 如何使用生成式的方式生成一个字典，写一段功能代码
答：

# 8.1把字典的key和value值掉换
d = {'a':1,'b':2}
print({v:k for k,v in d.items()})

# 8.2 把字典的值换成键的大写字母
>>>d = {'a':'apple','b':'bob','c':'cat'}
>>>{k:k.upper() for k,v in d.items()}
>>>{'a': 'A', 'b': 'B', 'c': 'C'}

# 8.3 大小写合并，key值最终为小写
>>>d1 = {'A':10,'b':3,'a':5,'B':8,'d':1}
>>>{k.lower():d1.get(k.upper(),0) + d1.get(k.lower(),0) for k,v in d1.items()}
>>>{'a': 15, 'b': 11, 'd': 1}
注： d.get(key,[default]) 如何key存在，即返回对应的值，不存在则返回default


# 9.如何把元组('a','b') 和元组（1,2）变成字典{'a':1,'b':2}
>>>t1= ('a','b')
>>>t2 = (1,2)
>>>dict(zip(t1,t2))
{'a': 1, 'b': 2}
或者
>>>dict([('a',1),('b',2)])
>>>{'a': 1, 'b': 2}

# 按字典的key排序输出key value
# key 无序输出
dict1 = {'b':24,'a':10,'c':8}

for k in dict1:
    print(k,dict1[k])

# key 有序输出
for k in sorted(dict1):
    print(k, dict1[k])

# 根据字典的值找对对应的键
dict1 = {'a':10,'b':24,'c':8}

def reverse_lookup(dic,value1):
    for key in dic:
        if dict1[key] == value1:
            return key
    
    # 没找到就抛个异常
    raise LookupError()

print(reverse_lookup(dict1,9))
```

# 练习二 集合的使用

```python
# 1. 将字符串hello中每个字符赋值给一个集合，将这个集合输出到屏幕
str1 = 'hello'
# 集合里的元素不能重复
print(set(str1))

```
