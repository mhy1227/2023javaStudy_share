# Map 基础笔记

## 1. 什么是 Map

`Map` 用来存：

- 键值对

也就是：

- `key -> value`

例如：

```java
Map<String, Integer> map = new HashMap<>();
map.put("Tom", 18);
map.put("Jerry", 20);
```

这里：

- `"Tom"` 是 key
- `18` 是 value

## 2. Map 和 List/Set 的区别

### List / Set

更像存一批值。

### Map

更像建立映射关系。

例如：

- 用户名 -> 年龄
- 商品 id -> 商品对象
- 单词 -> 出现次数

## 3. Map 的特点

当前阶段先抓住这几点：

1. 存的是键值对
2. key 通常不能重复
3. 后放入相同 key 时，value 会被覆盖

例如：

```java
map.put("Tom", 18);
map.put("Tom", 20);
```

这里最后 `"Tom"` 对应的值通常是：

- `20`

## 4. 常见实现类

当前阶段先记：

- `HashMap`
- `LinkedHashMap`
- `TreeMap`
- `Hashtable`

## 5. HashMap

最常用。

当前阶段先记：

- 日常开发中最常见
- 查找和存取都很常用

## 6. LinkedHashMap

可以先记：

- 在 `HashMap` 基础上更强调顺序表现

## 7. TreeMap

可以先记：

- 更偏向按 key 的规则进行组织

## 8. Hashtable

当前阶段只要知道：

- 是比较早期的实现
- 日常开发不作为主力

## 9. Map 常用方法

### `put(key, value)`

添加或覆盖键值对。

### `get(key)`

根据 key 获取 value。

### `remove(key)`

根据 key 删除数据。

### `containsKey(key)`

判断某个 key 是否存在。

### `size()`

查看键值对数量。

## 10. Map 的典型场景

适合这些需求：

- 通过某个标识快速找到对应数据
- 统计次数
- 建立名称和对象之间的对应关系

例如：

- 用户 id -> 用户对象
- 商品 id -> 商品信息
- 字符串 -> 次数

## 11. 当前阶段最该记住的结论

1. `Map` 不是 `Collection` 的子接口
2. `Map` 也是集合大章节的重要部分
3. `Map` 存的是 key-value
4. 最常见实现类是 `HashMap`
5. key 一般不能重复

## 12. 一句话总结

如果你的需求不是“存一批值”，而是“通过 key 找 value”，第一反应通常就是 `Map`。
