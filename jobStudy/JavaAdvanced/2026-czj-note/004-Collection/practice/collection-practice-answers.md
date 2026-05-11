# Collection 练习题参考答案

## 1. 基础概念题答案

### 题 1

`Collection` 和 `Map` 是并列关系。

- `Collection` 更像存一批单列元素
- `Map` 更像存 `key-value`

所以：

- `Map` 不是 `Collection` 的子接口

### 题 2

- `List`：有序、可重复
- `Set`：不可重复
- `Queue`：更偏队列语义

### 题 3

- `ArrayList`：普通有序列表主力
- `HashSet`：普通去重主力
- `HashMap`：普通映射主力

## 2. 场景选择题答案

### 题 4

应优先想到：

- `List`
- 更具体一点通常是 `ArrayList`

原因：

- 有序
- 可重复

### 题 5

应优先想到：

- `HashSet`

原因：

- 只关心去重
- 不关心顺序

### 题 6

应优先想到：

- `LinkedHashSet`

原因：

- 去重
- 顺序表现更稳定

### 题 7

应优先想到：

- `HashMap`

原因：

- 普通 key-value 映射场景最常见

### 题 8

应优先想到：

- `TreeMap`

原因：

- 按 key 排序

### 题 9

应优先想到：

- `ConcurrentHashMap`

原因：

- 并发场景下更常见的线程安全 `Map`

## 3. 遍历题答案

### 题 10

#### Iterator 遍历 List

```java
List<String> list = new ArrayList<>();
list.add("Tom");
list.add("Jerry");

Iterator<String> it = list.iterator();
while (it.hasNext()) {
    System.out.println(it.next());
}
```

#### for-each 遍历 Set

```java
Set<String> set = new HashSet<>();
set.add("A");
set.add("B");

for (String s : set) {
    System.out.println(s);
}
```

### 题 11

#### keySet() 遍历

```java
Map<String, Integer> map = new HashMap<>();
map.put("Tom", 18);
map.put("Jerry", 20);

for (String key : map.keySet()) {
    System.out.println(key + " -> " + map.get(key));
}
```

#### entrySet() 遍历

```java
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " -> " + entry.getValue());
}
```

## 4. 理解题答案

### 题 12

因为 `HashSet` 和 `HashMap` 都属于哈希类集合。

可以先这样理解：

1. 先根据 `hashCode()` 粗分
2. 再根据 `equals()` 精确判断

所以这两个方法和哈希集合直接相关。

### 题 13

因为：

- `String` 不可变
- `String` 已经正确重写了 `equals()` 和 `hashCode()`

所以它很适合作为 `HashMap` 的 key。

### 题 14

因为 `LinkedList` 不只是 `List` 实现类，它还支持双端队列相关语义，所以它也常出现在 `Deque` 这条线上。

## 5. 横向对比题答案

### 题 15

- `ArrayList`：普通列表主力，日常最常见
- `LinkedList`：既能做 `List`，也能做 `Deque`

### 题 16

- `HashSet`：普通去重
- `LinkedHashSet`：去重 + 顺序表现
- `TreeSet`：去重 + 排序

### 题 17

- `HashMap`：普通映射主力
- `LinkedHashMap`：映射 + 顺序表现
- `TreeMap`：映射 + 排序

### 题 18

- `HashMap`：最常用，一般不强调线程安全
- `Hashtable`：较早的线程安全实现
- `ConcurrentHashMap`：并发场景更常见的线程安全实现

## 6. 小练习题参考思路

### 题 19

```java
String[] arr = {"a", "b", "a", "c"};
Set<String> set = new HashSet<>();
for (String s : arr) {
    set.add(s);
}
System.out.println(set);
```

### 题 20

```java
String[] arr = {"java", "mysql", "java", "spring"};
Map<String, Integer> map = new HashMap<>();
for (String s : arr) {
    map.put(s, map.getOrDefault(s, 0) + 1);
}
System.out.println(map);
```

### 题 21

```java
int[] arr = {5, 2, 8, 2, 1, 5};
Set<Integer> set = new TreeSet<>();
for (int num : arr) {
    set.add(num);
}
System.out.println(set);
```

## 7. 一句话总结

这份答案版的重点不是背代码，而是帮你把“场景 -> 集合选择 -> 基本写法”连起来。
