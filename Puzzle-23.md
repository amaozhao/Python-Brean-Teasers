# Path to Nowhere

```python
path = 'c:\path\to\nowhere'
print(path)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

此代码将打印：

```python
c:\path o
owhere
```

Python 字符串中的 \ 用作转义序列来写入特殊字符。 \t 转换为制表符，而 \n 转换为换行符。

还有其他几种方法可以转义字符串中的特殊字符。

```python
s1 = '\x61'  # \x - 2 digits
print(s1)  # a

s2 = '\u2122'  # \u - 4 digits (8482 in hex)
print(s2)  # ™

s3 = '\U00002122'  # \U - 8 digits
print(s3)  # ™

s4 = '\N{trade mark sign}'
print(s4)  # ™
```

如果你想在你的字符串中加一个 \ 怎么办？你可以用另一个\来逃避它。

```python
path = 'c:\\path\\to\\nowhere'
```

> 更简单的方法是使用原始字符串。以下是文档中的内容：
>
> 字符串和字节文字都可以选择以字母“r”或“R”为前缀；此类字符串称为原始字符串，并将反斜杠视为文字字符。

在这种情况下

```python
path = r'c:\path\to\nowhere'
```

原始字符串的两个最常见用例是 Windows 路径（从资源管理器剪切和粘贴时）和定义具有以 \ 开头的特殊字符的正则表达式（例如，\s 表示空格）。

## 进一步阅读

- Python 参考中的字符串和字节文字
    http://docs.python.org/3/reference/lexical_analysis.html#string-and-bytes-literals
- 在 Unicode 表中查找有趣的 Unicode 字符
    http://unicode-table.com/en/
- Python 文档中的正则表达式语法
    http://docs.python.org/3/library/re.html#regular-expression-syntax