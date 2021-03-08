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
| 链表指针 | 双指针 | [LeetCode 206: 反转链表](https://leetcode-cn.com/problems/reverse-linked-list/) | [Leetcode 206](#3.1) | 简单 |
| 链表指针 | 三指针 | [LeetCode 24: 两两交换链表中的节点](https://leetcode-cn.com/problems/swap-nodes-in-pairs/) | [Leetcode 24](#3.2) | 中等 |
| 链表指针 | 双指针 | [LeetCode5: K个一组反转链表](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/) | [Leetcode 25](#3.3) | 困难 |


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
```

<h3 id = "3.2">LeetCode 24: 两两交换链表中的节点</h3>
这道题是链表反转问题的一个拓展，不同的地方在于 206 题只需要两个指针，这里需要三个指针：

- 思路：
  1. 如果是空节点 or 单节点，直接返回 head;
  2. 设置 sentinel 节点指向初始的 head，方便最终结果返回;
  3. 设置 nextMove 节点，保证 nextMove.next 一直指向 head;
  4. 设置 tmp 保存反转节点之后的 node，即 head.next.next;
- 注意：在循环的最后，要记得将 head 也指向tmp，亦即之前的 head.next.next，否则会出现以下情况

```java
Original: 1 -> 2 -> 3 -> 4
First swap: 2 -> 1 -> 3 -> 4
Second swap: 2 -> 3 -> 1 -> 4 (×)
             2 -> 1 -> 4 -> 3 (√)
```
代码如下：
```java
    public ListNode swapPairs(ListNode head) {

        if (head == null || head.next == null) return head;
        ListNode sentinel = new ListNode(0);
        sentinel.next = head;
        ListNode nextNodeMove = sentinel;
        while (head != null && head.next != null) {
            ListNode tmp = head.next.next;
            nextNodeMove.next = head.next;
            head.next.next = head;
            head.next = tmp;
            nextNodeMove = head;
            head = tmp;
        }
        return sentinel.next;

    }
```

<h3 id = "3.3">LeetCode 25: k 个一组翻转链表</h3>
1. 这道题就是之前两题的综合了。首先可以看出有一个反转链表的需求，因此可以将206题的答案作为子函数。
2. 然后问题就在于找到子链表的方法，如下所示，子链表用 start~end 标识，移动 k 次 end，不越界即为子链表


```java
    public ListNode reverseKGroup(ListNode head, int k) {
        if (k == 1 || head == null || head.next == null) return head;
        ListNode sentinel = new ListNode(-1);
        sentinel.next = head;
        ListNode prev = sentinel;
        ListNode end = sentinel;
        while (end != null) {
            // 移动到子链表位置
            for (int i = 0; i < k; i++) {
                end = end.next;
                if (end == null) return sentinel.next;
            }
            // 取出子链表，start 与 end 分别为子链表的首尾
            ListNode start = prev.next;
            ListNode nextNode = end.next;
            end.next = null;
            // 子链表取出完成，将其传入reverse 子函数，得到的即为已经reverse 的链表
            // 将子链表组装
            prev.next = reverseSubList(start);
            start.next = nextNode;
            // 移动指针到 start，继续往下寻找另一个子链表
            // 这里的 start 相当于之前的 sentinel
            prev = start;
            end = start;
            
        }
        return sentinel.next;
    }

    private ListNode reverseSubList(ListNode head) {
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
```
