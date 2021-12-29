# Click the Button

```python
display = []
buttons = []
for n in range(10):
    # A button is a function called when user clicks on it
    buttons.append(lambda: display.append(n))

btn = buttons[3]
btn()
print(display)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：[9]***


你可能期望 [3]，因为每个 lambda 都会附加它的 n 来显示。

但是，每个 lambda 使用的 n 与第 3 行中定义的 n 相同。这种类型的变量绑定称为闭包。

你有两种选择来修复此错误。 第一个，也是我的偏好，是有一个 make_button(n) 函数。

```python
display = []
buttons = []


def make_button(n):
    return lambda: display.append(n)


for n in range(10):
    # A button is a function called when user clicks on it
    buttons.append(make_button(n))

btn = buttons[3]
btn()
print(display)
```

第二种解决方案是利用默认函数参数在函数创建时评估一次的事实。

```python
display = []
buttons = []
for n in range(10):
    # A button is a function called when user clicks on it
    buttons.append(lambda n=n: display.append(n))  # <1>

btn = buttons[3]
btn()
print(display)
```

n=n 定义了一个函数参数，从外部作用域遮蔽 n。

## 进一步阅读

- PEP 227：静态嵌套作用域
    http://python.org/dev/peps/pep-0227/
- PEP 3104：访问外部作用域中的名称
    http://python.org/dev/peps/pep-3104/
- 维基百科的闭包
    http://en.wikipedia.org/wiki/Closure_(computer_programming)
- 维基百科上的变量阴影
    http://en.wikipedia.org/wiki/Variable_shadowing