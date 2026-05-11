# Collection 选择题与判断题

## 1. 判断题

### 题 1

`Map` 属于 `Collection` 的子接口。  

### 题 2

`List` 的元素不可重复。  

### 题 3

`Set` 的核心特点是不可重复。  

### 题 4

`HashSet` 的遍历顺序通常等于插入顺序。  

### 题 5

`TreeSet` 更偏排序。  

### 题 6

`HashMap` 最常用来保存 key-value。  

### 题 7

`LinkedHashMap` 更偏顺序表现。  

### 题 8

`ConcurrentHashMap` 更常见于并发场景。  

### 题 9

`Iterator` 只能遍历 `List`，不能遍历 `Set`。  

### 题 10

`String` 适合作为 `HashMap` 的 key。  

## 2. 单选题

### 题 11

如果要保存一批“有序、可重复”的元素，第一反应通常应该是：

- A. `Set`
- B. `Map`
- C. `List`
- D. `Queue`

### 题 12

如果要做普通去重，第一反应通常应该是：

- A. `ArrayList`
- B. `HashSet`
- C. `TreeMap`
- D. `LinkedList`

### 题 13

如果既想去重，又想让遍历顺序更稳定，优先想到：

- A. `HashSet`
- B. `LinkedHashSet`
- C. `TreeSet`
- D. `Vector`

### 题 14

如果需要保存 key-value，且普通业务最常用，优先想到：

- A. `TreeMap`
- B. `Hashtable`
- C. `HashMap`
- D. `Vector`

### 题 15

如果明确是并发场景下共享 `Map`，更常见的选择是：

- A. `HashMap`
- B. `Hashtable`
- C. `ConcurrentHashMap`
- D. `LinkedHashMap`

### 题 16

如果需要 key 自动排序，优先想到：

- A. `HashMap`
- B. `LinkedHashMap`
- C. `TreeMap`
- D. `ArrayList`

## 3. 参考答案

### 判断题答案

1. 错
2. 错
3. 对
4. 错
5. 对
6. 对
7. 对
8. 对
9. 错
10. 对

### 单选题答案

11. C
12. B
13. B
14. C
15. C
16. C

## 4. 一句话总结

如果选择题做下来还不顺，说明你对集合的“定位感”还不够稳，需要继续回看族谱和单体实现类文档。
