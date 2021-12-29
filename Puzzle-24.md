# 12 Angry Men

```python
from concurrent.futures import ProcessPoolExecutor
from itertools import repeat

guilty = 0


def juror():
    global guilty

guilty += 1


with ProcessPoolExecutor() as pool:
    for _ in repeat(None, 12):
        pool.submit(juror)
        
print(guilty)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：0***


线程和进程都是并发工作单元。主要区别在于线程共享相同的内存空间而进程不共享。

这意味着如果你有一个全局变量（例如，有罪的），同一进程中的所有线程都可以访问和修改它。而在进程中，你需要以某种方式（例如，套接字）在进程之间通信数据。

此急转弯使用 ProcessPoolExecutor，这意味着代码在不同的进程中执行。每个陪审员都会更改自己的有罪副本。

线程允许更快地访问共享数据，但它们更危险。 Python 中的所有内置类型（例如，列表、字典等）都不是线程安全的。如果你同时更改（即变异）来自两个线程的列表，则行为未定义。你需要使用 threading.Lock 来保护一次只有一个线程更改列表。

使所有内置类型成为线程安全的会使它们变慢，并且大多数 Python 代码仍然在单个线程中运行。这就是为什么内置类型在近期（或远期）不会是线程安全的。

什么时候应该使用线程，什么时候应该使用进程？经验法则是，如果你有受 CPU 限制的代码，则应该使用进程，如果你有受 I/O 限制的代码，则应该使用线程。

在转向线程或进程之前，请记住并行化对你的帮助是有限的，并且编写此类代码比编写顺序代码要困难得多。

## 进一步阅读

- concurrent.futures 模块
    http://docs.python.org/3/library/concurrent.futures.html
- 维基百科上的阿姆达尔定律
    http://en.wikipedia.org/wiki/Amdahl%27s_law
- 维基百科上的 I/O 绑定
    http://en.wikipedia.org/wiki/I/O_bound
- 维基百科上的 CPU 限制
    http://en.wikipedia.org/wiki/CPU-bound
- Python Lock 文档
    http://docs.python.org/3/library/threading.html#lock-objects
- Raymond Hettinger 的“使用重复超出范围”
    http://twitter.com/raymondh/status/1144527183341375488?lang=en