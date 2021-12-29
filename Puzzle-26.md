# Let’s Vote

```python
import re

text = 'The vote was 65 in favour, 43 against and 21 abstentions'
match = re.search(r'(\d+).*(\d+).*(\d+)', text)
print(match.group(1), match.group(2), match.group(3))
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：65 2 1***


你可能希望看到 65 43 21。此输出的原因是 .* 正则表达式是贪婪的，这意味着它将尽可能多地匹配。 这是发生的事情：

- The first .*(\d+) will match 65.*
- The .* after it will match in favour, 43 against and.
- The next .*(\d+) will match 2.*
- The .* after it will match the empty string since * means zero or more.
- The final .*(\d+) will match 1.

要使 .* 非贪婪，请添加 ? 在最后。 以下将按预期工作：

```python
match = re.search(r'(\d+).*?(\d+).*?(\d+)', text)
```

你可以使用诸如 http://www.pyregex.com/ 之类的站点来测试你的正则表达式。

## 进一步阅读

- re模块
    http://docs.python.org/3/library/re.html
- Python 文档中的“正则表达式 HOWTO”
    http://docs.python.org/3/howto/regex.html
