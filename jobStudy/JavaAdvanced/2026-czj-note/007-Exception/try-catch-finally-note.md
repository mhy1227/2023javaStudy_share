# try-catch-finally

## 1. 为什么这一块很重要

异常体系如果只看：

- `Throwable`
- `Error`
- `Exception`
- checked / unchecked

还不够。

因为真正写代码时，最常碰到的还是：

- 怎么 `try`
- 怎么 `catch`
- `finally` 到底什么时候执行

而且这一块在面试里非常高频，尤其喜欢问：

1. `try-catch-finally` 的执行顺序
2. `return` 和 `finally` 谁先谁后
3. `finally` 一定会执行吗
4. 能不能吞异常

## 2. 最基础的结构

最常见写法：

```java
try {
    System.out.println("try");
} catch (Exception e) {
    System.out.println("catch");
} finally {
    System.out.println("finally");
}
```

可以先记：

1. `try` 放可能出异常的代码
2. `catch` 负责捕获和处理异常
3. `finally` 负责收尾

## 3. 执行顺序怎么理解

### 情况一：没有异常

执行顺序通常是：

1. `try`
2. `finally`

### 情况二：有异常，而且被 catch 到

执行顺序通常是：

1. `try`
2. `catch`
3. `finally`

### 情况三：有异常，但没有被 catch 到

执行顺序通常是：

1. `try`
2. `finally`
3. 异常继续往外抛

所以可以先有个总体印象：

- `finally` 更像最后的收尾动作

## 4. finally 一定会执行吗

面试里更稳的说法不是：

- 一定会执行

而是：

- 在正常控制流下，`finally` 通常都会执行

但一些极端情况除外，例如：

1. JVM 直接退出
2. 进程被强制终止
3. 机器宕机

所以不要答得太绝对。

## 5. finally 最常拿来做什么

最典型的是：

1. 关闭文件流
2. 关闭数据库连接
3. 关闭网络连接
4. 释放锁
5. 做统一收尾

也就是说：

- `finally` 最重要的语义是资源收尾

## 6. 一个最容易考的点：try 里有 return 会怎样

示例：

```java
public int test() {
    try {
        return 1;
    } finally {
        System.out.println("finally");
    }
}
```

执行时：

- `finally` 还是会先执行

但最终返回值仍然是：

- `1`

所以更稳的说法是：

- `return` 并不会让 `finally` 失效

## 7. finally 里也有 return 会怎样

示例：

```java
public int test() {
    try {
        return 1;
    } finally {
        return 2;
    }
}
```

这个例子最终返回的是：

- `2`

也就是说：

- `finally` 里的 `return` 会覆盖前面的返回结果

这也是为什么实际开发里通常不建议：

- 在 `finally` 里写 `return`

## 8. 一个更完整的执行例子

```java
public int test() {
    try {
        int a = 10 / 0;
        return 1;
    } catch (ArithmeticException e) {
        return 2;
    } finally {
        System.out.println("finally");
    }
}
```

执行过程可以这样理解：

1. 先进入 `try`
2. 发生除零异常
3. 进入 `catch`
4. 准备返回 `2`
5. 在真正返回前，先执行 `finally`

最终返回：

- `2`

## 9. catch 应该注意什么

### 9.1 不要乱吞异常

下面这种写法很危险：

```java
try {
    // ...
} catch (Exception e) {
}
```

问题在于：

1. 异常被吞掉了
2. 没日志
3. 没上下文
4. 排查问题会很难

### 9.2 catch 不要过大

例如一上来就：

```java
catch (Exception e)
```

有时候太粗了。

更稳的思路是：

1. 能按具体异常分就尽量分
2. 真要兜底，也要说清楚原因

### 9.3 不是所有异常都该在当前层处理

有些层级其实处理不了异常，例如：

- DAO 层遇到数据库异常

很多时候更合理的方式不是：

- 吃掉异常然后返回 `null`

而是：

- 记录必要信息
- 包装后往上抛

## 10. finally 和资源释放的关系

早期常见写法是：

```java
FileInputStream fis = null;
try {
    fis = new FileInputStream("D:/test.txt");
} catch (IOException e) {
    e.printStackTrace();
} finally {
    if (fis != null) {
        try {
            fis.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

这个写法的重点是：

- 无论前面成功还是失败，最后都尽量把资源关掉

当然，现代 Java 里后面还会继续补：

- `try-with-resources`

## 11. 面试里怎么答更稳

可以这样答：

`try-catch-finally` 里，`try` 放可能抛异常的代码，`catch` 负责捕获和处理，`finally` 负责收尾和资源释放。正常情况下，`finally` 通常都会执行，即使 `try` 或 `catch` 里有 `return`，也会先执行 `finally`。但是如果 `finally` 里自己也写了 `return`，它会覆盖前面的返回结果，所以实际开发里通常不建议这么写。

## 12. 当前阶段最容易混的点

1. `finally` 不是绝对 100% 执行
2. `try` 里有 `return`，`finally` 通常还是会执行
3. `finally` 里有 `return` 会覆盖前面的结果
4. `catch (Exception e) {}` 这种吞异常写法不规范
5. 不是所有异常都应该在当前层直接处理

## 13. 当前阶段最该记住的结论

1. `finally` 的核心语义是收尾
2. `return` 不会直接跳过 `finally`
3. `finally` 里尽量不要写 `return`
4. 不能乱吞异常
5. 资源释放是 `finally` 的经典应用场景

## 14. 一句话总结

`try-catch-finally` 真正要掌握的，不只是语法，而是执行顺序、返回值覆盖、资源释放和异常处理边界。

## 15. 外部参考

1. 牛客：Java面试题  
   https://www.nowcoder.com/discuss/353149105474052096
2. 牛客：40道Java基础常见面试题及详细答案  
   https://www.nowcoder.com/discuss/353159104325689344
3. 牛客：Java异常处理详解  
   https://www.nowcoder.com/discuss/353149494940344320
4. LeetCode：Most Common Interview Question asked related to Exception Handling in Java  
   https://leetcode.com/discuss/post/4430844/Most-Common-Interview-Question-asked-related-to-Exception-Handling-in-Java/
