```
# 练习一  正则切分字符串


import re
s = 'info:xiaoZhang 33 shandong'
print(re.split(r'[\s\s:]+',s))

输出['info', 'xiaoZhang', '33', 'shandong']

# 参考答案：
## 分析：需要根据冒号或者空格切分

import re
s = 'info:xiaoZhang 33 shandong'
res = re.split(r':| ',s)




# 练习二

a = '你好        中国' ,去除多余空格只留一个空格
a1 = ' '.join(a.split())
print(a1)

# 编写程序，用户输入一段英文，然后输出这段英文中所有长度为3个字母的单词
import re
string = input('请输入一段英文：')
# 如果用这种来匹配，就匹配不了开头满足条件的，如果结尾没符号也匹配不了结尾的
# pat = re.compile(r'[^a-z]{1}([a-z]{3})[^a-z]{1}')
# \b 匹配一个单词边界，也就是指单词和空格间的位置。例如，'py\b'可以匹配'python'中的py,
# 但不能匹配'openpyxl'中的py
pat = re.compile(r'\b[a-zA-Z]{3}\b')
ret = pat.findall(string)
print(ret)

输出：
D:\Python36\python.exe E:/pycharm_test/python3_100例/001.py
请输入一段英文：kkk,sdkfjhsdf,dlk kdf,dlfj,wbd,dlkfj,sdd
['kkk', 'dlk', 'kdf', 'wbd', 'sdd']

Process finished with exit code 0

```
