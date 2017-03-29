---
layout:     post
title:      "Calendar用法"
date:       2017-3-28 20:00:00
author:     "Tang"
header-img: "img/java-calendar.jpg"
tags:
    - java
    - Calendar
---

# Calendar 一些用法

> 运用calendar加减日期，可以很方便的避免 因每月日期以及闰年日期不同的而产生的逻辑运算

```java

// 获取calendar对象
Calendar cal = Calendar.getInstance();

// 获取现在的时间戳，以毫秒为单位
// 1490099962065
// 用这个相比较 new Date() 获取效率高，
// 因为他也是通过调用 System.currentTimeMillis()来获取时间戳
System.currentTimeMillis()

// 用给定的 long 值(时间戳)设置此 Calendar 的当前时间值。设置的单位是毫秒
void setTimeInMillis(long millis)

// 使用给定的 Date 设置此 Calendar 的时间
void setTime(Date date)

//可以使用下面三个方法把日历定到任何一个时间：
set(int year ,int month,int date)     
set(int year ,int month,int date,int hour,int minute)     
set(int year ,int month,int date,int hour,int minute,int second)

//Calendar加减日期
cal.add(Calendar.YEAR,-1); //日期减1年
cal.add(Calendar.MONTH,3); //日期加3个月
cal.add(Calendar.Calendar.WEEK_OF_YEAR,1); //日期加一周
cal.add(Calendar.DAY_OF_YEAR,10);  //日期加10天

```

### 详细的Calender加减日期的操作

```java
// 24小时制 HH:mm:ss   12小时制 hh:mm:ss
SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日 HH时mm分ss秒");

// 设置long类型时，赋上的值需要在最后加上 L 。
long time = 946656000000L; // 毫秒级别，超出int的大小。

// calendar.add( field , amount );
// 测试的时间： 2000年01月01日 00时00分00秒

a.add(1,1);  // 2001年01月01日 00时00分00秒  field: 1 Calendar.YEAR;
b.add(2,1);  // 2000年02月01日 00时00分00秒  field: 2 Calendar.MONTH
c.add(3,1);  // 2000年01月08日 00时00分00秒  field: 3 Calendar.WEEK_OF_YEAR
d.add(4,1);  // 2000年01月08日 00时00分00秒  field: 4 Calendar.WEEK_OF_MONTH
e.add(5,1);  // 2000年01月02日 00时00分00秒  field: 5 Calendar.DATE; Calendar.DAY_OF_MONTH
f.add(6,1);  // 2000年01月02日 00时00分00秒  field: 6 Calendar.DAY_OF_YEAR
g.add(7,1);  // 2000年01月02日 00时00分00秒  field: 7 Calendar.DAY_OF_WEEK
h.add(8,1);  // 2000年01月08日 00时00分00秒  field: 8 Calendar.DAY_OF_WEEK_IN_MONTH
i.add(9,1);  // 2000年01月01日 12时00分00秒  field: 9 Calendar.AM_PM
j.add(10,1); // 2000年01月01日 01时00分00秒  field: 10 Calendar.HOUR
k.add(11,1); // 2000年01月01日 01时00分00秒  field: 11 Calendar.HOUR_OF_DAY
l.add(12,1); // 2000年01月01日 00时01分00秒  field: 12 Calendar.MINUTE
m.add(13,1); // 2000年01月01日 00时00分01秒  field: 13 Calendar.SECOND
```

根据上面的测试结果，我们可以把常量归类总结下：

* 加减年份： *Calendar.YEAR*; field: 1
* 加减月份： *Calendar.MONTH*; field: 2
* 加减周： *Calendar.WEEK_OF_YEAR*、*Calendar.WEEK_OF_MONTH*、***Calendar.DAY_OF_WEEK_IN_MONTH*** field: 3,4,8
* 加减日： *Calendar.DATE*、*Calendar.DAY_OF_MONTH*、*Calendar.DAY_OF_YEAR*、*Calendar.DAY_OF_WEEK* field: 5,6,7
* 加减小时： *Calendar.HOUR*、*Calendar.HOUR_OF_DAY* field: 10,11
* 加减分钟： *Calendar.MINUTE* field: 12
* 加减秒： *Calendar.SECOND* field: 13

> `Calendar.AM_PM` field: 9; 转换成12小时制

Calendar常量 基本上符合这样的规律：

 - Calendar.WEEK...   表示加减 周。
 - Calendar.DAY...   表示加减 日。
 - Calendar.HOUR...   表示加减小时。

 > 除了 `Calendar.DAY_OF_WEEK_IN_MONTH` 这个是表示加减 周。


```
//获得年份、月份、小时
cal.get(Calendar.MONTH)  //这样的方法 0表示一月，1表示二月    
cal.get(Calendar.DAY_OF_MONTH)  //获得这个月的第几天    
cal.get(Calendar.DAY_OF_WEEK)  //获得这个星期的第几天    
cal.get(Calendar.DAY_OF_YEAR)  //获得这个年的第几天    
cal.getTimeMillis()  //获得当前时间的毫秒表示    
```
