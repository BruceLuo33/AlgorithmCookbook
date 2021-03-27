# 动态规划

<span id ="0"></span>


## [一、知识点](#1)
 - [动态规划](#1.1)

## [二、高频题](#2)

## [三、题解笔记](#2)



<h2 id = "1">一、知识点</h2>

<h3 id = "1.1">动态规划</h3>

[返回目录](#0)

有四个特点：

1. 求解最优解
2. 可以分解为子问题，且子问题也有最优解
3. 子问题有更小的重叠子问题
4. 从上往下分析问题，从下往上求解问题


<h2 id = "2">二、高频题</h2>

[返回目录](#0)

<span id ="100"></span>



总结：

 知识点 | 技巧 | 题目地址 | 解题代码 | 难度 |
| --- | --- | --- | --- | --- |
| 动态规划 | 空间降低到O(1) | [LeetCode 70：爬楼梯 ](https://leetcode-cn.com/problems/climbing-stairs/) | [Leetcode 70](#3.1) | 简单 |
| 动态规划 |  | [LeetCode 198：打家劫舍 ](https://leetcode-cn.com/problems/house-robber/) | [Leetcode 198](#3.2) | 中等 |
| 动态规划 |  | [LeetCode 213：打家劫舍II ](https://leetcode-cn.com/problems/house-robber-ii/) | [Leetcode 213](#3.3) | 中等 |
| 动态规划 | 状态：hold 和 change | [LeetCode 121：买卖股票的最佳时机 ](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock/) | [Leetcode 121](#3.4) | 简单 |
| 动态规划 |  | [LeetCode 122：买卖股票的最佳时机II ](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-ii/) | [Leetcode ](#3.5) | 简单 |
| 动态规划 | 对于连续子数组的理解 | [LeetCode 53：最大子序和](https://leetcode-cn.com/problems/maximum-subarray/) | [Leetcode 53](#3.6) | 简单 |
| 动态规划 | 字串的常规定义 dp[i][j] 与 s(i...j) | [LeetCode 5：最长回文字串 ](https://leetcode-cn.com/problems/longest-palindromic-substring/) | [Leetcode 5](#3.7) | 中等 |
| 动态规划、双指针 | 从暴力法逐步优化的思路 | [LeetCode 42：接雨水](https://leetcode-cn.com/problems/trapping-rain-water/) | [Leetcode 42](#3.8) | 困难 |
| 动态规划 | dp[i][j] 表示 word1[i] 与 word2[j] 之间的距离| [LeetCode 72：编辑距离](https://leetcode-cn.com/problems/edit-distance/) | [Leetcode 72](#3.9) | 困难 |
| 动态规划 | 冷冻期也是不持有股票的状态 | [LeetCode 309：最佳买卖股票时机含冷冻期](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-with-cooldown/) | [Leetcode 309](#3.10) | 中等 |
| 动态规划 | O(n^2) 解法和二分法 | **[LeetCode 300：最长递增子序列]**(https://leetcode-cn.com/problems/longest-increasing-subsequence/) | [Leetcode 300](#3.11) | 中等 |
| 动态规划 | amount 和 coins 双重循环 | [LeetCode 322：零钱兑换](https://leetcode-cn.com/problems/coin-change/) | [Leetcode 322](#3.12) | 中等 |
| 动态规划 | 子序列，不是子数组（连续） | [LeetCode 1143：最长公共子序列](https://leetcode-cn.com/problems/longest-common-subsequence/) | [Leetcode 1143](#3.13) | 中等 |
| 动态规划 | 简单的基础题 | [LeetCode 62：不同路径](https://leetcode-cn.com/problems/unique-paths/) | [Leetcode 62](#3.14) | 中等 |
| 动态规划 | 上一题的简单拓展 | [LeetCode 63:不同路径II](https://leetcode-cn.com/problems/unique-paths-ii/) | [Leetcode 63](#3.15) | 中等 |
| 动态规划 | 62 题对路径进行加权 | [LeetCode 64：最小路径和](https://leetcode-cn.com/problems/minimum-path-sum/) | [Leetcode 64](#3.16) | 中等 |
| 动态规划 | 特殊的矩阵（三角形） | [LeetCode 120：三角形的最小路径和](https://leetcode-cn.com/problems/triangle/) | [Leetcode 120](#3.17) | 中等 |
| 动态规划 |  | [LeetCode ：]() | [Leetcode ](#3.18) |  |
|  |  | [LeetCode ：]() | [Leetcode ](#3.19) |  |
|  |  | [LeetCode ：]() | [Leetcode ](#3.20) |  |




<h2 id = "3">三、解题笔记</h2>


<h3 id = "3.1">LeetCode  ：</h3>

[返回高频题](#100)


<details>
<summary>LeetCode  -- </summary>

```java

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

<h3 id = "3.6">LeetCode  53：最大子序和 </h3>

[返回高频题](#100)

关键是递推公式：`f(n) = Max(f(n-1) + H(n), H(n))`

因为是**连续**的子序列，所以对于一个元素，之前的子序和只有两个选择：

1. 要不就加上目前的这个元素
2. 要不就放去之前的子序和，从当前元素开始重新计算

之所以没有其他选择，是因为子序和是**连续的**

注意：
- 子序和的最大值，不一定是 ans 数组的最后一位，所以需要用 res 来记录 ans 数组中的最大值
- res 不能设置为 Integer.MIN_VALUE，因为 for 循环是从 1 开始的

<details>
<summary>LeetCode 53--最大子序和代码 </summary>

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int len = nums.length;
        if (len == 1) return nums[0];
        int[] ans = new int[len];
        ans[0] = nums[0];
        int res = ans[0]; // res 不能设置为 Integer.MIN_VALUE，因为 for 循环是从 1 开始的
        for (int i = 1; i < len; i++) {
            ans[i] = Math.max(ans[i-1] + nums[i], nums[i]);
            res = Math.max(res, ans[i]); // 子序和的最大值，不一定是 ans 数组的最后一位，所以需要保留
        }
        return res;
    }
}
```
</details>


<h3 id = "3.7">LeetCode 5：最长回文子串 </h3>

[返回高频题](#100)

1. dp 数组的推导：
   - 状态的定义：dp[i][j] 表示 s(i...j) 是回文子串，因此，状态转移方程如下：
   - dp[i][j] = s(i) == s(j) && dp[i + 1][j - 1];
   - 数组下标不能越界：
     1. i < j;
     2. i + 1 <  j - 1 ===> j - i > 2
   - 上面的下标有两个约束：第一个是 j > i，表示如果要形成字串，下标之差至少要大于 1。第二个表示如果我们想用递推公式，在第一个下标要求之外，还要求 dp[i + 1][j - 1] 也是有效的
2. 循环开始的起始值为：`for (int j = 1; j < len; j++)` 和 `for (int i = 0; i < j; i++)`，这是为了保证两件事：
   - 只取对角线右上方的部分，这是由 j > i 决定的。
   - j 从 1 开始而不是从 0 开始，是因为对角线上面的值已经赋了初始值，都是 true，它表示单个字符一定是回文的
3. 当 `s(i) == s(j)` 但是 `dp[i + 1][j - 1]` 下标越界，即 j-i <= 2 的时候，dp[i][j] = true，为什么呢？这里又包含了两种情况：
   - 如果 j - i == 2，说明 s(i..j) 这个字串有三个字符，那么在已经保证了 `s(i) == s(j)` 的前提下，只要两端的字符相等，中间是什么其实不重要，因此 dp[i][j] = true；
   - 如果 j - i < 2，因为前面有了 j > i 的限制，因此在这里 j - i 只能等于 1，也就是说这时候只有两个字符。在这种情况下，也是 dp[i][j] = true

<details>
<summary>LeetCode 5--最长回文子串代码</summary>

```java
    public String longestPalindrome(String s) {
        int len = s.length();
        if (len == 1) return s;
        boolean[][] dp = new boolean[len][len];
        char[] sChar = s.toCharArray();
        int maxLen = 1, startIndex = 0;
        for (int i = 0; i < len; i++) {
            dp[i][i] = true;
        }
        for (int j = 1; j < len; j++) {
            for (int i = 0; i < j; i++) {
                // if (j - i + 1 < 0) continue;
                if (sChar[i] != sChar[j]) {
                    dp[i][j] = false;
                } else {
                    if (j - i > 2) {
                        dp[i][j] = dp[i + 1][j - 1];
                    } else {
                        dp[i][j] = true;
                    }
                }
                if (dp[i][j] && j - i + 1 > maxLen) {
                    maxLen = j - i + 1;
                    startIndex = i;
                }
            }
        }
        return s.substring(startIndex, startIndex + maxLen);
    }
```
</details>


<h3 id = "3.8">LeetCode 42 ：接雨水 </h3>

[返回高频题](#100)

一个位置能接多少雨水，取决于它左右两边的最短的挡板，也就是“木桶理论”。
1. 方法一：DP
   - 这个方法其实是来自于暴力法。暴力法的思路是对于每一个 height[i]，都去寻找一下 [0, i-1] 和 [i+1, n-1] 两边的最大值，然后取这两个最大值中的较小值，作为木桶的挡板，计算面积
   - 于是从这里就可以做出优化：分别从左到右和从右到左进行遍历，每次都取 maxHeight[i] 和 height[i] 的较大值，并放入数组
   - 最后再进行一次遍历，取 maxLeft[i] 和 maxRight[i] 的较小值，就是木桶的挡板
2. 方法二：双指针 
   - 这个方法其实是 DP 的优化。在 DP 中，需要先进行两次遍历，得到从左往右或者是从右往左位置的最大值数组，但是在这里，可以直接用两个指针进行比较，空间复杂度优化到了 O(1)
   - 移动两个指针 left 和 right，维护两个 int 变量：maxLeft 和 maxRight

<details>
<summary>LeetCode 42--接雨水（DP方法）代码 </summary>

```java
    public int trap(int[] height) {
        int len = height.length;
        if (len == 0) return 0;
        int[] maxLeft = new int[len];
        int[] maxRight = new int[len];
        int sum = 0;
        for (int i = 0; i < len; i++) {
            maxLeft[i] = i == 0 ? height[0] : Math.max(maxLeft[i-1], height[i]);
        }
        for (int i = len - 1; i >= 0; i--) {
            maxRight[i] = i == len - 1 ? height[len - 1] : Math.max(maxRight[i + 1], height[i]);
        }
        for (int i = 0; i < len; i++) {
            sum += Math.min(maxLeft[i], maxRight[i]) - height[i];
        }
        return sum;
    }
```
</details>

<details>
<summary>LeetCode 42--接雨水（双指针方法）代码 </summary>

```java
    public int trap(int[] height) {
        int len = height.length;
        if (len < 3) return 0;
        int sum = 0;
        int left = 0, right = len - 1;
        int maxLeft = height[left];
        int maxRight = height[right];
        while (left < right) {
            if (maxLeft < maxRight) {
                sum += maxLeft - height[left];
                left += 1;
                maxLeft = Math.max(maxLeft, height[left]);
            } else {
                sum += maxRight - height[right];
                right -= 1;
                maxRight = Math.max(maxRight, height[right]);
            }
        }
        return sum;
    }
```
</details>

<h3 id = "3.9">LeetCode 72：编辑距离</h3>

[返回高频题](#100)

关键还是在于 dp 数组的定义，或者说状态的定义。

我们想要求最值，那么这个大问题可以怎么分解为小问题呢？

状态定义：dp[i][j] 表示从 word1[i] 转换到 word2[j]需要的最小步数。

初始条件：如果某一个字符串为空，那么对应的图如下：

![image](https://user-images.githubusercontent.com/38673091/112263911-00769600-8cab-11eb-9881-0c16d095c07e.png)

- 第一行，是 word1 为空变成 word2 最少步数，就是插入操作
- 第一列，是 word2 为空，需要的最少步数，就是删除操作

所以，

- 当 word1[i] == word2[j]，dp[i][j] = dp[i-1][j-1]；
- 当 word1[i] != word2[j]，dp[i][j] = min(dp[i-1][j-1], dp[i-1][j], dp[i][j-1]) + 1

其中，dp[i-1][j-1] 表示替换操作，dp[i-1][j] 表示删除操作，dp[i][j-1] 表示插入操作。


了解了定义和储，代码就很容易写出来了。

<details>
<summary>LeetCode 72--编辑距离代码 </summary>

```java
    public int minDistance(String word1, String word2) {
        int len1 = word1.length();
        int len2 = word2.length();
        char[] charArrayOne = word1.toCharArray();
        char[] charArrayTwo = word2.toCharArray();
        int[][] dp = new int[len1 + 1][len2 + 1];
        for (int i = 0; i <= len1; i++) {
            dp[i][0] = i;
        }
        for (int i = 0; i <= len2; i++) {
            dp[0][i] = i;
        }
        for (int i = 1; i <= len1; i++) {
            for (int j = 1; j <= len2; j++) {
                if (charArrayOne[i - 1] == charArrayTwo[j - 1]) {
                    dp[i][j] = dp[i - 1][j - 1];
                } else {
                    dp[i][j] = Math.min(dp[i - 1][j - 1], Math.min(dp[i - 1][j], dp[i][j - 1])) + 1;
                }
            }
        }
        return dp[len1][len2];
    }
```
</details>


<h3 id = "3.10">LeetCode 209：最佳买卖股票时机含冷冻期 </h3>

[返回高频题](#100)

冷冻期，其实就是特殊的持有状态：不持有股票，但是也不能买入。具体见注释。

<details>
<summary>LeetCode 209--代码 </summary>

```java
    public int maxProfit(int[] prices) {
        if (prices == null || prices.length == 0) return 0;
        int len = prices.length;
        // dp 数组状态定义：第 i 天的时候，操作 or 不动，是/不是冷冻期的情况下，当天结束的时候获得的钱
        // x 维：第 i 天
        // y 维：0 不持股，1 持股且能购买，2 不持股因为冷冻期所以不能购买
        int[][] gain = new int[len][3];
        gain[0][0] = 0;
        gain[0][1] = -prices[0];
        gain[0][2] = 0;
        // gain[i][0]: 第 i 天的时候手上没有股票，说明要不前一天也没有股票，要不前一天是冷冻期
        // gain[i][1]：第 i 天的时候手上有股票，说明前一天不是冷冻期，且前一天手上有股票或者没有股票今天买入
        // gain[i][2]：第 i 天的时候是冷冻期，说明当天进行了卖出操作
        // 可能的疑问：冷冻期不是卖出第二天吗？事实上这个问题可以根据第二天分为两种情况：
        //  1. 第二天不动，那么就放在 gain[i][0] 中去处理
        //  2. 第二天买入，但是因为冷冻期，所以gain[i-1][2] 不会出现在 gain[i][1] 中
        for (int i = 1; i < len; i++) {
            gain[i][0] = Math.max(gain[i-1][0], gain[i-1][2]);
            gain[i][1] = Math.max(gain[i-1][1], gain[i-1][0] - prices[i]);
            gain[i][2] = gain[i-1][1] + prices[i];
        }
        return Math.max(gain[len - 1][0], gain[len - 1][2]);

    }
```
</details>


<h3 id = "3.11">LeetCode 300：最长递增子序列 </h3>

[返回高频题](#100)

思路简单，二分法还需完善。

<details>
<summary>LeetCode 300--代码（常规方法） </summary>

```java
    public int lengthOfLIS(int[] nums) {
        int len = nums.length;
        if (len == 1) return 1;
        int[] dp = new int[len];
        Arrays.fill(dp, 1);
        int ans = dp[0];
        for (int i = 1; i < len; i++) {
            for (int j = 0; j < i; j++) {
                if (nums[i] > nums[j]) {
                    dp[i] = Math.max(dp[i], dp[j] + 1);
                }
            }
            ans = Math.max(ans, dp[i]);
        }
        return ans;
    }
```
</details>


<details>
<summary>LeetCode 300--代码（二分法） </summary>

```java

```
</details>



<h3 id = "3.12">LeetCode 322：零钱兑换 </h3>

[返回高频题](#100)

递推公式：dp[i] = min(dp[i], dp[i - coin] + 1)，为什么还需要比较 dp[i] 见代码注释

<details>
<summary>LeetCode 322--代码 </summary>

```java
    public int coinChange(int[] coins, int amount) {
        if (amount == 0) return 0;
        int[] dp = new int[amount + 1];
        Arrays.fill(dp, amount + 1);
        // dp[i] = dp[i - coin] + 1
        dp[0] = 0;
        // 第一个 for 循环：从 1 到 amount 分别需要多少硬币
        for (int i = 1; i <= amount; i++) {
            for (int c : coins) {
                if (i - c < 0) { // i - c < 0, 说明这个硬币比当前的金额要大，不符合
                    continue;
                }
                // 可以选择不放这个 coin，并不一定必须要减去当前 coin 的值
                // [1,4], amount = 4，如果选择了 1，则需要四次，因此此时不选择 1 可以得到更少的步骤
                dp[i] = Math.min(dp[i], dp[i-c] + 1);
            }
        }
        return dp[amount] == amount + 1 ? -1 : dp[amount];
    }
```
</details>


<h3 id = "3.13">LeetCode 143：最长公共子序列 </h3>

[返回高频题](#100)

这里可以回顾 [300.最长递增子序列](#3.11)，思路简单见注释


<details>
<summary>LeetCode 143--代码 </summary>

```java
    public int longestCommonSubsequence(String text1, String text2) {
        int lenOne = text1.length(), lenTwo = text2.length();
        char[] sCharOne = text1.toCharArray();
        char[] sCharTwo = text2.toCharArray();
        int[][] dp = new int[lenOne + 1][lenTwo + 1];
        // 初始化，当 text2 为 "" 的时候，公共子序列长度为 0；
        for (int i = 0; i < lenOne; i++) {
            dp[i][0] = 0;
        }
        for (int i = 0; i < lenTwo; i++) {
            dp[0][i] = 0;
        }
        for (int i = 1; i <= lenOne; i++) {
            for (int j = 1; j <= lenTwo; j++) {
                if (sCharOne[i - 1] == sCharTwo[j - 1]) {
                    dp[i][j] = dp[i-1][j-1] + 1;
                } else {
                    dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
                }
            }
        }
        return dp[lenOne][lenTwo];
    }
```
</details>


<h3 id = "3.14">LeetCode 62：不同路径</h3>

[返回高频题](#100)

简单题

<details>
<summary>LeetCode 62--代码 </summary>

```java
    public int uniquePaths(int m, int n) {
        int[][] steps = new int[m][n];
        for (int i = 0; i < m; i++) {
            steps[i][0] = 1;
        }
        for (int j = 0; j < n; j++) {
            steps[0][j] = 1;
        }
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                steps[i][j] = steps[i-1][j] + steps[i][j-1];
            }
        }
        return steps[m - 1][n - 1];
    }
```
</details>


<h3 id = "3.15">LeetCode 63：不同路径II </h3>

[返回高频题](#100)

简单题

<details>
<summary>LeetCode 63--代码 </summary>

```java
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int m = obstacleGrid.length, n = obstacleGrid[0].length;
        int[][] steps = new int[m][n];
        if (obstacleGrid[0][0] == 1) return 0;
        steps[0][0] = 1;
        for (int i = 1; i < m; i++) {
            steps[i][0] = obstacleGrid[i][0] == 1 ? 0 : steps[i-1][0];
        }
        for (int j = 1; j < n; j++) {
            steps[0][j] = obstacleGrid[0][j] == 1 ? 0 : steps[0][j-1];
        }
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                if (obstacleGrid[i][j] == 1) {
                    steps[i][j] = 0;
                } else {
                    steps[i][j] = steps[i-1][j] + steps[i][j-1];
                }
            }
        }
        return steps[m - 1][n - 1];
    }
```
</details>



<h3 id = "3.16">LeetCode 64：最小路径和 </h3>

[返回高频题](#100)

62 的简单拓展

<details>
<summary>LeetCode 64--代码 </summary>

```java
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int m = obstacleGrid.length, n = obstacleGrid[0].length;
        int[][] steps = new int[m][n];
        if (obstacleGrid[0][0] == 1) return 0;
        steps[0][0] = 1;
        for (int i = 1; i < m; i++) {
            steps[i][0] = obstacleGrid[i][0] == 1 ? 0 : steps[i-1][0];
        }
        for (int j = 1; j < n; j++) {
            steps[0][j] = obstacleGrid[0][j] == 1 ? 0 : steps[0][j-1];
        }
        for (int i = 1; i < m; i++) {
            for (int j = 1; j < n; j++) {
                if (obstacleGrid[i][j] == 1) {
                    steps[i][j] = 0;
                } else {
                    steps[i][j] = steps[i-1][j] + steps[i][j-1];
                }
            }
        }
        return steps[m - 1][n - 1];
    }
```
</details>



<h3 id = "3.17">LeetCode 120：三角形的最小路径和 </h3>

[返回高频题](#100)

和 64 类似，三角形的数据格式稍有不同

<details>
<summary>LeetCode 120--代码 </summary>

```java
    public int minimumTotal(List<List<Integer>> triangle) {
        int height = triangle.size();
        int width = triangle.get(triangle.size() - 1).size();
        int[][] sum = new int[height][width];
        sum[0][0] = triangle.get(0).get(0);
        for (int i = 1; i < height; i++) {
            sum[i][0] = sum[i - 1][0] + triangle.get(i).get(0);
        }
        for (int i = 1; i < height; i++) {
            for (int j = 1; j <= i; j++) {
                if (j == i) {
                    sum[i][j] = sum[i-1][j-1] + triangle.get(i).get(j);
                } else {
                    sum[i][j] = Math.min(sum[i-1][j-1], sum[i-1][j]) + triangle.get(i).get(j);
                }
            }
        }
        int ans = sum[height - 1][0];
        for (int i = 1; i < width; i++) {
            ans = Math.min(ans, sum[height - 1][i]);
        }
        return ans;
    }
```
</details>



<h3 id = "3.18">LeetCode  ： </h3>

[返回高频题](#100)


<details>
<summary>LeetCode -- </summary>

```java

```
</details>


<h3 id = "3.19">LeetCode  ： </h3>

[返回高频题](#100)


<details>
<summary>LeetCode -- </summary>

```java

```
</details>


<h3 id = "3.20">LeetCode  ： </h3>

[返回高频题](#100)


<details>
<summary>LeetCode -- </summary>

```java

```
</details>
