# copy

## 导入方法

```python
import copy
```

## 用法

```text
x = copy.copy(y)        # make a shallow copy of y
x = copy.deepcopy(y)    # make a deep copy of y
```

## copy与deepcopy的区别

参见：[0.6 Python的内存管理](https://python3.ac.cn/0.-ji-chu-zhi-shi-yu-an-zhuang/6.-python-de-nei-cun-guan-li)

直接赋值：简单地拷贝对象的引用，两个对象的id相同。就是对象的引用（别名），就是给当前内存中的对象增加一个“标签”而已。通过使用内置函数 id\(\) ，可以看出指向内存中同一个对象。

copy拷贝父对象，不会拷贝对象的内部的子对象。即浅复制只复制对象本身，没有复制该对象所引用的对象。这时候id会出现变化

copy和deepcopy之间的区别仅与之相关复合对象（包含其他对象的对象，如列表或 类实例）。

deepcopy 完全拷贝了父对象及其子对象。即创建一个新的组合对象，同时递归地拷贝所有子对象，新的组合对象与原对象没有任何关联。



