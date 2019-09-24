---
layout:     post
title:      "leetcode组合两张表"
subtitle:   "oracle的左右连接运用"
date:        2018-07-02 16:50:00
author:     "RayChou"
header-img: "img/rn_bg.jpg"
tags:
   - sql
---

## 表结构

表1: Person

+-------------+---------+
| 列名         | 类型     |
+-------------+---------+
| PersonId    | int     |
| FirstName   | varchar |
| LastName    | varchar |
+-------------+---------+
PersonId 是上表主键
表2: Address

+-------------+---------+
| 列名         | 类型    |
+-------------+---------+
| AddressId   | int     |
| PersonId    | int     |
| City        | varchar |
| State       | varchar |
+-------------+---------+
AddressId 是上表主键
 

编写一个 SQL 查询，满足条件：无论 person 是否有地址信息，都需要基于上述两表提供 person 的以下信息：

 

FirstName, LastName, City, State

------

> 1. 分析题目需要用到左右连接：概念如下    
> 2. LEFT OUTER JOIN左联接：结果包括左表（出现在JOIN子句最左边）中的所有行，不包括右表中的不匹配行。
> 3. RIGHT OUTER JOIN右联接：结果包括右表（出现在JOIN子句最右边）中的所有行，不包括有左表中的不匹配的行。
> 4. 本题目中应该是person左连接address表，或者address右连接person

**解法1**
```
select p.FirstName, p.LastName, a.City, a.state
from Person p
LEFT JOIN Address a
ON p.PersonId = a.PersonId;
```

**解法2**
```
select p.FirstName, p.LastName, a.City, a.state
from Person p, Address a
where p.PersonId = a.PersonId(+);
```
## 开发流程
需要注意的是左连接对应在address后面添加（+），解法二耗时为解法一两倍