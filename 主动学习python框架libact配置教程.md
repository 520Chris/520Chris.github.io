# 主动学习python框架libact配置教程

## 配置教程

[libact](https://github.com/ntucllab/libact)是一个Python包，旨在让用户更容易地进行主动学习。该包不仅实现了几种流行的主动学习策略，而且还提供了一种“active learning by learning”算法，该算法可以帮助用户动态地自动选择最佳主动学习策略。此外，该包还提供了一个统一的接口，用于实现更多的主动学习策略。

接下来进入正题：如何安装libact

1. `git clone https://github.com/ntucllab/libact.git`，将源代码克隆到本地

2. `cd libact`，进入libact文件夹

3. `pip3 install -r requirements.txt`，安装必要的依赖(libact要求Python 2.7, 3.3, 3.4, 3.5，实际测试中发现python2.7不行，我的是python3.5)

4. 如果是Debian (>= 7) / Ubuntu (>= 14.04)

   ```shell
   sudo apt-get install build-essential gfortran libatlas-base-dev liblapacke-dev python3-dev
   ```

   如果是macOS

   ```shell
   brew install openblas
   ```

5. 解决了依赖关系之后，就可以安装libact了

   ```shell
   python3 setup.py build
   sudo python3 setup.py install
   ```

大功告成！

## 错误处理

我在进行到第五步的`python3 setup.py build`的时候，出现了如下错误：

```bash
ppnman@ubuntu:~/Desktop/libact$ python3 setup.py build
Platform Detection: Linux. Link to liblapacke...
running build
running build_py
creating build
creating build/lib.linux-x86_64-3.5
creating build/lib.linux-x86_64-3.5/libact
copying libact/__init__.py -> build/lib.linux-x86_64-3.5/libact
creating build/lib.linux-x86_64-3.5/libact/base
copying libact/base/interfaces.py -> build/lib.linux-x86_64-3.5/libact/base
copying libact/base/__init__.py -> build/lib.linux-x86_64-3.5/libact/base
copying libact/base/dataset.py -> build/lib.linux-x86_64-3.5/libact/base
creating build/lib.linux-x86_64-3.5/libact/models
copying libact/models/__init__.py -> build/lib.linux-x86_64-3.5/libact/models
copying libact/models/logistic_regression.py -> build/lib.linux-x86_64-3.5/libact/models
copying libact/models/sklearn_adapter.py -> build/lib.linux-x86_64-3.5/libact/models
copying libact/models/perceptron.py -> build/lib.linux-x86_64-3.5/libact/models
copying libact/models/svm.py -> build/lib.linux-x86_64-3.5/libact/models
creating build/lib.linux-x86_64-3.5/libact/models/multilabel
copying libact/models/multilabel/__init__.py -> build/lib.linux-x86_64-3.5/libact/models/multilabel
copying libact/models/multilabel/binary_relevance.py -> build/lib.linux-x86_64-3.5/libact/models/multilabel
copying libact/models/multilabel/dummy_clf.py -> build/lib.linux-x86_64-3.5/libact/models/multilabel
creating build/lib.linux-x86_64-3.5/libact/labelers
copying libact/labelers/interactive_labeler.py -> build/lib.linux-x86_64-3.5/libact/labelers
copying libact/labelers/__init__.py -> build/lib.linux-x86_64-3.5/libact/labelers
copying libact/labelers/ideal_labeler.py -> build/lib.linux-x86_64-3.5/libact/labelers
creating build/lib.linux-x86_64-3.5/libact/query_strategies
copying libact/query_strategies/active_learning_by_learning.py -> build/lib.linux-x86_64-3.5/libact/query_strategies
copying libact/query_strategies/variance_reduction.py -> build/lib.linux-x86_64-3.5/libact/query_strategies
copying libact/query_strategies/__init__.py -> build/lib.linux-x86_64-3.5/libact/query_strategies
copying libact/query_strategies/uncertainty_sampling.py -> build/lib.linux-x86_64-3.5/libact/query_strategies
copying libact/query_strategies/random_sampling.py -> build/lib.linux-x86_64-3.5/libact/query_strategies
copying libact/query_strategies/hintsvm.py -> build/lib.linux-x86_64-3.5/libact/query_strategies
copying libact/query_strategies/quire.py -> build/lib.linux-x86_64-3.5/libact/query_strategies
copying libact/query_strategies/query_by_committee.py -> build/lib.linux-x86_64-3.5/libact/query_strategies
copying libact/query_strategies/density_weighted_uncertainty_sampling.py -> build/lib.linux-x86_64-3.5/libact/query_strategies
creating build/lib.linux-x86_64-3.5/libact/query_strategies/multilabel
copying libact/query_strategies/multilabel/binary_minimization.py -> build/lib.linux-x86_64-3.5/libact/query_strategies/multilabel
copying libact/query_strategies/multilabel/multilabel_with_auxiliary_learner.py -> build/lib.linux-x86_64-3.5/libact/query_strategies/multilabel
copying libact/query_strategies/multilabel/__init__.py -> build/lib.linux-x86_64-3.5/libact/query_strategies/multilabel
copying libact/query_strategies/multilabel/maximum_margin_reduction.py -> build/lib.linux-x86_64-3.5/libact/query_strategies/multilabel
copying libact/query_strategies/multilabel/adaptive_active_learning.py -> build/lib.linux-x86_64-3.5/libact/query_strategies/multilabel
creating build/lib.linux-x86_64-3.5/libact/query_strategies/multiclass
copying libact/query_strategies/multiclass/hierarchical_sampling.py -> build/lib.linux-x86_64-3.5/libact/query_strategies/multiclass
copying libact/query_strategies/multiclass/__init__.py -> build/lib.linux-x86_64-3.5/libact/query_strategies/multiclass
copying libact/query_strategies/multiclass/expected_error_reduction.py -> build/lib.linux-x86_64-3.5/libact/query_strategies/multiclass
copying libact/query_strategies/multiclass/mdsp.py -> build/lib.linux-x86_64-3.5/libact/query_strategies/multiclass
copying libact/query_strategies/multiclass/active_learning_with_cost_embedding.py -> build/lib.linux-x86_64-3.5/libact/query_strategies/multiclass
creating build/lib.linux-x86_64-3.5/libact/utils
copying libact/utils/__init__.py -> build/lib.linux-x86_64-3.5/libact/utils
running build_ext
building 'libact.query_strategies._variance_reduction' extension
Warning: Can't read registry to find the necessary compiler setting
Make sure that Python modules winreg, win32api or win32con are installed.
C compiler: x86_64-linux-gnu-gcc -pthread -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -g -fstack-protector-strong -Wformat -Werror=format-security -Wdate-time -D_FORTIFY_SOURCE=2 -fPIC

creating build/temp.linux-x86_64-3.5
creating build/temp.linux-x86_64-3.5/libact
creating build/temp.linux-x86_64-3.5/libact/query_strategies
creating build/temp.linux-x86_64-3.5/libact/query_strategies/src
creating build/temp.linux-x86_64-3.5/libact/query_strategies/src/variance_reduction
compile options: '-I/home/ppnman/.local/lib/python3.5/site-packages/numpy/core/include -I/usr/include/lapacke -I/usr/include/python3.5m -c'
extra options: '-std=c11'
x86_64-linux-gnu-gcc: libact/query_strategies/src/variance_reduction/variance_reduction.c
x86_64-linux-gnu-gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions -Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-Bsymbolic-functions -Wl,-z,relro -g -fstack-protector-strong -Wformat -Werror=format-security -Wdate-time -D_FORTIFY_SOURCE=2 build/temp.linux-x86_64-3.5/libact/query_strategies/src/variance_reduction/variance_reduction.o -o build/lib.linux-x86_64-3.5/libact/query_strategies/_variance_reduction.cpython-35m-x86_64-linux-gnu.so -llapacke -llapack -lblas
/usr/bin/ld: cannot find -llapacke -llapack -lblas
collect2: error: ld returned 1 exit status
error: Command "x86_64-linux-gnu-gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions -Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-Bsymbolic-functions -Wl,-z,relro -g -fstack-protector-strong -Wformat -Werror=format-security -Wdate-time -D_FORTIFY_SOURCE=2 build/temp.linux-x86_64-3.5/libact/query_strategies/src/variance_reduction/variance_reduction.o -o build/lib.linux-x86_64-3.5/libact/query_strategies/_variance_reduction.cpython-35m-x86_64-linux-gnu.so -llapacke -llapack -lblas" failed with exit status 1

```

根据报错信息可以知道，由于这个错误`/usr/bin/ld: cannot find -llapacke -llapack -lblas`，导致

```bash
x86_64-linux-gnu-gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions -Wl,-Bsymbolic-functions -Wl,-z,relro -Wl,-Bsymbolic-functions -Wl,-z,relro -g -fstack-protector-strong -Wformat -Werror=format-security -Wdate-time -D_FORTIFY_SOURCE=2 build/temp.linux-x86_64-3.5/libact/query_strategies/src/variance_reduction/variance_reduction.o -o build/lib.linux-x86_64-3.5/libact/query_strategies/_variance_reduction.cpython-35m-x86_64-linux-gnu.so -llapacke -llapack -lblas
```

这个命令运行失败。去网上搜索了很久，说是缺少对应的动态链接库。把他们的方法挨个试了一遍，还是不行。最后灵机一动，把

```bash
x86_64-linux-gnu-gcc ...... -llapacke -llapack -lblas
```

这个命令在terminal里面手动运行了一下，再次运行`python3 setup.py build`，就没有问题了。

很奇怪的解决办法，估计是`setup.py`里面有什么问题吧。不过也懒得深究了，能跑起来就行了。
