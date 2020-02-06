# 永久性地修改PYTHONPATH

`import sys; sys.path.append()`这种方法用来临时修改PYTHONPATH。如果想要永久性的修改PYTHONPATH，有以下两种方法。

- 修改`~/.bashrc`，添加`export PYTHONPATH=$PYTHONPATH:/my/other/path`
- 以anaconda为例，在`~/anaconda3/envs/xxx/lib/python3.6/site-packages/`(这里的xxx为要修改的虚拟环境的名字)目录下新建`xxx.pth`(这里的xxx可以随意取名)文件，内容就是想要添加的目录，一条路径占一行。
