# Endgame

```python
avengers = ['Bruce', 'Carol', 'Natasha', 'Tony']
idx = 3
avengers[idx], idx = 'Peter', 2
print(avengers)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印： ['Bruce', 'Carol', 'Natasha', 'Peter']***


你正在执行多项任务，也称为拆包。 在第 3 行中，Python 将首先从左到右计算 = 的右侧，然后再分配到左侧，再次从左到右。

在 avengers[idx], idx = 'Peter', 2 行中，Python 首先计算 avengers[idx] = 'Peter'。 由于 idx 在这里仍然是 3，因此列表中的第四项 Tony 正在被替换。 然后 Python 将赋值 idx = 2。

这是令人困惑的并且被认为是不好的做法。 不要这样做。

## 进一步阅读

- PEP 3132：扩展的可迭代解包
    http://python.org/dev/peps/pep-3132/
- PEP 448：额外的解包概括
    http://python.org/dev/peps/pep-0448/
- Python 参考中的求值顺序
    http://docs.python.org/3/reference/expressions.html#evaluation-order