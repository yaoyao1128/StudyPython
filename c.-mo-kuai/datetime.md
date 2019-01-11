# datetime
**参见[https://docs.python.org/3.7/library/datetime.html](https://docs.python.org/3.7/library/datetime.html)**
## 可用类
### datetime.date
一个理想化的“naive”日期，假设当前的公历始终，并且始终将是有效的。 属性有：year, month, and day.

### datetime.time
一个理想化的时间，假设每天都有24 * 60 * 60秒（这里没有“闰秒”的概念），独立于任何特定的日子。属性有: hour, minute, second, microsecond, and tzinfo.

### datetime.datetime
一个时间与日期的集合。属性有: year, month, day, hour, minute, second, microsecond, and tzinfo.

### datetime.timedelta
表示两个日期，时间或日期时间对象间微秒之间差异的持续时间。

### datetime.tzinfo
时区信息对象的抽象类。 日期时间和时间类使用它们来提供可自定义的时间调整概念（例如，考虑时区和/或夏令时）。

### datetime.timezone
将tzinfo抽象基类实现为与UTC的固定偏移量的类。


## 可用对象
### date

#### 类方法

##### date.today()

返回当前本地时间，相当于 `date.fromtimestamp(time.time()).`

##### date.fromtimestamp(timestamp)
返回与POSIX时间戳对应的本地日期，例如time.time()返回的日期。 

##### date.fromordinal(ordinal)
返回Proleptic Gregorian历日期。其中第1年1月1日为序数1。

##### date.fromisoformat(date_string)
以date.isoformat() 的格式返回与日期字符串对应的日期。 具体来说，此函数支持格式为YYYY-MM-DD的字符串。


#### 类属性:

##### date.min
最小时间，date(MINYEAR, 1, 1).

##### date.max
最大时间，date(MAXYEAR, 12, 31).

##### date.resolution
非相等date对象之间的最小可能差异，timedelta(days=1).

#### 实例属性（只读）:

##### date.year
介于MINYEAR和MAXYEAR之间。

##### date.month
介于1到12之间。

##### date.day
在给定年份的给定月份的1和之间的天数。

##### date.replace(year=self.year, month=self.month, day=self.day)
返回具有相同值的日期，除了通过指定的任何关键字参数给定新值的那些参数。例如，如果d == date(2002, 12, 31), 则 d.replace(day=26) == date(2002, 12, 26).

##### date.timetuple()
Return a time.struct_time such as returned by time.localtime(). The hours, minutes and seconds are 0, and the DST flag is -1. d.timetuple() is equivalent to time.struct_time((d.year, d.month, d.day, 0, 0, 0, d.weekday(), yday, -1)), where yday = d.toordinal() - date(d.year, 1, 1).toordinal() + 1 is the day number within the current year starting with 1 for January 1st.

##### date.toordinal()
Return the proleptic Gregorian ordinal of the date, where January 1 of year 1 has ordinal 1. For any date object d, date.fromordinal(d.toordinal()) == d.

##### date.weekday()
Return the day of the week as an integer, where Monday is 0 and Sunday is 6. For example, date(2002, 12, 4).weekday() == 2, a Wednesday. See also isoweekday().

##### date.isoweekday()
Return the day of the week as an integer, where Monday is 1 and Sunday is 7. For example, date(2002, 12, 4).isoweekday() == 3, a Wednesday. See also weekday(), isocalendar().

##### date.isocalendar()
Return a 3-tuple, (ISO year, ISO week number, ISO weekday).

The ISO calendar is a widely used variant of the Gregorian calendar. See https://www.staff.science.uu.nl/~gent0113/calendar/isocalendar.htm for a good explanation.

The ISO year consists of 52 or 53 full weeks, and where a week starts on a Monday and ends on a Sunday. The first week of an ISO year is the first (Gregorian) calendar week of a year containing a Thursday. This is called week number 1, and the ISO year of that Thursday is the same as its Gregorian year.

For example, 2004 begins on a Thursday, so the first week of ISO year 2004 begins on Monday, 29 Dec 2003 and ends on Sunday, 4 Jan 2004, so that date(2003, 12, 29).isocalendar() == (2004, 1, 1) and date(2004, 1, 4).isocalendar() == (2004, 1, 7).

##### date.isoformat()
Return a string representing the date in ISO 8601 format, 'YYYY-MM-DD'. For example, date(2002, 12, 4).isoformat() == '2002-12-04'.


##### date.ctime()
Return a string representing the date, for example date(2002, 12, 4).ctime() == 'Wed Dec 4 00:00:00 2002'. d.ctime() is equivalent to time.ctime(time.mktime(d.timetuple())) on platforms where the native C ctime() function (which time.ctime() invokes, but which date.ctime() does not invoke) conforms to the C standard.

##### date.strftime(format)
Return a string representing the date, controlled by an explicit format string. Format codes referring to hours, minutes or seconds will see 0 values. For a complete list of formatting directives, see strftime() and strptime() Behavior.

### datetime
#### 类操作
##### datetime.today()
返回现在的时间，等效于`datetime.fromtimestamp(time.time())`.

##### datetime.now(tz=None)
返回当前的本地日期和时间。如果可选参数tz为None或未指定，则类似于today(), ，但是，如果可能，提供的精度高于通过time.time()时间戳。


如果tz不是None，则它必须是tzinfo子类的实例，并且当前日期和时间将转换为tz的时区。在这种情况下，结果等同于tz.fromutc(datetime.utcnow().replace(tzinfo=tz)). 

##### datetime.utcnow()
返回当前的UTC日期和时间，tzinfo为None。

##### datetime.fromtimestamp(timestamp, tz=None)
返回与POSIX时间戳对应的本地日期和时间，例如time.time().返回的日期和时间。如果可选参数tz为None或未指定，则时间戳将转换为平台的本地日期和时间，并且返回的datetime对象是天真的。

如果tz不是None，则它必须是tzinfo子类的实例，并且时间戳将转换为tz的时区。在这种情况下，结果等同于tz.fromutc(datetime.utcfromtimestamp(timestamp).replace(tzinfo=tz)).

##### datetime.utcfromtimestamp(timestamp)
返回与POSIX时间戳对应的UTC日期时间，tzinfo为无。

##### datetime.fromordinal(ordinal)
返回对应于公历格里高利序数的日期时间，其中第1年1月1日有序数1。

##### datetime.combine(date, time, tzinfo=self.tzinfo)
返回一个新的datetime对象，其日期组件等于给定的日期对象，并且其时间组件等于给定的时间对象。如果提供了tzinfo参数，则其值用于设置结果的tzinfo属性，否则使用time参数的tzinfo属性。

##### datetime.fromisoformat(date_string)
以date.isoformat() datetime.isoformat()发出的格式之一返回与date_string对应的日期时间。具体来说，此函数支持格式为YYYY-MM-DD [* HH [：MM [：SS [.fff [fff]]]] [+ HH：MM [：SS [.ffffff]]]]的字符串，其中*可以匹配任何单个字符。

##### datetime.strptime(date_string, format)
返回与date_string对应的日期时间，根据格式进行解析。详见最后：格式化时间。

#### 类属性:

##### datetime.min
最早的可表示日期时间，datetime(MINYEAR, 1, 1, tzinfo=None).

##### datetime.max
最新的可表示日期时间，datetime(MAXYEAR, 12, 31, 23, 59, 59, 999999, tzinfo=None).

##### datetime.resolution
非相等日期时间对象之间的最小可能差异，timedelta(microseconds=1).

#### 实例属性（只读）:

##### datetime.year
介于MINYEAR和MAXYEAR之间。

##### datetime.month
介于1到12之间。

##### datetime.day
在给定年份的给定月份的1和之间的天数。

##### datetime.hour
range(24)以内

##### datetime.minute
range(60)以内

##### datetime.second
range(60)以内

##### datetime.microsecond
range(1000000)以内

##### datetime.tzinfo
该对象作为tzinfo参数传递给datetime构造函数，如果没有传递则传递给None。

##### datetime.fold
在[0,1]中。用于消除重复间隔期间的“墙壁”时间。 

#### 实例方法:

##### datetime.date()
返回具有相同年，月和日的日期对象。

##### datetime.time()
返回时间对象具有相同的小时，分​​钟，秒，微秒和折叠。 tzinfo是None。

##### datetime.timetz()
返回具有相同小时，分钟，秒，微秒，折叠和tzinfo属性的时间对象。另请参见方法time().

在 3.6 版更改: The fold value is copied to the returned time object.

##### datetime.replace(year=self.year, month=self.month, day=self.day, hour=self.hour, minute=self.minute, second=self.second, microsecond=self.microsecond, tzinfo=self.tzinfo, * fold=0)
返回具有相同属性的日期时间，但通过指定的任何关键字参数给定新值的属性除外。请注意，可以指定tzinfo = None，以便从知道日期时间创建一个天真的日期时间，而不会转换日期和时间数据。

##### datetime.astimezone(tz=None)
返回具有新tzinfo属性tz的datetime对象，调整日期和时间数据，使得结果与self的UTC时间相同，但是在tz的本地时间。

##### datetime.utcoffset()
如果tzinfo为None，则返回None，否则返回self.tzinfo.utcoffset(self)

##### datetime.dst()
如果tzinfo为None，则返回None，否则返回self.tzinfo.dst(self)

##### datetime.tzname()
如果tzinfo为None，则返回None，否则返回self.tzinfo.tzname(self)

##### datetime.timetuple()


##### datetime.utctimetuple()


##### datetime.toordinal()
返回日期的格里高利序数。同于self.date().toordinal().

##### datetime.timestamp()
返回与datetime实例对应的POSIX时间戳。返回值是一个类似于time.time()返回的浮点值。

##### datetime.isoweekday()
以星期为单位返回星期几，其中星期一为1，星期日为7.

##### datetime.isocalendar()
返回3元组（ISO年份，ISO周编号，ISO工作日）。与self.date().isocalendar().相同。

##### datetime.isoformat(sep='T', timespec='auto')
返回表示ISO 8601格式的日期和时间的字符串，YYYY-MM-DDTHH：MM：SS.ffffff，如果微秒为0，则返回YYYY-MM-DDTHH：MM：SS

##### datetime.ctime()
返回表示日期和时间的字符串

##### datetime.strftime(format)
返回表示日期和时间的字符串，由显式格式字符串控制。有关格式化指令的完整列表，请参见下方“格式化字符串”

### time

#### 类方法 
##### time.fromisoformat(time_string)
Return a time corresponding to a time_string in one of the formats emitted by time.isoformat(). Specifically, this function supports strings in the format(s) HH[:MM[:SS[.fff[fff]]]][+HH:MM[:SS[.ffffff]]].


#### 类属性:

##### time.min
The earliest representable time, time(0, 0, 0, 0).

##### time.max
The latest representable time, time(23, 59, 59, 999999).

##### time.resolution
The smallest possible difference between non-equal time objects, timedelta(microseconds=1), although note that arithmetic on time objects is not supported.

#### 实例属性（只读）:

##### time.hour
In range(24).

##### time.minute
In range(60).

##### time.second
In range(60).

##### time.microsecond
In range(1000000).

##### time.tzinfo
The object passed as the tzinfo argument to the time constructor, or None if none was passed.

##### time.fold
In [0, 1]. Used to disambiguate wall times during a repeated interval. (A repeated interval occurs when clocks are rolled back at the end of daylight saving time or when the UTC offset for the current zone is decreased for political reasons.) The value 0 (1) represents the earlier (later) of the two moments with the same wall time representation.


#### 实例方法:

##### time.replace(hour=self.hour, minute=self.minute, second=self.second, microsecond=self.microsecond, tzinfo=self.tzinfo, * fold=0)
Return a time with the same value, except for those attributes given new values by whichever keyword arguments are specified. Note that tzinfo=None can be specified to create a naive time from an aware time, without conversion of the time data.

##### time.isoformat(timespec='auto')
Return a string representing the time in ISO 8601 format, HH:MM:SS.ffffff or, if microsecond is 0, HH:MM:SS If utcoffset() does not return None, a string is appended, giving the UTC offset: HH:MM:SS.ffffff+HH:MM[:SS[.ffffff]] or, if self.microsecond is 0, HH:MM:SS+HH:MM[:SS[.ffffff]].

The optional argument timespec specifies the number of additional components of the time to include (the default is 'auto'). It can be one of the following:

'auto': Same as 'seconds' if microsecond is 0, same as 'microseconds' otherwise.
'hours': Include the hour in the two-digit HH format.
'minutes': Include hour and minute in HH:MM format.
'seconds': Include hour, minute, and second in HH:MM:SS format.
'milliseconds': Include full time, but truncate fractional second part to milliseconds. HH:MM:SS.sss format.
'microseconds': Include full time in HH:MM:SS.ffffff format.

##### time.strftime(format)
Return a string representing the time, controlled by an explicit format string. For a complete list of formatting directives, see strftime() and strptime() Behavior.

##### time.utcoffset()
如果tzinfo为None，则返回None，否则返回self.tzinfo.utcoffset(None)

##### time.dst()
如果tzinfo为None，则返回None，否则返回self.tzinfo.dst(None)

##### time.tzname()
如果tzinfo为None，则返回None，否则返回self.tzinfo.tzname(None)

### timedelta
#### timedelta.min
The most negative timedelta object, timedelta(-999999999).

#### timedelta.max
The most positive timedelta object, timedelta(days=999999999, hours=23, minutes=59, seconds=59, microseconds=999999).

#### timedelta.resolution
The smallest possible difference between non-equal timedelta objects, timedelta(microseconds=1).
#### timedelta.total_seconds()
Return the total number of seconds contained in the duration. Equivalent to td / timedelta(seconds=1).

Note that for very large time intervals (greater than 270 years on most platforms) this method will lose microsecond accuracy.

### tzinfo

#### tzinfo.utcoffset(dt)
返回当地时间与UTC的偏移量，以UTC为单位的分钟数。如果当地时间在UTC以西，那么这应该是负数。

#### tzinfo.dst(dt)
返回夏令时（DST）调整，以UTC为单位的分钟，如果未知DST信息，则返回None。

#### tzinfo.tzname(dt)
返回与datetime对象dt对应的时区名称的字符串。

### timezone

#### timezone.utcoffset(dt)
返回构造时区实例时指定的固定值。 dt参数被忽略。返回值是timedelta实例，等于本地时间和UTC之间的差值。

#### timezone.tzname(dt)
返回构造时区实例时指定的固定值。

#### timezone.fromutc(dt)
返回 dt + offset. dt参数必须是一个有意识的日期时间实例，tzinfo设置为self。

#### 类属性:

##### timezone.utc
UTC时区，timezone(timedelta(0)).
