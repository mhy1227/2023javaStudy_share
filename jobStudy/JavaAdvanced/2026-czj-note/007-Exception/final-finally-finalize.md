# final、finally、finalize

## 1. 为什么这三个总容易混

因为它们长得非常像：

- `final`
- `finally`
- `finalize`

但它们其实分属三件完全不同的事情：

1. `final` 是关键字
2. `finally` 是异常处理结构的一部分
3. `finalize` 是 `Object` 里的方法

所以这题本质上不是背单词，而是分清：

- 它属于哪一层
- 它是干什么的

## 2. 先说最短结论

可以先这样记：

### final

- 表示“不能再改”

### finally

- 表示“最后通常都会执行的代码块”

### finalize

- 是对象被回收前可能调用的方法，但现在基本不推荐依赖

## 3. final 是什么

`final` 是 Java 关键字，可以修饰：

1. 类
2. 方法
3. 变量

### 3.1 final 修饰类

表示：

- 这个类不能被继承

例如：

```java
final class Animal {
}
```

像 `String` 就是典型的 `final` 类。

### 3.2 final 修饰方法

表示：

- 子类不能重写这个方法

例如：

```java
class Person {
    public final void eat() {
        System.out.println("eat");
    }
}
```

### 3.3 final 修饰变量

表示：

- 变量一旦赋值，就不能再重新赋值

例如：

```java
final int age = 18;
```

这里之后就不能再写：

```java
age = 20;
```

## 4. final 修饰引用类型时要注意什么

这个点很容易被问。

例如：

```java
final List<String> list = new ArrayList<>();
list.add("A");
```

这里是合法的。

因为：

- `final` 限制的是引用不能再指向别的对象
- 不是说对象内部状态完全不能变

也就是说：

```java
list = new ArrayList<>();
```

不行，但：

```java
list.add("A");
```

可以。

## 5. finally 是什么

`finally` 是异常处理结构里的代码块，通常和：

- `try`
- `catch`

一起出现。

它的核心作用可以先记成：

- 不管前面是否发生异常，最后通常都要执行的收尾逻辑

例如：

```java
try {
    System.out.println("try");
} catch (Exception e) {
    System.out.println("catch");
} finally {
    System.out.println("finally");
}
```

`finally` 常见用途：

1. 关闭资源
2. 释放连接
3. 做收尾处理

## 6. finally 一定会执行吗

通常要先记：

- 大多数情况下会执行

但不是绝对意义上的“100% 无条件”。

例如一些极端情况：

1. JVM 直接退出
2. 进程被强制终止
3. 机器宕机

这种情况下就不能机械地说：

- `finally` 一定执行

更稳的说法是：

- 正常控制流下，`finally` 通常都会执行

## 7. finalize 是什么

`finalize` 是 `Object` 类里的一个方法。

早期很多资料会把它理解成：

- 对象被垃圾回收前的“最后清理机会”

但当前阶段最重要的是记住：

- 现在基本不推荐依赖它

因为它有这些问题：

1. 调用时机不确定
2. 性能差
3. 不可靠

所以现代 Java 开发里一般不会把资源释放寄希望于 `finalize`。

## 8. finalize 为什么现在不推荐

因为它和：

- 垃圾回收时机

绑定得太重，而垃圾回收本身就不是你能精确控制的。

所以如果你把关键资源释放写在 `finalize` 里，就容易出现：

- 资源释放不及时
- 行为不可预测

现在更推荐的是：

1. 显式关闭资源
2. `try-with-resources`
3. `finally` 做收尾

## 9. 一个最常见的面试答法

可以这样答：

`final` 是关键字，可以修饰类、方法、变量，核心是“不能再改”；`finally` 是异常处理结构中的代码块，通常用于资源释放和收尾逻辑；`finalize` 是 `Object` 的方法，早期用来配合垃圾回收做清理，但现在基本不推荐依赖，因为调用时机不确定而且不可靠。

## 10. 当前阶段最容易混的点

最容易混的是：

1. `final` 和 `finally` 根本不是一类东西
2. `finally` 不是关键字修饰符，而是代码块
3. `finalize` 不是异常处理语法
4. `final` 修饰引用，不代表对象内容完全不能变
5. `finalize` 现在基本不作为推荐方案

## 11. 一句话速记

可以这样背：

- `final` 看“不能改”
- `finally` 看“最后执行的收尾块”
- `finalize` 看“旧时代的回收清理方法，现在别依赖”

## 12. 一句话总结

这三个词最容易混，但只要抓住主语义就不难分：`final` 是修饰，`finally` 是收尾，`finalize` 是旧方法。
