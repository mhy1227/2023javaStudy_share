# Collection 代码手写题

## 1. List 基础手写

### 题 1

创建一个 `ArrayList<String>`，加入 3 个名字并遍历输出。

参考要求：

- 使用 `add()`
- 使用 `for-each`

### 题 2

创建一个 `LinkedList<String>`，演示：

- 头部加入元素
- 尾部加入元素
- 从头部取元素

## 2. Set 手写

### 题 3

创建一个 `HashSet<String>`，加入一些重复元素，观察最终结果。

目标：

- 理解 `Set` 去重

### 题 4

创建一个 `LinkedHashSet<String>`，加入若干元素并遍历输出，观察顺序表现。

### 题 5

创建一个 `TreeSet<Integer>`，加入几个整数并输出，观察排序效果。

## 3. Map 手写

### 题 6

创建一个 `HashMap<String, Integer>`，保存几组“姓名 -> 年龄”数据，并按 key 输出。

### 题 7

遍历 `Map`：

- 用 `keySet()`
- 用 `entrySet()`

都各写一遍。

### 题 8

统计字符串数组中每个单词出现的次数。

例如：

```java
String[] arr = {"java", "mysql", "java", "spring", "java", "mysql"};
```

目标输出思路：

- `java -> 3`
- `mysql -> 2`
- `spring -> 1`

## 4. 场景小题

### 题 9

给定一个整数数组，去重后输出。

提示：

- `HashSet`

### 题 10

给定一个整数数组，去重并按从小到大输出。

提示：

- `TreeSet`

### 题 11

给定一组字符串，既要去重，又希望输出时尽量保持原来的插入顺序。

提示：

- `LinkedHashSet`

## 5. 思考题

### 题 12

为什么题 9 优先想到 `HashSet`，而不是 `ArrayList`？

### 题 13

为什么题 10 更容易想到 `TreeSet`？

### 题 14

为什么统计次数这类题通常会想到 `Map`？

## 6. 一句话总结

集合练习题最核心的训练目标，不是写复杂代码，而是养成“看到场景就想到对应集合”的条件反射。
