# An Inside Job

```python
def add_n(items, n):
    items += range(n)


items = [1]
add_n(items, 3)
print(items)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：[1, 0, 1, 2]***


在谜题 16，呼叫我也许谜题中，我们讨论了重新绑定与变异。大多数情况下，items += range(n) 被转换为 items = items + range(n)，这是重新绑定。

在某些情况下，对 += 进行了特殊优化。这是文档所说的（我的重点）：

> 像 x += 1 这样的增强赋值表达式可以重写为 x = x + 1 以获得类似但不完全相等的效果。在增强版本中，x 只计算一次。此外，在可能的情况下，实际操作会在原地执行，这意味着不是创建新对象并将其分配给目标，而是修改旧对象。

类型定义了 + 运算符与 \_\_add\_\_ 特殊方法的行为方式，并且可以将 \_\_iadd\_\_ 定义为 += 的特殊情况。文档说

> 调用这些方法来实现增广算术赋值（+=、-=、=、@=、/=、//=、%=、*=、<⇐、>>=、&=、^=、|= ）。这些方法应该尝试就地执行操作（修改 self）并返回结果（可以是但不一定是 self）。如果未定义特定方法，则增广赋值回退到正常方法。

内置的列表对象定义了\_\_iadd\_\_，它调用了extend 方法。

如果将 add_n 中的代码更改为 items = items + range(n) 会发生什么？你会得到一个异常：TypeError: can only concatenate list (not "range") to list。

在 Python 3 中，内置的 range 函数返回一个 range 对象。即使它看起来像一个列表（len、[] 和朋友都可以），你也无法将其添加到列表中。

如果你想让重新绑定代码工作，你需要写 items = items + list(range(n)) 然后输出将是 [1]。

作为一般规则，尽量不要改变传递给函数的对象。这种编程风格称为函数式编程。功能代码更容易测试和推理。试一试。很有趣。

## 进一步阅读

- 维基百科上的函数式编程
    http://en.wikipedia.org/wiki/Functional_programming
- 内置范围文档
    http://docs.python.org/3/library/functions.html#func-range
- Python 参考中的“增强赋值语句”
    http://docs.python.org/3/reference/simple_stmts.html#augmented-assignment-statements
- Python 文档中的“函数式编程 HOWTO”
    http://docs.python.org/3/howto/functional.html
- \_\_iadd\_\_ 文档
    http://docs.python.org/3/reference/datamodel.html#object.__iadd__
- Python 文档中的“更多列表”
    http://docs.python.org/3/tutorial/datastructures.html#more-on-lists