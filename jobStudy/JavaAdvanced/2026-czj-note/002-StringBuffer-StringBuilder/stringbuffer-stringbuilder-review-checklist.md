# StringBuffer 与 StringBuilder 复习清单

## 1. 基础概念是否清楚

检查自己能不能说清：

- `String` 不可变
- `StringBuffer` 可变
- `StringBuilder` 可变

如果这三个概念还混，先不要继续往下推。

## 2. 三者区别是否清楚

你应该能直接回答：

1. 谁不可变
2. 谁线程安全
3. 谁效率更高
4. 什么场景下该用谁

## 3. 常用方法是否会用

你应该会写这些方法：

- `append()`
- `insert()`
- `delete()`
- `replace()`
- `reverse()`
- `toString()`
- `length()`
- `capacity()`

至少要达到：

- 看到需求能想到对应方法

## 4. 高频场景是否能独立写

你应该能自己写出：

1. 循环拼接字符串
2. 在中间插入一段文本
3. 删除指定范围字符
4. 反转字符串
5. 把 `StringBuilder` 转成 `String`

## 5. 高频问题是否能答顺

你应该能回答：

1. 为什么 `StringBuilder` 效率高
2. 为什么循环里少用 `+`
3. `StringBuffer` 和 `StringBuilder` 有什么区别
4. 什么情况下该用 `StringBuilder`

## 6. 容易混淆的点

重点自查：

- 把 `StringBuilder` 当成线程安全
- 认为 `StringBuffer` 一定更常用
- 不知道 `length()` 和 `capacity()` 区别
- 只会 `append()`，不会 `insert()`、`delete()`、`reverse()`

## 7. 当前阶段达标标准

这一章复习达标，不要求你记底层扩容细节，但至少要做到：

1. 三者区别说得清
2. 常用方法会写
3. 循环拼接时知道优先用 `StringBuilder`

## 8. 一句话总结

如果你已经能把“区别 + 场景 + 常用方法”说顺并写出来，这一章就算过关了。
