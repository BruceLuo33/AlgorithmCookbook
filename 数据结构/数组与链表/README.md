# 数组与链表
<span id ="0">

## [一、知识点](#1)
 - [数组](#1.1)
 - [链表](#1.2)

## [二、高频题](#2)

## [三、题解笔记](#2)

<h2 id = "1">一、知识点</h2>

<h3 id = "1.1">数组</h3>

[返回目录](#0)


<h3 id = "1.2">链表</h3>

[返回目录](#0)

<h2 id = "2">二、高频题</h2>

总结：

 知识点 | 技巧 | 地址 | 解题笔记 | 难度 |
| --- | --- | --- | --- | --- |
| 链表 | 双指针 | [LeetCode 206: 反转链表](https://leetcode-cn.com/problems/reverse-linked-list/) | [Leetcode 206](#3.1) | 简单 |

<h2 id = "3">三、解题笔记</h2>

<h3 id = "3.1">LeetCode 206: 反转链表</h3>
入门级别的链表反转，最开始在 CS61B 中遇到这个问题，而后在 Leetcode 上找到了对应的题目。关键就在于每次翻转要注意保留之前的指针：

<div align=center><img width = "500" height = "250" src="https://user-images.githubusercontent.com/38673091/110267580-16256380-7ffb-11eb-8154-26ade72a1ab5.png"/></div>


```java
    public ListNode reverseList(ListNode head) {
        if (head == null || head.next == null) return head;
        ListNode cur = head;
        ListNode prev = null;
        while (cur != null) {
            cur = cur.next;
            head.next = prev;
            prev = head;
            head = cur;
        }
        return prev;
    }

