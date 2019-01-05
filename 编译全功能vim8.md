---
title: 编译全功能vim8
date: 2019-02-03 10:52:15
tags: vim
categories: 技术教程
---

这篇博客讲解如何在ubuntu下编译vim8源码。参考：[YCM](https://github.com/Valloric/YouCompleteMe/wiki/Building-Vim-from-source)

# 1.卸载原有的vim

```bash
sudo apt-get purge vim vim-runtime vim-gnome vim-common vim-tiny vim-gui-common
```

然后用`dpkg -l | grep vim`查看还有什么和vim相关的包，如果有，用`dpkg --purge`删除。

# 2.安装编译vim需要的依赖包

```bash
sudo apt install libncurses5-dev libgnome2-dev libgnomeui-dev \
libgtk2.0-dev libatk1.0-dev libbonoboui2-dev \
libcairo2-dev libx11-dev libxpm-dev libxt-dev python-dev \
python3-dev ruby-dev lua5.1 liblua5.1-dev libperl-dev
```

# 3.下载源码

```bash
git clone https://github.com/vim/vim.git
cd vim
```

# 4.配置

```bash
./configure --with-features=huge \
            --enable-multibyte \
            --enable-rubyinterp=yes \
            --enable-python3interp=yes \
            --with-python3-config-dir=/usr/lib/python3.5/config-3.5m-x86_64-linux-gnu \
            --enable-perlinterp=yes \
            --enable-luainterp=yes \
            --enable-gui=gtk2 \
            --enable-cscope \
            --prefix=/usr/local \
            --enable-fail-if-missing
```

参数说明

```
–with-features=hug 支持最大特性 
–enable-multibyte 多字节支持可以在Vim中输入中文 
–enable-rubyinterp 启用Vim对ruby编写的插件的支持 
–enable-python3interp 启用Vim对python3编写的插件的支持 
–enable-luainterp 启用Vim对于lua编写的插件的支持 
–enable-perlinterp 启用Vim对perl编写的插件的支持 
–enable-cscope 启用Vim对cscope的支持 
–with-python3-config-dir 指定python3路径 
–enable-gui=gtk2 gtk2支持，也可以使用gnome，表示生成gvim 
-prefix=/usr/local 编译安装路径
```

需要注意的是，ubuntu下编译的vim8不能同时支持python2和python3，具体可参见这个[问题](https://stackoverflow.com/questions/23023783/vim-compiled-with-python-support-but-cant-see-sys-version)。这里的编译选项是支持python3的。

# 5.编译并安装

```bash
make && sudo make install
```

# 6.打包vim的deb包

可以使用checkinstall工具对编译的vim进行打包生成deb安装包，方便以后直接安装。

## 6.1安装checkinstall

```
sudo apt-get install checkinstall
```

## 6.2生成deb包

```
cd vim
sudo checkinstall
```

如果您需要编译好的vim安装包，可以在博客下方告知于我，留下联系方式即可。