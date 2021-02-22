# [日期时间工具-DateUtil](https://hutool.cn/docs/#/core/日期时间/日期时间工具-DateUtil?id=日期时间工具-dateutil)



## [由来](https://hutool.cn/docs/#/core/日期时间/日期时间工具-DateUtil?id=由来)

考虑到Java本身对日期时间的支持有限，并且Date和Calendar对象的并存导致各种方法使用混乱和复杂，故使用此工具类做了封装。这其中的封装主要是日期和字符串之间的转换，以及提供对日期的定位（一个月前等等）。

对于Date对象，为了便捷，使用了一个DateTime类来代替之，继承自Date对象，主要的便利在于，覆盖了toString()方法，返回yyyy-MM-dd HH:mm:ss形式的字符串，方便在输出时的调用（例如日志记录等），提供了众多便捷的方法对日期对象操作，关于DateTime会在相关章节介绍。

## [方法](https://hutool.cn/docs/#/core/日期时间/日期时间工具-DateUtil?id=方法)

### [转换](https://hutool.cn/docs/#/core/日期时间/日期时间工具-DateUtil?id=转换)

#### [Date、long、Calendar之间的相互转换](https://hutool.cn/docs/#/core/日期时间/日期时间工具-DateUtil?id=date、long、calendar之间的相互转换)

```java
//当前时间
Date date = DateUtil.date();
//当前时间
Date date2 = DateUtil.date(Calendar.getInstance());
//当前时间
Date date3 = DateUtil.date(System.currentTimeMillis());
//当前时间字符串，格式：yyyy-MM-dd HH:mm:ss
String now = DateUtil.now();
//当前日期字符串，格式：yyyy-MM-dd
String today= DateUtil.today();Copy to clipboardErrorCopied
```

### [开始和结束时间](https://hutool.cn/docs/#/core/日期时间/日期时间工具-DateUtil?id=开始和结束时间)

有的时候我们需要获得每天的开始时间、结束时间，每月的开始和结束时间等等，DateUtil也提供了相关方法：

```java
String dateStr = "2017-03-01 22:33:23";
Date date = DateUtil.parse(dateStr);

//一天的开始，结果：2017-03-01 00:00:00
Date beginOfDay = DateUtil.beginOfDay(date);

//一天的结束，结果：2017-03-01 23:59:59
Date endOfDay = DateUtil.endOfDay(date);Copy to clipboardErrorCopied
```

### [日期时间差](https://hutool.cn/docs/#/core/日期时间/日期时间工具-DateUtil?id=日期时间差)

有时候我们需要计算两个日期之间的时间差（相差天数、相差小时数等等），Hutool将此类方法封装为between方法：

```java
String dateStr1 = "2017-03-01 22:33:23";
Date date1 = DateUtil.parse(dateStr1);

String dateStr2 = "2017-04-01 23:33:23";
Date date2 = DateUtil.parse(dateStr2);

//相差一个月，31天
long betweenDay = DateUtil.between(date1, date2, DateUnit.DAY);Copy to clipboardErrorCopied
```



### [计时器](https://hutool.cn/docs/#/core/日期时间/日期时间工具-DateUtil?id=计时器)

计时器用于计算某段代码或过程花费的时间

```java
TimeInterval timer = DateUtil.timer();

//---------------------------------
//-------这是执行过程
//---------------------------------

timer.interval();//花费毫秒数
timer.intervalRestart();//返回花费时间，并重置开始时间
timer.intervalMinute();//花费分钟数Copy to clipboardErrorCopied
```

