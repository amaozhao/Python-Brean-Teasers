# Look at the Pretty Colors

```python
colors = [
    'red',
    'green'
    'blue'
]

print(colors)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：['red', 'greenblue']***


Python 对空格的使用在编程语言中非常独特。有些人不喜欢它。我个人认为它使代码更具可读性。

> Python文档说
>
> 一条逻辑线是由一条或多条物理线按照显式或隐式连接规则构成的。

等等

圆括号、方括号或花括号中的表达式可以拆分为多个物理行，而无需使用反斜杠。

意思是

- ’a’ ’b’ is not valid.
- (’a’, ’b’) is a tuple (’a’, ’b’ is also a tuple).
- (’a’ ’b’) is the string ’ab’.

在急转弯中，“green”和“blue”之间缺少一个 , Python 会将它们连接在一起作为“greenblue”。

这就是为什么在编写颜色等表达式时应该使用悬空逗号的原因：

```python
colors = [
    'red',
    'green',
    'blue',  # ← A dangling comma
]
```

它不仅可以使你免于错误，在代码审查中，如果你添加另一种颜色，则只会更改一行。遗憾的是，并非每种语言或格式都允许使用悬空逗号。我在看着你 JSON 和 SQL。

> 黑色的
>
> 你可以在 IDE 中使用黑色代码格式化程序。它将格式化你的代码并添加悬空逗号。

你可以使用此隐式行连接使你的代码更清晰。这是 matplotlib 文档中的一个示例：

```python
plot(x, y, color='green', marker='o', linestyle='dashed', linewidth=2, markersize=12)
```

写成:

```python
plot(
    x, y,
    color='green',
    marker='o', markersize=12,
    linestyle='dashed', linewidth=2,
)
```

你甚至可以用 () 包围你的代码并进行方法链接：

```python
(
    df[df['passenger_count'] > 1]  # rides with more than 1
    ['tpep_pickup_datetime'].dt.hour  # extract hour
    .value_counts()  # count hours
    .sort_index()  # sort by hour
    .plot.bar(rot=45, title='11am rides')  # plot with 45° axis labels
)
```

## 进一步阅读

- Python 参考中的线条结构
    http://docs.python.org/3/reference/lexical_analysis.html#line-structure
- 何时在“Python 风格指南”（又名 PEP 8）中使用尾随逗号
    http://python.org/dev/peps/pep-0008/#id29
- Python Wiki 上的元组语法
    http://wiki.python.org/moin/TupleSyntax
- 戴夫·切尼（Dave Cheney）的“结尾逗号”
    http://dave.cheney.net/2014/10/04/that-trailing-comma
- Matplotlib 文档
    http://matplotlib.org
- Black Code Formatter
    http://black.readthedocs.io