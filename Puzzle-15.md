# Where’s Waldo?

```python
name = 'Waldo'
text = 'Can you find where Wally is?'

if text.find(name):
    print('Found Waldo')
else:
    print('Cannot find Waldo')
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：找到 Waldo***

> str.find 文档说
>
> 如果未找到 sub 则返回 -1。

我们在 Python 中有两个布尔值：True 和 False。他们并不总是在那里；它们是在 Python 2.3 中添加的。

没有 True 和 False 怎么做逻辑运算？有规则！一切都是真的，除了

- 0 个数字：0, 0.0, 0+0j, ...
- 空collections：[], {}, ”, ...
- None
- False

你可以使用内置的 bool 函数测试 Python 对象的真值。

回到急转弯，text.find(name) 返回-1，-1 的布尔值为True。

如果要检查字符串是否包含另一个字符串，请使用 in 运算符：

```python
if name in text:
    print('Found Waldo')
else:
    print('Cannot find Waldo')
```

这将打印无法找到 Waldo。

如果要为对象定义布尔逻辑，请实现 \_\_bool\_\_ 特殊方法。

## 进一步阅读

- str.find 文档
    http://docs.python.org/3/library/stdtypes.html#str.find
- PEP 285：添加 bool 类型
    http://python.org/dev/peps/pep-0285/
- Python 文档中的“真值测试”
    http://docs.python.org/3/library/stdtypes.html#truth-value-testing
- \_\_bool\_\_ 文档
    http://docs.python.org/3/reference/datamodel.html#object.__bool__