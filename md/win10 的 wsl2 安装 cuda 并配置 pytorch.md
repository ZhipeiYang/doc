> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/350399229)

1. 准备工作
-------

1.windows 预览体验计划开启，升级系统内部版本 按住 Windows 键 + R 键打开运行，在输入框内中输入 services.msc，并按下回车查看版本号。 Windows Update 服务再尝试检查更新和安装。

2. 安装 wsl2(见往期文章) 3. 安装 Ubuntu

2. 安装 cuda on wsl 驱动
--------------------

![](https://pic3.zhimg.com/v2-adef1578dca5f1ee328bf1deb1e7519e_r.jpg)

一路默认（可以不安一些东西，网上可以查到）

3. 换源安装 cuda-toolkit
--------------------

```
sudo apt-key adv --fetch-keys http://mirrors.aliyun.com/nvidia-cuda/ubuntu1804/x86_64/7fa2af80.pub

sudo sh -c 'echo "deb http://mirrors.aliyun.com/nvidia-cuda/ubuntu1804/x86_64 /" > /etc/apt/sources.list.d/cuda.list'

sudo apt-get update

sudo apt-get install -y cuda-toolkit-11-0

```

![](https://pic3.zhimg.com/v2-d97e94100a6d32d2018bd57db628726a_r.jpg)

4. 设置 cuda 环境变量
---------------

在主目录下的~/.bashrc 文件添加如下路径：

```
sudo su -
vim ~/.bashrc

```

末尾添加并保存：

```
export CUDA_HOME=/usr/local/cuda
export PATH=$PATH:$CUDA_HOME/bin
export LD_LIBRARY_PATH=/usr/local/cuda-10.1/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

```

如果提示缺少相应的依赖库，直接执行如下代码自动安装相应的依赖库

```
sudo apt-get install freeglut3-dev build-essential libx11-dev libxmu-dev libxi-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev

```

查看 cuda 是否安装成功：

```
nvcc -V

```

![](https://pic1.zhimg.com/v2-9f9eae42666e05f87aef032790009e74_r.jpg)

5. 安装 cudnn
-----------

安装 cudnn 的时候也需要登录 Nvidia 账号，直接下载:**cuDNN Library for Linux (x86)**

![](https://pic4.zhimg.com/v2-753a1a8e7f55eecec0e11b21623f8fbb_r.jpg)

然后打开终端执行：

```
tar -zxvf cudnn-10.2-linux-x64-v8.0.4.30.tgz
sudo cp -P cuda/lib64/libcudnn* /usr/local/cuda-11.0/lib64/
sudo cp  cuda/include/cudnn.h /usr/local/cuda-11.0/include/

```

为所有用户设置读取权限：

```
sudo chmod a+r /usr/local/cuda-11.0/include/cudnn.h 
sudo chmod a+r /usr/local/cuda-11.0/lib64/libcudnn*

```

6. 验证 cuda 是否安装成功
-----------------

![](https://pic1.zhimg.com/v2-ddaf4bcfd5e4429d01d4427e7b09a2f0_r.jpg)![](https://pic4.zhimg.com/v2-8c7d159cc859f12171cf103d9c88ce13_r.jpg)

```
cd /usr/local/cuda/samples/4_Finance/BlackScholes
sudo make
./BlackScholes
#好像是11.0可以这样

```

![](https://pic2.zhimg.com/v2-97b0a4bedcf1fd8d0c37ab11e93bd4fd_r.jpg)

成功标志

7. 安装 pytorch
-------------

```
pip install torch==1.7.1+cu110 torchvision==0.8.2+cu110 torchaudio===0.7.2 -f https://download.pytorch.org/whl/torch_stable.html

```

根据对应的 CUdA 版本安装对应的 pytorch 官网：_[https://pytorch.org/](https://link.zhihu.com/?target=https%3A//pytorch.org/)_ 下载 pytorch

![](https://pic2.zhimg.com/v2-10c09cd40dfc27ea94c0ff9eea8e66a9_r.jpg)

pip install torch===1.7.1+cu110 torchvision===0.8.2+cu110 torchaudio===0.7.2 -f [https://download.pytorch.org/whl/torch_stable.html](https://link.zhihu.com/?target=https%3A//download.pytorch.org/whl/torch_stable.html) [https://pytorch.org/get-started/locally/](https://link.zhihu.com/?target=https%3A//pytorch.org/get-started/locally/) 网速不行就需要下载好再安装：

```
pip install "/home/fortuneye/download/torch-1.7.1+cu110-cp37-cp37m-linux_x86_64.whl"

```

![](https://pic1.zhimg.com/v2-95419d526eb41974a19b3407b82e21f8_r.jpg)

8. 验证是否安装成功
-----------

为了确保 PyTorch 安装成功，我们需要运行简单的样例代码测试，例如打印出随机生成的张量矩阵，以及 gpu 是否可以使用。 首先在命令行输入 python，进入 python 的解释器，输入以下语句：

```
import torch
x = torch.rand(5,3)
print(x)

```

输出如下：

> tensor([[0.9943, 0.2830, 0.5508], [0.0765, 0.6474, 0.0059], [0.7241, 0.1868, 0.5398], [0.3217, 0.4664, 0.4242], [0.3351, 0.2482, 0.7371]])  

说明 PyTorch 安装成功。 接下来再输入

```
torch.cuda.is_available()

```

输出为`True`即证明支持 GPU 了。

参考：
---

[在 WSL 中使用 GPU：WSL2 + Ubuntu 18.04 + CUDA + Gnome 图形界面环境配置](https://link.zhihu.com/?target=https%3A//blog.csdn.net/Ashken/article/details/108974058) [官方安装指南](https://link.zhihu.com/?target=https%3A//docs.nvidia.com/cuda/wsl-user-guide/index.html%23installing-nvidia-drivers)

扩容移空间 [https://www.cnblogs.com/JiangOil/p/13869178.html](https://link.zhihu.com/?target=https%3A//www.cnblogs.com/JiangOil/p/13869178.html)

错误指南 [https://blog.csdn.net/LaughingMei/article/details/109962838](https://link.zhihu.com/?target=https%3A//blog.csdn.net/LaughingMei/article/details/109962838)

[https://blog.csdn.net/haozihuang/article/details/109544443](https://link.zhihu.com/?target=https%3A//blog.csdn.net/haozihuang/article/details/109544443)