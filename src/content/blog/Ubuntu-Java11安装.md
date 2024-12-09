---
title: 'Ubuntu Java11安装'
description: 'Ubuntu Java11安装'
pubDate: 2019-03-10 15:12:11
---

作为一个激进主义者，开始尝试使用 Ubuntu 18.04 和 Java11，记录下 Oracle Java 11 在机器上的安装步骤。

### 添加 PPA

```bash
add-apt-repository ppa:linuxuprising/java
apt-get update
```

对于 Ubuntu 18.04 及更高版本，可以跳过 apt-get update，它会在添加 PPA 后完成。

### 安装 Oracle JDK

```bash
apt-get install oracle-java11-installer
```

### 卸载

```bash
apt-get remove oracle-java11-installer
```

然后根据提示选择列表里我们需要的版本，切换它为默认的 Java 环境

### 配置环境变量

```bash
sudo vim /etc/environment
JAVA_HOME="/usr/lib/jvm/java-11-oracle"
source /etc/environment
echo $JAVA_HOME
```
