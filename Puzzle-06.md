# Spam, Spam, Spam

```python
from email.message import EmailMessage


msg = EmailMessage()
msg['From'] = 'prince@palace.ng'
msg['To'] = 'Scrooge McDuck <scoorge@disney.com>'
msg.set_content('''\
Dear Sir.

I'm a Nigerian prince who came into some misfortune.
...
''')
print(msg)
```

> 猜输出
>
> 在移至下一页之前尝试猜测输出是什么。

***此代码将引发 ModuleNotFoundError 异常。***


当 Python 寻找要导入的模块（例如，电子邮件）时，它会遍历 sys.path 中的目录并尝试找到与名称匹配的模块。 sys.path 中的第一个值是""（空字符串）。 ""代表当前目录，在当前目录中你有预告文件 email.py。 Python 将加载这个 email.py 而不是标准库中的那个，并且不会在其中找到消息子模块。

> 这里的教训：不要使用标准库已经采用的模块名称。 ☺

Python 的导入机制非常复杂。除了 .py 文件，它还可以导入以下内容：

- 内置模块（例如，sys 被内置到 Python 中）
- 包含 \_\_init\_\_.py 文件的目录
- 共享库（.so、.dll、.dyld ...）
- .pyc 字节编译文件（在 \_\_pycache\_\_ 目录中找到）
- 和更多

你还可以添加导入挂钩以从其他位置导入。有一个从 zip 文件导入的内置钩子，你可以在 sys.path 中看到 python38.zip。

为了允许发行版自定义导入路径，Python 会查找 site.py 并在它启动时加载它。可以运行 python -m site 查看导入路径。

如果你想更自由地使用包名，可以使用相对导入。如果你的包中有一个名为 email.py 的文件，它可以导入系统电子邮件。在你的包中，你可以使用 from .email import send_email 从你的包中导入 send_email。

## 进一步阅读

- 导入系统
    http://docs.python.org/3/reference/import.html
- 导入库模块
    http://docs.python.org/3/library/importlib.html
- “模块和包：生与死！”大卫·比兹利的视频
    http://youtube.com/watch?v=0oTh1CXRaQ0
- Monty Python“垃圾邮件歌曲”
    http://youtube.com/watch?v=mBcY3W5WgNU
- Python 文档中的相对导入
    http://docs.python.org/3/reference/import.html#package-relative-imports