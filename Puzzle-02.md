# A Slice of π

```python
π = 355 / 113
print(π)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：3.1415929203539825***


这里有两个令人惊讶的事情：一是 π 是一个有效的标识符，二是 355 / 113 计算为浮点数。

让我们从 π（希腊字母 pi）开始。 Python 3 将源文件的默认编码更改为 UTF-8 并允许使用 Unicode 标识符。

这写起来很有趣，但实际上它会让你的同事的生活更艰难。我可以在我使用的 Vim 编辑器中轻松输入 π；然而，大多数编辑器和 IDE 将需要更多的努力。

我发现 Unicode 标识符有用的一个领域是将数学公式转换为代码。除此之外，坚持使用普通的旧 ASCII。

现在是 355 / 113。Python 3 进行了正确的数学除法。如果你在 Python 2 中尝试这段代码，你会得到 3，因为 Python 2 展示了更多的 C 起源。如果你希望整数除法在 Python 3 中返回 int，请使用 // 运算符（例如，355 // 113）。这在计算指数时很方便，指数必须是整数。

## 进一步阅读

- Python 参考中的标识符和关键字
    http://docs.python.org/3/reference/lexical_analysis.html#identifiers
- PEP 3120：使用 UTF-8 作为默认源编码
    http://python.org/dev/peps/pep-3120/
- PEP 263：定义 Python 源代码编码
    http://python.org/dev/peps/pep-0263/
- Vim 编辑器
    http://vim.org