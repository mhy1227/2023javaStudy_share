# 常见异常场景例子

## 1. 为什么这一章一定要配例子

异常如果只背：

- `Throwable`
- `Error`
- `Exception`
- `RuntimeException`

很容易出现的问题是：

- 名字记住了
- 但一问到真实场景就答不上来

所以异常这一章更适合这样复习：

1. 先看族谱
2. 再看真实例子
3. 最后把例子和分类对应起来

## 2. 最常见的一组运行时异常例子

这一组异常平时最容易碰到，也最容易在面试里被拿来举例。

### 2.1 NullPointerException

示例：

```java
String name = null;
System.out.println(name.length());
```

可以怎么理解：

- `name` 是 `null`
- 结果直接去调方法
- 就会空指针

业务场景可以怎么说：

- 查数据库没查到数据
- 返回对象是 `null`
- 代码里没有判空就直接取属性或调方法

面试回答可以这样说：

`NullPointerException` 属于 `RuntimeException`。它通常反映的是代码逻辑和边界处理不到位，比如对象可能为空，但代码里没有做判空保护。

### 2.2 IndexOutOfBoundsException

示例：

```java
List<String> list = new ArrayList<>();
list.add("A");
System.out.println(list.get(1));
```

可以怎么理解：

- 列表里只有一个元素
- 但去取下标 `1`
- 就越界了

常见延伸：

- `ArrayIndexOutOfBoundsException`
- `StringIndexOutOfBoundsException`

业务场景可以怎么说：

- 循环边界写错
- 数组长度判断不严
- 字符串截取位置不对

面试回答可以这样说：

这类异常也属于运行时异常，本质上都是访问范围超界，常见于数组、集合、字符串下标处理不严谨。

### 2.3 ArithmeticException

示例：

```java
int a = 10 / 0;
```

可以怎么理解：

- 整数除以 `0`
- 会直接报异常

业务场景可以怎么说：

- 算比例
- 算平均值
- 算转化率

如果分母没先判断，就可能触发类似问题。

面试回答可以这样说：

`ArithmeticException` 也是典型运行时异常。虽然业务代码里不一定直接写 `10 / 0`，但只要有除法计算，又没有校验分母，就可能出现这个问题。

### 2.4 NumberFormatException

示例：

```java
int age = Integer.parseInt("18岁");
```

可以怎么理解：

- 这个字符串不是纯数字
- 转 `int` 时就会失败

业务场景可以怎么说：

- 前端参数格式不规范
- Excel 导入的数据不干净
- 数据库存的字符串不能直接转数字

面试回答可以这样说：

`NumberFormatException` 属于 `RuntimeException`，常见于字符串转数字时格式不合法，本质上是输入数据不符合预期。

### 2.5 ClassCastException

示例：

```java
Object obj = "hello";
Integer num = (Integer) obj;
```

可以怎么理解：

- 实际对象是字符串
- 却强转成 `Integer`
- 就会类型转换异常

业务场景可以怎么说：

- 向下转型判断不严
- 泛型使用不规范
- 老代码里大量 `Object` 强转

面试回答可以这样说：

`ClassCastException` 是运行时类型转换失败造成的异常，常见于强制类型转换前没有先判断真实类型。

## 3. checked exception 常见例子

这一组异常通常更像：

- 外部资源访问问题
- 编译期要求你面对它

### 3.1 IOException

示例：

```java
FileInputStream fis = new FileInputStream("D:/test.txt");
```

如果文件不存在、文件路径不对、文件访问失败，就可能触发文件相关 IO 异常。

业务场景可以怎么说：

- 读文件失败
- 写文件失败
- 网络流读取失败

面试回答可以这样说：

`IOException` 通常属于 checked exception，常出现在文件、网络流等外部资源操作中。它不是单纯的代码逻辑问题，而是资源访问可能失败，所以编译期通常要求显式处理或抛出。

### 3.2 SQLException

示例：

```java
String sql = "select * from user where id = ? and status = ?";
PreparedStatement ps = conn.prepareStatement(sql);
ps.setInt(1, 1001);
ResultSet rs = ps.executeQuery();
```

这个例子里：

- SQL 里有两个占位符
- 但代码只传了一个参数

就可能导致数据库执行异常。

业务场景可以怎么说：

1. SQL 写错
2. 占位符数量不匹配
3. 参数类型不对
4. 数据库连接异常

面试回答可以这样说：

`SQLException` 一般属于 checked exception，常见于 JDBC 操作。比如 SQL 语法错误、占位符和参数数量不一致、字段类型不匹配、数据库连接失败等，都会导致数据库相关异常。

### 3.3 ClassNotFoundException

示例场景：

- 反射加载类时，类名写错
- 运行环境里缺少对应类

例如：

```java
Class.forName("com.demo.NotExistClass");
```

面试回答可以这样说：

`ClassNotFoundException` 通常也属于 checked exception，更偏运行环境、类加载或反射相关问题。

## 4. Error 常见例子

这一组要重点记：

- 它们属于 `Error`
- 不属于平时普通业务异常处理主线

### 4.1 OutOfMemoryError

示例：

```java
List<byte[]> list = new ArrayList<>();
while (true) {
    list.add(new byte[1024 * 1024]);
}
```

可以怎么理解：

- 不断申请内存
- 不断往集合里堆对象
- 最后把内存打满

业务场景可以怎么说：

1. 缓存无限增长
2. 大对象太多
3. 集合里数据一直堆积
4. 对象生命周期过长

面试回答可以这样说：

`OutOfMemoryError` 属于 `Error`，通常说明内存资源耗尽或者程序设计存在严重问题，比如缓存失控、大量对象堆积、内存泄漏等。

### 4.2 StackOverflowError

示例：

```java
public static void test() {
    test();
}
```

可以怎么理解：

- 递归没有出口
- 方法调用层层压栈
- 最后把栈空间打满

业务场景可以怎么说：

- 递归出口写错
- 调用链太深
- 某些对象相互调用导致无限递归

面试回答可以这样说：

`StackOverflowError` 也属于 `Error`，更像程序结构问题，比如递归没有终止条件或者调用层级过深。

## 5. 怎么把这些例子和族谱串起来

可以先这样记：

### Error

- `OutOfMemoryError`
- `StackOverflowError`

### RuntimeException

- `NullPointerException`
- `IndexOutOfBoundsException`
- `ArithmeticException`
- `NumberFormatException`
- `ClassCastException`

### checked exception

- `IOException`
- `SQLException`
- `ClassNotFoundException`

## 6. 面试里怎么一口气回答更自然

可以这样答：

Java 异常我一般会结合场景去记。比如空指针、数组越界、类型转换失败、数字转换失败，这些都属于 `RuntimeException`，更偏代码逻辑和边界处理问题；像 `IOException`、`SQLException`、`ClassNotFoundException` 这类，更偏外部资源、数据库、类加载等问题，通常属于 checked exception；而 `OutOfMemoryError`、`StackOverflowError` 属于 `Error`，一般说明 JVM 资源或程序结构层面出了更严重的问题。

## 7. 当前阶段最该记住的结论

1. 异常分类一定要配场景记
2. 空指针、越界、数字转换失败这类最常见
3. SQL 占位符和参数不匹配是很好用的数据库异常例子
4. OOM 和栈溢出属于 `Error`
5. 面试更喜欢你“结合场景解释”，而不是只背类名

## 8. 一句话总结

异常这一章真正好用的复习方式，不是死背类名，而是能把每一类异常快速对应到一个真实代码场景。
