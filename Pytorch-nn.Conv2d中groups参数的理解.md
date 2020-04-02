# Pytorch-nn.Conv2d中groups参数的理解

`class torch.nn.Conv2d(in_channels, out_channels, kernel_size, stride=1, padding=0, dilation=1, groups=1, bias=True)`

group参数的作用是控制分组卷积。

直接通过实际的例子加以说明。

```python
import torch
import torch.nn as nn

x = torch.Tensor([1, 10, 100, 1000, 10000, 100000]).view(1, -1, 1, 1)
print("x:", x.int())
conv = nn.Conv2d(
    in_channels=6, out_channels=9, kernel_size=1, stride=1, padding=0, groups=3, bias=False
)
print("Conv weight size:", conv.weight.data.size())
conv.weight.data = torch.arange(1, 19).float().view(9, 2, 1, 1)
print("Conv weight data:", conv.weight.data.int())
output = conv(x).int()
print("Output:", output)
```

如果是正常的卷积，参数大小应该为: [9(输出通道), 6(输入通道), 1(核h), 1(核w)]。  
这是因为输出是9个通道，每个通道都需要一个[6, 1, 1]大小的卷积(输入的每个通道都参与到了运算)。  
但是我们可以从代码的运行结果中看到Conv层的参数大小为: [9, 2, 1, 1]。这就说明对于每个输出的通道，只有两个输入的通道参与了运算。  
事实就是这样，分组卷积的过程中只有部分输入的通道才参与了运算。我们就以上面的代码为例进行讲解。

- 首先将输入的6个通道分为3组: [1, 10], [100, 1000], [10000, 100000]，每一组都用来生成输出的一个通道。
- 3个组只能生成3个输出通道，但是要求输出是9个通道，所以每个组需要重复计算三次。
- 输出的第1个通道: `1 * 1 + 2 * 10 = 21`，需要用到输入的第1组。  
  输出的第2个通道: `3 * 1 + 4 * 10 = 43`，需要用到输入的第1组。  
  输出的第3个通道: `5 * 1 + 6 * 10 = 65`，需要用到输入的第1组。  
  输出的第4个通道: `7 * 100 + 8 * 1000 = 8700`，需要用到输入的第2组。  
  ......

根据上面的分析，我们可以得出结论: group参数必须整除输入的通道数(保证输入的通道能被正确分组)，  
还必须整除输出的通道数(保证group个分组重复若干次之后恰好等于输出通道数)。
