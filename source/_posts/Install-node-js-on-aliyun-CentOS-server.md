---
title: 在阿里云 CentOS linux服务器上编译安装NodeJS
date: 2017-09-28 19:50:13
tags:
- 编译安装NodeJS
- CentOS
categories:
- 安装
keywords:
- 安装NodeJS
comments:
meta:
---
<!-- toc -->
总结如何一步步地在Linux CentOS 服务器上编译安装 Node.js，并分享我的[阿里云幸运券](https://promotion.aliyun.com/ntms/act/ambassador/sharetouser.html?userCode=d4crc6kr&utm_source=d4crc6kr)
<!-- more -->
## 更新服务器软件包

```bash
sudo yum -y update
```
`-y` 表示默认在安装过程中回答 `yes`

## 下载编译所需工具，Nodejs 是有个 C++ 开发的，所以
### 方法1

```bash
yum install gcc gcc-c++ openssl-devel
```

### 方法2

也可以直接安装所需的软件开发包：
```bash
yum -y groupinstall "Development Tools"
```

## 进入服务器 `/usr/local` 目录下

```bash
cd /usr/local 
```

## 进入 Nodejs 官网，复制 `Source Code` 位置的二进制源代码压缩文件，并用 wget 下载

```bash
wget https://nodejs.org/dist/v6.11.3/node-v6.11.3.tar.gz
```
如果在服务器上用 `wget` 下载压缩文件很慢，可以考虑先下载到本地，再用 `ftp` 或者 `sftp` 工具上传到服务器
常用的文件传输软件和方式（均免费）：
- [filezilla](https://filezilla-project.org/)
- [xshell](https://www.netsarang.com/download/down_xsh5.html) 有一个 ftp 软件 xftp, 在 xshell 的主面板工具栏可以找到
- 在本地 bash 终端 用 `scp` 命令进行跨机远程拷贝
- [winscp](https://winscp.net/eng/docs/lang:chs)

## 解压，编译安装

- 打开压缩包
- 进入压缩包文件夹
- 配置安装路径为 `/usr/local/node/`
- 编译并安装

```bash
tar -zxf node-v6.11.3.tar.gz
cd node-v6.11.3.tar.gz
./configure --prefix=/usr/local/node/
make && make install
```
大约15分钟安装完之后，进入到 `/usr/local/` 目录下便可看到安装的 node 目录

## 配置 node 环境变量
### 方法1
进入到 `/etc/profile.d/` 目录下创建 node.sh 文件后进行配置
```bash
cd /etc/profile/
touch node.sh
vim node.sh
按 `i` 键后在第一行插入代码：
export PATH= $PATH:/usr/local/node/bin
```
写完后，按 `esc` 键退出编辑模式，键入 `:wq` 退出并保存
然后重新加载配置文件使其生效

### 方法2
建立软链接
```bash
sudo ln -s /usr/local/bin/node /usr/bin/node 
sudo ln -s /usr/local/lib/node /usr/lib/node 
sudo ln -s /usr/local/bin/npm /usr/bin/npm 
sudo ln -s /usr/local/bin/node-waf /usr/bin/node-waf
```

```bash
source /etc/profile.d/node.sh
```

## 检查版本

```bash
node -v
npm -v
```

## 配置 npm 淘宝镜像 cnpm

由于众所周知的原因，在大陆区域的阿里云服务器上下载 npm 资源包的时候速度是非常慢的，所以选择从国内的镜像仓库中安装
关于 cnpm 的详细说明可查看官网 [https://npm.taobao.org/](https://npm.taobao.org/)
```bash
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

## CentOS 编译安装 [mongodb](https://www.mongodb.com/download-center#community)

```bash
# 进入常用的软件安装位置
cd /usr/local
# 下载源代码文件
wget https://fastdl.mongodb.org/src/mongodb-src-r3.4.9.tar.gz
# 解压打开
tar zxvf mongodb-src-r3.4.9.tar.gz
# 重命名
mv mongodb-src-r3.4.9.tar.gz mongodb
# 在 var 文件夹中创建mongodb 文件夹，data 文件夹用于存放数据库数据，logs 用于存放日志
mkdir /var/mongodb
mkdir /var/mongodb/data
mkdir /var/mongodb/logs
# 添加开机启动项
vim /etc/rc.d/rc.local
# 在文件末尾添加如下命令：
/usr/local/mongodb/bin/mongod --dbpath=/var/mongodb/data --logpath /var/mongodb/logs/log.log -fork
# 启动mongodb
/usr/local/mongodb/bin/mongod --dbpath=/var/mongodb/data --logpath /var/mongodb/logs/log.log -fork
```

看到以下信息说明已经安装成功：
> forked process: 18394
> all output going to: /var/mongodb/logs/log.log

## 如果有需要阿里云产品的打折券的，我这里分享一个：[阿里云幸运券](https://promotion.aliyun.com/ntms/act/ambassador/sharetouser.html?userCode=d4crc6kr&utm_source=d4crc6kr)