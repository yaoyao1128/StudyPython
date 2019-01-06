# 求素数

## 题目描述

求10万以内的所有素数。

## 代码实现（非筛法）

```python
import datetime
start = datetime.datetime.now()
print(2,1)
count = 1
for x in range(3,100000,2):
    if x>5 and x% 5 ==0:
        continue
    for i in range (3, int(x**0.5)+1,2):
        if x % i == 0:
            break
    else:
        count += 1
        print(x,count)
print((datetime.datetime.now()-start).total_seconds())
```

## 运行结果

```text
太长了……不写了。最后一共9592个
```

