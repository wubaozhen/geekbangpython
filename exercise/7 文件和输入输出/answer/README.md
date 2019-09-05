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

# 实例：一个文件打印结果为：['罗恩102\n', '哈利383\n', '赫敏570\n', '马尔福275\n']，现需要操作此文件，将文件内容按分数从高到低写到新文件。
参考答案：
# 下面注释掉的代码，皆为检验代码（验证每一步的思路和代码是否达到目标，可解除注释后运行）。

file1 = open('winner.txt','r',encoding='utf-8')
file_lines = file1.readlines()
file1.close()

dict_scores = {}
list_scores = []
final_scores = []

# print(file_lines)
# print(len('\n'))

# 打印结果为：['罗恩102\n', '哈利383\n', '赫敏570\n', '马尔福275\n']
# 经过测试，发现'\n'的长度是1。所以，名字是“第0位-倒数第5位”，分数是“倒数第4位-倒数第二位”。
# 再根据“左取右不取”，可知：name-[:-4],score-[-4:-1]

for i in file_lines:  # i是字符串。
    print(i)
    name = i[:-4]  # 取出名字（注：字符串和列表一样，是通过偏移量来获取内部数据。）
    score = int(i[-4:-1])  # 取出成绩
    print(name)
    print(score)
    dict_scores[score] = name  # 将名字和成绩对应存为字典的键值对(注意：这里的成绩是键)
    list_scores.append(score)

# print(list_scores)
list_scores.sort(reverse=True)  # reverse，逆行，所以这时列表降序排列，分数从高到低。
# print(list_scores)

for i in list_scores:
    result = dict_scores[i] + str(i) + '\n'
    # print(result)
    final_scores.append(result)

print(final_scores)  # 最终结果

winner_new = open('winner_new.txt','w',encoding='utf-8')
winner_new.writelines(final_scores)
winner_new.close()

## 稍微改一下，让原始文件输出为['罗恩 102\n', '哈利 383\n', '赫敏 570\n', '马尔福 275\n']，即名字和分数之间有空格

## 我的答案：

with open('winner.txt','r',encoding='utf-8') as file1:
    file_lines = file1.readlines()

print(file_lines)
dict_scores = {}
list_scores = []
final_scores = []

# 将name作为键，value作为值，写入字典
for i in file_lines:
    dict_scores[i.split()[0]] = i.split()[1]

print(dict_scores)

# 字典按value降序排列，x[1]表示按值，x[0]表示按键，reverse=True,降序排列
list_scores = sorted(dict_scores.items(),key = lambda x:x[1],reverse=True)
print(list_scores)

for i in list_scores:
    result = i[0] + ' ' + i[1] + '\n'
    final_scores.append(result)

print(final_scores)

with open('winner_new.txt','w',encoding='utf-8') as file2:
    file2.writelines(final_scores)

```

