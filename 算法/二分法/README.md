# 二分法

<span id ="0"></span>


## [一、知识点](#1)
 - [二分法](#1.1)




## [二、高频题](#2)

## [三、题解笔记](#2)



<h2 id = "1">一、知识点</h2>

<h3 id = "1.1">二分法</h3>

[返回目录](#0)




<h2 id = "2">二、高频题</h2>

[返回目录](#0)

<span id ="100"></span>



总结：

 知识点 | 技巧 | 题目地址 | 解题代码 | 难度 |
| --- | --- | --- | --- | --- |
| 二分法 | 区间指针 | [LeetCode 153: 寻找旋转排序数组中的最小值](https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array/) | [Leetcode 153](#3.1) | 中等 |
| 二分法 | 区间指针 | [LeetCode 154: 寻找旋转排序数组中的最小值II](https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array-ii/) | [Leetcode 153](#3.2) | 困难 |
| 同上题 | 同上题 | [剑指Offer 11 旋转数组的最小数字: ](https://leetcode-cn.com/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/) | [剑指Offer 11 ](#3.2) | 简单 |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |




<h2 id = "3">三、解题笔记</h2>


<h3 id = "3.1">LeetCode 153 ： 寻找旋转排序数组中的最小值</h3>

[返回高频题](#100)

这道题是很经典的一道题，也是理解二分法的入门，注意这里的几个条件：
1. 原本有序的数组
2. 数组中没有重复元素
3. 推论：第一个元素一定大于（或等于，在154中有用）最后一个元素
同时，要注意为了避免陷入死循环，left = mid + 1 而不是 left = mid。

<details>
<summary>LeetCode 153 --寻找旋转排序数组中的最小值 </summary>

```java
class Solution {
    public int findMin(int[] nums) {
        if (nums.length == 1) return nums[0];
        int left = 0, right = nums.length - 1;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] <= nums[right]) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return nums[right];
    }
}
```
</details>


<h3 id = "3.2">LeetCode 154：寻找旋转排序数组中的最小值II </h3>
（同 剑指 Offer 11）

[返回高频题](#100)

这道题和 153 非常相似，但是不同的地方在于这里会有重复的值。在《剑指 Offer》中，采用的方法是如果 left，mid，right 三个指针指向的值相等，就直接使用顺序查找，复杂度退化为 O(n)。

但是在这里，可以使用另一个方法，即如果出现了 `nums[mid] == nums[right]`，就让 right -= 1，往左边移动一格。这样就可以避免出现找不到的情况。

因为二分法其实就是一个针对特殊数组（已排序）的抽样，上面的判断就是针对抽样不能反应整体的处理。

<details>
<summary>LeetCode 154 -- 寻找旋转排序数组中的最小值II</summary>

```java
    public int findMin(int[] nums) {
        if (nums.length == 0) return -1;
        if (nums.length == 1) return nums[0];
        int left = 0, right = nums.length - 1;
        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] == nums[right]) {
                right -= 1;
            } else if (nums[mid] < nums[right]) {
                right = mid;
            } else {
                left = mid + 1;
            }
        }
        return nums[right];
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
