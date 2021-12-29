# Loop de Loop

```python
for n in range(5):
    print(n, end=' ')
    n = 5
print()
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：0 1 2 3 4***


Python 的 for 循环是“for each”。 Python 中的迭代涉及两种类型：

*可迭代的*
我们正在迭代的对象（例如，str、list、dict……）

*迭代器*
是否进行实际迭代；只能获取下一项并通过引发 StopIteration 来表示它已完成（即耗尽）

下面是 for 循环的内幕。

```python
iterable = range(5)  # range is the iterable
iterator = iter(iterable)  # extract iterator from iterable
while True:
    try:
        n = next(iterator)
        # Code inside "for" loop
        print(n, end=' ')
        n = 5  # Will be overridden by line 5 in next iteration
    except StopIteration:  # iterator signaled it's exhausted
        break
print()  # Code after "for" loop
```

从这段代码中，很清楚为什么 n = 5 不会停止 for 循环。

你可以通过创建一个实现两个方法的类来为你自己的类型创建迭代器：\_\_next\_\_ 和 \_\_iter\_\_。你的可迭代类型应该实现返回迭代器的 \_\_iter\_\_。

或者……你可以选择更简单的路径并实现生成器。

## 进一步阅读

- \_\_next\_\_ 文档
    http://docs.python.org/3/library/stdtypes.html#iterator.__next__
- \_\_iter\_\_ 文档
    http://docs.python.org/3/library/stdtypes.html#iterator.__iter__
- Python 文档中的迭代器类型
    http://docs.python.org/3/library/stdtypes.html#iterator-types
- Python Wiki 上的生成器
    http://wiki.python.org/moin/Generators
- David Beazley 的“系统程序员的生成器技巧”
    http://dabeaz.com/generators/
- itertools 模块代码示例
    http://docs.python.org/3/library/itertools.html