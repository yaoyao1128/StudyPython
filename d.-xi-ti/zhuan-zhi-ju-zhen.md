# 转置矩阵

## 题目详情：

有任意一个矩阵，不一定是方阵，求其转置矩阵。

## 代码实现：

### 解法1：

```python
new = []
for i in range(len(matrix[0])):
    new.append([])
    for j in range(len(matrix)):
        new[i].append(matrix[j][i])
```

### 解法2：

```python
new = [0] * len(matrix[0])
new = [[0 for j in range(len(matrix))] for i in range(len(matrix[0]))]
for i in range(len(matrix)):
    for j in range(len(matrix[i])):
        new[j][i]=matrix[i][j]
```

