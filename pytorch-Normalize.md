# torch.nn.functional.normalize

`torch.nn.functional.normalize(input, p=2, dim=1, eps=1e-12, out=None)`

**功能**：将某一个维度除以那个维度对应的范数(默认是2范数)。
$$
v = \frac{v}{\max(\lVert v \rVert_p, \epsilon)}
$$

主要讲以下三种情况：

- 输入为一维`Tensor`

  ```python
  a = torch.Tensor([1,2,3])

  torch.nn.functional.normalize(a, dim=0)

  tensor([0.2673, 0.5345, 0.8018])
  ```

  可以看到每一个数字都除以了这个`Tensor`的范数：$\sqrt{1^2+2^2+3^2}=3.7416$

- 输入为二维`Tensor`

  ```python
  b = torch.Tensor([[1,2,3], [4,5,6]])

  torch.nn.functional.normalize(b, dim=0)

  tensor([[0.2425, 0.3714, 0.4472],
          [0.9701, 0.9285, 0.8944]])
  ```

  因为`dim=0`，所以是对列操作。以第一列为例，整体除以了第一列的范数：$\sqrt{1^2+4^2}=4.1231$

  ```python
  b = torch.Tensor([[1,2,3], [4,5,6]])

  torch.nn.functional.normalize(b, dim=1)

  tensor([[0.2673, 0.5345, 0.8018],
          [0.4558, 0.5698, 0.6838]])
  ```

  因为`dim=1`，所以是对行操作。以第一行为例，整体除以了第一行的范数：$\sqrt{1^2+2^2+3^2}=3.7416$

- 输入为三维`Tensor`

  ```python
  b = torch.Tensor([[[1,2,3], [4,5,6]], [[1,2,3], [4,5,6]]])

  torch.nn.functional.normalize(b, dim=2)

  tensor([[[0.2673, 0.5345, 0.8018],
           [0.4558, 0.5698, 0.6838]],

          [[0.2673, 0.5345, 0.8018],
           [0.4558, 0.5698, 0.6838]]])
  ```

  注意此时`dim=2`，所以是对第三个维度，也就是每一行操作。以第一行为例，除以了第一行的范数：$\sqrt{1^2+2^2+3^2}=3.7416$

  ```python
  b = torch.Tensor([[[1,2,3], [4,5,6]], [[1,2,3], [4,5,6]]])

  torch.nn.functional.normalize(b, dim=1)

  tensor([[[0.2425, 0.3714, 0.4472],
           [0.9701, 0.9285, 0.8944]],

          [[0.2425, 0.3714, 0.4472],
           [0.9701, 0.9285, 0.8944]]])
  ```

  注意此时`dim=1`，所以是对第二个维度操作。第二个维度是二维数组，所以此时相当于对二维数组的第0维操作。
  以`[[1,2,3], [4,5,6]]`为例，此时要对它的列操作。第一列要除以这一列的范数：$\sqrt{1^2+4^2}=4.1231$。

  ```python
  b = torch.Tensor([[[1,2,3], [4,5,6]], [[1,2,3], [4,5,6]]])

  torch.nn.functional.normalize(b, dim=0)

  tensor([[[0.7071, 0.7071, 0.7071],
           [0.7071, 0.7071, 0.7071]],

          [[0.7071, 0.7071, 0.7071],
           [0.7071, 0.7071, 0.7071]]])
  ```

  `dim=0`的时候现在还看不懂，以后再补吧。

参考：[pytorch-document](https://pytorch.org/docs/stable/nn.functional.html#normalization-functions)
