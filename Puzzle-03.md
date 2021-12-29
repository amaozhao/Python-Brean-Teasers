# When in Kraków

```python
city = 'Kraków'
print(len(city))
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将打印：7***

> Unicode
>
> 如果你正在阅读这本书的电子版，请不要复制和粘贴书中的代码；由于 Unicode 翻译问题，你可能会得到不同的答案。使用本书源代码。请参阅“关于代码”部分，了解在哪里可以找到它。
> 如果你数一数克拉科夫的字符数，结果会是 6 个。那为什么是 7 个呢？原因是……历史。

起初，计算机是在英语国家——英国和美国开发的。当早期的开发人员想在只能理解位的计算机中编码文本时，他们提出了以下方案。使用一个字节（8 位）来表示一个字符。例如，a 是 97 (01100001)，b 是 98，依此类推。一个字节足以容纳英文字母表，包含二十六个小写字母、二十六个大写字母和十个数字。甚至还有一些空间留给其他特殊字符（例如，9 表示制表符）。这种编码称为 ASCII。 （准确地说，ASCII 仅使用 7 位，而 LATIN-1 将其扩展为 8 位。）

过了一段时间，其他国家开始使用计算机，他们想用自己的母语写作。 ASCII 不够好；单个字节无法容纳表示不同语言字母所需的所有数字。这导致了几种不同的编码方案；最常见的是UTF-8。

UTF-8 中的一些字符是控制字符。在本例中，我们在位置 4 处有字符 o，其后是一个控制字符，上面写着“给前一个字符添加一个元音变音”。这就是字符串长度为 7 的原因。

在 Python 3 中，你有 str（一个不可变的 Unicode 代码点序列）和 bytes（一个不可变的字节序列）。在程序的边缘，当你获得字节时，使用 decode 方法将其转换为 str 。发送数据时，使用 str.encode 方法将其转换为字节。在内部，在代码中使用 str 。

## 进一步阅读

- Unicode HOWTO
    http://docs.python.org/3/howto/unicode.html
- Unicode 和你
    http://betterexplained.com/articles/unicode/
- 维基百科上的 Unicode
    http://en.wikipedia.org/wiki/Unicode
- “实用的 Unicode，或者，我如何停止痛苦？” （视频）
    http://youtube.com/watch?v=sgHbC6udIqc
- 维基百科上的 ASCII
    http://en.wikipedia.org/wiki/ASCII
- 维基百科上的 UTF-8
    http://en.wikipedia.org/wiki/UTF-8
- Python 文档中的 bytes.decode
    http://docs.python.org/3/library/stdtypes.html#bytes.decode
- Python 文档中的 str.encode
    http://docs.python.org/3/library/stdtypes.html#str.encode