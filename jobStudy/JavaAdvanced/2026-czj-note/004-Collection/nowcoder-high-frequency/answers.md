# 集合高频面试题：参考回答版

## 1. Java 集合框架的大体结构是什么

Java 集合大体分成两块：

- `Collection`
- `Map`

其中：

- `List`、`Set`、`Queue` 属于 `Collection`
- `Map` 是并列的一支，不是 `Collection` 子接口

## 2. List 的核心特点是什么

- 有序
- 可重复

所以它适合存一批按顺序组织、允许重复的数据。

## 3. ArrayList 和 LinkedList 的区别

- 两者都属于 `List`
- 两者都具备有序、可重复特点
- `ArrayList` 更像普通列表主力实现
- `LinkedList` 更特殊，还可以作为 `Deque` 使用

## 4. 为什么日常开发更常用 ArrayList

因为大多数场景只是：

- 存一批元素
- 顺序遍历
- 偶尔按索引访问

这类普通列表需求下，`ArrayList` 最常见、最自然。

## 5. Set 的核心特点是什么

- 不可重复

这也是它和 `List` 最大的区别之一。

## 6. HashSet、LinkedHashSet、TreeSet 的区别

- `HashSet`：普通去重主力，不强调顺序
- `LinkedHashSet`：去重，同时顺序表现更稳定
- `TreeSet`：去重，同时更偏排序

## 7. 为什么 HashSet 能去重

因为它的判重逻辑和：

- `equals()`
- `hashCode()`

强相关。

所以如果自定义对象比较规则没处理好，`HashSet` 的去重就可能不符合预期。

## 8. Queue 和 Deque 的区别

- `Queue` 更偏普通队列语义
- `Deque` 是双端队列，两端都能进出

## 9. LinkedList 为什么既能当 List，又能当 Deque

因为 `LinkedList` 不只是 `List` 实现类，它同时也支持队列 / 双端队列相关语义。

## 10. PriorityQueue 和普通队列有什么不同

普通队列更偏先进先出。

`PriorityQueue` 更偏：

- 按优先级出队

## 11. Map 的核心特点是什么

- 存 `key-value`
- key 一般不能重复

它更适合建立映射关系，而不是单纯存一批值。

## 12. HashMap、LinkedHashMap、TreeMap 的区别

- `HashMap`：普通映射主力
- `LinkedHashMap`：映射 + 更稳定的顺序表现
- `TreeMap`：映射 + key 排序

## 13. 为什么普通业务更常用 HashMap

因为大多数场景只关心：

- 通过 key 找 value

而不要求：

- 保序
- 排序

## 14. HashMap、Hashtable、ConcurrentHashMap 的区别

- `HashMap`：最常用，普通场景主力，一般不强调线程安全
- `Hashtable`：较早的线程安全实现
- `ConcurrentHashMap`：并发场景更常见的线程安全实现

## 15. 为什么平时很少直接用 Hashtable

因为它更多是：

- 早期线程安全 `Map` 的代表

现在通常不是日常主流首选。

## 16. 为什么并发场景更常提 ConcurrentHashMap

因为它的定位就是：

- 现代并发场景下常见的线程安全 `Map`

## 17. 三者对 null 的处理有什么不同

当前阶段先记住常见结论：

- `HashMap` 对 `null` 更宽松
- `Hashtable` 和 `ConcurrentHashMap` 更严格

## 18. 集合常见遍历方式有哪些

最常见的是：

- `Iterator`
- `for-each`

## 19. Iterator 的 hasNext() 和 next() 分别做什么

- `hasNext()`：判断后面还有没有元素
- `next()`：取出当前元素，并把指针往后移动

## 20. Map 常见遍历方式有哪些

常见方式有：

- 遍历 `keySet()`
- 遍历 `entrySet()`

## 21. 为什么 HashSet 和 HashMap 会关心 equals() 与 hashCode()

因为哈希类集合在判断元素或 key 时，通常会结合：

- `hashCode()`
- `equals()`

一起工作。

## 22. 为什么重写 equals() 往往要一起重写 hashCode()

因为 Java 有一个重要约定：

- 如果两个对象 `equals()` 为 `true`
- 那它们的 `hashCode()` 必须相同

否则哈希集合中的行为可能异常。

## 23. 为什么 String 适合做 HashMap 的 key

因为：

- `String` 不可变
- `String` 已经正确重写了 `equals()` 和 `hashCode()`

## 24. 为什么普通列表通常优先选 ArrayList

因为普通业务更多只是：

- 存一批数据
- 顺序遍历
- 按位置访问

这时 `ArrayList` 最常见。

## 25. 为什么普通去重通常优先选 HashSet

因为很多去重场景并不要求：

- 顺序
- 排序

所以直接用 `HashSet` 最自然。

## 26. 为什么普通映射通常优先选 HashMap

因为大多数映射场景不需要额外的顺序或排序要求。

## 27. 什么时候会选 LinkedHashMap

当你既需要：

- key-value 映射

又希望：

- 遍历顺序更稳定

## 28. 什么时候会选 TreeSet 或 TreeMap

当题目明确强调：

- 自动排序
- 比较规则

时，会更多想到：

- `TreeSet`
- `TreeMap`

## 29. 什么时候会选 ConcurrentHashMap

当场景明确是：

- 多线程
- 并发访问共享 Map

时，会优先想到：

- `ConcurrentHashMap`

## 30. 一句话总结

集合题的主线其实就三层：

1. 先分清家谱
2. 再记住每个实现类的定位
3. 最后能回答“为什么选它，不选别的”
