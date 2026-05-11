# 树题代码模板

## 1. 这份模板怎么用

这份文档不是为了背整套代码，而是为了让你在手撕时能快速想起：

- 递归函数返回什么
- 层序遍历为什么要按层处理
- BST 校验为什么要带上下界
- LCA 为什么能那样返回

建议使用方式：

1. 先口述思路
2. 再默写模板骨架
3. 最后替换成具体题目的业务判断

## 2. 常用节点定义

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
    }
}
```

## 3. 递归 DFS 模板

最通用的树题模板通常长这样：

```java
public void dfs(TreeNode root) {
    if (root == null) {
        return;
    }

    // 处理当前节点

    dfs(root.left);
    dfs(root.right);
}
```

核心记忆点：

1. 先处理空节点
2. 再决定当前节点处理位置
3. 最后进入左右子树

## 4. 前序遍历模板

```java
public List<Integer> preorderTraversal(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    preorder(root, result);
    return result;
}

private void preorder(TreeNode root, List<Integer> result) {
    if (root == null) {
        return;
    }
    result.add(root.val);
    preorder(root.left, result);
    preorder(root.right, result);
}
```

口诀：

- 根左右

## 5. 中序遍历模板

```java
public List<Integer> inorderTraversal(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    inorder(root, result);
    return result;
}

private void inorder(TreeNode root, List<Integer> result) {
    if (root == null) {
        return;
    }
    inorder(root.left, result);
    result.add(root.val);
    inorder(root.right, result);
}
```

口诀：

- 左根右

## 6. 后序遍历模板

```java
public List<Integer> postorderTraversal(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    postorder(root, result);
    return result;
}

private void postorder(TreeNode root, List<Integer> result) {
    if (root == null) {
        return;
    }
    postorder(root.left, result);
    postorder(root.right, result);
    result.add(root.val);
}
```

口诀：

- 左右根

## 7. 层序遍历模板

```java
public List<List<Integer>> levelOrder(TreeNode root) {
    List<List<Integer>> result = new ArrayList<>();
    if (root == null) {
        return result;
    }

    Queue<TreeNode> queue = new LinkedList<>();
    queue.offer(root);

    while (!queue.isEmpty()) {
        int size = queue.size();
        List<Integer> level = new ArrayList<>();

        for (int i = 0; i < size; i++) {
            TreeNode node = queue.poll();
            level.add(node.val);

            if (node.left != null) {
                queue.offer(node.left);
            }
            if (node.right != null) {
                queue.offer(node.right);
            }
        }

        result.add(level);
    }

    return result;
}
```

关键点：

1. 队列里装的是“当前待处理节点”
2. `size = queue.size()` 是当前层节点数
3. 按层处理时，`for` 循环不能直接写成 `while (!queue.isEmpty())`

## 8. 最大深度模板

```java
public int maxDepth(TreeNode root) {
    if (root == null) {
        return 0;
    }
    return Math.max(maxDepth(root.left), maxDepth(root.right)) + 1;
}
```

这个模板常作为：

- 高度题
- 平衡树题
- 直径题

的基础骨架。

## 9. 判断两棵树是否相同模板

```java
public boolean isSameTree(TreeNode p, TreeNode q) {
    if (p == null && q == null) {
        return true;
    }
    if (p == null || q == null) {
        return false;
    }
    if (p.val != q.val) {
        return false;
    }
    return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
}
```

这种题最稳的写法是：

1. 先处理双空
2. 再处理单空
3. 再处理值不同
4. 最后递归比较左右子树

## 10. 对称二叉树模板

```java
public boolean isSymmetric(TreeNode root) {
    if (root == null) {
        return true;
    }
    return isMirror(root.left, root.right);
}

private boolean isMirror(TreeNode left, TreeNode right) {
    if (left == null && right == null) {
        return true;
    }
    if (left == null || right == null) {
        return false;
    }
    if (left.val != right.val) {
        return false;
    }
    return isMirror(left.left, right.right)
            && isMirror(left.right, right.left);
}
```

关键点：

- 比的不是“同侧”，而是“镜像位置”

## 11. 判断 BST 模板

### 写法一：上下界约束

```java
public boolean isValidBST(TreeNode root) {
    return valid(root, Long.MIN_VALUE, Long.MAX_VALUE);
}

