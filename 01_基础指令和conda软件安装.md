### 1. 需要学习的基础指令
    cd 文件夹间跳转
    cp 文件拷贝
    ll 显示文件目录
    ls 显示文件目录
    mv 移动文件/重命名文件
    ln 文件软连接
    rm 删除文件
    vi 编辑文件
    mkdir 创建文件夹
    cat 查看文件内容
    less 查看文件内容
    more 查看文件内容
    head 查看文件前部
    tail 查看文件尾部
    grep 文件内容查找
    find 查找文件
    wget 下载

### 2. conda软件安装
#### 1. conda主软件安装
在个人目录下创建用于软件安装的文件夹
```shell
mkdir software
```
  
[conda下载页面](https://www.anaconda.com/products/distribution)  
选择Linux文件下载后使用Xshell上传至自己目录下  
或者直接在服务器下载  
```shell
cd software

wget https://repo.anaconda.com/archive/Anaconda3-2022.05-Linux-x86_64.sh ./
```
运行下载好的安装脚本
```shell
sh Anaconda3-2022.05-Linux-x86_64.sh
```
**注意：**  

    1. 安装过程中需要指定安装路径且路径文件夹不可以存在
    
    2. 安装最后会提示是否设为全局选择NO，不要影响其他人部署软件
安装完成后使用export指定安装路径的conda环境，例如：  
```shell
export PATH=/public/home/dk_ckq/metagenomics/XXX/software/conda/bin:$PATH
```
调用后使用which指令查看conda软件是否是自己安装路径的那个
```shell
which conda
```

#### 2. conda软件安装
conda软件安装分为在主环境中安装和创建新的环境安装
```shell
主环境直接安装
conda install fastqc


创建新环境安装
conda create -n AAA python=3.6 ## 创建一个名为AAA的环境，可以在后面指定python版本，也可以不指定  

source activate AAA  ## 激活AAA环境  

conda install fastqc  ## 在AAA环境中安装fastqc  

source deactivate  ## 退出环境  

conda remove -n AAA --all  ## 删除AAA环境  
```
**注意：** 

    1. 创建环境同一账户下名字会重复，创建时注意使用conda env list查看是否已有重名环境
    
    2. 由于账户目前共用，统一独立创建环境进行后续操作

**需要安装准备软件有：**  
    fastqc
    trimmomatic
    bowtie2
    metaphlan2
    humann

**注意：** 
有些软件可以不适用conda安装，直接下载安装即可
