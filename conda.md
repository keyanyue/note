# conda 的常用操作命令

## 添加Anaconda的TUNA镜像
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/

## 设置搜索时显示通道地址
conda config --set show_channel_urls yes

## 创建一个名为python34的环境，指定python版本时3.4（不用管时3.4.x，conda会为我们自动寻找3.4.x中的最新版本）
conda create --name python34 python==3.4

## 安装好后，使用active激活某个环境
activate python34       #for windows
source activate python34    #for Linux & Mac
## tips:激活后，会发现terminal输入的地方多了python34的字样，实际上，此时系统做的事情就是把环境切换到刚刚创建好的环境。

## 返回默认环境
deactivate python34       #for windows
source deactivate python34      #for Linux & Mac

## 删除一个已有环境
conda remove --name python34 --all


# 使用conda管理包

## 安装scipy
conda install scipy
## conda 会从远程搜索scipy的相关信息和依赖项目，对于python3.4，conda 会同时安装numpy和mkl（运算加速的库）

## 查看已经安装的packages
conda list
## 最新版的conda是从site-packages文件夹中搜索已经安装的包，不依赖于pip，因此可以显示出通过各种方法安装的包

## 查看当前环境下已经安装的包
conda list

## 查看某个指定环境的已安装包
conda list -n python34

## 查找packages信息
conda search numpy

## 给指定环境安装指定packages
conda install -n python34 numpy
### 如果不用-n指定环境名称，则被安装在当前的活跃环境
### 也可以通过-c指定通过某个channel安装

## 更新packages
conda update -n python34 numpy

## 删除packages
conda remove -n python34 numpy

## 更新conda，保持conda最新
conda update conda

## 更新anaconda
conda update anaconda

## 更新python
conda update python
### 假设当前环境是python3.4，conda会将python升级为3.4.x系列的当前最新版本

#在pycharm上anaconda的配置：
1.在pycharm的Files>>settings>>Project Interpreter>>Add local里面添加Anaconda python.exe 应用之后就可以调用各种Anacoda的库啦，如果下载了其他版本的python，将envs中的python.exe也添加到Project Interpreter中，在需要的时候进行切换就好

# 切换源（channels）
## windows下
在清华源和中科大源之间切换

添加清华源：
命令行中直接使用以下命令
conda config --add channels conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/
conda config --add channels https://mirrors.tuna.tsinghua.deu.cn/cloud/conda-forge
conda config --add channels https://mirrors.tuna.tsinghua.deu.cn/cloud/msys2/

设置搜索时显示通道地址
conda config --set show_channel_urls yes

添加中科大源：
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/msys2/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/bioconda/
conda config --add channels https://mirrors.ustc.edu.cn/anaconda/cloud/menpo/

conda config --set show_channel_urls yes

## linux下
将以上配置写在~/.condarc中
vim ~/.condarc

channels:
-https://mirrors.ustc.edu.cn/anaconda/pkgs/main/
-https://mirrors.tuna.tsinghua.deu.cn/cloud/conda-forge
-https://mirrors.tuna.tsinghua.deu.cn/anaconda/pkgs/free/
-defaults
show_channel_urls:true

其实当下载速度确实很慢的情况下，可以临时指定安装源
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
