---
layout:     post
title:      "【leetcode】合并两个有序链表Java实现"
subtitle:   "java"
date:        2019-8-9 17:20:00
author:     "RayChou"
header-img: "img/bg-java.jpeg"
tags:
   - java
---

# 【leetcode】合并两个有序链表Java实现

      
#### 题目
将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

####示例：

输入：1->2->4, 1->3->4

输出：1->1->2->3->4->4

-
两个有序链表的排序，实际上可以看成一个单链表使用归并排序的最后一个环节：“将两个排好序的子序列合并为一个子序列：每次都是从未比较的两个子序列的最小值中选出一个更小值”。

-
```
class Solution(object):
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;//当前节点的值
 *     ListNode next;//下一个节点的引用值
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode temp=new ListNode(0);
        ListNode head=temp;//保留头节点的引用
        while(l1!=null&&l2!=null){
           if(l1.val<l2.val) 
           {
               temp.next=l1;
               l1=l1.next;
           }   
           else
           {
               temp.next=l2;
               l2=l2.next;
           }
           temp=temp.next;
        }
        if(l1==null)  temp.next=l2;//l1子序列为空，则直接拼届l2
        if(l2==null)  temp.next=l1;
        return head.next;//返回头节点指向的序列
    }
}
```
-