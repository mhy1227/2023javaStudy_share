# 集合高频面试题：题目版

## 1. 集合整体结构

1. Java 集合框架的大体结构是什么？
2. `Collection` 和 `Map` 是什么关系？
3. `List`、`Set`、`Queue` 分别属于哪一支？
4. `Map` 为什么不属于 `Collection`？

## 2. List

1. `List` 的核心特点是什么？
2. `ArrayList` 和 `LinkedList` 有什么区别？
3. 为什么日常开发中更常用 `ArrayList`？
4. 什么场景下会更想到 `LinkedList`？
5. `Vector` 和 `ArrayList` 有什么区别？

## 3. Set

1. `Set` 的核心特点是什么？
2. `HashSet`、`LinkedHashSet`、`TreeSet` 有什么区别？
3. 为什么 `HashSet` 能去重？
4. `TreeSet` 为什么和排序有关？
5. 什么场景下会选 `LinkedHashSet`？

## 4. Queue / Deque

1. `Queue` 和 `Deque` 有什么区别？
2. `LinkedList` 为什么既能当 `List`，又能当 `Deque`？
3. `PriorityQueue` 和普通队列有什么不同？

## 5. Map

1. `Map` 的核心特点是什么？
2. `HashMap`、`LinkedHashMap`、`TreeMap` 有什么区别？
3. 为什么普通业务场景更常用 `HashMap`？
4. 什么场景下会选 `TreeMap`？
5. `HashMap` 的 key 为什么通常不能重复？

## 6. 线程安全与并发 Map

1. `HashMap`、`Hashtable`、`ConcurrentHashMap` 有什么区别？
2. 为什么平时很少直接用 `Hashtable`？
3. 并发场景下为什么更常提 `ConcurrentHashMap`？
4. 这三者对 `null` 的处理有什么不同？

## 7. 遍历

1. 集合常见的遍历方式有哪些？
2. `Iterator` 和 `for-each` 有什么关系？
3. `Iterator` 的 `hasNext()` 和 `next()` 分别做什么？
4. `Map` 常见遍历方式有哪些？

## 8. equals 与 hashCode

1. 为什么 `HashSet` 和 `HashMap` 会关心 `equals()` 和 `hashCode()`？
2. 为什么重写 `equals()` 往往要一起重写 `hashCode()`？
3. 为什么 `String` 适合做 `HashMap` 的 key？
4. 自定义对象放进 `HashSet` 时为什么可能去重失败？

## 9. 选型题

1. 为什么普通列表通常优先选 `ArrayList`？
2. 为什么普通去重通常优先选 `HashSet`？
3. 为什么普通映射通常优先选 `HashMap`？
4. 什么时候会选 `LinkedHashMap`？
5. 什么时候会选 `TreeSet` 或 `TreeMap`？
6. 什么时候会选 `ConcurrentHashMap`？
