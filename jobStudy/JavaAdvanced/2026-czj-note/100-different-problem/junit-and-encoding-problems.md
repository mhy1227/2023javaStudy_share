# JUnit 与源码编码问题记录

## 1. `import org.junit.Test;` 爆红

### 现象

代码里已经写了：

```java
import org.junit.Test;
```

但 IDEA 仍然提示：

```text
Cannot resolve symbol 'Test'
```

### 常见原因

1. 没有下载 `JUnit` 相关 jar
2. 已经下载了 jar，但没有加到当前模块依赖
3. IDEA 里有库配置，但当前工程没有有效模块
4. 当前文件所在 `src` 没有被标记为模块源码目录

### 这次遇到的两种真实情况

#### 情况 A：库有了，但模块没有建好

表现：

- `.idea/libraries` 里已经有 `JUnit4-local`
- 但工程缺少 `.iml` 或 `modules.xml`
- 结果是 IDEA 知道“有库”，但不知道“库该挂给哪个模块”

处理：

- 补模块配置
- 把 `src` 声明为源码目录
- 把 `JUnit4-local` 挂到模块依赖

#### 情况 B：模块有了，但模块没有挂 JUnit

表现：

- 已有 `.iml`
- `src` 也已经是源码目录
- 但 `.iml` 里没有 `library` 依赖项

处理：

- 在 IDEA 中进入 `File -> Project Structure -> Modules -> Dependencies`
- 加入：
  - `junit-4.13.2.jar`
  - `hamcrest-core-1.3.jar`

### 结论

`org.junit.Test` 爆红，不一定是没下 jar。很多时候是 IDEA 工程结构不完整，或者依赖没有真正挂到当前模块。

## 2. `Too many characters in character literal`

### 现象

例如下面这种写法会报错：

```java
String s2 = s1.replace('to', 'too');
String s3 = s1.replace('you', 'him');
```

### 原因

Java 里的单引号表示 `char`，只能放一个字符：

```java
'a'
```

像下面这些都属于非法字符字面量：

```java
'to'
'too'
'you'
'him'
```

### 正确写法

要替换字符串片段，必须使用双引号：

```java
String s2 = s1.replace("to", "too");
String s3 = s1.replace("you", "him");
```

## 3. `非法字符` 报错

### 现象

文件内容看起来正常，但 IDEA 或编译器提示：

```text
非法字符
```

### 原因

这类问题往往不是 Java 语法错，而是源码文件编码错。

这次排查发现，出问题的文件是 `UTF-16 LE` 编码，并带有 BOM：

```text
FF FE
```

Java 源文件通常应该使用：

- `UTF-8`
- 最好无 BOM

### 如何判断

如果十六进制开头是：

```text
FF FE
```

并且每个普通字符后面都夹着 `00`，通常就是 `UTF-16 LE`。

### 处理方式

在 IDEA 中：

1. 打开文件
2. 点击右下角编码显示
3. 选择 `Convert to UTF-8`
4. 保存文件

注意：

- 要选 `Convert`
- 不要只选 `Reload`

### 结论

“非法字符” 很多时候是在说“文件编码不对”，不是代码逻辑有问题。

## 4. 这次排障后的经验

以后遇到 Java 文件报错，建议按这个顺序检查：

1. 先看是不是语法写错
2. 再看是不是缺第三方 jar
3. 再看 jar 是否真的挂到了当前模块
4. 再看 `src` 是否被模块接管
5. 最后看文件编码是不是 UTF-8
