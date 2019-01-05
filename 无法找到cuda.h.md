# Fatal error: cuda.h, No such file or directory

最近在编译别人源代码的时候，`gcc`报了如下错误：`Fatal error: cuda.h, No such file or directory`

解决方法分为两步：

1. 在`~/.bashrc`中设置环境变量

   ```bash
   export CUDA_HOME=/home/usr/local/cuda-9.0
   export PATH=$CUDA_HOME/bin:$PATH
   export LD_LIBRARY_PATH=$CUDA_HOME/lib64:$LD_LIBRARY_PATH
   ```

2. 一般来说第一步就可以解决问题了，但是我的情况还需要进行第二步操作，即创建一个软连接：

   ```bash
   ln -s /home/usr/local/cuda-9.0 /usr/local/cuda
   ```