private boolean valid(TreeNode root, long lower, long upper) {
    if (root == null) {
        return true;
    }
    if (root.val <= lower || root.val >= upper) {
        return false;
    }
    return valid(root.left, lower, root.val)
            && valid(root.right, root.val, upper);
}
```

这一版最适合面试解释，因为它直接体现：

- BST 是全局范围约束

### 写法二：中序遍历有序

```java
private long prev = Long.MIN_VALUE;

public boolean isValidBST2(TreeNode root) {
    if (root == null) {
        return true;
    }
    if (!isValidBST2(root.left)) {
        return false;
    }
    if (root.val <= prev) {
        return false;
    }
    prev = root.val;
    return isValidBST2(root.right);
}
```

## 12. 最近公共祖先模板

```java
public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    if (root == null || root == p || root == q) {
        return root;
    }

    TreeNode left = lowestCommonAncestor(root.left, p, q);
    TreeNode right = lowestCommonAncestor(root.right, p, q);

    if (left != null && right != null) {
        return root;
    }
    return left != null ? left : right;
}
```

这题要会解释：

1. 左边找到了谁
2. 右边找到了谁
3. 为什么左右都不为空时当前节点就是答案

## 13. 平衡二叉树模板

```java
public boolean isBalanced(TreeNode root) {
    return height(root) != -1;
}

private int height(TreeNode root) {
    if (root == null) {
        return 0;
    }

    int left = height(root.left);
    if (left == -1) {
        return -1;
    }

    int right = height(root.right);
    if (right == -1) {
        return -1;
    }

    if (Math.abs(left - right) > 1) {
        return -1;
    }

    return Math.max(left, right) + 1;
}
```

这一题的精华是：

- 用 `-1` 同时表示“不平衡状态”

## 14. 重建二叉树模板

题型：

- 前序 + 中序重建二叉树

```java
public TreeNode buildTree(int[] preorder, int[] inorder) {
    Map<Integer, Integer> indexMap = new HashMap<>();
    for (int i = 0; i < inorder.length; i++) {
        indexMap.put(inorder[i], i);
    }
    return build(preorder, 0, preorder.length - 1,
            inorder, 0, inorder.length - 1, indexMap);
}

private TreeNode build(int[] preorder, int preLeft, int preRight,
        int[] inorder, int inLeft, int inRight,
        Map<Integer, Integer> indexMap) {
    if (preLeft > preRight) {
        return null;
    }

    int rootVal = preorder[preLeft];
    TreeNode root = new TreeNode(rootVal);
    int index = indexMap.get(rootVal);
    int leftSize = index - inLeft;

    root.left = build(preorder, preLeft + 1, preLeft + leftSize,
            inorder, inLeft, index - 1, indexMap);
    root.right = build(preorder, preLeft + leftSize + 1, preRight,
            inorder, index + 1, inRight, indexMap);

    return root;
}
```

关键点：

1. 前序第一个元素是根
2. 中序里根左边是左子树，右边是右子树
3. 真正容易错的是索引区间

## 15. 手撕时的快速检查清单

写完树题后，立刻检查：

1. `root == null` 出口有没有漏
2. 左右子树递归顺序对不对
3. 返回值含义能不能解释清楚
4. 层序遍历有没有按层处理
5. BST 判断是不是用了全局约束
6. 时间复杂度和空间复杂度能不能顺口说出来

## 16. 一句话总结

树题模板真正要背的不是“整段代码”，而是“递归出口、返回值定义、左右子树关系、按层处理队列、BST 的全局约束”。

## 17. 外部参考

1. LeetCode Binary Tree Explore  
   https://leetcode.com/explore/learn/card/data-structure-tree/
2. LeetCode Binary Search Tree Explore  
   https://leetcode.com/explore/learn/card/introduction-to-data-structure-binary-search-tree/
3. 牛客在线编程 / 面试 TOP101  
   https://www.nowcoder.com/exam/oj
4. 牛客模板速刷 TOP101  
   https://www.nowcoder.com/ta/format-top101
