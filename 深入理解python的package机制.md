---
title: 深入理解python的package机制
date: 2019-02-16 14:12:13
tags: python
categories: python
---

参考：[深入理解python package](https://sanyuesha.com/2017/09/14/deep-understand-python-package/)

# 类(class)，模块(module)，包(package)

模块就是python文件，里面包含着代码(类)。包是一个包含 `__init__.py` 的文件夹。

三者的关系就是：模块包含类，包至少包含一个名为 `__init__.py` 的模块。

一个包的例子如下：

```
package
├── __init__.py
├── submodule.py
└── subpackage
    └── __init__.py
```

# `__init__.py`

如果一个文件夹里面有`__init__.py`，那么python解释器就会将这个文件夹看做包。`__init__.py`告诉了python解释器，导入这个包的时候实际要导入什么内容。

#  `from package import *` 语句

如果 `__init__.py` 中定义了 `__all__` 变量(一个`list`)，那么仅仅只有这个`__all__`变量中定义的内容才会被导入。也就是说：**`__all__`变量是告诉python`from package import *`的时候，那个`*`到底代表着什么。**

如果没有定义`__all__`变量，python的导入规则是这样的：

1. 执行 `__init__.py` 中可被执行的代码
2. `__init__.py` 中定义的变量被导入
3. `__init__.py` 中显式导入的模块被导入

# 容易弄错的情况

假如现在`package`里面的`__init__.py`为空。如果`import package` ，实际上导入的是一个空包，因为`__ini__.py`告诉python解释器，导入这个包的时候实际上什么都别导入。

但是如果运行`import package.subpackage`，是可以成功的。因为这个时候python是根据路径找到的`subpackage`，而不是根据`__init__.py`提供的信息。

