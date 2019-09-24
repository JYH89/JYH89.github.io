---
layout:     post
title:      "leetcode上升的温度"
subtitle:   "oracle同表比较"
date:        2018-10-02 14:20:00
author:     "RayChou"
header-img: "img/bg-sql.jpg"
tags:
   - sql
---
# leetcode上升的温度--oracle同表比较
     
给定一个 Weather 表，编写一个 SQL 查询，来查找与之前（昨天的）日期相比温度更高的所有日期的 Id。

+---------+------------------+------------------+
| Id(INT) | RecordDate(DATE) | Temperature(INT) |
+---------+------------------+------------------+
|       1 |       2015-01-01 |               10 |
|       2 |       2015-01-02 |               25 |
|       3 |       2015-01-03 |               20 |
|       4 |       2015-01-04 |               30 |
+---------+------------------+------------------+
例如，根据上述给定的 Weather 表格，返回如下 Id:

+----+
| Id |
+----+
|  2 |
|  4 |
+----+

**方法：**
oracle 日期类型的直接使用+1来表示日期差。
因此，我们可以通过将 weather 与自身比较
```
在项目目录生成
/* Write your PL/SQL query statement below */
select a.Id from Weather a,Weather b where a.RecordDate=b.RecordDate+1 and a.Temperature>b.Temperature
```





