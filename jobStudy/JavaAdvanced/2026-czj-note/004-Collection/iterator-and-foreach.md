# Iterator 与 foreach

## 1. 为什么这一块必须单独学

集合学到后面，最常见的操作之一就是：

- 遍历

而在 Java 里，遍历集合最常见的两种方式就是：

- `Iterator`
- `for-each`

这两者在面试和实际开发里都非常常见。

## 2. Iterator 是什么

`Iterator` 可以先理解成：

- 迭代器

它的作用是：

- 按顺序把集合中的元素一个一个取出来

## 3. Iterator 的基本使用

例如：

```java
Collection<String> coll = new ArrayList<>();
coll.add("Tom");
coll.add("Jerry");
coll.add("Jack");

Iterator<String> iterator = coll.iterator();
while (iterator.hasNext()) {
    String str = iterator.next();
    System.out.println(str);
}
```

这里最常用的两个方法是：

- `hasNext()`
- `next()`

## 4. `hasNext()` 和 `next()` 的作用

### `hasNext()`

表示：

- 后面还有没有元素

### `next()`

表示：

- 取出当前元素，并让指针往后移动

## 5. foreach 是什么

`for-each` 也叫增强 `for` 循环。

例如：

```java
for (String str : coll) {
    System.out.println(str);
}
```

它看起来更简洁，底层思想仍然和迭代遍历强相关。

## 6. Iterator 和 foreach 的区别

### Iterator

优点：

- 更显式
- 需要时更适合配合删除等操作理解遍历过程

### foreach

优点：

- 写法更简洁
- 读起来更自然

所以平时一般：

- 简单遍历优先 `for-each`
- 需要更细控制时会更多想到 `Iterator`

## 7. 为什么不能一边遍历一边随意改集合

这是一个高频易错点。

例如：

```java
for (String str : coll) {
    coll.remove(str);
}
```

这种写法通常会出问题。

当前阶段先记住一个结论：

- 遍历集合时，不要随意直接修改集合结构

如果要在遍历中删除元素，通常要更谨慎，后面学深入一点再展开。

## 8. 哪些集合能用 foreach

只要支持迭代遍历的集合，通常都能用 `for-each`。

常见例如：

- `List`
- `Set`
- `Queue`

`Map` 也可以遍历，但通常会遍历：

- `keySet()`
- `entrySet()`
- `values()`

## 9. Map 遍历的常见方式

例如：

```java
Map<String, Integer> map = new HashMap<>();
map.put("Tom", 18);
map.put("Jerry", 20);

for (String key : map.keySet()) {
    System.out.println(key + " -> " + map.get(key));
}
```

或者：

```java
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " -> " + entry.getValue());
}
```

## 10. 当前阶段最该记住的结论

1. `Iterator` 是集合遍历的重要方式
2. `for-each` 更简洁
3. `Iterator` 常用 `hasNext()` 和 `next()`
4. 遍历时不要随意直接修改集合结构
5. `Map` 通常遍历 `keySet()` 或 `entrySet()`

## 11. 一句话总结

集合遍历的主线很简单：先会 `Iterator`，再熟练 `for-each`，最后再理解不同集合的遍历差异。
