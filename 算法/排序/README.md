# 排序

<span id ="0"></span>


## [一、知识点](#1)
 - [排序](#1.1)




## [二、高频题](#2)

## [三、题解笔记](#2)



<h2 id = "1">一、知识点</h2>

<h3 id = "1.1">排序</h3>

[返回目录](#0)

![image](https://user-images.githubusercontent.com/38673091/112747866-a64b3d00-8fea-11eb-8e0b-4489b14a2ed8.png)



<h2 id = "2">二、高频题</h2>

[返回目录](#0)

<span id ="100"></span>



总结：

 知识点 | 技巧 | 题目地址 | 解题代码 | 难度 |
| --- | --- | --- | --- | --- |
| 排序 | 快排，new Comparator | [LeetCode 56：合并区间 ](https://leetcode-cn.com/problems/merge-intervals/) | [Leetcode 56](#3.1) | 中等 |
| 排序 | 归并排序 | [LeetCode 148：排序链表 ](https://leetcode-cn.com/problems/sort-list/) | [Leetcode 148](#3.2) | 中等 |
|  |  | [LeetCode ：]() | [Leetcode ](#3.) |  |




<h2 id = "3">三、解题笔记</h2>


<h3 id = "3.1">LeetCode 56：合并区间 </h3>

[返回高频题](#100)

这道题用的是 Arrays.sort 这个 java 自带的库，对于实现快排的代码，可以参考 Leetcode 315

步骤比较简单：
1. 先将所有的 interval 数组按照左边界进行排序
2. 然后比较结果集和 intervals[i] 是否有相交的边界，有则合并，没有则添加进结果集，并将其用来比作下一次比较的对象

<details>
<summary>LeetCode 56--代码 </summary>

```java
    public int[][] merge(int[][] intervals) {
        int length = intervals.length;
        if (length < 2) return intervals;

        Arrays.sort(intervals, new Comparator<int[]>() {
            public int compare(int[] intervalOne, int[] intervalTwo) {
                return intervalOne[0] - intervalTwo[0];
            }
        });

        List<int[]> ans = new ArrayList<>();
        ans.add(intervals[0]);
        for (int i = 1; i < length; i++) {
            int[] curInterval = intervals[i];
            int[] peekInterval = ans.get(ans.size() - 1);

            if (peekInterval[1] < curInterval[0]) {
                ans.add(curInterval);
            } else {
                peekInterval[1] = Math.max(peekInterval[1], curInterval[1]);
            }
        }
        return ans.toArray(new int[ans.size()][]);
    } 
```
</details>


<h3 id = "3.2">LeetCode 148：排序链表 </h3>

[返回高频题](#100)

归并排序的实操.
1. 先用快慢指针找到链表的中点，然后递归地执行这个函数
2. 在 merge 函数中将其合并，这里就和 Leetcode 21 - 合并两个有序链表的代码是一致的

<details>
<summary>LeetCode 148 -- 代码</summary>

```java
    public ListNode sortList(ListNode head) {
        return head == null ? head : mergeSort(head);
    }

    private ListNode mergeSort(ListNode head) {
        if (head.next == null) {
            return head;
        }

        ListNode fast = head, slow = head;
        ListNode saveNode = new ListNode();
        while (fast!= null && fast.next != null) {
            saveNode = slow;
            fast = fast.next.next;
            slow = slow.next;
        }
        saveNode.next = null;
        ListNode leftList = mergeSort(head);
        ListNode rightList = mergeSort(slow);
        return merge(leftList, rightList);
    }

    private ListNode merge(ListNode leftList, ListNode rightList) {
        ListNode sentinel = new ListNode(-1);
        ListNode move = sentinel;
        while (leftList != null && rightList != null) {
            if (leftList.val < rightList.val) {
                move.next = leftList;
                move = move.next;
                leftList = leftList.next;
            } else {
                move.next = rightList;
                move = move.next;
                rightList = rightList.next;
            }
            move.next = leftList == null ? rightList : leftList;
        }
        return sentinel.next;
    }
```
</details>


<h3 id = "3.3">LeetCode  ： </h3>

[返回高频题](#100)



<details>
<summary>LeetCode -- </summary>

```java


```
</details>



<h3 id = "3.4">LeetCode  ： </h3>

[返回高频题](#100)


<details>
<summary>LeetCode -- </summary>

```java

```
</details>



<h3 id = "3.5">LeetCode  ： </h3>

[返回高频题](#100)


<details>
<summary>LeetCode -- </summary>

```java

```
</details>
