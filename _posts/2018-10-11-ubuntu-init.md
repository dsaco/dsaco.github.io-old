---
layout: post
title:  "项目启动日志"
date:   2018-10-11 09:57:00 +0800
tags: ubuntu
---

### Install application
docker
```
sudo apt install docker.io
```
[nvm](https://github.com/creationix/nvm)
```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
```
redis
```
sudo apt install redis-server
```
mongodb
```
sudo apt install mongodb

sudo mkdir -p /data/db/

# when error: /data/db/mongod.lock errno:13 Permission denied Is a mongod instance already running?, terminating
whoami
sudo chown `USERNAME` /data/db

# 官方安装方式(ubuntu 16)
1. sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4
2. echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/4.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.0.list
3. sudo apt-get update
4. sudo apt-get install -y mongodb-org
# 配置文件
/etc/mongod.conf

```

查看是否启动
```
pgrep mongo -l
pgrep redis -l
```