# sorted? reversed?

```python
nums = [4, 1, 3, 2]
rev = reversed(nums)
print(sorted(rev) == sorted(rev))
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印： False***


内置的 reversed 函数返回一个迭代器。

Python 的迭代器可以做两件事：

- 返回下一项（通过使用 for 循环或调用内置的 next 函数）
- 通过引发 StopIteration 来表示没有更多项目（我们说迭代器已用完）

第一次调用 sorted(rev) 会消耗迭代器中的所有内容。当你第二次调用 sorted(rev) 时，迭代器将立即引发 StopIteration 并且 sorted 将假定一个空迭代器。

第一个 sorted(rev) 的结果是 [1, 2, 3, 4]，第二个 sorted(rev) 的结果是 []（空列表）。这就是比较返回 False 的原因。

## 进一步阅读

- reversed 文档
    http://docs.python.org/3/library/functions.html#reversed
- “函数式编程HOWTO”迭代器
    http://docs.python.org/3/howto/functional.html#functional-howto-iterators
- Python Wiki 上的迭代器
    http://wiki.python.org/moin/Iterator
- David Beazley 的“系统程序员的生成器技巧”
    http://dabeaz.com/generators/
- 大卫·比兹利的“发电机：最后的前沿”视频
    http://youtube.com/watch?v=D1twn9kLmYg
- itertools 模块代码示例
    http://docs.python.org/3/library/itertools.html
- next 文档
    http://docs.python.org/3/library/functions.html#next