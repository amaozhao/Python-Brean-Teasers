# Ready Player One

```python
class Player:
    # Number of players in the Game
    count = 0
    
    def __init__(self, name):
        self.name = name
        self.count += 1
    
p1 = Player('Parzival')
print(Player.count)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：0***


当你编写 self.count 时，你正在执行属性查找。 在这种情况下，你要查找的属性是计数。

在 Python 中获取属性是一项复杂的操作。 几乎每个 Python 对象都将其属性存储在名为 \_\_dict\_\_ 的字典中。 Python 将首先尝试在实例字典中查找属性，然后在实例的类 (\_\_class\_\_) 字典中，然后向上继承层次结构 (\_\_mro\_\_)。 最后，如果找不到你要查找的属性，Python 将引发 AttributeError。

> 属性查找
>
> Python 的属性查找实际上比前面的解释更复杂。 一些对象，如 C 扩展和带有 \_\_slots\_\_ 的类没有 \_\_dict\_\_，还有描述符、\_\_getattribute\_\_ 特殊方法和其他特殊情况。

下面是这个算法的可能代码，它由内置的 getattr 在 Python 中实现：

```python
def get_attr(obj, name):
    """Emulate built in getattr"""
    if name in obj.__dict__:
        print(f'found {name} in obj')
        return obj.__dict__[name]
    if name in obj.__class__.__dict__:
        print(f'found {name} in class')
        return obj.__class__.__dict__[name]
    for cls in obj.__class__.__mro__:
        if name in cls.__dict__:
            print(f'found {name} in {cls.__name__}')
            return cls.__dict__[name]
    raise AttributeError(name)
```

当你在急转弯中执行 self.count += 1 时会发生什么？ Python 会将其转换为 self.count = self.count + 1。然后它会使用 getattr(self, count) 并获取 Player 中定义的值为 0 的计数。一旦 Python 具有 self.count + 的值1 = 1 在赋值 (=) 的右侧，它会调用 setattr(self, count, 1)。 setattr 将在 self.\_\_dict\_\_ 中创建一个新条目，它将影响 Player 中的计数。

最后，你打印 Player.count，它仍然是 0。如果你打印 p1.count，你将得到 1。

## 进一步阅读

- 类实例
    http://docs.python.org/3/reference/datamodel.html#index-49
- 特殊属性
    http://docs.python.org/3/library/stdtypes.html#special-attributes
- Python 的类开发工具包（Raymond Hettinger 提供的视频）
    http://youtube.com/watch?v=HTLu2DFODTg
- 自定义模块属性访问
    http://docs.python.org/3/reference/datamodel.html#customizing-module-attribute-access
- 维基百科上的变量阴影
    http://en.wikipedia.org/wiki/Variable_shadowing
- getattr 文档
    http://docs.python.org/3/library/functions.html#getattr