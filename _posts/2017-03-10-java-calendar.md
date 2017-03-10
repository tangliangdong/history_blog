---
layout:     post
title:      "Calendar用法"
date:       2017-3-9 23:00:00
author:     "Tang"
header-img: "img/java-calendar.jpg"
tags:
    - java
    - Calendar
---

# Calendar 一些用法

> 运用calendar加减日期，可以很方便的避免 因每月日期以及闰年日期不同的而产生的逻辑运算


```java

//获取calendar对象
Calendar cal = Calendar.getInstance();

//用给定的 long 值(时间戳)设置此 Calendar 的当前时间值。
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
cal.add(Calendar.DAY_OF_YEAR,10);  //日期加10天

//获得年份、月份、小时
cal.get(Calendar.Month)  //这样的方法 0表示一月，1表示二月    
cal.get(Calendar.DAY_OF_MONTH)  //获得这个月的第几天    
cal.get(Calendar.DAY_OF_WEEK)  //获得这个星期的第几天    
cal.get(Calendar.DAY_OF_YEAR)  //获得这个年的第几天    
cal.getTimeMillis()  //获得当前时间的毫秒表示    
```

