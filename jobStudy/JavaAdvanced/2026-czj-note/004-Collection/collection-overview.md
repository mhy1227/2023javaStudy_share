# 集合整体结构总览

## 1. 集合这一章怎么理解

Java 里的集合，不是单个类，而是一整套容器体系。

平时大家口语里会把：

- `List`
- `Set`
- `Map`

都统称为“集合”。

但从结构上看，它们并不是完全同一条继承链。

## 2. 大的结构怎么分

可以先这样记：

- 集合大体系
  - `Collection`
  - `Map`

其中：

- `Collection` 主要存单列数据
- `Map` 主要存键值对数据

## 3. Collection 这一支

`Collection` 下面最重要的是两大类：

- `List`
- `Set`

### List

特点通常是：

- 有序
- 可重复

常见实现类：

- `ArrayList`
- `LinkedList`
- `Vector`

### Set

特点通常是：

- 不可重复

常见实现类：

- `HashSet`
- `LinkedHashSet`
- `TreeSet`

## 4. Map 这一支

`Map` 不是 `Collection` 的子接口，但通常也放在集合这一章一起学。

它存的是：

- key-value

常见实现类：

- `HashMap`
- `LinkedHashMap`
- `TreeMap`
- `Hashtable`

## 5. 为什么 Map 要单独看

因为它和 `List`、`Set` 的思路不一样。

### List / Set

更像：

- 存一批值

### Map

更像：

- 一个 key 对应一个 value

例如：

```java
List<String> list
Set<String> set
Map<String, Integer> map
```

这里：

- `list` 和 `set` 存的是值
- `map` 存的是键值对

## 6. 集合这一章的推荐学习顺序

建议顺序：

1. 为什么需要集合
2. 集合整体结构
3. `List`
4. `Set`
5. `Map`
6. 迭代器与遍历
7. `equals()` 和 `hashCode()` 与集合的关系

## 7. 当前阶段最该记住的结论

1. `Collection` 和 `Map` 是并列的大类
2. `List` 和 `Set` 属于 `Collection`
3. `Map` 主要存键值对
4. `List`、`Set`、`Map` 的特点和适用场景不同

## 8. 一句话总结

集合这一章的核心不是背类名，而是先分清：谁是单列容器，谁是键值对容器，谁有序，谁可重复，谁负责去重。
