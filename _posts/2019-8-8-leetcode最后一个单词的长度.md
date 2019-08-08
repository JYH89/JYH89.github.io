---
layout:     post
title:      "【leetcode】58. 最后一个单词的长度"
subtitle:   "split()方法学习"
date:        2019-8-9 17:20:00
author:     "RayChou"
header-img: "img/post_bg_python.jpeg"
tags:
   - 每日练习 python
---

# 【leetcode】58. 最后一个单词的长度
今天做了leetcode的最后一个单词的长度一题的心得
      
#### 题目
给定一个仅包含大小写字母和空格 ' ' 的字符串，返回其最后一个单词的长度。

如果不存在最后一个单词，请返回 0 。

说明：一个单词是指由字母组成，但不包含任何空格的字符串。

###示例 1:

输入: "Hello World"
输出: 5
来源：力扣（LeetCode）
链接：<https://leetcode-cn.com/problems/jewels-and-stones>

> 别人的解法一：
```
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        return len(s.rstrip().split(" ")[-1])
```
> 别人的解法二：
```
class Solution:
    def lengthOfLastWord(self, s: str) -> int:
        s_ = s.rstrip()
        if s_ == '':
            return 0
        sub = s_.split(' ')
        lenth = len(sub[-1])
        return lenth
```

#### 我的解法：
```
class Solution:
    def lengthOfLastWord(self, S):
        return 0 if len(S.split())<1 else len(S.split()[-1])

```
1、首先没有意识到split()分隔字符串函数的正确使用s_.split(' '),而我使用的是S.split()
通过查看str类下的方法如下：
```
 |  split(...)
 |      S.split(sep=None, maxsplit=-1) -> list of strings
 |      
 |      Return a list of the words in S, using sep as the
 |      delimiter string.  If maxsplit is given, at most maxsplit
 |      splits are done. If sep is not specified or is None, any
 |      whitespace string is a separator and empty strings are
 |      removed from the result.
``` 
2、通过测试如下，来理解上述文档含义
```>>> s=" "
>>> s.split()
[]
>>> s.split(" ")
['', '']
>>> 
```


**重新梳理解题思路：**

1）字符串可能的组成形式有：空串'',包含一个空格的串' ',只有一个单词的字符串'hello',包含若干空格的单词'hello my baby',整个字符串的开头结尾包含空格的' hello baba '
2）获取最后一个单词，首先想到的就是split，使用空格分隔
3）对1中的情况分类：
   考虑字符串首尾可能有空格，但是我们只关心最后一个单词，所以可以在分隔字符串前，使用rstrip()方法去掉字段串尾部的空格
   对于获取最后一个单词可以使用切片-1获取

***tip: 要学会使用help去查看方法的具体使用方法***
