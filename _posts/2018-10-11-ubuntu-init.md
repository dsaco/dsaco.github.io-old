---
layout: post
title:  "项目启动日志"
date:   2018-10-11 09:57:00 +0800
tags: Ubuntu
---

##### 初始化
```
apt-get update
apt-get install git
apt-get install nginx
apt-get install redis-server
apt-get install docker.io
```
##### 安装 [mongodb](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/)
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4

echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list

sudo apt-get update

sudo apt-get install -y mongodb-org
```

##### 添加ssh公钥
```
ssh-keygen -t rsa -C <your_email@example.com>
```

##### 安装 [nvm](https://github.com/creationix/nvm)

```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
```
