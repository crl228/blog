---
title: 'Ubuntu Docker安装'
description: 'Ubuntu Docker安装'
pubDate: 2018-12-05 16:51:49
---

记录下 Docker 安装步骤。使用清华源

#### 更新 APT

apt 源使用 HTTPS 以确保软件下载过程中不被篡改。

```bash
sudo apt-get update

sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```

需要添加软件源的 GPG 密钥

```bash
curl -fsSL https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu/gpg | sudo apt-key add -
```

```bash
sudo add-apt-repository \
    "deb [arch=amd64] https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu \
    $(lsb_release -cs) \
    stable"
```

#### 安装 Docker CE

安装 docker-ce

```bash
sudo apt-get update
sudo apt-get install docker-ce
```

#### 脚本安装

```bash
curl -fsSL get.docker.com -o get-docker.sh
sudo sh get-docker.sh --mirror Aliyun
```

#### 启动

```bash
sudo systemctl enable docker
sudo systemctl start docker
```
