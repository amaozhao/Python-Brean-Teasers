# Tell Me the Future

```python
from datetime import datetime

date = datetime(10_000, 1, 1)
print(f'The party started on {date: %B, %d %Y} and lasted a 10 days')
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将引发 ValueError。***


计算机和时间有着复杂的关系。有夏令时、闰年、时区和更多细节需要解决。

计算机将时间存储为自格林威治标准时间 1970 年 1 月 1 日起经过的秒数，称为 Unix 或纪元时间。这意味着在 2038 年，时间将在 32 位机器上溢出。哎哟!

Python 有两个库来处理时间：

- time模块
- 新的闪亮的datetime模块

这个预告片使用了 datetime，它主要是用 C 编写的，并且有固定的空间来存储时间信息。这意味着日期时间有最大值和最小值。

```python
>>> from datetime import datetime
>>> print(datetime.min, datetime.max)
0001-01-01 00:00:00 9999-12-31 23:59:59.999999
```

## 进一步阅读

- 时间模块文档
    http://docs.python.org/3/library/time.html
- 日期时间模块文档
    http://docs.python.org/3/library/datetime.html
- 程序员相信时间的谎言
    http://infiniteundo.com/post/25326999628/falsehoods-programmers-believe-about-time
- 维基百科上的 Unix 时间
    http://en.wikipedia.org/wiki/Unix_time
- 维基百科上的 2038 年问题
    http://en.wikipedia.org/wiki/Year_2038_problem