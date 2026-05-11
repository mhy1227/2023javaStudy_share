# Collection 复习检查清单

## 1. 集合总结构

你应该先能说清：

- Java 集合大体系分成 `Collection` 和 `Map`
- `Map` 不是 `Collection` 的子接口
- `List`、`Set`、`Queue` 属于 `Collection`

如果这一步还混，后面所有实现类都会乱。

## 2. 家谱是否清楚

你应该至少认识这些名字和位置：

- `Collection`
- `List`
- `Set`
- `Queue`
- `Deque`
- `Map`
- `ArrayList`
- `LinkedList`
- `HashSet`
- `LinkedHashSet`
- `TreeSet`
- `HashMap`
- `LinkedHashMap`
- `TreeMap`
- `Hashtable`
- `ConcurrentHashMap`

## 3. List 这一支

你应该能说清：

- `List` 有序
- `List` 可重复
- 最常见实现类是 `ArrayList`
- `LinkedList` 除了是 `List`，还可以承担 `Deque` 语义

## 4. Set 这一支

你应该能说清：

- `Set` 的核心特点是不可重复
- `HashSet` 偏普通去重
- `LinkedHashSet` 偏去重加顺序表现
- `TreeSet` 偏去重加排序

## 5. Map 这一支

你应该能说清：

- `Map` 存的是 `key-value`
- key 一般不能重复
- 最常见实现类是 `HashMap`
- `LinkedHashMap` 偏顺序表现
- `TreeMap` 偏 key 排序

## 6. Queue / Deque

你应该至少知道：

- `Queue` 更偏队列语义
- `Deque` 是双端队列
- `LinkedList` 和 `ArrayDeque` 都常出现在这块
- `PriorityQueue` 更偏优先级，不是普通先进先出

## 7. 遍历方式

你应该会：

- 用 `Iterator`
- 用 `for-each`
- 知道 `Iterator` 常用 `hasNext()` 和 `next()`
- 知道 `Map` 常遍历 `keySet()` 或 `entrySet()`

## 8. equals 和 hashCode

你应该能说清：

- 为什么 `HashSet` 和 `HashMap` 会关心 `equals()` 与 `hashCode()`
- 为什么重写 `equals()` 往往要一起重写 `hashCode()`
- 为什么 `String` 适合作为 `HashMap` 的 key

## 9. 单体实现类定位

你应该对这些类有“第一反应”：

### 普通列表主力

- `ArrayList`

### 列表 + 队列语义

- `LinkedList`

### 普通去重主力

- `HashSet`

### 去重 + 顺序

- `LinkedHashSet`

### 去重 + 排序

- `TreeSet`

### 普通映射主力

- `HashMap`

### 映射 + 顺序

- `LinkedHashMap`

### 映射 + 排序

- `TreeMap`

### 早期线程安全 Map

- `Hashtable`

### 并发场景线程安全 Map

- `ConcurrentHashMap`

## 10. 横向对比是否说得顺

你应该能回答这些高频问题：

1. `ArrayList` 和 `LinkedList` 区别是什么
2. 为什么很多时候优先 `ArrayList`
3. `HashSet`、`LinkedHashSet`、`TreeSet` 区别是什么
4. `HashMap`、`LinkedHashMap`、`TreeMap` 区别是什么
5. `HashMap`、`Hashtable`、`ConcurrentHashMap` 区别是什么

## 11. 选型题是否能答

你应该能判断：

- 普通列表为什么优先 `ArrayList`
- 普通去重为什么优先 `HashSet`
- 普通映射为什么优先 `HashMap`
- 有顺序要求时为什么想到 `LinkedHashSet` 或 `LinkedHashMap`
- 有排序要求时为什么想到 `TreeSet` 或 `TreeMap`
- 并发场景下为什么想到 `ConcurrentHashMap`

## 12. 易混点

重点自查：

- 把 `Map` 当成 `Collection` 子接口
- 以为 `Set` 就一定有序
- 以为 `Queue` 就只有先进先出
- 把 `HashSet` 和 `HashMap` 混成同一支
- 不清楚 `LinkedList` 为什么会在 `List` 和 `Deque` 两边都出现

## 13. 当前阶段达标标准

集合第一轮复习达标，不要求你立刻吃透源码，但至少要做到：

1. 家谱清楚
2. 四大块特性清楚
3. 常见实现类定位清楚
4. 遍历方式会用
5. 高频横向对比答得出来

## 14. 一句话总结

如果你已经能把“家谱、单体定位、横向对比、遍历、哈希规则”这几条主线说顺，集合这一章的第一轮复习就算站住了。
