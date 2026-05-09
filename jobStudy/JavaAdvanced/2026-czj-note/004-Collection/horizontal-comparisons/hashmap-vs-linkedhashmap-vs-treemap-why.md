# HashMap vs LinkedHashMap vs TreeMap

## 1. 为什么这三个常被一起问

因为它们都是：

- `Map`

而 `Map` 的高频问题往往不只是“能不能存 key-value”，而是：

- 顺序怎么样
- 要不要排序
- 应该选哪一个

## 2. 共同点

它们共同点很明确：

- 都存 `key-value`
- key 一般不能重复

## 3. 核心差异

### HashMap

- 最常见
- 普通映射主力

### LinkedHashMap

- 在 `HashMap` 基础上更强调顺序表现

### TreeMap

- 在 `Map` 基础上更偏按 key 排序

## 4. 为什么平时更常选 HashMap

因为大多数业务场景的核心诉求只是：

- 用 key 找 value

并没有额外要求：

- 保持更稳定的遍历顺序
- 自动排序

这时用：

- `HashMap`

最自然。

## 5. 为什么会选 LinkedHashMap

如果你的需求是：

- 不只是存映射
- 还想让遍历结果更有顺序感

那就更容易想到：

- `LinkedHashMap`

## 6. 为什么会选 TreeMap

如果题目明确强调：

- 按 key 有序
- 自动排序

那就会更多考虑：

- `TreeMap`

## 7. 为什么很多时候“不选 TreeMap”

因为很多普通映射场景并不需要排序。

如果没有排序要求，直接上 `TreeMap` 会让问题多出：

- 比较规则
- 排序成本

当前阶段先记住这个选型倾向就够了。

## 8. 一个稳妥的选择思路

### 普通映射

优先：

- `HashMap`

### 映射 + 更稳定的顺序表现

优先：

- `LinkedHashMap`

### 映射 + key 自动排序

优先：

- `TreeMap`

## 9. 面试里怎么答更稳

可以按这个顺序答：

1. 三者都属于 `Map`
2. 三者都存 `key-value`
3. `HashMap` 最常用
4. `LinkedHashMap` 在普通映射基础上更强调顺序表现
5. `TreeMap` 更偏按 key 排序

## 10. 一句话总结

这三者的核心差异很好记：`HashMap` 看普通映射，`LinkedHashMap` 看映射加顺序，`TreeMap` 看映射加排序。
