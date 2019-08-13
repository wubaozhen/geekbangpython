## numpy
### numpy 求平均值
```
import numpy as np
L = [23,44,45,22,12]
avg = np.mean(L) # 求平均值
avg1 = sum(L)/len(L)
print(avg,avg1)

输出：
>>>29.2 29.2
```
### numpy 比较元素大小
```
import numpy as np
L = [23,44,45,22,12]
avg = np.mean(L)
print('平均值为：{}'.format(avg))

L1 = np.array(L) # 复制了L
print('低于平均值的有：{}'.format(L1[L1<avg]))

输出：
>>>平均值为：29.2
低于平均值的有：[23 22 12]

```
