# 常用的ipdb调试命令

常用的`ipdb`命令整理如下。

- `h(help)`：帮助命令
- `s(step into)`：进入函数内部
- `n(next)`：执行下一行
- `b(break)`: `b line_number`打断点
- `cl(clear)`: 清除断点
- `c(continue)`: 一直执行到断点
- `r(return)`: 从当前函数返回
- `j(jump)`: `j line_number`，跳过代码片段，直接执行指定行号所在的代码
- `l(list)`: 列出上下文代码
- `a(argument)`: 列出传入函数所有的参数值
- `p/pp`: `print` 和 `pretty print`打印出变量值
- `r(restart)`: 重启调试器
- `q(quit)`: 推出调试，清除所有信息
