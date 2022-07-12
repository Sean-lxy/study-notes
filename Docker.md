### 介绍

Docker 主要分为 **Docker Desktop** 与 **Docker Engine**。前者是专门为个人使用而设计的，支持Mac 和 windows 快速安装，具有可视化界面。后者是完全免费，但只能在Linux 上运行的，只能通过命令行操作。

#### 安装

```bash

# 安装 Docker Engine
sudo apt install docker.io

# 启动 Docker 服务
sudo service docker start

# 将当前用户加入 docker 组
sudo usermod -aG docker ${USER}

# 查看 Docker 客户端和服务器端 各自的版本信息
docker version

# 显示当前 Docker 系统相关的信息，例如，CPU、内存、容器数量、镜像数量、容器运行时、存储文件系统等等。
docker info


```



### 使用

#### docker ps 

列出当前系统里运行的容器

#### docker images

列出当前 Docker 所存储的所有镜像

#### docker pull