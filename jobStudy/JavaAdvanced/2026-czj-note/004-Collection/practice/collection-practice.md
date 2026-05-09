# Collection 练习题

## 1. 基础概念题

### 题 1

请说明：

- `Collection` 和 `Map` 的关系是什么
- 为什么 `Map` 不属于 `Collection`

### 题 2

请说明：

- `List`、`Set`、`Queue` 分别有什么核心特点

### 题 3

请说明：

- `ArrayList`
- `HashSet`
- `HashMap`

分别最适合解决什么问题。

## 2. 场景选择题

### 题 4

需要保存一批“有顺序、允许重复”的字符串，应该优先想到什么集合？

### 题 5

需要对用户标签去重，不关心顺序，应该优先想到什么集合？

### 题 6

需要对元素去重，同时希望遍历时顺序更稳定，应该优先想到什么集合？

### 题 7

需要保存 key-value，并且根据 key 快速拿 value，普通业务场景下优先用什么？

### 题 8

需要根据 key 保存映射，同时希望 key 自动排序，应该优先想到什么集合？

### 题 9

多线程共享一个 `Map`，应该优先想到什么集合？

## 3. 遍历题

### 题 10

请分别写出：

- 用 `Iterator` 遍历 `List`
- 用 `for-each` 遍历 `Set`

### 题 11

请写出两种遍历 `Map` 的方式：

- 遍历 `keySet()`
- 遍历 `entrySet()`

## 4. 理解题

### 题 12

为什么 `HashSet` 和 `HashMap` 会和 `equals()`、`hashCode()` 有关？

### 题 13

为什么 `String` 适合做 `HashMap` 的 key？

### 题 14

为什么 `LinkedList` 既能出现在 `List` 里，又能出现在 `Deque` 里？

## 5. 横向对比题

### 题 15

请简要对比：

- `ArrayList`
- `LinkedList`

### 题 16

请简要对比：

- `HashSet`
- `LinkedHashSet`
- `TreeSet`

### 题 17

请简要对比：

- `HashMap`
- `LinkedHashMap`
- `TreeMap`

### 题 18

请简要对比：

- `HashMap`
- `Hashtable`
- `ConcurrentHashMap`

## 6. 小练习题

### 题 19

给定一个字符串数组，要求去重后输出。

提示：

- 优先考虑 `Set`

### 题 20

给定一个字符串数组，统计每个单词出现的次数。

提示：

- 优先考虑 `Map<String, Integer>`

### 题 21

给定一批整数，要求去重并按从小到大输出。

提示：

- 想一想 `TreeSet`

## 7. 复习建议

做题顺序建议：

1. 先做题 1 到题 9
2. 再做题 10 到题 18
3. 最后做题 19 到题 21

## 8. 一句话总结

这一组练习题的目标不是刷难题，而是训练你“看到场景就想到合适集合”的反应。
