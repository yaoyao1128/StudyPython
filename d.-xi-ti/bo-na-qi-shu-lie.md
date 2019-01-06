# 斐波那契数列

### 100以内

```python
print(1)
a = 0
b = 1
while True:
    c = a + b
    if c > 100: break
    a = b 
    b = c
    print(c)
```

### 第101项

```python
a = 1
b = 1
index = 2
while True:
    c = a + b
    index += 1
    if index ==  101: break
    a = b 
    b = c
print(c)
```

