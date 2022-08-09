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

