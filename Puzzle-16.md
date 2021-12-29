# Call Me Maybe

```python
from functools import wraps


def metrics(fn):
    ncalls = 0
    name = fn.__name__

	@wraps(fn)
    def wrapper(*args, **kw):
        ncalls += 1
        print(f'{name} called {ncalls} times')

	return wrapper


@metrics
def inc(n):
    return n + 1


inc(3)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将引发 UnboundLocalError 异常。***


当你在 Python 中有一个变量（名称）时（例如，cart = ['lamp']），你可以执行两种操作：

*变异*
更改变量指向的对象（例如，cart.append('mug')）

*重新绑定*
让变量指向另一个对象（例如，cart = ['carrots']）

变异时，变量可以在任何范围内。 但是，当你重新绑定一个变量时，你需要与该变量在同一范围内。

这些范围是什么？ 这是你当前使用的名称的定义位置。 让我们看一个例子：

```python
scale = 1.1


def make_mul(n):
    def mul(val):
        out = val * n * scale
        return out
    return mul


mul7 = make_mul(7)
print(mul7(3))  # 23.1
```

- val 是局部作用域，n 是封闭作用域，scale 是全局作用域。
- out 来自本地范围。

当 Python 看到一个名称（例如 ncalls）时，它会按 LEGB 顺序查找它：

- Local
- Enclosing (closure)
- Global
- Builtin

内置是指内置模块。

> 滥用内置模块
>
> 如果你想定义一些可以从任何模块访问的东西，你可以把它放在内置函数中。 不要那样做。 ☺

由于整数在 Python 中是不可变的，+= 运算符将其左侧的变量重新绑定到一个新的整数对象。 由于 ncalls 来自封闭范围，因此你无法在不更具体的情况下重新绑定它。

Python 2 具有用于重新绑定全局变量的 global 关键字，Python 3 添加了用于重新绑定封闭变量的 nonlocal 关键字。 你可以在此预告片中使用 nonlocal。

```python
from functools import wraps


def metrics(fn):
    ncalls = 0
    name = fn.__name__

    @wraps(fn)
    def wrapper(*args, **kw):
        nonlocal ncalls
        ncalls += 1
        print(f'{name} called {ncalls} times')
        return wrapper


@metrics
def inc(n):
    return n + 1


inc(3)
```

如果你使用的是 Python 2，则执行以下技巧（称为装箱）。

```python
from functools import wraps


def metrics(fn):
    ncalls = [0]
    name = fn.__name__

    @wraps(fn)
    def wrapper(*args, **kw):
        ncalls[0] += 1  
        print(f'{name} called {ncalls[0]} times')
        return wrapper


@metrics
def inc(n):
    return n + 1


inc(3)
```

现在，在第 10 行，你没有重新绑定 ncall；你正在改变它，这没关系。

## 进一步阅读

- Python 文档中的赋值语句
    http://docs.python.org/3/reference/simple_stmts.html#assignment-statements
- PEP 227：静态嵌套作用域
    http://python.org/dev/peps/pep-0227/
- Python 文档中的 Nonlocal 语句
    http://docs.python.org/3/reference/simple_stmts.html#nonlocal
- Python 文档中的全局语句
    http://docs.python.org/3/reference/simple_stmts.html#global
- “Python 中局部变量和全局变量的规则是什么？”在 Python 常见问题解答中
    http://docs.python.org/3/faq/programming.html#what-are-the-rules-for-local-and-global-variables-in-python
- “当变量有值时，为什么我会收到 UnboundLocalError？”在 Python 常见问题解答中
    http://docs.python.org/3/faq/programming.html#why-am-i-getting-an-unboundlocalerror-when-the-variable-has-a-value
- 内置模块
    http://docs.python.org/3/library/builtins.html#module-builtins