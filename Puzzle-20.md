# A Divided Time

```python
class timer:
    def __init__(self, name):
        self.name = name
        
        def __enter__(self):
            ...
            
        def __exit__(self, exc_type, exc_value, traceback):
            result = 'OK' if exc_type is None else 'ERROR'
            print(f'{self.name} - {result}')
            return True


with timer('div'):
    1 / 0
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：div - 错误***


你可能希望看到 ZeroDivisionError 异常。

timer 是一个上下文管理器。上下文管理器与 with 语句一起使用，通常用于管理资源。例如， with open('input.txt') 将确保在上下文管理器中的代码完成后文件关闭，即使 with 中的代码引发异常。

Python 标准库中有几种类型可以与 with 语句一起使用：

- 一个文件将被关闭。
- 一个套接字将被关闭。
- 一个 threading.Lock 将被释放。

有一种资源不需要显式管理：内存。 Python 有一个垃圾收集器，可以为你管理内存。

所有其他资源都需要手动管理。例如，如果你忘记关闭文件，你将达到操作系统对打开文件数的限制。一段时间后，你的服务器将因打开文件错误过多而开始出现故障。

一些数据库包也支持 with 语句，但语义不同。如果没有错误，他们将发出 COMMIT；否则，他们将发出 ROLLBACK。

你可以通过使用 \_\_enter\_\_ 和 \_\_exit\_\_ 方法编写一个类（就像我们在预告片中所做的那样）或使用 contextlib.contextmanager 装饰器来实现上下文管理器。

\_\_exit\_\_ 方法在 with 语句中的代码完成时被调用，如果没有异常，它的参数将为 None 。如果 \_\_exit\_\_ 返回 False 值，则异常将传播；否则，异常将被抑制。

大多数 \_\_exit\_\_ 方法不返回值，这在 Python 中意味着它返回 None，其布尔值为 False。

在预告片中，\_\_exit\_\_ 返回 True，抑制 ZeroDivisionError。

哦，第 6 行中的 ... 称为省略号；它是有效的 Python。

## 进一步阅读

- Python 文档中的上下文管理器类型
    http://docs.python.org/3/library/stdtypes.html#typecontextmanager
- PEP 343：“with”声明
    http://python.org/dev/peps/pep-0343/
- 上下文库模块
    http://docs.python.org/3/library/contextlib.html
- 在维基百科上提交
    http://en.wikipedia.org/wiki/Commit_(data_management)
- 在维基百科上回滚
    http://en.wikipedia.org/wiki/Rollback_(data_management)
- Python 文档中的省略号
    http://docs.python.org/3/library/constants.html#Ellipsis