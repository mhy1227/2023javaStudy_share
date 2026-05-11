# HashMap vs Hashtable vs ConcurrentHashMap

## 1. 为什么这三个总被放在一起问

因为它们都是：

- `Map`

而且经常围绕这些问题被比较：

- 谁最常用
- 谁线程安全
- 谁更老
- 并发场景该选谁

## 2. 共同点

它们共同点很明确：

- 都属于 `Map`
- 都存 `key-value`

## 3. 核心差异

### HashMap

- 最常用
- 一般不强调线程安全
- 普通业务场景主力

### Hashtable

- 较早的线程安全实现
- 现在更多是“比较对象”

### ConcurrentHashMap

- 并发场景常见线程安全实现
- 更贴近现代并发开发

## 4. 为什么平时更常选 HashMap

因为大多数普通业务代码的需求是：

- 存映射
- 根据 key 查值

并没有明确并发共享要求。

这时第一反应通常就是：

- `HashMap`

## 5. 为什么很多时候不选 Hashtable

因为它在现在更多是：

- 早期线程安全 `Map` 的代表

面试里会问，但日常开发中通常不会优先想到它。

## 6. 为什么并发下更常提 ConcurrentHashMap

因为它的定位就是：

- 并发场景下更常见的线程安全 `Map`

所以如果题目明确是：

- 多线程
- 并发访问

那就会优先想到：

- `ConcurrentHashMap`

## 7. null 处理上的常见区别

当前阶段只要记住常见结论：

- `HashMap` 对 `null` 更宽松
- `Hashtable` 对 `null` 更严格
- `ConcurrentHashMap` 也通常不接受 `null`

## 8. 一个稳妥的选择思路

### 普通单线程或一般业务场景

优先：

- `HashMap`

### 老知识点、老方案对比

会提到：

- `Hashtable`

### 并发场景

优先：

- `ConcurrentHashMap`

## 9. 面试里怎么答更稳

可以按下面这条线答：

1. 三者都属于 `Map`
2. `HashMap` 最常用，普通场景下主力使用
3. `Hashtable` 是较早的线程安全实现
4. `ConcurrentHashMap` 是并发场景更常见的线程安全实现
5. `HashMap` 对 `null` 更宽松，另外两个更严格

## 10. 一句话总结

三者的主线很好记：`HashMap` 看常用，`Hashtable` 看历史线程安全，`ConcurrentHashMap` 看现代并发场景。
