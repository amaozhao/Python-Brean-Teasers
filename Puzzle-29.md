# Not My Type

```python
def add(a: int, b: int) -> int:
    return a + b


val = add('1', '2')
print(val)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：12***


Python 3 添加了对类型提示的支持。但顾名思义，它们只是提示，不被 Python 解释器强制执行。 Python 对这些提示（有时称为注释）所做的唯一一件事就是将它们作为 \_\_annotations\_\_ 属性添加到函数对象中。

```python
>>> add.__annotations__
{'a': int, 'b': int, 'return': int}
```

随着时间的推移，类型注释变得更加强大。你可以注释变量（例如，答案：int = 42）和属性。有一个专用的打字模块等等。

你可能想知道为什么类型注释如此受欢迎。以下是一些原因：

**正确性**
有一些外部工具，例如 mypy，可以检查类型的正确性。一些团队将 mypy 作为测试套件的一部分。

**文档**
看到像 def current_user(session: dict) → User: 这样的定义，就知道输入输出类型是什么了。

**工装**
一旦工具知道对象的类型，它就会变得更智能。大多数 IDE（例如 PyCharm）使用类型注释来帮助完成。

**代码**
一旦有了注释，就可以编写诸如数据类之类的模块。

回到我们的预告片。你添加了 str 类型的“a”和“b”。 + 运算符，由 \_\_add\_\_ 定义，在 str 中进行连接，例如，'a' + 'b' → 'ab'。

## 进一步阅读

- PEP-3107：函数注释
    http://python.org/dev/peps/pep-3107/
- typing模块
    http://docs.python.org/3/library/typing.html
- 用于轻松创建类的数据类模块
    http://docs.python.org/3/library/dataclasses.html
- PEP 483：类型提示理论
    http://python.org/dev/peps/pep-0483/
- PEP 484：类型提示
    http://python.org/dev/peps/pep-0484/
- mypy 类型检查器（甚至适用于 Python 2 代码）
    http://mypy-lang.org