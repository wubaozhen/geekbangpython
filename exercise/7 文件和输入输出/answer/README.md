# 练习一 文件的创建和使用
```python
# 1. 创建一个文件，并写入当前日期
import datetime
now = datetime.datetime.now()
with open('c.txt', 'w') as f:
    # 注意write( )方法写入的内容是字符串类型
    f.write(str(now))


# 2. 再次打开这个文件，读取文件的前4个字符后退出
with open('c.txt', 'r') as f:
    text_4 = f.read(4)
    print(text_4)
    
# 3.在读文件操作时会使用read , readline 或者 readlines,简述它们各自的作用
答：read()每次读取整个文件，通常用于将文件内容存放到一个字符串变量中.readline()和readlines()都是按行来读取，后者是一次性读取整个文件，可以用for... in ..来处理,而readline()是每次只读取一行，当没有足够内存可以一次性读取文件时才有readline().

# 4. write()和writelines()区别
答：write() 参数为str,writelines()参数为序列，比如列表，它会迭代帮你写入文件

# 5.有两个磁盘文件A和B，各存放一行字母，要求把这两个文件中的信息合并（按字母顺序排列），输出到一个新文件C中
方法一：
with open('1.txt','r')  as f1:
    f1t = f1.read()

with open('2.txt','r')  as f2:
    f2t = f2.read()

f3t = f1t + f2t
f3t = sorted(f3t)  # sorted()返回的是一个列表

with open('3.txt','w')  as f3:
    f3.writelines(f3t)
    
方法二：
with open('1.txt','r')  as f1:
    f1t = f1.readline()

with open('2.txt','r')  as f2:
    f2t = f2.readline()

f3t = f1t + f2t
f3t = sorted(f3t)

with open('3.txt','w')  as f3:
    f3.write(''.join(f3t)) # 将列表转换为字符串

```

