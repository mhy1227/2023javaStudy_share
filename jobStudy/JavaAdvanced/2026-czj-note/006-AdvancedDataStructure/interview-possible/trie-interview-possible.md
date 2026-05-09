# Trie 面试可能问及

## 1. Trie 为什么也值得知道

Trie 的整体频率通常不如图和并查集高，但它有一个特点：

- 一旦命中题型，辨识度很高

所以它很适合作为：

- 第三步补充专题

## 2. Trie 这块更偏什么

Trie 在面试里通常既可能：

- 直接让你实现

也可能：

- 问你为什么前缀匹配适合 Trie

所以它属于：

- 手撕和口述都可能出现

## 3. Trie 的常见手撕方向

最常见的是：

1. 实现 Trie
2. 插入单词
3. 查询完整单词
4. 查询某个前缀是否存在
5. 带通配符的搜索题

更进一层会碰到：

1. 搜索建议系统
2. 单词搜索 II
3. 前后缀搜索

## 4. Trie 的口述追问方向

常见追问有：

1. Trie 适合解决什么问题
2. 为什么前缀查询适合 Trie
3. 为什么不用 HashMap 直接存全部字符串
4. Trie 的空间代价为什么会偏大
5. Trie 和普通字符串查找各自适合什么场景

## 5. 最值得优先练的题型

如果只刷一轮，建议优先：

1. Implement Trie
2. Add and Search Word
3. 搜索建议类题型先有印象

这样足够建立：

- 节点结构
- 插入
- 查询
- 前缀匹配

## 6. Trie 最容易暴露的问题

1. 节点结构设计不清
2. 结束标记忘记处理
3. 只会实现，不会解释为什么适合前缀匹配
4. 空间开销这件事没有意识

## 7. 当前阶段最该记住的结论

1. Trie 是前缀匹配很典型的树形结构
2. 整体频率低于图和并查集
3. 但命中题型后很典型，值得补
4. 实现 Trie 和前缀查询是主线

## 8. 一句话总结

Trie 不是当前最优先的下一层主题，但它在前缀匹配和设计题里非常典型，所以适合作为第三步补充。

## 9. 外部参考

1. LeetCode Trie 教程与练习题  
   https://leetcode.com/discuss/study-guide/931977/beginner-friendly-guide-to-trie-tutorial-practice-problems
2. LeetCode Trie 相关题单讨论  
   https://leetcode.com/discuss/general-discussion/853098/trie-or-search-related-question-and-good-explanation
3. 牛客：面试手撕算法汇总  
   https://www.nowcoder.com/discuss/40811
