# Numpy和Pytorch连接数组

## Numpy

Numpy的连接符合我们直观上的感受，以`a = np.array([1, 2, 3])`为例。

### hstack

水平方向连接。

```python
print(np.hstack((a, a, a)))

array([1, 2, 3, 1, 2, 3, 1, 2, 3])
```

### vstack

竖直方向连接。

```python
print(np.vstack((a, a, a)))

array([[1, 2, 3],
       [1, 2, 3],
       [1, 2, 3]])
```

在连接的过程中，只有在需要的时候，才会扩展数组的维度。

## Pytorch

Pytorch的连接
