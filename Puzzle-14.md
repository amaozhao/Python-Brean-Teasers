# The Great Divide

```python
def div(a, b):
    return a / b


if div(1, 2) > 0 or div(1, 0) > 0:
    print('OK')
else:
    print('oopsie')
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：OK***


由于 div(1, 0)，你可能希望此代码引发 ZeroDivisionErro。

如果你自己调用 div(1, 0) ，你会看到异常。然而，Python 中的逻辑运算符和和或是短路运算符。

> 以下是文档中关于and的内容 ：
>
> 这是一个短路运算符，因此它仅在第一个参数为假时才计算第二个参数。

相比之下，函数调用的所有参数都在调用函数之前进行评估。这意味着你不能编写自己的 my_and 函数，该函数的行为与内置 and 类似。

你可以充分利用这一点。假设你希望仅当用户不在会话中时才从数据库加载当前用户（慢速操作）。

```python
user = session.get('user') or load_current_user()
```

仅当 session.get('user') 返回 None （在 Python 中为 False）时才会调用 load_current_user()。

如果你写

```python
user = session.get('user', load_current_user())
```

然后 load_current_user() 每次都会被调用，即使用户在会话中。

## 进一步阅读

- Python 文档中的“布尔运算——与、或、非”
    http://docs.python.org/3/library/stdtypes.html#boolean-operations-and-or-not
- 维基百科上的短路评估
    http://en.wikipedia.org/wiki/Short-circuit_evaluation