# Pytorch Tensor和tensor的区别

`torch.Tensor`是`torch.FloatTensor`的别名，是python类，只能创建`FloatTensor`。从首字母大写也可以看出一些端倪。

`torch.tensor`是一个函数，可以将其它数据结构转化成tensor，可以创建`FloatTensor`，`IntTensor`等等。

例子：

```python
>>> torch.Tensor([1, 2]).dtype
>>> torch.float32
>>> torch.tensor([1, 2]).dtype
>>> torch.int64
>>> torch.tensor([1, 2], dtype=torch.float32).dtype
>>> torch.float32
```
