# Attention Seeker

```python
class Seeker:
    def __getattribute__(self, name):
        if name not in self.__dict__:
            return '<not found>'
        return self.__dict__[name]


s = Seeker()
print(s.id)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将引发 RecursionError 异常。***


当你编写 s.id 时，Python 会进行属性查找（参见谜题 1、谜题 1、玩家一号）。 Python 定义了几个钩子来绕过通常的属性查找算法。两个主要选项是 \_\_getattr\_\_ 和 \_\_getattribute\_\_。

> 其他选项
>
> 还有其他几种修改属性访问的方法，例如静态方法、类方法、属性、描述符等。

\_\_getattr\_\_ 在常规属性查找失败时被调用，它通常是你应该使用的。 \_\_getattribute\_\_ 绕过属性查找并让你完全控制。

> 拥有权利的同时也被赋予了重大的责任。
>
> -- 本叔叔

由于 \_\_getattribute\_\_ 绕过了属性查找，第 3 行中的代码 self.\_\_dict\_\_ 将再次调用 \_\_getattribute\_\_，你将陷入无限递归。 Python 可以防止无限递归。一旦调用堆栈大小超过 sys.getrecursionlimit() 将引发 RecursionError。这就是你在此急转弯中看到的内容。

你可以使用 sys.setrecursionlimt 增加递归限制。除非你有很好的理由，否则不要这样做。

Python 中的字典为 \_\_getattr\_\_ 提供了一个类似的钩子，称为 \_\_missing\_\_。你可以使用 \_\_missing\_\_ 实现 collections.defaultdict 等。

## 进一步阅读

- 类实例
    http://docs.python.org/3/reference/datamodel.html#index-49
- Python 参考中的“自定义属性访问”
    http://docs.python.org/3/reference/datamodel.html#customizing-attribute-access
- Python 文档中的“描述符操作指南”
    http://docs.python.org/3/howto/descriptor.html
- \_\_getattr\_\_ 文档
    http://docs.python.org/3/reference/datamodel.html#object.__getattr__
- \_\_getattribute\_\_ 文档
    http://docs.python.org/3/reference/datamodel.html#object.__getattribute__)
- \_\_missing\_\_ 文档
    http://docs.python.org/3/reference/datamodel.html#object.__missing__
- collections.defaultdict 文档
    http://docs.python.org/3/library/collections.html#collections.defaultdict