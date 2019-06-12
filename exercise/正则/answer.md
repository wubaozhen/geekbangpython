# 练习一  正则切分字符串

```
import re
s = 'info:xiaoZhang 33 shandong'
print(re.split(r'[\s\s:]+',s))
```
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

