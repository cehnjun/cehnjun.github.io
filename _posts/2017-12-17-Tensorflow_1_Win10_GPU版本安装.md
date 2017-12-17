---
layout: post
title: Tensorflow-GPU-Win10安装
date: 2017-12-17
tags: 博客   
---

---
### 1. VS2015安装
要编译 **CUDA** 里的例子工程可以安装 **VS2015** ，不安装对于使用 **tensorflow-gpu** 没有影响，建议先安装 **VS2015** 以备后续使用例子需要。去官网下载 **VS2015** ，选择 **C++** 模块安装即可。按照官网说明匹配相应的 **Compiler** 即可，不用一定是 **VS2015** ：

![CUDA](..\images\posts\markdown\CUDA1.PNG)  

### 2. CUDA安装
本文作者在安装 **tensorflow-gpu** 时，tenforflow-gpu支持的 **CUDA** 最高版本还是  [CUDA Toolkit 8.0 - Feb 2017](https://developer.nvidia.com/cuda-toolkit-archive)，去官网下载相应安装程序默认安装即可。可以到[CUDA-Enabled GeForce Products](https://developer.nvidia.com/cuda-gpus)查看GPU支持，环境变量由安装程序默认配置好。(安装路径不用管，即使改了路径，依然会安装在 **C** 盘路径)

### 3. cuDNN安装
官网下载相应 **CUDA** 版本的 **cudnn-8.0-windows10-x64-v6.0.zip** 解压文件，将得到的三个文件夹(*/bin,/include,/lib* )覆盖至 **CUDA** 安装目录  
>  
 C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0

### 4. Tensorflow-gpu安装
按照官网教程[Installing TensorFlow on Windows](https://tensorflow.google.cn/install/install_windows)安装，本文选择 **Installing with Anaconda3**，使用清华镜像安装 [Anaconda](https://mirrors.tuna.tsinghua.edu.cn/help/anaconda/)，添加清华镜像仓库源。打开 **Anaconda Prompt** 输入:  
```
:conda create -n tensorflow-gpu python=3.5 #创建Python虚拟环境
:activate tensorflow-gpu #激活tensorflow-gpu环境
:pip install --ignore-installed --upgrade tensorflow-gpu #pip安装
```
本文使用 **Python3.6** 安装时出错，采用 **Python3.5** 安装，如果在创建虚拟环境时出错，提示网络问题，找到 *.condarc* 文件(使用 **everthing** 搜索方便)，删除 **-default** 一行。(前面已添加清华镜像仓库源)

### 5. 测试MNIST数据集
激活 **tensorflow-gpu** 虚拟环境后,下载 **mnist** 测试集(手写数字识别):
```
:git clone https://github.com/martin-gorner/tensorflow-mnist-tutorial.git
:python mnist_1.0_softmax.py
```
首次运行如果出错，提示网络连接中断，一般是数据集下载中断，需要借助梯子上网。成功后如下显示使用 **GPU** 设备：
**（/device:GPU:0）**

![MNIST1](..\images\posts\markdown\MNIST1.png)

![MNIST2](..\images\posts\markdown\MNIST2.png)
