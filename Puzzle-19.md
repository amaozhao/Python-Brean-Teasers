# TF (Without IDF)

```python
import re
from collections import defaultdict


def word_freq(text, freqs=defaultdict(int)):
    """Calculate word frequency in text. freqs are previous frequencies"""
    for word in [w.lower() for w in re.findall(r'\w+', text)]:
        freqs[word] += 1
    return freqs


freqs1 = word_freq('Duck season. Duck!')
freqs2 = word_freq('Rabbit season. Rabbit!')
print(freqs1)
print(freqs2)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

此代码将打印：

```python
defaultdict(<class 'int'>, {'duck': 2, 'season': 2, 'rabbit': 2})
defaultdict(<class 'int'>, {'duck': 2, 'season': 2, 'rabbit': 2})
```

谜题 11， 点击按钮 谜题的解决方案之一是利用这样一个事实，即函数的默认参数在定义函数时计算一次。 在这里你会看到这个相位的阴暗面。

可变默认参数被认为是不好的做法，诸如 flake8 或 pylint 之类的 linter 会将这个 Teaser 代码中的第 5 行标记为错误。

解决方案是使用 None 作为默认值，并在函数本身中创建可变默认值。

```python
import re
from collections import defaultdict


def word_freq(text, freqs=None):
    """Calculate word frequency in text. freqs are previous frequencies"""
    freqs = defaultdict(int) if freqs is None else freqs
    for word in [w.lower() for w in re.findall(r'\w+', text)]:
        freqs[word] += 1
    return freqs


freqs1 = word_freq('Duck season. Duck!')
freqs2 = word_freq('Rabbit season. Rabbit!')
print(freqs1)
print(freqs2)
```

## 进一步阅读

- flake8 Linter
    http://flake8.pycqa.org
- pylint Linter
    http://pylint.org
- Python 教程中的默认参数值
    http://docs.python.org/3/tutorial/controlflow.html#default-argument-values
- “Python 搭便车指南”中的常见问题
    http://docs.python-guide.org/writing/gotchas/
- 维基百科上的 tf-idf
    http://en.wikipedia.org/wiki/Tf%E2%80%93idf