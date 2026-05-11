# try-with-resources

## 1. 为什么 IO 这块一定会讲它

因为 IO 代码几乎绕不开一件事：

- 资源要关闭

前面在异常那一章已经讲过：

- `finally`

早期很多 IO 代码都是：

- `try-catch-finally`
- 在 `finally` 里关流

但这个写法会比较啰嗦，所以 Java 后面提供了：

- `try-with-resources`

## 2. 什么是 try-with-resources

可以先理解成：

- 在 `try` 语法里直接声明资源，代码结束后自动帮你关闭

最基础的写法：

```java
try (FileInputStream fis = new FileInputStream("D:/test.txt")) {
    int data = fis.read();
    System.out.println(data);
} catch (IOException e) {
    e.printStackTrace();
}
```

这里的重点是：

- 不需要手动再写 `finally` 去关闭 `fis`

## 3. 它比 finally 方案好在哪

可以先总结成 3 点：

1. 代码更简洁
2. 资源关闭更自然
3. 不容易漏关资源

也就是说，它的核心价值是：

- 让资源管理更安全、更省事

## 4. 一个传统写法对比

早期常见写法：

```java
FileInputStream fis = null;
try {
    fis = new FileInputStream("D:/test.txt");
    int data = fis.read();
    System.out.println(data);
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

这个写法的问题不是错，而是：

1. 太长
2. 层次多
3. 容易漏细节

所以如果场景合适，`try-with-resources` 通常更自然。

## 5. 什么资源能写进 try-with-resources

不是所有对象都能直接写进去。

通常要先有一个印象：

- 能被自动关闭的资源，才适合这样用

也就是说，这类资源通常要和：

- `close()`

这件事有关。

当前阶段先记住：

- 各种流对象通常都很适合放进去

例如：

1. `FileInputStream`
2. `FileOutputStream`
3. `FileReader`
4. `FileWriter`
5. `BufferedReader`
6. `BufferedWriter`

## 6. 多个资源怎么写

也可以同时写多个资源：

```java
try (
        FileInputStream fis = new FileInputStream("D:/test.txt");
        FileOutputStream fos = new FileOutputStream("D:/out.txt")
) {
    int data;
    while ((data = fis.read()) != -1) {
        fos.write(data);
    }
} catch (IOException e) {
    e.printStackTrace();
}
```

这个例子可以先理解成：

- 打开输入资源
- 打开输出资源
- 读一边写一边
- 最后统一自动关闭

## 7. 它和异常处理是什么关系

这个点很重要。

`try-with-resources` 并不是不要异常处理了，而是：

- 把资源关闭这件事自动化

但如果中间读写出错，通常还是要：

- `catch`
- 或者继续往外抛

所以可以先记：

- 它解决的是“资源关闭”
- 不是“异常永远不处理”

## 8. 它和 finally 是替代关系吗

可以先粗记：

- 在资源关闭这个场景里，`try-with-resources` 经常比 `finally` 更推荐

但这不代表：

- `finally` 完全没用了

因为有些收尾逻辑不只是关闭资源，还可能有：

- 解锁
- 打日志
- 收尾统计

这些仍然可能会用到 `finally`。

## 9. try-with-resources 这块面试里容易问什么

常见问题有：

1. 它是做什么的
2. 为什么比手写 `finally` 更好
3. 它能解决什么问题
4. 多个资源怎么写
5. 它和异常处理是什么关系

## 10. 当前阶段最容易混的点

1. `try-with-resources` 不是不要 `catch`
2. 它主要解决的是资源自动关闭
3. 它不是所有对象都能随便放进去
4. 它和 `finally` 不是完全对立关系

## 11. 当前阶段最该记住的结论

1. `try-with-resources` 是更现代的资源关闭写法
2. 它在 IO 场景里非常常见
3. 它能减少样板代码
4. 它的核心价值是自动关闭资源

## 12. 一句话总结

`try-with-resources` 最核心的意义，就是让 IO 代码在“资源关闭”这件事上更安全、更简洁。
