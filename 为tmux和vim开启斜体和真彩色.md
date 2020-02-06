# 为tmux和vim开启斜体和真彩色

这篇文章是我上一篇博客：[为tmux和vim开启真彩色](https://zjli.top/2019/02/09/%E4%B8%BAtmux%E5%92%8Cvim%E5%BC%80%E5%90%AF%E7%9C%9F%E5%BD%A9%E8%89%B2/)的拓展

一般终端会支持斜体，但是`tmux`中是无法显示斜体的。网上的很多教程都已经过时，今天我来分享下如何在`tmux`中启用斜体吧。参考：[reference](https://medium.com/@dubistkomisch/how-to-actually-get-italics-and-true-colour-to-work-in-iterm-tmux-vim-9ebe55ebc2be)

## 1. 检查`tmux`中能否显示斜体

```bash
echo -e "\e[3mitalic\e[23m"
```

## 2. 创建新的终端类型

我们创建一种新的终端类型`tmux-256colors`(有些电脑里可能已经存在了)。

- 创建一个新的文件`tmux-256color.terminfo`，内容如下

  ```bash
  tmux-256color|tmux with 256 colors,
    ritm=\E[23m, rmso=\E[27m, sitm=\E[3m, smso=\E[7m, Ms@,
    khome=\E[1~, kend=\E[4~,
    use=xterm-256color, use=screen-256color,
  ```

- 安装新终端`tic -x tmux-256color.terminfo`

## 3. 修改`.tmux.conf`

在`~/.tmux.conf`里面加入如下内容

```bash
set -g default-terminal 'tmux-256color'
set -as terminal-overrides ',xterm*:Tc:sitm=\E[3m'
```

这里的`Tc`是在`tmux`中开启真彩色，`sitm`是开启斜体。

## 4. 修改`~/.vimrc`

在`vimrc`中添加如下内容：

```vim
if has("termguicolors")
    " fix bug for vim
    set t_8f=^[[38;2;%lu;%lu;%lum
    set t_8b=^[[48;2;%lu;%lu;%lum

    " enable true color
    set termguicolors
endif
```

这几行的作用是在`vim`中开启真彩色，上一篇博客[为tmux和vim开启真彩色](https://zjli.top/2019/02/09/%E4%B8%BAtmux%E5%92%8Cvim%E5%BC%80%E5%90%AF%E7%9C%9F%E5%BD%A9%E8%89%B2/)中也提到了。

下方的两行代码修复了`vim`的bug，强制在`vim`中开启真彩色。

如果没有这两句话，只有`set termguicolors`，那么`tmux`中的`vim`将失去色彩！

```vim
set t_8f=^[[38;2;%lu;%lu;%lum
set t_8b=^[[48;2;%lu;%lu;%lum
```

好了，大功告成，再去运行`echo -e "\e[3mitalic\e[23m"`试验一下吧！