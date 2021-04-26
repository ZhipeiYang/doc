> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [baiyue.one](https://baiyue.one/archives/1651.html)

[教程](https://baiyue.one/archives/category/%e6%95%99%e7%a8%8b) [佰阅部落](https://baiyue.one/archives/author/2894049053qq-com) 10 个月前 (06-29) 2571 次浏览

在 Build 2020 大会上，Microsoft 宣布 Windows 子系统 wsl2 上支持 GPU 计算。本篇就来实际操作下究竟如何使用 NVIDA 显卡的 CUDA，来加速计算人工智能研究。  
[![](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629130145.png)](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629130145.png)

0. 原理图
------

如上图所展示，大意就是在 Windows 和 Linux 之间，通过 wsl2 的专用 CUDA 驱动来实现的。

1. 准备条件
-------

*   Windows 预览版：内核为 2004
*   WSL2 的 ubantu 子系统
*   Windows Terminal
*   WSL 上的 CUDA 驱动程序

上述条件，预览版可以在 Windows 设置里修改，选择 windwos 预览版即可。`wsl2`和`windows terminal`都可以在微软商店搜索安装。wsl 的专用 CUDA 驱动程序，可以在 [NVIDA 官方下载安装](https://baiyue.one/%e9%83%a8%e8%90%bd%e8%b7%b3%e8%bd%ac.html?url=https://developer.nvidia.com/cuda/wsl/download)。  
[![](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629131244.png)](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629131244.png)

2. Docker 环境和 NIVIDA 环境设置
-------------------------

docker 环境安装，可以用我们常用的一键脚本，也可以手动。不过在执行脚本前，先更新一下本地宝包管理器。  
注意：下面代码运行前，请先开全局梯子，否则有些过程网速很慢。

```
apt update -y
```

然后在 wsl 中安装 Docker

```
echo y | bash <(curl -L -s https://raw.githubusercontent.com/Baiyuetribe/codes/master/docker.sh)
```

接着安装 NVida 容器工具包

```
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
curl -s -L https://nvidia.github.io/libnvidia-container/experimental/$distribution/libnvidia-container-experimental.list | sudo tee /etc/apt/sources.list.d/libnvidia-container-experimental.list

```

[![](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629132124.png)](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629132124.png)  
上述命令可以整块粘贴过去。  
刷新 Ubuntu apt 存储库，然后安装 Nvidia 依赖包：

```
sudo apt update && sudo apt install -y nvidia-docker2
```

[![](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629132309.png)](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629132309.png)  
然后在 CMD 或 POWERSHELL 里关闭`Ubantu`

```
wsl.exe --shutdown Ubuntu
```

[![](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629132513.png)](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629132513.png)  
至此，环境准备已完毕。

3. 测试 CGP 计算
------------

在 Windows Terminal 打开 Ubantu，然后启动 Docker：

```
service docker start
```

[![](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629134759.png)](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629134759.png)  
下面开始具体测试，运行下面的脚本：

```
docker run --gpus all nvcr.io/nvidia/k8s/cuda-sample:nbody nbody -gpu -benchmark
```

如果一切正常，会输出如下结果：  
[![](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629135017.png)](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629135017.png)  
恭喜，你已经搭建好了一套 CUDA 加速的开发系统。

4. 实际应用
-------

下面为 GPU 计算的 jupyter 在线开发环境，文件比较大，本站就不做演示了，可以在谷歌 Colab 现成体验或者按下面步骤自己安装测试。

```
docker run -u $(id -u):$(id -g) -it --gpus all -p 8888:8888 tensorflow/tensorflow:latest-gpu-py3-jupyter
```

[![](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629135835.png)](https://cdn.jsdelivr.net/gh/Baiyuetribe/yyycode@dev/img/20/yyycode_com20200629135835.png)  
有点奇怪的是，使用谷歌 colab 实验室，转本地 jupter 接口时，提示无法连接，有点异常。

5. 更多资料
-------

*   [Announcing CUDA on Windows Subsystem for Linux 2](https://baiyue.one/%e9%83%a8%e8%90%bd%e8%b7%b3%e8%bd%ac.html?url=https://developer.nvidia.com/blog/announcing-cuda-on-windows-subsystem-for-linux-2/)
*   [GPU Compute, WSL Install and WSL Update arrive in the latest Insider build for the Windows Subsystem for Linux](https://baiyue.one/%e9%83%a8%e8%90%bd%e8%b7%b3%e8%bd%ac.html?url=https://devblogs.microsoft.com/commandline/gpu-compute-wsl-install-and-wsl-update-arrive-in-the-windows-insiders-fast-ring-for-the-windows-subsystem-for-linux/)

* * *