# 练习一  正则切分字符串

```
import re
s = 'info:xiaoZhang 33 shandong'
print(re.split(r'[\s\s:]+',s))
```
输出['info', 'xiaoZhang', '33', 'shandong']
