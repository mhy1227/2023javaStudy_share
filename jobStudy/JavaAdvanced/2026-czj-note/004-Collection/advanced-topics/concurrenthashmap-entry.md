# ConcurrentHashMap 入门

## 1. 为什么要单独讲 ConcurrentHashMap

因为在集合面试里，只要提到：

- 线程安全 `Map`
- 并发场景

几乎都会出现：

- `ConcurrentHashMap`

它的出场频率明显高于：

- `Hashtable`

## 2. 它解决什么问题

最直接的理解是：

- 普通 `HashMap` 不适合直接当并发共享 `Map`
- 并发场景下需要更合适的线程安全实现

这时就会想到：

- `ConcurrentHashMap`

## 3. 它和 Hashtable 的关系

这两个类经常一起被问。

当前阶段先记：

- `Hashtable` 是较早的线程安全 `Map`
- `ConcurrentHashMap` 是并发场景下更常见、更现代的线程安全 `Map`

所以在现在的面试和开发语境里，更多会提：

- `ConcurrentHashMap`

## 4. 它和 HashMap 的关系

你可以先这样理解：

- `HashMap` 更适合普通场景
- `ConcurrentHashMap` 更适合并发场景

这也是选型题里最常见的一条线。

## 5. 它为什么不能简单理解成“加锁版 HashMap”

因为面试官问这个类时，通常不是只想听：

- “它线程安全”

而是想看你是否知道：

- 它的设计目标是让并发访问更合理
- 不只是简单粗暴地把整个容器都锁死

当前阶段不必展开具体实现细节，但要先知道：

- `ConcurrentHashMap` 的价值不只是“能用锁”
- 而是“更适合并发访问”

## 6. 为什么面试常追问它

因为它能顺手考你：

- 线程安全和非线程安全容器的区别
- 为什么 `HashMap` 不适合并发写
- 为什么现在更少直接提 `Hashtable`

## 7. null 的问题

当前阶段先记住常见结论：

- `ConcurrentHashMap` 一般不接受 `null`

这也是它和 `HashMap` 的一个明显差异点。

## 8. 面试里怎么答更稳

如果问：

- `ConcurrentHashMap` 和 `HashMap`、`Hashtable` 有什么区别

可以按这条线答：

1. `HashMap` 最常用，但一般不强调线程安全
2. `Hashtable` 是较早的线程安全实现
3. `ConcurrentHashMap` 是并发场景下更常见的线程安全实现
4. `ConcurrentHashMap` 更贴近现代并发开发
5. 它对 `null` 更严格

## 9. 当前阶段最该记住的结论

1. `ConcurrentHashMap` 是并发场景高频 `Map`
2. 它比 `Hashtable` 更值得优先掌握
3. 它和普通 `HashMap` 的核心差异在于线程安全场景
4. 它是集合章节通向并发章节的重要桥梁

## 10. 一句话总结

`ConcurrentHashMap` 不只是“线程安全 Map”，更是集合章节里最值得提前认识的并发容器。
