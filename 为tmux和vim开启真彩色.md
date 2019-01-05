---
title: 为tmux和vim开启真彩色
date: 2019-02-09 15:34:25
tags:
 - tmux
 - vim
categories: 技术教程
---

有一些`vim`主题（如`solarized`）在`GUI`和终端下效果不同，有可能是因为这个主题需要`true color`（24位颜色）的支持，而通常终端只开启256色（如`xterm-256color`）。下面来看看怎么开启`true color`支持。

# 验证终端的色彩支持

真彩色的支持是需要终端的支持的，常用的终端（如`iterm2`，`konsole`等）都已经支持了。

我们可以自己验证终端是否支持真彩色。

在终端里执行

```
curl https://raw.githubusercontent.com/JohnMorales/dotfiles/master/colors/24-bit-color.sh | bash
```

如果颜色是渐变的，则支持真彩色，否则不支持。

# tmux开启真彩色

`tmux > 2.2`后开始支持真彩色，**注意检查你的版本**！在`.tmux.conf`中添加如下内容：

```
set -g default-terminal "screen-256color"
set-option -ga terminal-overrides ",*256col*:Tc"
```

# vim 开启真彩色

`vim >= 7.4.1770`及`neovim >= 0.2.2`都支持真彩色，但需要少许配置。在`.vimrc`中加入：

```
if has("termguicolors")
    " fix bug for vim
    set t_8f=^[[38;2;%lu;%lu;%lum
    set t_8b=^[[48;2;%lu;%lu;%lum
    
    " enable true color
    set termguicolors
endif
```


其中`termguicolors`用来开启`vim`的真彩色，前面两行用来解决`vim`的BUG（`neovim`不需要），其中`^[`是代表`ESC`键，需要在`vim`中按`Ctrl-v ESC`来输入。

大功告成，好好享受真彩色的终端吧！