# 树练习题

## 1. 这一组练习主要练什么

树这一组的重点不是背术语，而是先把“树会怎么遍历、节点关系怎么判断”练明白。

重点放在：

- 前中后序遍历
- 层序遍历
- 高度和深度
- 二叉树判断
- 二叉搜索树基础

## 2. 基础操作题

### 题 1 说出根节点、叶子节点

给定一棵树：

- 根是 `A`
- `B`、`C` 是 `A` 的子节点
- `D`、`E` 是 `B` 的子节点

要求：

- 说出根节点
- 说出叶子节点

### 题 2 前序遍历顺序

给定二叉树：

```text
    1
   / \
  2   3
 / \
4   5
```

要求：

- 写出前序遍历结果

### 题 3 中序遍历顺序

沿用上面这棵树，写出中序遍历结果。

### 题 4 后序遍历顺序

沿用上面这棵树，写出后序遍历结果。

### 题 5 层序遍历顺序

沿用上面这棵树，写出层序遍历结果。

### 题 6 求树的最大深度

要求：

- 说清楚最大深度是什么意思

### 题 7 判断两棵树是否相同

核心考点：

- 递归比较

## 3. 高频题

### 题 8 翻转二叉树

### 题 9 判断是不是对称二叉树

核心考点：

- 镜像比较

### 题 10 判断是不是平衡二叉树

核心考点：

- 左右子树高度差

### 题 11 二叉树层序遍历

核心考点：

- 队列

### 题 12 二叉树的最近公共祖先

核心考点：

- 递归返回信息

### 题 13 判断是不是二叉搜索树

核心考点：

- 中序有序
- 上下界约束

### 题 14 二叉搜索树中查找某个值

### 题 15 二叉搜索树的插入

## 4. 做这一组题最容易犯的错

1. 前中后序顺序记混
2. 递归出口写错
3. 层序遍历忘了用队列
4. 把“树高”与“节点个数”混在一起
5. 判断 BST 时只看当前节点，不看全局范围

## 5. 一句话总结

树题的核心，是把“节点关系”和“遍历顺序”先稳住，然后再往递归判断题上扩展。

## 6. 外部参考

下面这些链接主要用于后续继续补题、查树高频题型分类和校对训练顺序：

1. LeetCode Top Interview Questions Easy - Trees  
   https://leetcode.com/explore/interview/card/top-interview-questions-easy/94/trees/627
2. LeetCode Binary Tree Explore  
   https://leetcode.com/explore/learn/card/data-structure-tree/
3. LeetCode Binary Search Tree Explore  
   https://leetcode.com/explore/learn/card/introduction-to-data-structure-binary-search-tree/
4. 牛客在线编程 / 面试 TOP101  
   https://www.nowcoder.com/exam/oj
5. 牛客模板速刷 TOP101  
   https://www.nowcoder.com/ta/format-top101
