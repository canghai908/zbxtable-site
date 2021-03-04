---
title: "RPM部署【推荐】"
linkTitle: "RPM部署【推荐】"
weight: 5
date: 2020-07-24 19:00:32
description: >
  使用RPM包方式部署ZbxTable
---

{{% pageinfo %}}
ZbxTable 最新版本 1.1.2
{{% /pageinfo %}}

由于 ZbxTable 使用 Go 语言编写，无任何系统以来组建，建议使用 RPM 方式进行安装，推荐使用 ZbxTable 的 yum 源，可方便安装各个组件并可使用 yum update 对组件进行更新。

## 添加 yum 源

CentOS 6.x x86_64

```
rpm -Uvh https://repo.cactifans.com/zbxtable/1.0/rhel/6/x86_64/zbxtable-release-1.0-1.el6.noarch.rpm
yum clean all
```

CentOS 7.x x86_64

```
rpm -Uvh https://repo.cactifans.com/zbxtable/1.0/rhel/7/x86_64/zbxtable-release-1.0-1.el7.noarch.rpm
yum clean all
```

CentOS 8.x x86_64

```
rpm -Uvh https://repo.cactifans.com/zbxtable/1.0/rhel/8/x86_64/zbxtable-release-1.0-1.el8.noarch.rpm
dnf clean all
```
## 安装
如果是全新安装，可按照以下步骤进行
安装 Zbxtable

```
yum install zbxtable -y
```

安装 ms-agent

```
yum install ms-agent -y
```

## 配置

### ZbxTable 配置

#### 数据库初始化

按照以下命令创建数据库及用户，根据使用数据库类型选择执行
mysql 数据库

```
# mysql -uroot -p
password
mysql> create database zbxtable character set utf8 collate utf8_bin;
mysql> create user zbxtable@localhost identified by 'zbxtablepwd123';
mysql> grant all privileges on zbxtable.* to zbxtable@localhost;
mysql> quit;
```

postgres 数据库

```
# su - postgres
psql
postgres=# create user zbxtable with password 'zbxtablepwd123';
postgres=# create database zbxtable owner zbxtable;
postgres=# grant all on database zbxtable to zbxtable;
postgres=# \q
```

#### 系统初始化

新版本配置文件需要手动生成，生成步骤如下:
```
cd /usr/local/zbxtable/
./zbxtable init
```
会进入交互式命令行，根据实际情况输入数据库账号及密码，以及zabbix连接信息，最后确认即可生成配置文件。如数据库及zabbix连接错误，会要求重新输入连接信息，否则无法生成配置文件。

[![asciicast](https://asciinema.org/a/8a8ejNzObhUZujYJ1CaZ0yRR7.svg)](https://asciinema.org/a/8a8ejNzObhUZujYJ1CaZ0yRR7)
#### 配置MS-Agent
MS-Agent为告警消息采集客户端，采集zabbix产生的告警信息，并发送到ZbxTable平台，zbxtable需要在zabbix server上配置对应的Action等。配置步骤如下
```
cd /usr/local/zbxtable/
./zbxtable install
```
执行后会根据之前提供的zabbix信息，配置action，过程如下。
[![asciicast](https://asciinema.org/a/jz68MHVjyV0AfyAY6bKtycfSW.svg)](https://asciinema.org/a/jz68MHVjyV0AfyAY6bKtycfSW)

会自动在zabbix上建立一个ms-agent用户，密码为随机，权限为管理员。最后输出MS-Agent token为MS-Agent 与ZbxTable通信的token，需要和MS-Agent 配置文件里的token保持一致，否则无法正常收到告警。 
Token可在conf/app.conf文件里找到。   
#### 启动

修改好配置后，使用以下命令启动

```
systemctl enable --now zbxtable
```

重启

```
systemctl restart zbxtable
```

查看服务状态

```
systemctl status zbxtable
```

一定要确保 zbxtable 服务是 Active: active (running) 状态，如不是正常状态，建议查看日志/usr/local/zbxtable/logs/zbxtable.log或者系统/var/log/message日志

#### Debug

如启动失败或者出现错误错误，可修改通过需改程序配置文件,修改运行模式为 dev 模式,并重启 zbxtable,查看程序日志解决,日志位于 logs/zbxtable.log

### Zbxtable-Web 配置
Zbxtable Web需使用nginx
```
yum install nginx -y
```

拷贝 nginx 配置文件

```
cp /usr/local/zbxtable/nginx.conf /etc/nginx/conf.d/
```

重启 nginx

```
systemctl restart nginx
```

配置开机启动

```
systemctl enable  nginx
```

使用 http://ip:8088 即可访问系统，系统默认账号：admin 密码：Zbxtable

### ms-agent 配置

#### 初始化配置

ms-agent 需使用 zbxtable 命令完成在 Zabbix Server 的配置,确保已配置成功。

#### 环境信息

环境信息

| 程序     | 路径                                  | 作用                                             |
| :------- | :------------------------------------ | :----------------------------------------------- |
| ms-agent | /usr/lib/zabbix/alertscripts/ms-agent | 接收 Zabbix 平台产生的告警并发送到 ZbxTable 平台 |
| app.ini  | /etc/ms-agent/app.ini                 | ms-agent 配置文件                                |

如果你的 Zabbix Server 的 alertscripts 目录不为/usr/lib/zabbix/alertscripts/ 需要移动 ms-agen 到你的 zabbix server 的 alertscripts 目录下即可,否则会在 Zabbix 告警页面出现找不到 ms-agent 的错误提示，也无法收到告警消息。
也可以修改 Zabbix Server 的配置文件，将 alertscripts 目录指向/usr/lib/zabbix/alertscripts/
```
vi zabbix_server.conf
```
修改如下配置为
```
AlertScriptsPath=/usr/lib/zabbix/alertscripts
```

修改后重启 Zabbix Server 生效

#### 配置文件

/etc/ms-agent/app.ini 为程序配置文件，默认内容如下

```
[app]
Debug = 0
TenantID = zabbix01
LogSavePath = /tmp
Host = http://192.168.10.10:8088/v1/receive
Token = 2d7a7ab0b0be493ab0bb9a925e4a30d2
```

Debug 为程序日志级别 0 是 debug，1 为 info

LogSavePath 为日志目录，默认为/tmp 目录

Host 为 ZbxTable 系统地址，默认为 http 服务器 IP+/v1/receive

Token 与 ZbxTable 通信的 Token,可自行修改,需要与 ZbxTable 平台配置保持一致即可，否则无法接收告警。

#### Debug

可修改配置文件打开 Debug 模式，查看日志文件名格式如下/tmp/ms-agent_yyyymmdd.log
