# Here Kitty Kitty

```python
pali = 'Was it a cat I saw?'
print(pali[::-1])
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印： ?was I tac a ti saW***

> 回文
>
> “是我看到的猫吗？”是回文。回文可以向后和向前阅读相同的内容。

不，里普利警官，你看到的不是猫。 ☺
这是在 Python 中反转字符串的最佳方法：

pali[::-1] 是一个字符串切片。切片具有开始、停止和步进，每个都是可选的。开始到停止是一个半开区间，这意味着你将从第一个索引到但不包括最后一个索引。此外，如果你指定负停止，它将是从结束的偏移量。

让我们看一些例子：

```python
>>> 'Python'[1:4]  # start & stop
'yth'
>>> 'Python'[1:]  # only start
'ython'
>>> 'Python'[:4]  # only stop
'Pyth'
>>> 'Python'[1:-1] # start & negative stop
'ytho'
>>> 'Python'[::2]  # only step
'Pto'
```

一般来说，步骤必须与停止 - 启动的方向相匹配。例如，'Python'[4:2] 将返回空字符串，这正是你在此预告片中所期望的。 ::-1 是一种特殊情况，将反向工作。

如果你真的想玩转切片，请查看科学的 Python 包，例如将切片提升到另一个层次的 numpy 和 pandas。[1]

## 进一步阅读

- Python 参考中的切片
    http://docs.python.org/3/reference/expressions.html#slicings
- Python 教程中的字符串切片
    http://docs.python.org/3/tutorial/introduction.html#strings
- 切片类
    http://docs.python.org/3/library/functions.html#slice
- Python 2.3“新增功能”中的“扩展切片”
    http://docs.python.org/3/whatsnew/2.3.html#extended-slices
- 科学 Python 文档
    http://docs.scipy.org/doc/numpy/reference/arrays.indexing.html