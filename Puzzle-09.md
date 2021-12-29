# A Simple Math

```python
print(1.1 * 1.1)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：1.2100000000000002***


你可能已经预料到 1.21，这是正确的数学答案。

一些新开发人员看到这个或类似的输出时，来到留言板说：“我们在 Python 中发现了一个错误！”通常的答案是“阅读精美的手册”（或简称 RTFM）。

> 浮点有点像量子物理学：你看得越近，它就越混乱。
>
> — 格兰特·爱德华兹

这个问题背后的基本思想是浮点数牺牲了速度的准确性（即作弊）。不要感到震惊。这是我们在计算机科学中做了很多的权衡。

你看到的结果符合浮点规范。如果你在 C、Java、Go 中运行相同的代码……你将看到相同的输出。

如果你有兴趣了解有关浮点工作原理的更多信息，请参阅下一节中的链接。你需要记住的主要事情是它们不准确；并且随着数字变大，准确性会变差。

一个含义是，当测试涉及浮点时，你需要检查大致相等并确定可接受的阈值。对于这些情况，内置的 unittest 模块有一个 assertAlmostEqual 方法。在科学的 Python 世界中，numpy 提供了一个多功能的 allclose 函数。

浮点数还有其他一些奇怪之处。例如，有一个特殊的 nan 值（非数字的缩写）。 nan 不等于任何数字，包括它自己。

```python
>>> float('nan') == float('nan')
False
```

要检查值是否为 nan，你需要使用特殊函数，例如 math.isnan。

如果你需要更高的精度，请查看小数模块，它提供正确舍入的十进制浮点运算。

## 进一步阅读

- Python 文档中的“浮点运算：问题和限制”
    http://docs.python.org/3/tutorial/floatingpoint.html
- Julia Evans 的浮点杂志
    http://twitter.com/b0rk/status/986424989648936960
- 每个计算机科学家都应该了解的关于浮点运算的知识
    http://docs.oracle.com/cd/E19957-01/806-3568/ncg_goldberg.html
- 维基百科上的 IEEE 754
    http://en.wikipedia.org/wiki/IEEE_754
- 内置十进制模块
    http://docs.python.org/3/library/decimal.html
- assertAlmostEqual 文档
    http://docs.python.org/3/library/unittest.html#unittest.TestCase.assertAlmostEqual
- numpy 的 allclose
    http://docs.scipy.org/doc/numpy/reference/generated/numpy.allclose.html