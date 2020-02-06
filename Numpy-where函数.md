# Numpy-where函数

用法：`numpy.where(condition)`，输出满足条件的元素的坐标。这里的坐标以`tuple`的形式给出。原数组有多少维，输出的`tuple`中就包含几个数组，分别对应符合条件元素的各维坐标。

例子：

```python
>>> a = np.array([2, 4, 6, 8, 10])
>>> np.where(a > 5)             # 返回索引
(array([2, 3, 4]),)
>>> a[np.where(a > 5)]          # 等价于 a[a>5]
array([ 6,  8, 10])
>>> np.where([[0, 1], [1, 0]])
(array([0, 1]), array([1, 0]))
```
