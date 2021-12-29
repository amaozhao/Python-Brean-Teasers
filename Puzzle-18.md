# Round and Round We Go

```python
print(round(1.5), round(2.5))
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印： 2 2***


四舍五入似乎很容易。 round(1.1) 的计算结果为 1。 round(1.8) 的计算结果为 2。问题是，你如何舍入 .5 数字？你应该四舍五入吗？向下？事实证明，有很多方法可以做到。

Python 3 使用银行家舍入。奇数四舍五入；偶数四舍五入。这种方法背后的原因是，如果你对一个数字列表进行四舍五入，假设奇数和偶数的数量大致相同，误差（四舍五入）将相互抵消。

Python 2 使用一种不同的方法，称为从零开始舍入。如果你在 Python 2 中运行此预告片，你将看到 (2.0, 3.0) 作为输出。

## 进一步阅读

- 维基百科上的四舍五入
    http://en.wikipedia.org/wiki/Rounding
- 内置圆形文档
    http://docs.python.org/3/library/functions.html#round
- 浮点运算：Python 教程中的问题和限制
    http://docs.python.org/3/tutorial/floatingpoint.html#tut-fp-issues