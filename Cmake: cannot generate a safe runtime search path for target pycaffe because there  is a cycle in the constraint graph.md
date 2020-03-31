# Cannot generate a safe runtime search path for target pycaffe because there is a cycle in the constraint graph

## 错误信息

```bash
CMake Warning at python/CMakeLists.txt:9 (add_library):
  Cannot generate a safe runtime search path for target pycaffe because there
  is a cycle in the constraint graph:

    dir 0 is [/home/zjli/Desktop/person_search_caffe/caffe/build/lib]
    dir 1 is [/home/zjli/anaconda3/envs/caffe/lib]
      dir 4 must precede it due to runtime library [libz.so.1]
    dir 2 is [/home/zjli/openmpi/lib]
    dir 3 is [/usr/local/lib]
    dir 4 is [/home/zjli/anaconda3/lib]
      dir 1 must precede it due to runtime library [libsnappy.so.1]
    dir 5 is [/usr/local/cuda-8.0/lib64]

  Some of these libraries may not be found correctly.
```

## 解决办法

删除build目录，重新cmake即可。
