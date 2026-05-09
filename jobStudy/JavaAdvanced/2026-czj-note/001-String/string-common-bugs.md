# String 常见问题与易错点

## 1. 为什么要单独记这份文档

复习 `String` 时，很多问题不是不会方法，而是：

- 方法混了
- 比较方式错了
- 引号写错了
- 正则没转义
- `null` 没处理

所以这份文档专门记录常见坑。

## 2. 用 `==` 比较字符串内容

### 错误写法

```java
String s1 = new String("abc");
String s2 = new String("abc");
System.out.println(s1 == s2);
```

### 问题

`==` 比较的是：

- 地址

不是：

- 内容

### 正确写法

```java
System.out.println(s1.equals(s2));
```

### 结论

比较字符串内容，优先用：

- `equals()`

## 3. 忘了处理 `null`

### 错误写法

```java
String s = null;
System.out.println(s.equals("abc"));
```

### 问题

会直接抛：

```text
NullPointerException
```

### 更稳的写法

```java
System.out.println("abc".equals(s));
```

### 结论

常量写前面，更安全。

## 4. 把 `isEmpty()` 当成判空

### 错误理解

很多人以为：

```java
s.isEmpty()
```

可以判断：

- 是否为 `null`

其实不是。

### 实际情况

`isEmpty()` 判断的是：

- 字符串长度是否为 `0`

### 例子

```java
String s1 = "";
String s2 = "   ";
String s3 = null;
```

这里：

- `s1.isEmpty()` 为 `true`
- `s2.isEmpty()` 为 `false`
- `s3.isEmpty()` 会空指针

## 5. 误以为 `trim()` 会去掉中间空格

### 错误理解

```java
String s = "  he  llo  ";
System.out.println(s.trim());
```

很多人以为结果会变成：

```text
hello
```

### 实际结果

`trim()` 只会去掉：

- 首部空格
- 尾部空格

不会删掉中间空格。

## 6. `substring()` 边界搞错

### 常见错误

```java
String s = "abcdef";
System.out.println(s.substring(2, 5));
```

很多人误以为会取：

- 2 到 5 全部

### 实际规则

`substring(begin, end)` 是：

- 左闭右开

所以取到的是：

- 2
- 3
- 4

不会包含 5。

## 7. 单引号和双引号混用

### 错误写法

```java
'to'
'hello'
```

### 问题

Java 中：

- 单引号表示 `char`
- 双引号表示 `String`

所以：

```java
'a'
```

是合法的。

但：

```java
'to'
```

会报：

```text
Too many characters in character literal
```

### 正确写法

```java
"to"
"hello"
```

## 8. `replace()` 和 `replaceAll()` 混了

### 问题场景

想替换某个正则规则时，却用了：

```java
replace()
```

### 区别

`replace()`：

- 普通替换
- 按字面值处理

`replaceAll()`：

- 正则替换

### 示例

```java
String str = "12hello34world";
System.out.println(str.replaceAll("\\d+", ","));
```

这里必须用：

- `replaceAll()`

## 9. `matches()` 当成“包含匹配”

### 错误理解

```java
"abc123".matches("\\d+")
```

很多人以为只要里面“有数字”就会返回 `true`。

### 实际情况

`matches()` 要求：

- 整个字符串都符合规则

所以这里会返回：

- `false`

### 结论

`matches()` 不是“包含”，而是“整串校验”。

## 10. `split()` 忘记转义

### 错误写法

```java
String s = "hello.world.java";
String[] arr = s.split(".");
```

### 问题

`.` 在正则中表示：

- 任意单个字符

所以这不是按点切分。

### 正确写法

```java
String[] arr = s.split("\\.");
```

同理：

```java
String s = "hello|world|java";
String[] arr = s.split("\\|");
```

### 结论

这些特殊字符要特别注意：

- `.`
- `|`
- `\`

## 11. 忘了 String 不可变

### 错误理解

```java
String s = "abc";
s.replace("a", "m");
System.out.println(s);
```

很多人以为输出会是：

```text
mbc
```

### 实际结果

输出还是：

```text
abc
```

因为 `replace()` 返回了新字符串，但没有接收。

### 正确写法

```java
s = s.replace("a", "m");
```

## 12. 忽略编码问题

### 现象

文件内容看着正常，但 IDE 报：

- 非法字符

### 常见原因

文件编码不对，比如：

- `UTF-16 LE`

而 Java 源文件通常更适合：

- `UTF-8`

### 处理方式

在 IDEA 中：

1. 查看右下角编码
2. 选择 `Convert to UTF-8`

## 13. 拼接字符串时滥用 `+`

### 问题场景

在循环里频繁写：

```java
String s = "";
for (int i = 0; i < 1000; i++) {
    s += i;
}
```

### 问题

会产生很多中间字符串对象，效率不高。

### 更合适的写法

```java
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000; i++) {
    sb.append(i);
}
String result = sb.toString();
```

## 14. 复习时最容易混的几个点

建议你重点区分下面几组：

### 第一组

- `==`
- `equals()`

### 第二组

- `replace()`
- `replaceAll()`

### 第三组

- `isEmpty()`
- `null`

### 第四组

- `split(".")`
- `split("\\.")`

### 第五组

- `'a'`
- `"a"`

## 15. 一句话总结

String 这一章最常见的问题，不是方法不会，而是：

- 比较错
- 转义错
- 引号错
- 编码错
- 以为字符串会原地修改
