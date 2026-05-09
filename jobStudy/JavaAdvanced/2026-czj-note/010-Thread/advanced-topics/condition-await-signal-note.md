# Condition / await / signal 说明

## 1. 为什么这一份要单独补

只要面试里继续往显式锁方向问，很容易追到：

- `Condition` 是什么？
- `await()` 和 `signal()` 是干什么的？
- 它和 `wait()` / `notify()` 有什么区别？

所以这一份主要补的是：

- `Condition` 的定位
- 它和 `ReentrantLock` 的关系
- 它和 `wait/notify` 的区别

## 2. 先一句话理解 `Condition`

可以先记一个口径：

- `Condition` 可以理解成显式锁体系下的条件等待与唤醒机制

更直白一点说：

- 它像是 `Lock` 体系里的“等待室”

## 3. 为什么会有 `Condition`

前面已经学过：

- `wait()`
- `notify()`
- `notifyAll()`

这些方法是基于：

- 对象监视器

但如果你走的是：

- `ReentrantLock`

这条路线，那大家会希望也有一套更匹配显式锁的等待唤醒方式。

于是就有了：

- `Condition`

## 4. 常见写法怎么理解

最常见的主线是：

```java
Lock lock = new ReentrantLock();
Condition condition = lock.newCondition();
```

然后你会看到：

- `await()`
- `signal()`
- `signalAll()`

你可以粗理解成：

- `await()` 对应等待
- `signal()` 对应唤醒一个
- `signalAll()` 对应唤醒全部

## 5. `await()` 是什么

可以先粗理解成：

- 当前线程先进入等待状态

但它不是乱用的。

通常它要配合：

- `Lock`

一起使用。

## 6. `signal()` 是什么

可以先粗理解成：

- 唤醒一个在当前条件上等待的线程

如果你想和前面知识连起来记，可以对应：

- `notify()`

## 7. `signalAll()` 是什么

可以先粗理解成：

- 唤醒当前条件上所有等待线程

它更像对应：

- `notifyAll()`

## 8. `Condition` 和 `wait/notify` 的关系

这是面试高频。

可以先记最核心的一组对照：

1. `wait/notify` 是基于对象监视器
2. `Condition` 是基于 `Lock` 体系
3. `wait/notify` 更像内置同步配套
4. `Condition` 更像显式锁配套

所以它们解决的问题很像，但所依附的体系不一样。

## 9. 为什么说 `Condition` 更灵活

一个很重要的点是：

- 一个 `Lock` 可以创建多个 `Condition`

这意味着你可以把不同类型的等待线程分开管理。

这比“所有线程都挤在同一个对象监视器等待队列里”更灵活。

所以面试里如果问：

- 为什么 `Condition` 更适合复杂协作场景？

你可以从这里答。

## 10. 它适合什么场景

比较适合的场景通常有：

1. 生产者消费者
2. 多条件协作
3. 需要分组唤醒不同线程

例如：

- 一个条件等“队列非空”
- 另一个条件等“队列未满”

这就是它比传统 `wait/notify` 更好讲的地方。

## 11. 面试里怎么回答“`Condition` 和 `wait/notify` 有什么区别”

可以直接背一版：

`Condition` 可以理解成显式锁体系下的条件等待和唤醒机制，通常配合 `ReentrantLock` 使用；而 `wait/notify` 是基于对象监视器的，通常配合同步代码块使用。它们解决的问题类似，都是线程协作，但 `Condition` 更灵活，因为一个锁可以关联多个条件队列，适合更复杂的线程协作场景。

## 12. 面试里怎么回答“什么时候会用 `Condition`”

可以背一版短的：

如果我只是做简单同步，`synchronized` 加 `wait/notify` 也能解决问题；但如果我已经使用 `ReentrantLock`，而且线程协作比较复杂，比如需要多个等待条件或者分组唤醒，我会更倾向用 `Condition`。

## 13. 当前阶段记忆重点

这一份最少要记住：

1. `Condition` 是显式锁体系下的条件机制
2. `await` / `signal` / `signalAll` 分别对应等待、唤醒一个、唤醒全部
3. 它和 `wait/notify` 解决的问题相似，但体系不同
4. 一个 `Lock` 可以创建多个 `Condition`
5. 它更适合复杂线程协作场景

