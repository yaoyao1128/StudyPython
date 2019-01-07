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

## 代码实现（筛法）

```python
import datetime
start = datetime.datetime.now()
n = 1000000
count = 1
pri = [2]
for i in range(3,n,2):
    flag = True
    edge=int(i**0.5)
    for j in pri :
        if i%j == 0 :
            flag = False
            break
        if j > edge:         
            flag = True
            break
    if flag:
        count += 1
        pri.append(i)
delta = (datetime.datetime.now()-start).total_seconds()
print(delta)
print(len(pri))
```

## 运行结果

```text
太长了……不写了。最后一共9592个
```

