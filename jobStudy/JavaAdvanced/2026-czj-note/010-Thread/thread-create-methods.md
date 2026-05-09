# 线程创建方式与常见缺漏点

## 1. 这一份主要解决什么

这一份主要解决三个问题：

1. Java 里线程怎么写
2. 线程到底怎么启动
3. 面试里这一块最容易漏什么

也就是说，这一份不是只贴代码，而是把“写法 + 原理 + 常见追问”放在一起。

## 2. Java 里创建线程的常见方式

最常见的回答通常是这几种：

1. 继承 `Thread`
2. 实现 `Runnable`
3. 实现 `Callable`
4. 配合 `FutureTask`
5. 线程池提交任务

## 3. 第一种：继承 `Thread`

### 3.1 基本写法

```java
class MyThread extends Thread {
    @Override
    public void run() {
        System.out.println("thread is running");
    }
}

public class Demo {
    public static void main(String[] args) {
        MyThread t = new MyThread();
        t.start();
    }
}
```

### 3.2 这一种怎么理解

这种方式最直观，适合入门时理解线程启动流程。

核心点：

- 重写的是 `run()`
- 真正启动线程要调用的是 `start()`

### 3.3 这一种的缺点

1. Java 是单继承，继承了 `Thread` 后就不能再继承别的类
2. 任务和线程对象耦合得比较紧
3. 实际开发里通常不是最推荐方式

## 4. 第二种：实现 `Runnable`

### 4.1 基本写法

```java
class MyRunnable implements Runnable {
    @Override
    public void run() {
        System.out.println("runnable is running");
    }
}

public class Demo {
    public static void main(String[] args) {
        Thread t = new Thread(new MyRunnable());
        t.start();
    }
}
```

### 4.2 为什么这一种更常用

因为它把：

- 线程对象
- 任务逻辑

拆开了。

这样更符合面向对象里的组合思想，也避免占用单继承。

### 4.3 面试里怎么说

可以说：

实际开发里，相比直接继承 `Thread`，更常见的是实现 `Runnable`，因为任务和线程解耦了，也更灵活。

## 5. 第三种：实现 `Callable`

### 5.1 基本写法

```java
class MyCallable implements Callable<Integer> {
    @Override
    public Integer call() {
        return 100;
    }
}
```

### 5.2 这一种和 `Runnable` 的区别

`Callable` 和 `Runnable` 最大的区别：

1. `Callable` 可以有返回值
2. `Callable` 可以抛出受检异常
3. `Runnable` 的 `run()` 没有返回值

## 6. 第四种：配合 `FutureTask`

### 6.1 基本写法

```java
class MyCallable implements Callable<Integer> {
    @Override
    public Integer call() {
        return 100;
    }
}

public class Demo {
    public static void main(String[] args) throws Exception {
        FutureTask<Integer> futureTask = new FutureTask<>(new MyCallable());
        Thread t = new Thread(futureTask);
        t.start();
        Integer result = futureTask.get();
        System.out.println(result);
    }
}
```

### 6.2 这一种适合回答什么

这适合回答：

- 线程任务如果需要返回结果怎么办
- `Callable` 怎么真正跑起来

## 7. 第五种：线程池提交任务

### 7.1 基本写法

```java
ExecutorService executorService = Executors.newFixedThreadPool(3);

executorService.submit(() -> {
    System.out.println("task running");
});

executorService.shutdown();
```

### 7.2 为什么这在实际开发里更常见

因为项目里通常不会手动频繁 `new Thread()`。

更常见的方式是：

- 把任务交给线程池统一管理

这样更方便控制：

- 线程数量
- 任务队列
- 资源消耗

## 8. `run()` 和 `start()` 的区别

这是必问题。

### 8.1 `run()`

`run()` 只是普通方法调用。

如果你直接写：

```java
t.run();
```

那本质上还是当前线程在执行，不会真正启动新的线程。

### 8.2 `start()`

`start()` 才会真正启动一个新线程，然后由新线程去执行 `run()` 方法里的逻辑。

### 8.3 面试里的标准主线

可以这样说：

`run()` 只是线程执行逻辑的方法体，本身像普通方法调用；`start()` 才是真正启动线程的方法，调用后会由 JVM 和操作系统配合创建新的执行路径，再去执行 `run()`。

## 9. `Runnable` 和 `Callable` 的区别

高频回答主线：

1. `Runnable` 没有返回值，`Callable` 有返回值
2. `Runnable` 不能直接抛受检异常，`Callable` 可以
3. `Callable` 通常配合 `Future` 或 `FutureTask` 使用

## 10. 实际开发里更推荐哪种

如果是面试回答，建议这样分层：

1. 入门演示可以用继承 `Thread`
2. 一般代码更推荐 `Runnable`
3. 需要返回结果时用 `Callable`
4. 生产环境里更推荐线程池，而不是手动频繁创建线程

## 11. 这一块最容易漏的点

### 11.1 只会写继承 `Thread`

很多人一说线程创建，就只会这一种。

这太单薄了。

至少要能继续补：

- `Runnable`
- `Callable`
- 线程池

### 11.2 说不清 `run()` 和 `start()`

这是非常高频的追问。

如果这一点说不清，线程基础会显得不扎实。

### 11.3 只会写代码，不会讲为什么不推荐直接 `new Thread()`

需要补充：

- 创建和销毁线程有成本
- 线程太多会造成调度压力
- 实际项目里更常交给线程池管理

### 11.4 只会说“实现 Runnable 更好”，但说不出为什么

至少要能补一句：

- 避免单继承限制
- 任务和线程对象解耦

## 12. 面试里怎么回答“线程怎么创建”

可以这样答：

Java 里创建线程常见有几种方式：继承 `Thread`、实现 `Runnable`、实现 `Callable` 并配合 `FutureTask`，以及通过线程池提交任务。面试里如果问基础写法，我会先举 `Thread` 和 `Runnable`；如果问实际开发，我会补充更常用的是线程池，因为手动频繁创建线程成本高，也不方便统一管理。

## 13. 当前阶段最该记住的结论

1. 线程创建不止一种方式
2. `start()` 才是真正启动线程，`run()` 只是方法体
3. `Runnable` 更适合解耦任务和线程
4. `Callable` 适合有返回值的任务
5. 实际开发里通常更推荐线程池

## 14. 一句话总结

线程创建这一块，不只是会写几段代码，而是要能讲清楚：有哪些方式、各自适合什么场景、为什么 `start()` 和 `run()` 不一样，以及为什么生产环境更推荐线程池。
