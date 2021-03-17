# 回溯

<span id ="0"></span>


## [一、知识点](#1)
 - [回溯](#1.1)




## [二、高频题](#2)

## [三、题解笔记](#2)



<h2 id = "1">一、知识点</h2>

<h3 id = "1.1">回溯</h3>

[返回目录](#0)

backtrack 的公式：
```java
result = []
def backtrack(路径, 选择列表):
    if 满足结束条件:
        result.add(路径)
        return
    
    for 选择 in 选择列表:
        做选择
        backtrack(路径, 选择列表)
        撤销选择
```


<h2 id = "2">二、高频题</h2>

[返回目录](#0)

<span id ="100"></span>

[LeetCode 关于回溯经典题目代码](https://leetcode.com/problems/combination-sum/discuss/16502/A-general-approach-to-backtracking-questions-in-Java-(Subsets-Permutations-Combination-Sum-Palindrome-Partitioning))

总结：

 知识点 | 技巧 | 题目地址 | 解题代码 | 难度 |
| --- | --- | --- | --- | --- |
| 回溯 | 选择与撤销选择 | [LeetCode 46:全排列 ](https://leetcode-cn.com/problems/permutations/) | [Leetcode 46](#3.1) | 中等 |
| 回溯 | 回溯 | [LeetCode 47:全排列II ](https://leetcode-cn.com/problems/permutations-ii/) | [Leetcode 47](#3.2) | 中等 |
| 回溯 | 去重（答案顺序）与剪枝 | [LeetCode 39:组合总和](https://leetcode-cn.com/problems/combination-sum/) | [Leetcode 39](#3.3) | 中等 |
| 回溯 | 去重（不同位置相同值） | [LeetCode 40:组合总和II](https://leetcode-cn.com/problems/combination-sum-ii/) | [Leetcode 40](#3.4) | 中等 |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |




<h2 id = "3">三、解题笔记</h2>


<h3 id = "3.1">LeetCode 46：全排列 </h3>

[返回高频题](#100)

这题是回溯法的经典题目，参考上面的模板，可以很快地写出如下代码

方法二来自于剑指offer 12&13，这次没有使用全局变量，而是用了一个 visited 数组来判断是否访问过节点。

<details>
<summary>LeetCode 46 -- 全排列（方法一）</summary>

```java
    List<List<Integer>> ans = new ArrayList<>();
    public List<List<Integer>> permute(int[] nums) {
        if (nums == null || nums.length == 0) return ans;
        List<Integer> results = new ArrayList<>();
        backtrack(nums, results);
        return ans;
    }

    private void backtrack(int[] nums, List<Integer> results) {
        if (results.size() == nums.length) {
            ans.add(new ArrayList<>(results));
        }
        for (int i = 0; i < nums.length; i++) {
            if (results.contains(nums[i])) {
                continue;
            }
            results.add(nums[i]);
            backtrack(nums, results);
            results.remove(results.size() - 1);
        }
    }
```
</details>


<details>
<summary>LeetCode 46 -- 全排列（方法二）</summary>

```java
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> res = new ArrayList<>();
        int[] visited = new int[nums.length];
        backtrack(res, nums, new ArrayList<Integer>(), visited);
        return res;
    }

    private void backtrack(List<List<Integer>> res, int[] nums, ArrayList<Integer> tmp, int[] visited) {
        if (tmp.size() == nums.length) {
            res.add(new ArrayList<>(tmp));
            return;
        }
        for (int i = 0; i < nums.length; i++) {
            // 剔除重复项
            if (visited[i] == 1) continue;
            // 做出选择
            visited[i] = 1;
            tmp.add(nums[i]);
            // 回溯，去找下一个选项
            backtrack(res, nums, tmp, visited);
            // 回溯之后，如果又走到了这里，说明之前的选项要不就已经被添加，要不就没有合适的选项
            // 因此，还需要撤销之前的选择
            visited[i] = 0;
            tmp.remove(tmp.size() - 1);
        }
    }
```
</details>


<h3 id = "3.2">LeetCode 47：全排列II </h3>

[返回高频题](#100)

- 思路：这道题与上一题46很像，不同之处在于这里需要剪枝。在剪枝之前，需要先对数据进行排序。尽管排序也会花一定的时间，但是与回溯算法本身的复杂度相比还是低很多
- 同时要注意，这里给定的序列中就有重复元素，所以最终的排列结果，会出现[1,1,2] 和 [1,1,2]，需要去除其中的一个。
  1. 在主函数中，将 nums[] 排序
  2. 和 46 题相比，多用一个 used[] 数组来记录某一个元素是否已经在前面出现过。具体方法为：在 `track.add(nums[i])` 之后，将 `used[i] = true`；同时，在回退状态之后，将 `used[i] = false`
  3. 核心的步骤，在于对重复元素的判断。在上一题中，我们使用的是 `if (track.contains(nums[i])) continue`，但是在这里行不通，原因是在给定的数组中就已经有了重复元素。这条语句的适用条件为 [1,2,3] 这样的数组，但是题目给出的是 [1,1,2] 等类似的数组。如果用这条语句来判断是否跳过，则会出现错误。
  4. 基于第三点，和之前设置的 used 数组，我们可以用这条语句来判定：`if (used[i] == 1 || i > 0 && nums[i] == nums[i-1] && used[i-1] == 0) continue;`，它表示了两种情况：第一，used[i] 已经用过了，那么肯定要跳过；第二，used[i-1] 都没用过，但是nums[i] == nums[i-1]，这相当于在判断used[i] 之前，就已经判断了元素是否重复。因为我们事先排序了，所以这个判断才能实现。
- 注意：判断重复的时候，要判断 `used[i-1] == 0`，而不能是 `used[i] == 0`，这是因为 used[i] 的值可能还没有设置

<details>
<summary>LeetCode  47--全排列II </summary>

```java
    public List<List<Integer>> permuteUnique(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        int[] used = new int[nums.length];
        Arrays.sort(nums);
        backtrack(nums, used, ans, new ArrayList<Integer>());
        return ans;
    }

    private void backtrack(int[] nums, int[] used,  List<List<Integer>> ans, ArrayList<Integer> tmp) {
        if (tmp.size() == nums.length) {
            ans.add(new ArrayList<>(tmp));
            return;
        }
        for (int i = 0; i < nums.length; i++) {
            boolean visited = used[i] == 1;
            boolean repeated = (i > 0 && nums[i] == nums[i - 1] && used[i-1] == 0);
            if (visited || repeated) {
                continue;
            }
            // 做出选择 
            used[i] = 1;
            tmp.add(nums[i]);
            // 继续去找下一个叶子节点的选择
            backtrack(nums, used, ans, tmp);
            // 撤销选择
            used[i] = 0;
            tmp.remove(tmp.size() - 1);
        }
    }
```
</details>


<h3 id = "3.3">LeetCode 39：组合总和 </h3>

[返回高频题](#100)

这道题仍然是回溯法模板，不同的地方在于这里对于相同元素不同位置的答案，需要进行去重。

进行去重的方式，是在 for 循环里面，每次不是从 0 开始，而是从一个 start 参数开始，[leetcode](https://leetcode.com/problems/combination-sum/discuss/16502/A-general-approach-to-backtracking-questions-in-Java-(Subsets-Permutations-Combination-Sum-Palindrome-Partitioning)/185237) 上对此有解释

> (2)passing argument 'start' will make sure each combination of num run once.
> I think combined with sort() method to explain it will be easy to understand.
> e.g. Like [3,2,4], after sorted, turn to [2,3,4]. (ignore target, just look for what's going on)
> First reached list will be 2,2,2 return --> 2,2,3 return--> 2,2,4 return--> 2,3,3 ...
> After 2,2,4 return, it should go to 2,3,3 (due to arg start) instead of 2,3,2. Because 2,2,3 we already reached.

<details>
<summary>LeetCode 39--组合总和代码 </summary>

```java
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> ans = new ArrayList<>();
        int index = 0;
        Arrays.sort(candidates);
        backtrack(candidates, target, ans, index, new ArrayList<Integer>());
        return ans;
    }

    private void backtrack(int[] candidates, int target, List<List<Integer>> ans, int index, ArrayList<Integer> tmp) {
        if (target == 0) {
            ans.add(new ArrayList<Integer>(tmp));
            return;
        }
        for (int i = index; i < candidates.length; i++) {
            if (target - candidates[i] < 0) {
                return;
            }
            target -= candidates[i];
            tmp.add(candidates[i]);
            backtrack(candidates, target, ans, i, tmp);
            target += candidates[i];
            tmp.remove(tmp.size() - 1);
        }

    }

```
</details>



<h3 id = "3.4">LeetCode 40：组合总和II </h3>

[返回高频题](#100)

这道题和上一题很相似，一开始想着用 visited 数组和 i = start 的方式来避免重复，但是会出现下面的情况：

> 输入
> [10,1,2,7,6,1,5]
> 8
> 输出
> [[1,1,6],[1,2,5],[1,7],[1,2,5],[1,7],[2,6]]
> 预期结果
> [[1,1,6],[1,2,5],[1,7],[2,6]]

对应的，在 leetcode 题解区对此做出了解释

[例子](https://leetcode.com/problems/combination-sum-ii/discuss/16861/Java-solution-using-dfs-easy-understand/16652)
> to avoid duplicate combinations. Consider following example:
> Search in [1, 1, 1, 2, 2] for target 4, without the expression, you will get three identical combinations:
> [1, 1, 2, 2] from index [0, 1, 3, 4] of the candidates;
> [1, 1, 2, 2] from index [0, 2, 3, 4] of the candidates;
> [1, 1, 2, 2] from index [1, 2, 3, 4] of the candidates.

在这个例子中，同一个元素没有使用两次，但是因为重复项的存在，使得最终的答案出现了重复。

因此，可以使用下面的语句进行去重：

```java
  if (i > start && candidates[i] == candidates[i-1]) {
      continue;
  }
```

为什么能这么使用呢？因为 i > start 说明 i = start 这一层的答案，例如 [1,1,2,2] 已经找出来了，这时候已经走到了后面的参数，
例如 i = 1（这里的 i 是指的 index），这时候如果 `candidates[i] == candidates[i-1]`，就会出现上面例子中的重复项。因此需要排除。

参考 leetcode 题解区的[回答](https://leetcode.com/problems/combination-sum-ii/discuss/16861/Java-solution-using-dfs-easy-understand/196147)

> Our path array contains some element which picked from cand[0...cur-1].
> We start from i=cur, now it is i> cur, which means we already tried the elements between cur to i-1 (i-1>=cur).
> Now we are in candidate[i] and candidate[i]==candidate[i-1]. Now need to try another time.

- 另外，递归的时候传入的 start 参数是 i+1 而不是 i，i + 1 代表从下一个元素开始继续找，意思就是不允许重复元素出现
- 递归如果传入 i，代表允许重复项，这是上一题 Leetcode 39 的要求
- `backtrack(candidates, target - candidates[i], ans, tmp, i + 1);`

<details>
<summary>LeetCode 40--组合总和II </summary>

```java
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
        List<List<Integer>> ans = new ArrayList<>();
        if (candidates == null || candidates.length == 0) return ans;
        Arrays.sort(candidates);
        backtrack(candidates, target, ans, new ArrayList<Integer>(), 0);
        return ans;
    }

    private void backtrack(int[] candidates, int target, List<List<Integer>> ans, ArrayList<Integer> tmp, int start) {
        if (target == 0) {
            ans.add(new ArrayList<>(tmp));
            return;
        }
        for (int i = start; i < candidates.length; i++) {
            if (target - candidates[i] < 0) return;
            if (i > start && candidates[i] == candidates[i-1]) {
                continue;
            }
            tmp.add(candidates[i]);
            backtrack(candidates, target - candidates[i], ans, tmp, i + 1);
            tmp.remove(tmp.size() - 1);
        }
    }
```
</details>



<h3 id = "3.5">LeetCode  ： </h3>

[返回高频题](#100)


<details>
<summary>LeetCode -- </summary>

```java

```
</details>
