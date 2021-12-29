# Highly Valued

```python
a = eval('a = 7')
val = eval('a * 3')
print(val)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将引发 SyntaxError 异常。***


eval 内置函数将 Python 表达式作为字符串并返回其值。

我们倾向于将代码分为两类：

**表达式**
表达式是具有值的东西（例如，5 / 7, 1 < 3）。

**声明**
语句是一种没有值的操作，主要有副作用（例如，a = 3，导入 csv）。

有些语言只有表达式，然后 a = 3 会有一些值（通常是 3）。在 Python 中，我们有表达式和语句。

内置的 eval 函数只适用于表达式，我们传递的参数 (a = 3) 是一个语句。

如果要评估语句，则需要使用内置的 exec 函数。 exec 返回 None，那么如何从 exec 中获取新变量？它只会出现：

```python
>>> exec('answer = 42')
>>> answer
42
```

默认情况下， exec 将更改全局符号。如果你不想污染全局命名空间，你还可以向它传递一个 locals 字典以供使用。

```python
>>> env = {}
>>> exec('answer = 42', None, env)      # ①
>>> env
{'answer': 42}
>>> answer      # ②
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
    NameError: name 'answer' is not defined
```

- ① None 参数用于全局符号表，默认为全局变量
- ② 在全局符号表中找不到答案

eval 为你提供了很多权力，但可能非常危险。如果你评估（或执行）来自用户的随机字符串，可能会发生不好的事情。内置 pickle 和外部 PyYaml 等模块在幕后使用 exec。简而言之，听从特工 Mulder 的建议，“不要相信任何人”。

## 进一步阅读

- eval文档
    http://docs.python.org/3/library/functions.html#eval
- exec文档
    http://docs.python.org/3/library/functions.html#exec
- globals文档
    http://docs.python.org/3/library/functions.html#globals
- Python 文档中的“表达式”
    http://docs.python.org/3/reference/expressions.html#expressions
- Python 文档中的“简单语句”
    http://docs.python.org/3/reference/simple_stmts.html
- 维基百科上的表达
    http://en.wikipedia.org/wiki/Expression_(computer_science)
- 维基百科声明
    http://en.wikipedia.org/wiki/Statement_(computer_science)
- eval 和 exec 的可能用途
    http://github.com/tebeka/ingress
- PyYAML yaml.load(input) 弃用
    http://github.com/yaml/pyyaml/wiki/PyYAML-yaml.load(input)-Deprecation
- pickle 文档中的警告
    http://docs.python.org/3/library/pickle.html#restricting-globals
- XKCD对妈妈的利用
    http://xkcd.com/327/
- 特工穆德
    http://en.wikipedia.org/wiki/Fox_Mulder

## 脚注

[1] http://numpy.org 和 http://pandas.pydata.org