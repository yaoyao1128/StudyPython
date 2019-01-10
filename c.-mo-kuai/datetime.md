# datetime

## datetime模块

### today

返回本地时区当前时间的datetime对象

### now\(tz=None\)

返回本地时区当前时间的datetime对象，

### utcnoe

返回没有时区当前时间的datetime对象

### fromtimestamp\(timestamp\)

从一个时间戳返回datetime对象

### timestamp

时间戳，从1970年1月1日0点到现在的秒数（UTC）

## datetime对象

### 构造方法

```python
datetime = datetime.datetime(2018,9,10,20,18,1)
```

### 对象属性与操作

year

month

hour

weekday  \|（从0开始）

isoweekday

（）

date

日期

isocalendar

第几周第几天

replace

替换某一部分构造的对象

可以相减，可以加减timedelta

### timedelta对象

total\_seconds\(\)返回时间差总秒数

### 日期格式化

```python
"{}".format(d1)
"{:%Y/%m/%d %H:%S:%M}".format(d1)
"{:%y}".format(d1)
```

### striptime——字符串转时间

```python
datetime.datetime.strptime("01/09/2019 20:10:05", "%d/%m/%Y %H:%M:%S")
```

### strftime——格式化时间

```python
datetimeobject.strftime("%Y-%m-%d %H:%M:%S")
```































