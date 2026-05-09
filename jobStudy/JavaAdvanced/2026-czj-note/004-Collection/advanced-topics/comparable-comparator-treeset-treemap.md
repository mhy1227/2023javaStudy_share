# Comparable、Comparator 与 TreeSet / TreeMap

## 1. 为什么这四个要放在一起讲

因为：

- `TreeSet`
- `TreeMap`

都和排序规则强相关。

而 Java 里最常见的排序规则来源，就是：

- `Comparable`
- `Comparator`

所以这四个知识点天然是一组。

## 2. Comparable 是什么

`Comparable` 可以理解成：

- 让类自己定义“默认比较规则”的接口

典型写法是：

```java
class Person implements Comparable<Person> {
    @Override
    public int compareTo(Person o) {
        return this.age - o.age;
    }
}
```

这表示：

- `Person` 自己知道怎么和同类对象比较

## 3. Comparator 是什么

`Comparator` 可以理解成：

- 在类外部额外提供一套比较规则

它更像：

- “外置比较器”

例如：

```java
Comparator<Person> comparator = new Comparator<Person>() {
    @Override
    public int compare(Person o1, Person o2) {
        return o1.getName().compareTo(o2.getName());
    }
};
```

## 4. Comparable 和 Comparator 的区别

### Comparable

- 类自己定义默认规则

### Comparator

- 类外部定义额外规则

所以一个稳妥记法是：

- `Comparable` 是内置规则
- `Comparator` 是外置规则

## 5. 为什么 TreeSet 会和它们有关

因为 `TreeSet` 的重点是：

- 排序

既然要排序，就必须知道：

- 元素怎么比大小

所以：

- 如果元素自身实现了 `Comparable`，可以按默认规则排
- 如果传入了 `Comparator`，可以按外部规则排

## 6. 为什么 TreeMap 也会和它们有关

因为 `TreeMap` 的重点是：

- key 的排序

所以它也需要明确：

- key 怎么比较

这就是它和 `Comparable` / `Comparator` 的关系。

## 7. TreeSet / TreeMap 为什么不仅仅是“排序”

因为它们还涉及：

- 去重或 key 判定
- 比较规则是否一致

当前阶段先记住一个关键点：

- 在 `TreeSet` / `TreeMap` 中，比较规则不仅影响顺序，也影响元素或 key 的判定逻辑

## 8. 面试里常见问法

1. `Comparable` 和 `Comparator` 有什么区别？
2. `TreeSet` 为什么和比较规则有关？
3. `TreeMap` 为什么会按 key 排序？
4. 自定义对象放进 `TreeSet` 为什么可能报错或行为不符合预期？

## 9. 怎么答更稳

如果问：

- `Comparable` 和 `Comparator` 区别是什么

可以答：

1. `Comparable` 是类内部定义默认比较规则
2. `Comparator` 是类外部定义额外比较规则
3. `TreeSet` / `TreeMap` 都依赖比较规则来组织元素或 key

## 10. 当前阶段最该记住的结论

1. `TreeSet` 和 `TreeMap` 的核心关键词是排序
2. 排序离不开比较规则
3. `Comparable` 是内置规则
4. `Comparator` 是外置规则
5. 这组知识点是集合章节和排序章节之间的重要桥梁

## 11. 一句话总结

只要看到 `TreeSet` 或 `TreeMap`，就要立刻想到：这里的关键不是哈希，而是比较规则。
