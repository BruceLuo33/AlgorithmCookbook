# 数组与链表
<span id ="0"></span>

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
<a name ="problem"></a>

总结：

 知识点 | 技巧 | 题目地址 | 解题代码 | 难度 |
| --- | --- | --- | --- | --- |
| 链表指针 | 双指针 | [LeetCode 206: 反转链表](https://leetcode-cn.com/problems/reverse-linked-list/) | [Leetcode 206](#3.1) | 简单 |
| 链表指针 | 三指针 | [LeetCode 24: 两两交换链表中的节点](https://leetcode-cn.com/problems/swap-nodes-in-pairs/) | [Leetcode 24](#3.2) | 中等 |
| 链表指针 | 双指针 | [LeetCode 5: K个一组反转链表](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/) | [Leetcode 25](#3.3) | 困难 |
| 链表指针 | 双指针 | [LeetCode 19: 删除链表倒数第 N 个节点](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/) | [Leetcode 19](#3.4) | 简单 |
| 链表指针 | 迭代法 | [LeetCode 21: 合并两个有序链表](https://leetcode-cn.com/problems/merge-two-sorted-lists/) | [Leetcode 21](#3.5) | 简单 |


<h2 id = "3">三、解题笔记</h2>

<h3 id = "3.1">LeetCode 206: 反转链表</h3>
[返回高频题表](#problem)

入门级别的链表反转，最开始在 CS61B 中遇到这个问题，而后在 Leetcode 上找到了对应的题目。关键就在于每次翻转要注意保留之前的指针：

<div align=center><img width = "500" height = "250" src="https://user-images.githubusercontent.com/38673091/110267580-16256380-7ffb-11eb-8154-26ade72a1ab5.png"/></div>

<details>
<summary>LeetCode206</summary>

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
</details>
<h3 id = "3.2">LeetCode 24: 两两交换链表中的节点</h3>
[返回高频题表](#problem)

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
[返回高频题表](#problem)

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

<h3 id = "3.4">LeetCode 21: 删除链表倒数的第 N 个结点</h3>
[返回高频题表](#problem)

很经典的做法：双指针。
1. 初始化三个指针：sentinel.next = head、first = sentinel、second = sentinel；
   - 注意 first 和 second 指针需要指向sentinel，这样最后 return sentinel.next 才不会传回 head。因为 head 指针实际上没有变化，所以如果 return head 在corner case [1,2] N = 1 的情况下就会返回原始数组
2. 第一个指针 first 先走 n 步
3. 让两个指针 first 和 second 一起走，知道 first.next == null，此时说明 first 指针已经走到了链表的最末尾，并且 second 也走到了倒数的第 N+ 1 个位置
   - 之所以 second 要走到倒数 N+1 个位置是因为这是单向链表，需要使用 second.next = second.next.next 来删除倒数第 N 个结点。如果直接指向第 N 个结点，就无法删除本身结点了。
```java
    public ListNode removeNthFromEnd(ListNode head, int n) {
        if (head.next == null) return null;
        // 初始化节点，first 和 second 都必须指向 sentinel
        ListNode sentinel = new ListNode(-1, head);
        ListNode first = sentinel;
        ListNode second = sentinel;
        // 第一个指针先走 N 步
        for (int i = 0; i < n; i++) {
            first = first.next;
        }
        // first 和 second 指针一起移动，直到链表末尾
        while (first.next != null) {
            first = first.next;
            second = second.next;
        }
        // 删除倒数第 N 个结点
        second.next = second.next.next;
        return sentinel.next;
    }
```   


<h3 id = "3.5">LeetCode 21: 合并两个有序链表</h3>
[返回高频题表](#problem)

这道题仍然是链表指针的问题，使用一个 move 指针来将两个有序链表合并。
- 注意：move.next 即为下一个 ListNode，所以不需要将 l1、l2 的链表破坏即可形成新的链表。

```java
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode sentinel = new ListNode(0);
        ListNode move = sentinel;
        if (l1 == null) return l2;
        if (l2 == null) return l1;
        /**
         * 引入sentinel node，方便return
         * 不能再引入 moveOne/moveTwo 指向 l1/l2 的原因：
         * 会将sentinel指向空指针，并且并没有形成新的链表。
         */
        while (l1 != null && l2 != null) {
            if (l1.val < l2.val) {
                // move 指针只去寻找更小的 node
                move.next = l1;
                l1 = l1.next;
            } else {
                move.next = l2;
                l2 = l2.next;
            }
            move = move.next;
        }
        /**
         * 上述循环只用完了短链表中的值，但是对于长链表，还有node没有连接上
         * 因为while循环是从小到大排列，所以接下来剩余的链表，直接连到move最后就可以了*/
        move.next = l1 == null ? l2 : l1;
        return sentinel.next;
    }
```