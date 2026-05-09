# HashMap 单体笔记

## 1. HashMap 是什么

`HashMap` 是最常见的 `Map` 实现类。

它的定位可以先简单记成：

- 日常开发中最常用的键值对容器

## 2. 核心特点

- 存储 `key-value`
- key 一般不能重复
- 允许 `null` key 和 `null` value
- 一般不强调线程安全

## 3. 什么时候优先想到它

适合这些场景：

- 通过 key 找 value
- 统计次数
- 建立 id 和对象的映射关系

## 4. 常见方法

- `put()`
- `get()`
- `remove()`
- `containsKey()`
- `size()`

## 5. 为什么它重要

因为 `Map` 题里如果没有特殊说明，最常见默认实现就是：

- `HashMap`

## 6. 当前阶段注意点

- 后面学 `Map` 深入时，会和 `equals()`、`hashCode()`、哈希结构强关联

## 7. 一句话总结

`HashMap` 是“普通映射场景”的默认主力集合。
