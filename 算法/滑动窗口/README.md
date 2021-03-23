# 滑动窗口

<span id ="0"></span>


## [一、知识点](#1)
 - [滑动窗口](#1.1)

## [二、高频题](#2)

## [三、题解笔记](#2)



<h2 id = "1">一、知识点</h2>

<h3 id = "1.1">滑动窗口</h3>

[返回目录](#0)




<h2 id = "2">二、高频题</h2>

[返回目录](#0)

<span id ="100"></span>



总结：

 知识点 | 技巧 | 题目地址 | 解题代码 | 难度 |
| --- | --- | --- | --- | --- |
| 滑动窗口 | 滑动窗口、哈希表、注意指针移动的表达式 | [LeetCode 3:无重复字符的最长字串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/) | [Leetcode 3](#3.1) | 中等 |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |




<h2 id = "3">三、解题笔记</h2>


<h3 id = "3.1">LeetCode 3 ：无重复字符的最长字串</h3>

[返回高频题](#100)

注意，在判断 index 位置的字符的确在 hashMap 中之后，就需要移动 left 指针，但不能简单的设置 `left = map.get(s.charAt(index)) + 1`,
- 例如对于这个例子：`"abba"`，
- 遇到最后一个 a 的时候，这时候的 left = 3，而 `map.get(s.charAt(index)) + 1 = 1`，相当于重新去遍历数组去了，得到的答案肯定就是不正确的
- 正确的移动left 指针的方式：`left = Math.max(left, map.get(sChar[index]) + 1);`

<details>
<summary>LeetCode 3 -- 无重复字符的最长字串代码</summary>

```java
    public int lengthOfLongestSubstring(String s) {
        if (s.length() == 0) return 0;
        if (s.length() == 1) return 1;
        char[] sChar = s.toCharArray();
        HashMap<Character, Integer> map = new HashMap<>();
        int ans = 0, left = 0;
        for (int index = 0; index < sChar.length; index++) {
            if (map.containsKey(sChar[index])) {
                left = Math.max(left, map.get(sChar[index]) + 1);
            }
            ans = Math.max(ans, index - left + 1);
            map.put(sChar[index], index);
        }
        return ans;
    }
```
</details>


<h3 id = "3.2">LeetCode  ： </h3>

[返回高频题](#100)



<details>
<summary>LeetCode  -- </summary>

```java

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
