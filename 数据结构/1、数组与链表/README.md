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

[返回目录](#0)

<span id ="100"></span>



总结：

 知识点 | 技巧 | 题目地址 | 解题代码 | 难度 |
| --- | --- | --- | --- | --- |
| 链表指针 | 双指针 | [LeetCode 206: 反转链表](https://leetcode-cn.com/problems/reverse-linked-list/) | [Leetcode 206](#3.1) | 简单 |
| 链表指针 | 三指针 | [LeetCode 24: 两两交换链表中的节点](https://leetcode-cn.com/problems/swap-nodes-in-pairs/) | [Leetcode 24](#3.2) | 中等 |
| 链表指针 | 双指针 | [LeetCode 5: K个一组反转链表](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/) | [Leetcode 25](#3.3) | 困难 |
| 链表指针 | 双指针 | [LeetCode 19: 删除链表倒数第 N 个节点](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/) | [Leetcode 19](#3.4) | 中等 |
| 链表指针 | 迭代法 | [LeetCode 21: 合并两个有序链表](https://leetcode-cn.com/problems/merge-two-sorted-lists/) | [Leetcode 21](#3.5) | 简单 |
| 链表指针 | 双指针 | [LeetCode 141: 环形链表](https://leetcode-cn.com/problems/linked-list-cycle/) | [Leetcode 141](#3.6) | 简单 |
| 链表指针 | 双指针 | [LeetCode 142: 环形链表II](https://leetcode-cn.com/problems/linked-list-cycle-ii/) | [Leetcode 142](#3.7) | 中等 |
| 链表指针 | 双指针 | [LeetCode 876: 链表的中间节点](https://leetcode-cn.com/problems/middle-of-the-linked-list/) | [Leetcode 876](#3.8) | 简单 |
| 链表指针 | 指针 + 哈希 | [LeetCode 146: LRU 缓存机制](https://leetcode-cn.com/problems/lru-cache/) | [Leetcode 146](#3.9) | 中等 |
| 数组指针 | 左右双指针 | [LeetCode 11：盛最多水的容器](https://leetcode-cn.com/problems/container-with-most-water/) | [Leetcode 11](#3.10) | 中等 |
| 数组指针 | 前后双指针 | [LeetCode 283：移动零](https://leetcode-cn.com/problems/move-zeroes/) | [Leetcode 283](#3.11) | 简单 |
| 数组DP | 动态规划 | [LeetCode 70：爬楼梯](https://leetcode-cn.com/problems/climbing-stairs/) | [Leetcode 70](#3.12) | 简单 |
| 数组指针 | 首尾双指针 | [LeetCode 15：三数之和](https://leetcode-cn.com/problems/3sum/) | [Leetcode 15](#3.13) | 中等 |
| 数组指针 | 前后双指针 | [LeetCode 26：移除排序数组中的重复项](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/) | [Leetcode 26](#3.14) | 简单 |
| 数组指针 | 首尾双指针 | [LeetCode 167：两数之和II](https://leetcode-cn.com/problems/two-sum-ii-input-array-is-sorted/) | [Leetcode 167](#3.15) | 简单 |
| 数组 | 多次翻转 | [LeetCode 189：旋转数组](https://leetcode-cn.com/problems/rotate-array/) | [Leetcode 189](#3.16) | 中等 |
| 数组指针 | 双指针 | [LeetCode 88：合并两个有序数组](https://leetcode-cn.com/problems/merge-sorted-array/) | [Leetcode 88](#3.17) | 简单 |
| 数组 | 双指针/哈希表 | [LeetCode 1：两数之和](https://leetcode-cn.com/problems/two-sum/) | [Leetcode 1](#3.18) | 简单 |
| 数组 |  | [LeetCode 66：加一](https://leetcode-cn.com/problems/plus-one/) | [Leetcode 66](#3.19) | 简单 |



<h2 id = "3">三、解题笔记</h2>

<h3 id = "3.1">LeetCode 206: 反转链表</h3>

[返回高频题](#100)


入门级别的链表反转，最开始在 CS61B 中遇到这个问题，而后在 Leetcode 上找到了对应的题目。关键就在于每次翻转要注意保留之前的指针：

<div align=center><img width = "500" height = "250" src="https://user-images.githubusercontent.com/38673091/110267580-16256380-7ffb-11eb-8154-26ade72a1ab5.png"/></div>

<details>
<summary>LeetCode 206 代码</summary>

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

[返回高频题](#100)

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
<details>
<summary>LeetCode 24 代码</summary>

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

</details>

<h3 id = "3.3">LeetCode 25: k 个一组翻转链表</h3>

[返回高频题](#100)


1. 这道题就是之前两题的综合了。首先可以看出有一个反转链表的需求，因此可以将206题的答案作为子函数。
2. 然后问题就在于找到子链表的方法，如下所示，子链表用 start~end 标识，移动 k 次 end，不越界即为子链表

<details>
<summary>LeetCode25 代码</summary>

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
</details>


<h3 id = "3.4">LeetCode 21: 删除链表倒数的第 N 个结点</h3>

[返回高频题](#100)


很经典的做法：双指针。
1. 初始化三个指针：sentinel.next = head、first = sentinel、second = sentinel；
   - 注意 first 和 second 指针需要指向sentinel，这样最后 return sentinel.next 才不会传回 head。因为 head 指针实际上没有变化，所以如果 return head 在corner case [1,2] N = 1 的情况下就会返回原始数组
2. 第一个指针 first 先走 n 步
3. 让两个指针 first 和 second 一起走，知道 first.next == null，此时说明 first 指针已经走到了链表的最末尾，并且 second 也走到了倒数的第 N+ 1 个位置
   - 之所以 second 要走到倒数 N+1 个位置是因为这是单向链表，需要使用 second.next = second.next.next 来删除倒数第 N 个结点。如果直接指向第 N 个结点，就无法删除本身结点了。

<details>
<summary>LeetCode 19 代码</summary>

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
</details>


<h3 id = "3.5">LeetCode 21: 合并两个有序链表</h3>

[返回高频题](#100)


这道题仍然是链表指针的问题，使用一个 move 指针来将两个有序链表合并。
- 注意：move.next 即为下一个 ListNode，所以不需要将 l1、l2 的链表破坏即可形成新的链表。


<details>
<summary>LeetCode 21 代码</summary>

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
</details>


<h3 id = "3.6">LeetCode 141: 环形链表</h3>

[返回高频题](#100)

这题是快慢双指针的运用，一个 fast 指针，一个 slow 指针，一开始都指向 head：
- 然后 fast 每次往前移动两步，slow 每次往前移动一步，当 fast.next 和 fast.next.next 都不为空的情况下，如果二者相等，说明有环


<details>
<summary>LeetCode 141--环形链表 代码</summary>

```java
    public boolean hasCycle(ListNode head) {
        if (head == null || head.next == null) return false;
        ListNode fast = head;
        ListNode slow = head;
        while (fast.next != null && fast.next.next != null) {
            fast = fast.next.next;
            slow = slow.next;
            if (fast == slow) {
                return true;
            } 
        }
        return false;
    }
```
</details>

<h3 id = "3.7">LeetCode 142：环形链表II</h3>

[返回高频题](#100)

1. 先利用找环形链表的技巧，设置两个指针：fast 与 slow，循环至二者相遇，否则返回 null；
2. 设置一个 chase Node，从起点 head 出发，每次步进一个 node，同时从 fast/slow 节点出发，步进一；
3. 当 chase 与 fast 相遇，即为环的入口。

<details>
<summary>LeetCode 142--环形链表II 代码</summary>

```java
public ListNode detectCycle(ListNode head) {
    if (head == null || head.next == null) return null;
    int pos = 0;
    ListNode fast = new ListNode(-1);
    ListNode slow = new ListNode(-1);
    ListNode chase = new ListNode(-1);
    fast.next = head;
    slow.next = head;
    chase.next = head;
    while (fast.next != null && fast.next.next != null) {
        fast = fast.next.next;
        slow = slow.next;
        if (fast == slow) break;
    }
    if (fast != slow) return null;
    while (chase != slow) {
        chase = chase.next;
        slow = slow.next;
    }
    return chase;
}
```
</details>

<h3 id = "3.8">LeetCode 876: 链表的中间节点</h3>

[返回高频题](#100)

这题和环形指针一样，仍然是快慢双指针的运用，一个 fast 指针，一个 slow 指针，一开始都指向 head：
当 fast 走到了最后一个结点的时候，返回 slow.next 即可

<details>
<summary>LeetCode 141--环形链表 代码</summary>

```java
    public ListNode middleNode(ListNode head) {
        if (head == null || head.next == null) return head;
        ListNode fast = new ListNode(-1);
        ListNode slow = new ListNode(-1);
        fast.next = head;
        slow.next = head;
        while (fast.next != null && fast.next.next != null) {
            fast = fast.next.next;
            slow = slow.next;
        }
        return slow.next;
    }
```
</details>

<h3 id = "3.9">LeetCode 146: LRU 缓存机制</h3>

[返回高频题](#100)

这是一个数据结构设计题。使用 HashMap + 双向链表的方式来完成。
1. 需要新建两个子类：Node 和 DoubleList
2. Node 类即为双向链表的结点，有前驱后继指针，在 DoubleList 中写关键逻辑方法
3. DoubleList：remove、removeLast、addFirst、getSize 等方法

<details>
<summary>LeetCode 146--LRU缓存 代码</summary>

```java
class LRUCache {

    class Node {
        int key, val;
        Node prev, next;
        public Node (int key, int val) {
            this.key = key;
            this.val = val;
        }
    }

    class DoubleList {
        private Node head, tail;
        int size;
        public DoubleList () {
            head = new Node(0, 0);
            tail = new Node(0, 0);
            tail.prev = head;
            head.next = tail;
            size = 0;
        }

        public void addFirst(Node x) {
            size += 1;
            x.next = head.next;
            head.next = x;
            x.prev = head;
            x.next.prev = x;
        }

        public void remove(Node x) {
            size -= 1;
            x.next.prev = x.prev;
            x.prev.next = x.next;
        }

        public Node removeLast() {
            if (tail.prev == head) return null;
            size -= 1;
            Node tmp = tail.prev;
            tmp.prev.next = tail;
            tail.prev = tmp.prev;
            tmp.next = null;
            tmp.prev = null;
            return tmp;

        }

        public int size() {
            return size;
        }

    }


    private DoubleList list;
    private HashMap<Integer, Node> map;
    private int capacity;

    public LRUCache(int capacity) {
        this.capacity = capacity;
        list = new DoubleList();
        map = new HashMap<>();
    }
    
    public int get(int key) {
        if (!map.containsKey(key)) {
            return -1;
        }
        int val = map.get(key).val;
        put(key, val);
        return val;
    }
    
    public void put(int key, int value) {
        Node curNode = new Node(key, value);
        if (map.containsKey(key)) {
            list.remove(map.get(key));
            list.addFirst(curNode);
            map.put(key, curNode);
        } else {
            if (list.size == capacity) {
                Node lastNode = list.removeLast();
                map.remove(lastNode.key);
            }
            list.addFirst(curNode);
            map.put(key, curNode);
        }
    }
}
```
</details>

<h3 id = "3.10">LeetCode 11：盛最多水的容器</h3>

[返回高频题](#100)

1. 一开始的时候，会想到从最左侧的原点出发，使用双指针，第一个指针从左到右标识左边界，第二个指针从第一个指针的位置开始往右走，依次遍历，每走一步都求一次面积
2. 但是这个方法的问题在于，复杂度很高，O(n^2) 的复杂度
3. 联想到剑指 Offer 04，这里我们可以从两端往中间走，只需要一次遍历就能完成

<details>
<summary>LeetCode 11--盛最多水的容器 代码</summary>

```java
    public int maxArea(int[] height) {
        int leftIndex = 0, rightIndex = height.length - 1;
        int maxArea = (rightIndex - leftIndex) * Math.min(height[rightIndex], height[leftIndex]);
        while (leftIndex < rightIndex) {
            if (height[leftIndex] < height[rightIndex]) {
                leftIndex += 1;
            } else {
                rightIndex -= 1;
            }
            if (leftIndex < rightIndex) {
                int tmpArea = (rightIndex - leftIndex) * Math.min(height[rightIndex], height[leftIndex]);
                maxArea = tmpArea > maxArea ? tmpArea : maxArea;
            }
        }
        return maxArea;
    }
```
</details>

<h3 id = "3.11">LeetCode 283：移动零</h3>

[返回高频题](#100)

属于很经典的双指针了：
1. 使用两个指针，第一个为 move 指针，从头遍历到末尾
2. 第二个指针为 lastNonZero 指针，指向从左到右出现的第一个零前面的位置

<details>
<summary>LeetCode 11--盛最多水的容器 代码</summary>

```java
    public void moveZeroes(int[] nums) {
        int move = 0;
        int lastNonZero = 0;
        for (move = 0; move < nums.length; move++) {
            if (nums[move] != 0) {
                nums[lastNonZero] = nums[move];
                lastNonZero += 1;
            }
        }
        while (lastNonZero < nums.length) {
            nums[lastNonZero] = 0;
            lastNonZero += 1;
        }
    }
```
</details>




<h3 id = "3.12">LeetCode 70：爬楼梯</h3>

[返回高频题](#100)

斐波那契数列的简单移植。
- 每一个台阶，都是前一个状态的台阶走 1 步或者 2 步上来的，因此状态转移方程也就出来了：
- third = first + second

<details>
<summary>LeetCode 70--爬楼梯 代码</summary>

```java
    public int climbStairs(int n) {
        if ( n < 2) return n;
        int first = 1, second = 2;
        int third = 0;
        for (int i = 3; i <= n; i++) {
            third = first + second;
            first = second;
            second = third;
        }
        return second;
    }
```
</details>



<h3 id = "3.13">LeetCode 15：三数之和</h3>

[返回高频题](#100)

和 **Leetcode 11 -- 盛最多水的容器** 类似的思路，左右双指针。
- 注意：如果是简单的固定一个指针，然后另外两个指针从两端往中间走，这样的复杂度仍然会超时
- 需要用一些判断来取重：即如果两个相邻的数字相同，则指针往中间移动一位
- 要先对数组排序

<details>
<summary>LeetCode 15--三数之和 代码</summary>

```java
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        if (nums == null || nums.length == 0 || nums.length < 3) return ans;
        int sum;
        int first, second, third = nums.length - 1;
        Arrays.sort(nums);
        int minValue = nums[0] + nums[1] + nums[2];
        int maxValue = nums[third] + nums[third - 1] + nums[third - 2];
        if (minValue > 0 || maxValue < 0) {
            return ans;
        }
        for (first = 0; first < nums.length - 2; first++) {
            if (first > 0 && nums[first] == nums[first - 1]) {
                continue;
            }
            second = first + 1;
            third = nums.length - 1;
            while (second < third) {
                sum = nums[first] + nums[second] + nums[third];
                if (sum == 0) {
                    Integer[] subList = {nums[first], nums[second], nums[third]};
                    ans.add(Arrays.asList(subList));
                    second += 1;
                    third -= 1;
                    while (second < third &&  nums[second] == nums[second - 1]) {
                        second += 1;
                    }
                    while (second < third &&  nums[third] == nums[third + 1]) {
                        third -= 1;
                    }
                } else if (sum < 0) {
                    second += 1;
                } else if (sum > 0) {
                    third -= 1;
                }
            }
        }
        return ans;
    }
```
</details>


<h3 id = "3.14">LeetCode 26：移出排序数组中的重复项</h3>

[返回高频题](#100)

和 283 移动零一样的思路，两个指针，第一个指针从头到尾遍历数组，第二个指针指向最后一个确定的非重复项
1. 如果两个指针指向的值相等，说明有了重复项，因此第二个指针 sign 就保持不动，只去移动第一个指针
2. 如果值不相等，说明出现了重复项，因为 sign 指向的是最后一个**确定的**重复项，那么对于 sign + 1 是否重复其实是不关心的，所以，直接将 move 的值赋给 sign + 1 即可，然后两个指针都往前走一步； 
- 注意：最后返回的是 sign + 1，因为sign 是数组下标，但是需要的是数组的元素个数
<details>
<summary>LeetCode 26--移出排序数组中的重复项 代码</summary>

```java
    public int removeDuplicates(int[] nums) {
        if (nums == null || nums.length == 0) return 0;
        if (nums.length == 1) return 1;
        int sign = 0, move = 0;
        while (move < nums.length) {
            if (nums[move] != nums[sign]) {
                sign += 1;
                nums[sign] = nums[move];
            }
            move += 1;
        }
        return sign + 1;
    }
```
</details>

<h3 id = "3.15">LeetCode 167 ：两数之和 II</h3>

[返回高频题](#100)

和 3sum 一样的思路，首尾双指针。

<details>
<summary>LeetCode 167-- 两数之和II代码</summary>

```java
    public int[] twoSum(int[] numbers, int target) {
        int[] ans = new int[2];
        int first = 0, last = numbers.length - 1;
        int minValue = numbers[0] + numbers[1];
        int maxValue = numbers[last] + numbers[last - 1];
        if (minValue > target || maxValue < target) return ans;
        int sum;
        while (first < last) {
            sum = numbers[first] + numbers[last];
            if (sum == target) {
                ans[0] = first + 1;
                ans[1] = last + 1;
                return ans;
            } else if (sum < target) {
                first += 1;
                while (first < last && numbers[first] == numbers[first - 1]) {
                    first += 1;
                }
            } else {
                last -= 1;
                while (first < last && numbers[last] == numbers[last + 1]) {
                    last -= 1;
                }
            }
        }
        return ans;
    }
```
</details>

<h3 id = "3.16">LeetCode  189： 旋转数组</h3>

[返回高频题](#100)

这道题有多种方法：
1. 使用临时数组，然后按照 k%length 的顺序放入原数组的值；
2. 三次翻转：先翻转整个数组，然后翻转处理后数组的前 [0, k-1] 的子数组，再翻转 [k, len-1] 的子数组；
3. 循环移动：每次移动 k 步，然后将该位置 n 的值改为 n-k 的值，并用一个临时变量保存，以此类推。

<details>
<summary>LeetCode -- </summary>

```java
    public void rotate(int[] nums, int k) {
        k = k % nums.length;
        reverse(nums, 0, nums.length - 1);
        reverse(nums, 0, k-1);
        reverse(nums, k, nums.length - 1);
        return;
    }

    public void reverse(int[] nums, int start, int end) {
        if (start > end) return;
        while (start < end) {
            int tmp = nums[start];
            nums[start] = nums[end];
            nums[end] = tmp;
            start += 1;
            end -= 1;
        }
    }
```
</details>



<h3 id = "3.17">LeetCode 88：合并两个有序数组 </h3>

[返回高频题](#100)

这道题的启发来自于剑指offer.05 替换空格。数组内元素移动的问题，就要考虑移动的复杂度较高，因此可以从后往前移动。

<details>
<summary>LeetCode 88-- 合并两个有序数组</summary>

```java
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int index = m + n - 1;
        int firstIndex = m - 1, secondIndex = n - 1;
        while (firstIndex >= 0 && secondIndex >= 0) {
            if (nums1[firstIndex] > nums2[secondIndex]) {
                nums1[index] = nums1[firstIndex];
                firstIndex -= 1;
                index -= 1;
            } else {
                nums1[index] = nums2[secondIndex];
                secondIndex -= 1;
                index -= 1;
            }
        }
        while (secondIndex >= 0) {
            nums1[index--] = nums2[secondIndex--];
        }
        return;
    }
```
</details>


<h3 id = "3.18">LeetCode  1： 两数之和</h3>

[返回高频题](#100)

这道题有几种解法：
1. 暴力双重循环。固定一个指针，然后另一个指针循环地去找 target-nums[i] 是否存在
2. 首尾双指针。这个技巧在前面的三数之和、两数之和II 中都已经使用过。在这里可以获得比前一种方法更低的时间复杂度，即 Arrays.sort 的复杂度
3. hashmap。在哈希表中存放(value, pos) 的键值对，每次都去寻找 target-nums[i] 这个差值是否能在 map 中找到
   - 如果能找到，说明当前的 nums[i] 需要的差值，就是之前遍历过的数组中的某个值，返回 hashMap 中的值即可
   - 如果找不到，就将当前的 nums[i] 放入 hashMap，这时候它就作为差值，来继续接下来的匹配
- 时间复杂度：从O(n^2) 降低到 O(NlogN) 进一步降低到了 O(N)

<details>
<summary>LeetCode 1--两数之和 </summary>

```java
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int diff = target - nums[i];
            if (map.containsKey(diff)) {
                return new int[] {i, map.get(diff)};
            }
            map.put(nums[i], i);
        }
        return null;
    }
```
</details>


<h3 id = "3.19">LeetCode 66：加一</h3>

[返回高频题](#100)

直接数组本身求解

<details>
<summary>LeetCode 66-- 加一</summary>

```java
    public int[] plusOne(int[] digits) {
        int len = digits.length;
        for (int i = len - 1; i >= 0; i--) {
            if (digits[i] != 9) {
                digits[i] += 1;
                return digits;
            }
            digits[i] = 0;
        }
        int[] tmp = new int[len + 1];
        tmp[0] = 1;
        return tmp;
    }
```
</details>

<h3 id = "3.20">LeetCode  ： </h3>

[返回高频题](#100)


<details>
<summary>LeetCode -- </summary>

```java

```
</details>

<h3 id = "3.21">LeetCode  ： </h3>

[返回高频题](#100)


<details>
<summary>LeetCode -- </summary>

```java

```
</details>