# vim和系统粘贴板交互

默认情况下，`vim`是无法和系统粘贴板交互的，如何实现这两者的沟通呢？

## 查看vim是否支持`clipboard`

```bash
vim --version | grep "clipboard"
```

如果显示的是`-clipboard`，则需要安装图形化界面的`vim`，或者重新编译`vim`。

安装图形化界面的`vim`。

```bash
sudo apt-get install vim-gnome
```

安装的时候可能会出现依赖问题，我的解决方法是把和`vim`有关的包全部卸载掉。

```bash
sudo apt remove vim***
```

再重新安装`vim`和`vim-gnome`。

## vim的寄存器

如果`vim`支持`clipboard`，在`vim`的命令行模式下执行`:reg`，就可以看到`+`寄存器了。

`"+y`把vim的内容拷贝至系统粘贴板。

`"+p`把系统粘贴板的内容粘贴至`vim`。
