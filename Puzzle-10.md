# Will It Fit?

```python
a = [1, 2, 3, 4]
a[1:2] = [10, 20, 30]
print(a)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印： [1, 10, 20, 30, 3, 4]***


Python 的切片运算符是半开 (数学中的 [))，这意味着你将从第一个索引到但不包括最后一个索引。 a[1:2] 的大小为 1，但我们为其分配了一个大小为 3 的列表。

分配文档有点难读（如果你有兴趣，请参见下文）。这是摘录（我的剪辑和重点）：

> 如果目标是切片： ... 最后，要求序列对象用指定序列的项目替换切片。切片的长度可能与分配序列的长度不同……

简而言之，当你写 a[1:2] = [10, 20, 30] 就像写 a = a[:1] + [10, 20, 30] + a[2:]。

## 进一步阅读

- Python 参考中的赋值语句
    http://docs.python.org/3/reference/simple_stmts.html#assignment-statements
- Python 的非正式介绍
    http://docs.python.org/3/tutorial/introduction.html
- 切片类型
    http://docs.python.org/3/library/functions.html#slice
- Python 的列表类型
    http://docs.python.org/3/tutorial/datastructures.html#more-on-lists