# collections

## defaultdict

参见（[2. 内置数据结构/字典](https://python3.ac.cn/2.-nei-zhi-shu-ju-jie-gou/6.-zi-dian)）

### 用法

```python
from collections import defaultdict
import random
d3 = defaultdict(list)
for k in 'abcde':
    for v in range(random.randint(1,5)):
        d3[k].append(random.randint(1,100))
print(d3)
```

### 解释

```python
defaultdict(default_factory)
```

如果不存在，则根据 `default_factory`（一个函数）自动创建一个kv对。

## namedtuple

参见（[2. 内置数据结构**/**元组](https://python3.ac.cn/2.-nei-zhi-shu-ju-jie-gou/2.-yuan-zu)）

## OrderedDict

参见（[2. 内置数据结构/字典](https://python3.ac.cn/2.-nei-zhi-shu-ju-jie-gou/6.-zi-dian)）

### 用法

```python
from collections import OrderdDict
od = OrderedDict()
od['b'] = 100
od['d'] = 3
od['c'] = 50
od['a'] = 0
od[1] = 1
od[(2,)] = 2
od
```

返回值：

```text
OrderedDict([('b', 100), ('d', 3), ('c', 50), ('a', 0), (1, 1), ((2,), 2)])
```

记录的是**插入dict**的顺序，不代表dict有序！

是一个类字典，可以使用`keys`等操作。

3.6版本以后，默认记录插入dict的顺序。



