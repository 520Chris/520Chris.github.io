# Pytorch创建requires_grad=True的tensor

有以下四种方法

- `x = torch.randn(2, 3, requires_grad=True)`
- `x = Variable(torch.Tensor([2, 3]), requires_grad=True)`
- `x = torch.tensor([2.0, 3], requires_grad=True)`或者`x = torch.tensor([2, 3], requires_grad=True, dtype=torch.float32)`(Pytorch中浮点类型的tensor才能有梯度)
- `x = torch.Tensor([2, 3]); x.requires_grad=True`
