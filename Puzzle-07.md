# User! Identify Yourself

```python
next_uid = 1


class User:
    def __init__(self, name):
        global next_uid
        self.name = name
        self.__id = next_uid
        next_uid += 1


u = User('daffy')
print(f'name={u.name}, id={u.__id}')
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将引发 AttributeError 异常。***


Python 不像其他语言那样具有私有和受保护的属性（我们开玩笑说 Python 是一种成人同意的语言）。

按照惯例，如果你在属性（或变量）前加上 _（称为下划线），则它们被视为实现细节。你仍然可以访问它们，但作者不认为它们是公共 API 的一部分，可能会在下一个版本中重命名或删除它们。

假设你选择在 User 中使用 _id。现在 User 的所有子类都不能使用自己的 _id 属性，因为它们可能会覆盖 User 中使用的方法的 _id。 Python 提供的解决方案称为名称修改。

让我们来看看 u 的属性。

```python
>>> print(vars(u))  # Also print(u.__dict__)
{'name': 'daffy', '_User__id': 0}
```

\_\_id 被转换成 _User\_\_id。在 User 方法中，你可以使用 \_\_id 并且它会起作用。但是从“外部”，包括子类，这个属性是 _User__id。

这种方法释放了类可以用于非公共属性和方法的名称集。你可以选择一个名称，在它之前添加 __，并确保没有子类会覆盖它。

如果有人真的想要，他们仍然可以打印（u._User__id）并且它会起作用。然而，他们是故意做一些冒险的事情。

名称修改并不是 Python 独有的东西。它也用于 C、Java 和其他语言。有关详细信息，请参阅以下链接。

## 进一步阅读

- Python 文档中的私有变量
    http://docs.python.org/3/tutorial/classes.html#private-variables
- 维基百科上的名称修改
    http://en.wikipedia.org/wiki/Name_mangling
- Raymond Hettinger 的“Python 的类开发工具包”视频
    http://youtube.com/watch?v=HTLu2DFODTg