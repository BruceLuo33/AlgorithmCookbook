# 哈希表与集合

<span id ="0"></span>


## [一、知识点](#1)
 - [HashMap](#1.1)
 - [HashSet](#1.2)

## [二、高频题](#2)

## [三、题解笔记](#2)



<h2 id = "1">一、知识点</h2>

<h3 id = "1.1">HashMap</h3>

[返回目录](#0)


<h3 id = "1.2">HashSet</h3>

[返回目录](#0)



<h2 id = "2">二、高频题</h2>

[返回目录](#0)

<span id ="100"></span>



总结：

 知识点 | 技巧 | 题目地址 | 解题代码 | 难度 |
| --- | --- | --- | --- | --- |
| 哈希 | 投票法 | [LeetCode 242: 有效的字母异位词](https://leetcode-cn.com/problems/valid-anagram/) | [Leetcode 242](#3.1) | 简单 |
| 哈希 |  | [LeetCode 49: 字母异位词分组](https://leetcode-cn.com/problems/group-anagrams/) | [Leetcode 49](#3.2) | 中等 |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |




<h2 id = "3">三、解题笔记</h2>


<h3 id = "3.1">LeetCode 242 ：有效的字母异位词</h3>

[返回高频题](#100)

- 思路一：暴力破解。将string sort，然后比较每一个元素。
- 思路二：HashMap。第一个循环将 s 中的所有char 放入map，然后再去检查 t 中每一个元素是否在里面
  1. 在这道题中，因为比较的元素只有 26 个字母，所以我们事实上可以用数组来充当 HashMap，0-25 分别代表 a-z
  2. 遍历两个字符串， String s 中出现的字母，将其对应数组值 +1，String t 中出现的字母，将其对应数组值 -1，最后判断这个数字是否为空即可。
- 复杂度分析：1、O（NlogN）；2、O（N）
- 注意：不要将 s/t 转换为 charArray，直接用 charAt 来做就可以了

<details>
<summary>LeetCode 242 -- 有效的字母异位词</summary>

```java
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;
        int[] ans = new int[26];
        for (int i = 0; i < s.length(); i++) {
            ans[s.charAt(i) - 'a'] += 1;
            ans[t.charAt(i) - 'a'] -= 1;
        }
        for (int a : ans) {
            if (a != 0) return false;
        }
        return true;
    }
```
</details>


<h3 id = "3.2">LeetCode  49：字母异位词分组 </h3>

[返回高频题](#100)

两种方法：
1. 第一种，先将 String 转换成 charArray，然后再 sort，这样所有的字母异位词就能够呈现同样的顺序
2. 第二种方法，统计每个单词中 char 出现的次数，然后用类似 a2b4z2 的方式来表示
- 注意，hashMap 中，key 是一样的元素，即第一种方法中的转换之后的charArray.toString()，第二种方法中的 a2b4z2

<details>
<summary>LeetCode  -- </summary>

```java
    public List<List<String>> groupAnagrams(String[] strs) {
        HashMap<String, List<String>> ans = new HashMap<>();
        if (strs == null || strs.length == 0) return null;
        for (String str : strs) {
            int[] freq = new int[26];
            for (char c : str.toCharArray()) {
                freq[c - 'a'] += 1;
            }
            StringBuffer sb = new StringBuffer();
            for (int i = 0; i < freq.length; i++) {
                if (freq[i] != 0) {
                    sb.append((char) ('a' + i)).append(freq[i]);
                }
            }
            String key = sb.toString();
            List<String> value = ans.getOrDefault(key, new ArrayList<String>());
            value.add(str);
            ans.put(key, value);
        }
        return new ArrayList<List<String>>(ans.values());
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
