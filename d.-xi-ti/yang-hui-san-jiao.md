# 杨辉三角

## 代码实现

### 直接解法

```python
# 直接解法
import datetime
start = datetime.datetime.now()
n = 10
yangHui = []
for i in range(0,n):
    yangHui.append([])
    for j in range (i+1):
        yangHui[i].append(1) if (j==0) or (j == i) else  yangHui[i].append(yangHui[i-1][j]+yangHui[i-1][j-1])
print((datetime.datetime.now()-start).total_seconds())
for i in range(n):
    for j in range (i+1):
        print(yangHui[i][j],end=" ")
    print()

```

### 补0法

```python
oldline = [1]
print(oldline)
for i in range (1, 10):
    oldline.append(0)
    newline = []
    for j in range(i+1):
        newline.append(oldline[j-1] + oldline[j])
    print(newline)
    oldline = newline
```

### 对称性

```python
trangle = [[1],[1,1]]
for i in range (2, 10):
    row = [1] * (i + 1)
    trangle.append(row)
    for j in range (i//2):
        row[j+1] = trangle[i-1][j] + trangle[i-1][j+1]
        if i%2 == 0 and (j+1) == i//2:
            continue
        row[-j-2] = row[j+1]
print(trangle)
```

### 单列表解法

```python
n = 10
line = [1] * n
for i in range (n):
    offset = n - i
    swap = 1
    for j in range(1, i//2+1):
        val = line[j] + swap
        swap = line[j]
        line[j] = val
        if i != 2 * j:
            line[-j - offset] = val
    print(line[:i+1])
```

## 运行效果

```text
[1]
[1, 1]
[1, 2, 1]
[1, 3, 3, 1]
[1, 4, 6, 4, 1]
[1, 5, 10, 10, 5, 1]
[1, 6, 15, 20, 15, 6, 1]
[1, 7, 21, 35, 35, 21, 7, 1]
[1, 8, 28, 56, 70, 56, 28, 8, 1]
[1, 9, 36, 84, 126, 126, 84, 36, 9, 1]
```

