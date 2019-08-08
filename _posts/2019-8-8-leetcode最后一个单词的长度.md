---
layout:     post
title:      "【leetcode】771. 宝石与石头"
subtitle:   "他人的写法，我的写法"
date:        2019-8-9 17:20:00
author:     "RayChou"
header-img: "img/post_bg_python.jpeg"
tags:
   - 每日练习 python
---

# 【leetcode】771. 宝石与石头
今天做了leetcode的宝石与石头一题的心得
      
#### 题目
给定字符串J 代表石头中宝石的类型，和字符串 S代表你拥有的石头。 S 中每个字符代表了一种你拥有的石头的类型，你想知道你拥有的石头中有多少是宝石。

J 中的字母不重复，J 和 S中的所有字符都是字母。字母区分大小写，因此"a"和"A"是不同类型的石头。

###示例 1:

输入: J = "aA", S = "aAAbbbb"
输出: 3
示例 2:

输入: J = "z", S = "ZZ"
输出: 0
注意:
S 和 J 最多含有50个字母。J 中的字符不重复。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/jewels-and-stones

> 别人的解法一：
```
class Solution(object):
    def numJewelsInStones(self, J, S):
        """
        :type J: str
        :type S: str
        :rtype: int
        """
        for i in J:
             S.count(i)
        return sum(S.count(i) for i in J)
```
> 别人的解法二：
```
class Solution(object):
    def numJewelsInStones(self, J, S):
        """
        :type J: str
        :type S: str
        :rtype: int
        """
        return len([i for i in S if i in J])
```

#### 我的解法：
```
from collections import Counter

class Solution(object):
    def numJewelsInStones(self, J, S):
        """
        :type J: str
        :type S: str
        :rtype: int
        """
        sum = 0
        jewels = list(J)
        stones = dict(Counter(S))
        for i in range(len(jewels)):
            if jewels[i] in stones:
                sum = sum+stones[jewels[i]]
        return sum

```
1、首先没有意识到可以直接遍历字符串，for in ,而我使用的是for in range(len())
https://blog.csdn.net/cadi2011/article/details/85333068
2、关于求和，没有意识到可以使用sum(),而我使用的是sum+=
3、查找一个字符串中某个字符出现的次数可以用S.count，而我使用的是转换成字典


以上的两种解题思路：
1）依次遍历J中的宝石类型，找到每种宝石出现的次数，并且求和
2）依次遍历S中的所有石头类型，如果找到了，则将该石头放入宝石列表，最后返回宝石列表的长度
所以说第一种优于第二种

我的问题。不要过分的依赖第三方包，尽量写得pythonic
并且在写得时候记不住最基础的字符串和字典的方法，仍然去翻阅了API接口文档
