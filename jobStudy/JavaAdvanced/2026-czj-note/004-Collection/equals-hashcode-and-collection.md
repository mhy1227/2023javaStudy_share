# equals、hashCode 与集合

## 1. 为什么这个点要放在集合里

很多人前面学 `Object`、`String` 时，已经见过：

- `equals()`
- `hashCode()`

但真正开始学集合后，这两个方法才会变得特别重要。

因为：

- `HashSet`
- `HashMap`

这些集合的行为，和它们直接相关。

## 2. `equals()` 是干什么的

`equals()` 用来判断：

- 两个对象在“逻辑上是否相等”

例如：

```java
String s1 = new String("abc");
String s2 = new String("abc");
System.out.println(s1.equals(s2)); // true
```

## 3. `hashCode()` 是干什么的

`hashCode()` 可以简单理解成：

- 用来生成一个哈希值

这个值在哈希结构中很重要。

## 4. 为什么 HashSet 和 HashMap 会关心这两个方法

因为哈希类集合在判断元素位置或是否重复时，通常不是只靠一个方法。

可以先这样理解：

1. 先看 `hashCode()`
2. 再看 `equals()`

所以：

- `hashCode()` 更像“先粗分”
- `equals()` 更像“再精确确认”

## 5. 为什么重写 equals() 往往要一起重写 hashCode()

这是高频面试题。

原因是 Java 有一个重要约定：

- 如果两个对象 `equals()` 为 `true`
- 那它们的 `hashCode()` 也必须相同

如果只重写 `equals()`，不重写 `hashCode()`，就会导致哈希集合行为异常。

## 6. 一个典型问题

假设你自定义了一个 `Person` 类，只重写了 `equals()`，没有重写 `hashCode()`。

然后把两个“逻辑上相同”的 `Person` 放进 `HashSet`。

可能出现的现象是：

- 你以为会去重
- 但结果没有按预期去重

原因就在于：

- 哈希规则没有和相等规则保持一致

## 7. 对 List、Set、Map 的影响有什么不同

### List

`List` 更关心：

- 顺序
- 可重复

所以 `equals()` / `hashCode()` 的影响没有 `HashSet`、`HashMap` 那么核心。

### Set

特别是 `HashSet`，会强依赖：

- `equals()`
- `hashCode()`

来判断重复。

### Map

特别是 `HashMap`，会强依赖：

- key 的 `equals()`
- key 的 `hashCode()`

来判断 key 是否相同。

## 8. 为什么 String 适合做 HashMap 的 key

因为：

- `String` 是不可变对象
- `String` 已经正确重写了 `equals()` 和 `hashCode()`

所以它非常适合做：

- key

## 9. 当前阶段最该记住的结论

1. `HashSet` 和 `HashMap` 与 `equals()` / `hashCode()` 强相关
2. `equals()` 相等时，`hashCode()` 必须相同
3. 自定义类如果要参与哈希集合判重，通常要同时重写这两个方法
4. `String` 是典型的“已经处理好这两个方法”的类

## 10. 一句话总结

对象章节学 `equals()` 和 `hashCode()`，集合章节才真正知道它们为什么重要，尤其是对 `HashSet` 和 `HashMap`。
