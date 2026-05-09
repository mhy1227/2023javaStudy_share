# String 练习题整理

## 1. 练习目标

复习 `String`，不能只看概念，还要自己写几道小题。

这份练习题重点覆盖：

- 基础方法使用
- 字符串查找
- 截取与替换
- 简单正则处理
- 常见面试风格题

## 2. 基础热身题

### 题 1：统计字符串长度

给定：

```java
String s = "HelloWorld";
```

要求：

- 输出字符串长度
- 输出第一个字符
- 输出最后一个字符

考点：

- `length()`
- `charAt()`

### 题 2：大小写转换

给定：

```java
String s = "HelloWorld";
```

要求：

- 输出全小写
- 输出全大写

考点：

- `toLowerCase()`
- `toUpperCase()`

### 题 3：判断空串

要求区分：

- `""`
- `"   "`
- `null`

考点：

- `isEmpty()`
- `trim()`
- `null` 判断

## 3. 查找与截取题

### 题 4：判断字符串是否包含某子串

给定：

```java
String s = "helloworld";
```

要求判断：

- 是否以 `hello` 开头
- 是否以 `world` 结尾
- 是否包含 `low`

考点：

- `startsWith()`
- `endsWith()`
- `contains()`

### 题 5：查找子串第一次和最后一次出现的位置

给定：

```java
String s = "hellorworld";
```

要求：

- 找出 `"or"` 第一次出现的索引
- 找出 `"or"` 最后一次出现的索引

考点：

- `indexOf()`
- `lastIndexOf()`

### 题 6：截取用户名

给定邮箱：

```java
String email = "filwsx123@qq.com";
```

要求：

- 截取 `@` 前面的用户名部分

提示：

- 先找 `@` 的索引
- 再用 `substring()`

## 4. 替换相关题

### 题 7：普通替换

给定：

```java
String s = "北京市人民政府，北京人儿";
```

要求：

- 把所有 `北` 替换成 `东`
- 把所有 `"北京"` 替换成 `"上海"`

考点：

- `replace(char, char)`
- `replace(CharSequence, CharSequence)`

### 题 8：去掉字符串首尾空格

给定：

```java
String s = "   hello world   ";
```

要求：

- 去掉首尾空格

考点：

- `trim()`

## 5. 正则入门题

### 题 9：判断字符串是否全为数字

给定：

```java
String s = "12345";
```

要求：

- 判断它是否全部由数字组成

考点：

- `matches("\\d+")`

### 题 10：判断电话格式

给定：

```java
String tel = "0571-4534289";
```

要求：

- 判断是否符合杭州固定电话格式

考点：

- `matches("0571-\\d{7,8}")`

### 题 11：按规则拆分字符串

给定：

```java
String s1 = "hello|world|java";
String s2 = "hello.world.java";
```

要求：

- 分别拆分成字符串数组

考点：

- `split("\\|")`
- `split("\\.")`

### 题 12：去掉数字，只保留单词块

给定：

```java
String str = "12hello34world5java7891mysql456";
```

要求：

- 最终得到：

```text
hello,world,java,mysql
```

考点：

- `replaceAll("\\d+", ",")`
- `replaceAll("^,|,$", "")`

## 6. 面试风格练习题

### 题 13：`==` 和 `equals()` 的区别

要求你自己用一句话回答：

- `==` 比较什么
- `equals()` 比较什么

### 题 14：String 为什么不可变

要求：

- 用自己的话说出 3 个点

建议答题方向：

- 内容不能直接改
- 修改会返回新对象
- 安全、常量池复用、适合做 key

### 题 15：String、StringBuffer、StringBuilder 的区别

要求：

- 说明三者区别
- 说出各自适用场景

## 7. 编码练习题

### 题 16：反转字符串

给定：

```java
String s = "abcdef";
```

要求：

- 输出 `"fedcba"`

提示：

- 可以用 `charAt()`
- 也可以用 `StringBuilder`

### 题 17：统计某字符出现次数

给定：

```java
String s = "abkkcadkabkebfkabkskab";
```

要求：

- 统计字符 `'k'` 出现了多少次

### 题 18：获取两个字符串的最大相同子串

给定：

```java
String s1 = "abcwerthelloyuiodef";
String s2 = "cvhellobnm";
```

要求：

- 找出它们的最大相同子串

这个题难度比前面高一点，适合复习中后期再做。

## 8. 推荐练习顺序

建议按这个顺序做：

1. 题 1 到题 8
2. 题 9 到题 12
3. 题 13 到题 15
4. 题 16 到题 18

## 9. 做题时的要求

不要只看答案，至少做到：

1. 自己先写
2. 说清楚考点
3. 说清楚为什么这么写
4. 做完后回顾有没有更简单的方法

## 10. 一句话总结

String 练习的目标不是“会背方法名”，而是看到题目时，知道该用哪个方法解决问题。
