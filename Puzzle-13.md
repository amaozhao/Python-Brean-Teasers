# Identity Crisis

```python
a, b = 12, 3
x = a * b
y = b * a
print(x is y)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：True***


Python 变量是指向 Python 对象的名称。当你有两个变量（比如 x 和 y）时，你可以问两个问题：

*相等*
这些变量指向的对象是否相等？ （== 运算符）

*身份*
这两个变量是否指向同一个对象？ （is 运算符）

由于你对 x 和 y 进行了两次单独的计算，因此你希望它们相等但不相同。一般来说，你是对的。将b的值改为333，重新运行；你将看到 False 作为输出。

你看到 True 的原因是实现细节。由于小数字被大量使用，Python 正在对它们进行实习。

> 以下是文档中的内容：
>
> 当前的实现为 -5 到 256 之间的所有整数保留了一个整数对象数组；当你在该范围内创建 int 时，你实际上只是返回对现有对象的引用。

这意味着 Python 程序中只有一个数字 1 的副本。每个结果为 1 的计算都返回相同的对象。

## 进一步阅读

- PyLong_FromLong 文档
    http://docs.python.org/3/c-api/long.html#c.PyLong_FromLong
- 维基百科上的字符串实习
    http://en.wikipedia.org/wiki/String_interning
- 维基百科上的享元模式
    http://en.wikipedia.org/wiki/Flyweight_pattern