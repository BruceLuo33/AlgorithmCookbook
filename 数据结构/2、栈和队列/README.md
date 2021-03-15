# 数组与链表

<span id ="0"></span>


## [一、知识点](#1)
 - [栈](#1.1)
 - [队列](#1.2)
 - [单调栈](#1.3)
 - [优先队列](#1.4)

## [二、高频题](#2)

## [三、题解笔记](#2)



<h2 id = "1">一、知识点</h2>

<h3 id = "1.1">栈</h3>

[返回目录](#0)


<h3 id = "1.2">队列</h3>

[返回目录](#0)


<h3 id = "1.3">单调栈</h3>

[返回目录](#0)


<h3 id = "1.4">优先队列</h3>

[返回目录](#0)


<h2 id = "2">二、高频题</h2>

[返回目录](#0)

<span id ="100"></span>



总结：

 知识点 | 技巧 | 题目地址 | 解题代码 | 难度 |
| --- | --- | --- | --- | --- |
| 栈 | 辅助栈 | [LeetCode 20 : 有效的括号](https://leetcode-cn.com/problems/valid-parentheses/) | [Leetcode 20](#3.1) | 简单 |
| 栈 |  | [LeetCode 155 : 最小栈 ](https://leetcode-cn.com/problems/min-stack/) | [Leetcode 155](#3.2) | 简单 |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |
|  |  | [LeetCode : ]() | [Leetcode ](#3.) |  |




<h2 id = "3">三、解题笔记</h2>


<h3 id = "3.1">LeetCode 20 ：有效的括号</h3>

[返回高频题](#100)

这道题的思维比较巧妙，遇到左括号的时候，就将对应的右括号入栈。遇到右括号的时候，再弹出对比是否匹配。
- 思路：栈。题目的要求并不仅仅是左括号的数量等于右括号，而且还要中间没有其他括号：
  1. 遇到左括号，就将其对应的右括号压入栈；
  2. 如果不是左括号，就判断是否等于栈顶元素，如果不是，说明两个对应的括号中间有其他左括号，return false；
  3. 如果是空栈，也要return false；
  4. 最后的返回项，不是 true，因为可能 string 中全都是左括号，这样 for 循环也不会报错，因此需要返回 stack.isEmpty();

<details>
<summary>LeetCode 20 -- 有效的括号</summary>

```java
    public boolean isValid(String s) {
        if (s == null || s.length() == 1) return false;
        char[] sChar = s.toCharArray();
        Stack<Character> stack = new Stack<>();
        for (char c : sChar) {
            if (c == '(') stack.push(')');
            else if (c == '[') stack.push(']');
            else if (c == '{') stack.push('}');
            else if (stack.isEmpty() || c != stack.pop()) return false;
        }
        return stack.isEmpty();
    }
```
</details>


<h3 id = "3.2">LeetCode 155 ：最小栈 </h3>

[返回高频题](#100)

这道题的思想，就是经典的用时间换空间。
- 每次入栈的时候，压入两个元素：一个是当前要压入的值，另一个是到目前为止的最小值。
- 有两种实现方式：
  1. 第一种直接用 Stack 数据结构
  2. 第二种用链表来实现

<details>
<summary>LeetCode 155 -- 最小栈（Stack 实现）</summary>

```java
class MinStack {

    /** initialize your data structure here. */
    Stack<Integer> stack;
    public MinStack() {
        stack = new Stack<>();
    }
    
    public void push(int x) {
        if (stack.isEmpty()) {
            stack.push(x);
            stack.push(x);
        } else {
            int tmpMin = stack.peek();
            stack.push(x);
            stack.push(x >= tmpMin ? tmpMin : x);
        }
    }
    
    public void pop() {
        stack.pop();
        stack.pop();
    }
    
    public int top() {
        return stack.get(stack.size() - 2);
    }
    
    public int getMin() {
        return stack.peek();
    }
}
```
</details>


<details>
<summary>LeetCode 155 -- 最小栈（List 实现）</summary>

```java
class MinStack {

    /** initialize your data structure here. */
    private Node head;
    public MinStack() {
        
    }
    
    public void push(int x) {
        if (head == null) {
            head = new Node(x, x);
        } else {
            head = new Node(x, Math.min(x, head.min), head);
        }
    }
    
    public void pop() {
        head = head.next;
    }
    
    public int top() {
        return head.val;
    }
    
    public int getMin() {
        return head.min;
    }

    class Node {
        int val;
        int min;
        Node next;

        public Node(int val, int min) {
            this(val, min, null);
        }

        public Node(int val, int min, Node next) {
            this.val = val;
            this.min = min;
            this.next = next;
        }
    }
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



<h3 id = "3.44">LeetCode  ： </h3>

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
