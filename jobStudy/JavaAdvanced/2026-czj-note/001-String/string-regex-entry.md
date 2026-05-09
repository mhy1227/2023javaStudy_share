# String 中和正则相关的方法入门

## 1. 为什么 String 里会碰到正则

复习 `String` 时，很多人会卡在下面几个方法上：

- `replaceAll()`
- `matches()`
- `split()`

原因是它们都和正则表达式有关。

但当前阶段不用把正则学得很复杂，只要先掌握：

- 替换
- 校验
- 切分

这 3 种使用场景就够了。

## 2. `replace()` 和 `replaceAll()` 的区别

### `replace()`

普通替换，按字面值处理。

```java
String s = "北京市人民政府，北京人儿";
System.out.println(s.replace('北', '东'));
System.out.println(s.replace("北京", "上海"));
```

### `replaceAll()`

按正则表达式替换。

```java
String str = "12hello34world5java7891mysql456";
String result = str.replaceAll("\\d+", ",");
System.out.println(result);
```

这里的 `\\d+` 表示：

- `\\d`：一个数字
- `+`：前面的内容出现一次或多次

合起来就是：

- 一串连续数字

## 3. `replaceAll()` 的典型清洗流程

```java
String str = "12hello34world5java7891mysql456";
String result = str.replaceAll("\\d+", ",").replaceAll("^,|,$", "");
System.out.println(result);
```

拆开理解：

### 第一步

```java
str.replaceAll("\\d+", ",")
```

把所有连续数字替换成逗号。

结果近似于：

```text
,hello,world,java,mysql,
```

### 第二步

```java
.replaceAll("^,|,$", "")
```

把开头和结尾的逗号去掉。

其中：

- `^,`：匹配开头的逗号
- `,$`：匹配结尾的逗号
- `|`：表示“或者”

最后得到：

```text
hello,world,java,mysql
```

## 4. `matches()` 是做什么的

`matches()` 用来判断整个字符串是否满足某个规则。

### 示例 1：是否全是数字

```java
String str = "12345";
boolean result = str.matches("\\d+");
System.out.println(result);
```

结果为 `true`。

### 示例 2：是否符合固定电话格式

```java
String tel = "0571-4534289";
boolean result = tel.matches("0571-\\d{7,8}");
System.out.println(result);
```

这里的意思是：

- 前面必须是 `0571-`
- 后面跟 7 位或 8 位数字

### 一个关键点

`matches()` 是整串匹配。

例如：

```java
"abc123".matches("\\d+")
```

结果是 `false`，因为整个字符串不是纯数字。

## 5. `split()` 是做什么的

`split()` 用来按规则拆分字符串。

### 示例 1：按 `|` 拆

```java
String str = "hello|world|java";
String[] arr = str.split("\\|");
```

### 示例 2：按 `.` 拆

```java
String str = "hello.world.java";
String[] arr = str.split("\\.");
```

## 6. 为什么 `|` 和 `.` 要加转义

因为在正则里：

- `|` 表示“或”
- `.` 表示“任意单个字符”

所以如果你真想按字符本身去拆，就必须转义。

在 Java 字符串中，`\` 本身还要再转义一次，所以最终写成：

- `"\\|"`
- `"\\."`

## 7. 当前阶段需要记住的几个简单正则

### `\\d`

表示一个数字。

### `\\d+`

表示一串连续数字。

### `{7,8}`

表示前面的内容出现 7 到 8 次。

### `^`

表示开头。

### `$`

表示结尾。

### `|`

表示“或者”。

### `\\.`

表示真正的点号 `.`。

### `\\|`

表示真正的竖线 `|`。

## 8. 当前阶段不用学太深的内容

先不用急着学这些：

- 复杂分组
- 捕获组
- 反向引用
- 零宽断言
- 贪婪与非贪婪的复杂场景

对现在的 Java 基础复习来说，会用下面这几个就够了：

- `replaceAll()`
- `matches()`
- `split()`

## 9. 看代码时的思考顺序

以后看到含正则的字符串，可以按这个顺序理解：

1. 这个方法是替换、校验还是切分
2. 正则想匹配的对象是什么
3. 是否有特殊字符需要转义
4. 最终输出想变成什么样

## 10. 一句话总结

String 里的正则入门，不是让你学“正则理论”，而是学会这三件事：

- 用 `replaceAll()` 清洗字符串
- 用 `matches()` 做格式校验
- 用 `split()` 做规则切分
