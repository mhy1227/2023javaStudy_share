# String 基础笔记

## 1. String 是什么

`String` 是 Java 中最常用的引用数据类型之一，用来表示字符串。

最重要的一个特点：

- `String` 是不可变的

例如：

```java
String s = "abc";
s = s.replace("a", "m");
```

这里不是把原来的 `"abc"` 改掉了，而是生成了一个新的字符串，再把新对象的地址赋给 `s`。

## 2. 为什么说 String 不可变

一旦一个 `String` 对象创建完成，它内部保存的字符内容就不能再直接修改。

所以像下面这些方法：

- `toUpperCase()`
- `toLowerCase()`
- `trim()`
- `replace()`
- `substring()`

本质上都是返回一个新字符串。

## 3. String 常用创建方式

```java
String s1 = "hello";
String s2 = new String("hello");
```

常见理解：

- 直接写字面量，常量池里可能复用
- `new String("hello")` 会显式创建新对象

复习时先记住一个结论：

- 比较内容用 `equals()`
- 不要用 `==` 比较字符串内容

## 4. 常用基础方法

### 4.1 获取长度和字符

```java
String s = "HelloWorld";
System.out.println(s.length());
System.out.println(s.charAt(0));
```

常见用途：

- 获取字符串长度
- 获取某个位置上的字符

### 4.2 大小写转换

```java
System.out.println(s.toLowerCase());
System.out.println(s.toUpperCase());
```

### 4.3 判空

```java
String s = "";
System.out.println(s.isEmpty());
```

注意：

- `isEmpty()` 判断的是长度是否为 `0`
- 不是判断 `null`

### 4.4 去掉首尾空格

```java
String s = "   hello world   ";
System.out.println(s.trim());
```

`trim()` 只去掉首尾空格，不会去掉中间空格。

### 4.5 比较内容

```java
String s1 = "Hello";
String s2 = "hello";
System.out.println(s1.equals(s2));
System.out.println(s1.equalsIgnoreCase(s2));
```

### 4.6 拼接

```java
String s = "abc";
System.out.println(s.concat("def"));
```

### 4.7 截取子串

```java
String s = "filwsx";
System.out.println(s.substring(2));
System.out.println(s.substring(2, 5));
```

规则：

- `substring(beginIndex)`：从指定位置截到结尾
- `substring(beginIndex, endIndex)`：左闭右开

## 5. 查找相关方法

### 5.1 判断开头、结尾、包含

```java
String s = "helloworld";
System.out.println(s.startsWith("he"));
System.out.println(s.endsWith("ld"));
System.out.println(s.contains("low"));
```

### 5.2 查找索引

```java
String s = "hellorworld";
System.out.println(s.indexOf("or"));
System.out.println(s.lastIndexOf("or"));
```

理解：

- `indexOf()`：从前往后找第一次出现的位置
- `lastIndexOf()`：找最后一次出现的位置

## 6. replace 和 replaceAll 的区别

这是复习时很容易混的一个点。

### 6.1 replace

`replace` 更偏向普通替换。

```java
String s = "北京市人民政府，北京人儿";
System.out.println(s.replace('北', '东'));
System.out.println(s.replace("北京", "上海"));
```

特点：

- 可以替换字符
- 也可以替换字符串
- 按字面值处理，不按正则表达式解释

### 6.2 replaceAll

`replaceAll` 按正则表达式替换。

```java
String str = "12hello34world5java7891mysql456";
String result = str.replaceAll("\\d+", ",").replaceAll("^,|,$", "");
System.out.println(result);
```

这里的意思是：

- `\\d+`：把连续数字替换成逗号
- `^,|,$`：把开头或结尾多余的逗号删掉

最后得到：

```text
hello,world,java,mysql
```

## 7. matches 的作用

`matches()` 用来判断整个字符串是否符合某个正则规则。

```java
String str = "12345";
System.out.println(str.matches("\\d+"));
```

这里是在判断：

- 这个字符串是否全部由数字组成

再比如：

```java
String tel = "0571-4534289";
System.out.println(tel.matches("0571-\\d{7,8}"));
```

这里是在判断：

- 是否符合杭州固定电话格式

要点：

- `matches()` 是整串匹配
- 不是“只要包含一部分就行”

## 8. split 的作用

`split()` 用来按规则切分字符串。

```java
String str = "hello|world|java";
String[] arr = str.split("\\|");
```

再比如：

```java
String str = "hello.world.java";
String[] arr = str.split("\\.");
```

这里要注意：

- `|` 和 `.` 在正则里有特殊含义
- 所以要写成 `\\|` 和 `\\.`

## 9. 字符串常见易错点

### 9.1 不要用 `==` 比较内容

```java
String s1 = "abc";
String s2 = new String("abc");
System.out.println(s1.equals(s2));
```

### 9.2 单引号和双引号不要混

```java
'a'      // char
"abc"    // String
```

错误示例：

```java
'to'
'you'
```

这会报：

```text
Too many characters in character literal
```

### 9.3 `matches()` 是整体匹配

```java
"123abc".matches("\\d+")
```

结果是 `false`，因为不是整个字符串都为数字。

## 10. 当前阶段怎么复习 String

建议顺序：

1. 先掌握最常用基础方法
2. 再区分 `replace`、`replaceAll`、`matches`、`split`
3. 最后做几道字符串处理小题

建议优先看这些文件：

- [`StringTest.java`](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/src/com/filwsx/JavaStudyAdvanced/basicClass/StringTest.java)
- [`StringMethodTest.java`](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/src/com/filwsx/JavaStudyAdvanced/basicClass/StringMethodTest.java)
- [`StringExercise.java`](D:/CourseShop_2/2023javaStudy_share/jobStudy/JavaAdvanced/src/com/filwsx/JavaStudyAdvanced/basicClass/StringExercise.java)

## 11. 一句话总结

复习 `String`，先抓住三件事：

- 不可变
- 常用方法
- 和正则相关的几个高频方法区别
