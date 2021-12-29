# A Task to Do

```python
from heapq import heappush, heappop


tasks = []
heappush(tasks, (30, 'work out'))
heappush(tasks, (10, 'wake up'))
heappush(tasks, (20, 0xCAFFE))
heappush(tasks, (20, 'feed cat'))
heappush(tasks, (40, 'write book'))

while tasks:
    _, payload = heappop(tasks)
    print(payload)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将引发 TypeError 异常。***


内置的 heapq 模块在列表上实现了最小堆。

使用堆作为优先队列是很常见的。从堆中推入和删除是 log(N) 操作，并且堆中的第一项（例如，tasks[0]）总是最小的。

为了比较堆中的项目，heapq 使用对象类型中定义的比较（使用 < 运算符，它映射到特定类型的 __lt__ 特殊方法）。任务堆中的对象是元组。 Python 以字典顺序对元组和列表进行排序，非常类似于图书馆中的书籍排序。字典顺序比较前两项，然后是后两项，依此类推。最后，如果所有项都相等，则较长的元组被认为更大。

在第 11 行，你从任务中弹出第一项，即 (10, 'wake up')。将该项从堆中移除后，heapq 会将最小的项移至堆的顶部。有两个候选（20, 'feed cat'）和（20, 0xCAFFE）；由于这些元组中的第一项是相等的，Python 将尝试比较第二项。

> l33t代码
>
> 0xCAFFE 是一个十六进制（基数为 16）的数字。以这种方式书写"English"称为“leet”（或“l33t”）。
> 将“feed cat”（一个 str）与 0xCAFFE（一个 int）进行比较将引发异常。

## 进一步阅读

- heapq 模块
    http://docs.python.org/3/library/heapq.html
- 维基百科上的堆数据结构
    http://en.wikipedia.org/wiki/Heap_(data_structure)
- 维基百科上的字典顺序
    http://en.wikipedia.org/wiki/Lexicographical_order
- 元组和序列
    http://docs.python.org/3/tutorial/datastructures.html#tuples-and-sequences