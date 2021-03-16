# 树

<span id ="0"></span>


## [一、知识点](#1)
 - [二叉树](#1.1)
 - [二叉搜索树](#1.2)
 - [AVL 树](#1.3)
 - [B树](#1.4)
 - [B+树](#1.5)
 - [红黑树](#1.6)



## [二、高频题](#2)

## [三、题解笔记](#2)



<h2 id = "1">一、知识点</h2>

<h3 id = "1.1">二叉树</h3>

[返回目录](#0)


<h3 id = "1.2">二叉搜索树</h3>

[返回目录](#0)


<h3 id = "1.3">AVL树</h3>

[返回目录](#0)


<h3 id = "1.4">B 树</h3>

[返回目录](#0)


<h3 id = "1.5">B+树</h3>

[返回目录](#0)


<h3 id = "1.6">红黑树</h3>

[返回目录](#0)



<h2 id = "2">二、高频题</h2>

[返回目录](#0)

<span id ="100"></span>



总结：

 知识点 | 技巧 | 题目地址 | 解题代码 | 难度 |
| --- | --- | --- | --- | --- |
| 二叉树中序遍历 | 递归 | [LeetCode 94:二叉树的中序遍历](https://leetcode-cn.com/problems/binary-tree-inorder-traversal/) | [Leetcode 94](#3.1) | 中等 |
| 二叉树前序遍历 | 递归 | [LeetCode 144:二叉树的前序遍历](https://leetcode-cn.com/problems/binary-tree-preorder-traversal/) | [Leetcode 144](#3.2) | 中等 |
| 二叉树后序遍历 | 递归 | [LeetCode 145:二叉树的后序遍历](https://leetcode-cn.com/problems/binary-tree-postorder-traversal/) | [Leetcode 145](#3.3) | 中等 |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |




<h2 id = "3">三、解题笔记</h2>


<h3 id = "3.1">LeetCode 94 ：二叉树的中序遍历</h3>

[返回高频题](#100)

- 思路一：递归中序遍历，二叉树经典算法。
  1. 递归左树
  2. append root value
  3. 递归右树
- 思路二：用栈来模拟递归：回想中序遍历的顺序：先是左子树，然后是根节点，最后是右子树。因此，可以用栈来模拟这个过程：
  1. 将 root 和 root.left 循环地放入栈中；
  2. 当 node 为 null 的时候，说明左子树的路径走到了终点，这时候将其从栈中弹出，并且根据之前讨论的顺序，将此时的最左侧节点 val 值加入到 ans 列表中
  3. 继续往右边去寻找是否有子节点，如果有，查找这个右节点是否有左子树
  4. 如果没有右节点，这时候重新进入循环，根据 !stack.isEmpty() 的判断，继续拿出stack 中的节点，这也就是需要对 stack 做出非空判断的原因
- 复杂度分析：O（N），空间复杂度：O（logN）~ O（N），取决于 root 的形态


<details>
<summary>LeetCode 94 -- 二叉树中序遍历代码（递归）</summary>

```java
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> ans = new ArrayList<>();
        inOrderHelper(root, ans);
        return ans;
    }
    public void inOrderHelper(TreeNode root, List<Integer> ans) {
        if (root == null) return;
        inOrderHelper(root.left, ans);
        ans.add(root.val);
        inOrderHelper(root.right, ans);
    }
```
</details>

<details>
<summary>LeetCode 94 -- 二叉树中序遍历代码（循环--用栈模拟递归）</summary>

```java
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> ans = new ArrayList<>();
        Stack<TreeNode> stack = new Stack<>();
        TreeNode cur = root;
        while (cur != null || !stack.isEmpty()) {
            while (cur != null) {
                stack.push(cur);
                cur = cur.left;
            } 
            cur = stack.pop();
            ans.add(cur.val);
            cur = cur.right;
        }
        return ans;
    }
```
</details>


<h3 id = "3.2">LeetCode 144 ：二叉树的前序遍历 </h3>

[返回高频题](#100)

- 思路一：前序遍历，经典算法。
  1. append root value
  2. 递归左树
  3. 递归右树
- 复杂度分析：O（N），空间复杂度：O（logN）~ O（N），取决于 root 的形态
- 思路二：与 94 题一样，用 stack 来辅助进行递归，步骤如下：
  1. 把根结点加入stack中。
  2. 开始遍历 while(!stack.isEmpty()) 执行下面的3、4步
  3. 从stack中取出栈顶的TreeNode node结点，把它加入到结果集res中
  4. 依次加入node的右孩子、左孩子（如果存在的话）。前序遍历的顺序是中--左--右。因为 stack 的特征是 FILO，所以需要先压入 right 节点，然后再压入 left 节点。
  5. 得到结果集res，返回

<details>
<summary>LeetCode 144 --二叉树的前序遍历代码（递归） </summary>

```java
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> ans = new ArrayList<>();
        helper(root, ans);
        return ans;
    }
    private void helper(TreeNode root, List<Integer> ans) {
        if (root == null) return;

        ans.add(root.val);
        helper(root.left, ans);
        helper(root.right, ans);
    }
```
</details>

<details>
<summary>LeetCode 144 --二叉树的前序遍历代码（迭代：用栈模拟递归） </summary>

```java
    public List<Integer> preorderTraversal(TreeNode root) {
        Stack<TreeNode> stack = new Stack<>();
        List<Integer> ans = new ArrayList<>();
        if (root == null) return ans;
        stack.push(root);
        while (!stack.isEmpty()) {
            TreeNode cur = stack.pop();
            ans.add(cur.val);
            if (cur.right != null) {
                stack.push(cur.right);
            }
            if (cur.left != null) {
                stack.push(cur.left);
            }
        }
        return ans;
    }
```
</details>


<h3 id = "3.3">LeetCode 145 ：二叉树的后序遍历 </h3>

[返回高频题](#100)

和前面的两道题一样，这里也有递归和迭代两种写法。

<details>
<summary>LeetCode 145--二叉树的后序遍历代码 </summary>

```java
public List<Integer> postorderTraversal(TreeNode root) {
    List<Integer> res = new ArrayList<Integer>();
    if(root == null)
        return res;
    Stack<TreeNode> stack = new Stack<TreeNode>();
    stack.push(root);
    while(!stack.isEmpty()){
        TreeNode node = stack.pop();
        if(node.left != null) stack.push(node.left);//和传统先序遍历不一样，先将左结点入栈
        if(node.right != null) stack.push(node.right);//后将右结点入栈
        res.add(0,node.val);                        //逆序添加结点值
    }     
    return res;
}
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
