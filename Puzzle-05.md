# Send It to the Printer

```python
from threading import Thread
from time import sleep


def printer():
    for i in range(3):
        print(i, end=' ')
        sleep(0.1)


thr = Thread(target=printer, daemon=True)
thr.start()
print()  # Add newline
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：0***

> 输出
>
> 由于线程的不可预测性，此代码可能不会打印任何内容。
> 在第 11 行，你启动了一个守护线程。

> Python文档说
>
> 当没有存活的非守护线程时，整个 Python 程序就会退出。

由于在 print() 行之后没有更多的非守护线程在运行，进程将退出。 打印机将设法打印第一个数字 (0)，然后程序将退出，并删除线程。

如果你看到你的 Python 程序完成了工作，但似乎“卡住了”，这通常表明有一个非守护线程泄漏。

如果你确实想等待一个线程终止，你可以使用线程的 join 方法。

```python
from threading import Thread
from time import sleep


def printer():
    for i in range(3):
        print(i, end=' ')
        sleep(0.1)


thr = Thread(target=printer, daemon=True)
thr.start()
thr.join()
print()  # Add newline
```

## 进一步阅读

- 线程模块
    http://docs.python.org/3/library/threading.html
- Thread.join 文档
    http://docs.python.org/3/library/threading.html#threading.Thread.join