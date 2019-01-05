# PowerShell字符串太长怎么办

平时遇到的`PowerShell`字符串的问题有两种情况

## 1. 单行字符串太长

```PowerShell
$str = "It's a very very very very very very very long string"
```

可以通过字符串拼接的方法解决这个问题：

```PowerShell
$str = "It's a very very very very " +
       "very very very long string"
```

## 2. 带换行符的字符串

我们有四种方法可以实现这个功能。

### 方法一：`\r\n`

```PowerShell
"Hello`r`nWorld"
```

### 方法二：占位符

```PowerShell
"Hello{0}World" -f [environment]::NewLine
```

### 方法三：定义字符串的时候直接换行

```PowerShell
"Hello
World"
```

### 方法四：`Here-String`

```PowerShell
@"
Hello
World
"@
```

这么多方法，总有一个适合你。
