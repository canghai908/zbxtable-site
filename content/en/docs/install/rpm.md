---
title: "RPM [Recommended]"
linkTitle: "RPM [Recommended]"
weight: 5
date: 2020-07-24 19:00:32
description: >
  Deploy ZbxTable using RPM package
---

{{% pageinfo %}}
It is recommended to add Zbxtable repo for system installation and update.
{{% /pageinfo %}}

Since ZbxTable is written in Go language, there is no system built, it is recommended to use RPM to install, it is recommended to use ZbxTable's yum source, which can facilitate the installation of various components and use yum update to update the components.

## Add yum repo

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

## Installation

Install Zbxtable

```
yum install zbxtable -y
```

Install Zbxtable-Web

```
yum install zbxtable-web -y
```

Install ms-agent

```
yum install ms-agent -y
```

## Configuration

### Zbxtable Configuration

#### Database initialization

Follow the commands below to create a database and user

```
# mysql -uroot -p
password
mysql> create database zbxtable character set utf8 collate utf8_bin;
mysql> create user zbxtable@localhost identified by 'zbxtablepwd123';
mysql> grant all privileges on zbxtable.* to zbxtable@localhost;
mysql> quit;
```

#### Modify the configuration file
The configuration file is  conf/app.conf

```
#zbxtable
appname = zbxtable
httpport = 8084
runmode = prod
autorender = false
copyrequestbody = true
EnableDocs = true
#session expiration time, the unit is hour, the default is 12 hours. If you need to automatically refresh the large screen, it is recommended to configure a larger configuration time
session_timeout = 12

#database
hostname = localhost
username = zbxtable
dbpsword = zbxtablepwd123
database = zbxtable
port = 3306
dbprefix = zbxtable_

#zabbix web info
zabbix_server = http://192.168.10.12
zabbix_user = Admin
zabbix_pass = zabbix

#alarm send token
token = ec573cf7388da56916f75ba9bbe46a69
```

Main configuration

- zabbix web info 为 访问 zabbix web 的地址及账号密码,**确保使用 zabbix_server 所配置的地址能使用浏览器访问 zabbix web 页面**，如果你的zabbix web访问地址为http://xxx.xxx.xxx.xx/zabbix 则这里也需要加后缀/zabbix，配置用户建议为Admin管理员用户，其他用户可能存在权限问题无法查看图形。
- token 为 ms-agent 与 ZbxTable 平台通信的 token，可自行修改及配置,与 ms-agent 配置的 token 保持一致即可，具体可查看 ms-agent 文档https://github.com/canghai908/ms-agent

#### Startup

After modifying the configuration, use the following command to start

```
systemctl enable --now zbxtable
```

restart

```
systemctl restart zbxtable
```
Check service status

```
systemctl status zbxtable
```
一定要确保zbxtable服务是Active: active (running) 状态，如不是正常状态，建议查看日志/usr/local/zbxtable/logs/zbxtable.log

#### Debug

如启动失败或者出现错误错误，可修改通过需改程序配置文件,修改运行模式为 dev 模式,并重启 zbxtable,查看程序日志解决,日志位于 logs/zbxtable.log

### Zbxtable-Web 配置

安装好之后文件位于/usr/local/zbxtable/web
前端为纯静态文件，需使用 nginx，如机器未安装 nginx，使用以下命令安装 nginx

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

使用http://ip:8088 即可访问系统，系统默认账号：admin 密码：Zbxtable

### ms-agent 配置

#### 初始化配置

ms-agent 需使用 zbxtable 命令完成在 Zabbix Server 的配置,包括创建用户,配置动作等配置。配置过程如下,确保 ZbxTable 配置文件里的 Zabbix Server 信息配置正确

```
cd /usr/local/zbxtable
./zbxtable install
```

显示如下日志

```
2020/07/18 23:22:16.881 [I] [install.go:43]  Zabbix API Address: http://zabbix-server/api_jsonrpc.php
2020/07/18 23:22:16.881 [I] [install.go:44]  Zabbix Admin User: Admin
2020/07/18 23:22:16.881 [I] [install.go:45]  Zabbix Admin Password: xxxxx
2020/07/18 23:22:17.716 [I] [install.go:52]  登录zabbix平台成功!
2020/07/18 23:22:17.879 [I] [install.go:69]  创建告警媒介成功!
2020/07/18 23:22:18.027 [I] [install.go:82]  创建告警用户组成功!
2020/07/18 23:22:18.198 [I] [install.go:113]  创建告警用户成功!
2020/07/18 23:22:18.198 [I] [install.go:114]  用户名:ms-agent
2020/07/18 23:22:18.198 [I] [install.go:115]  密码:xxxx
2020/07/18 23:22:18.366 [I] [install.go:167]  创建告警动作成功!
2020/07/18 23:22:18.366 [I] [install.go:168]  插件安装完成!
```

表示配置成功.此步骤会在 Zabbix Server 创建 ms-agent，密码为随机，并配置相关 Action 和 Media Type，并关联到用户.

#### 环境信息

环境信息

| 程序     | 路径                                  | 作用                                             |
| :------- | :------------------------------------ | :----------------------------------------------- |
| ms-agent | /usr/lib/zabbix/alertscripts/ms-agent | 接收 Zabbix 平台产生的告警并发送到 ZbxTable 平台 |
| app.ini  | /etc/ms-agent/app.ini                 | ms-agent 配置文件                                |

如果你的 Zabbix Server 的 alertscripts 目录不为/usr/lib/zabbix/alertscripts/ 需要移动 ms-agen 到你的 zabbix server 的 alertscripts 目录下即可,否则会在 Zabbix 告警页面出现找不到 ms-agent 的错误提示，也无法收到告警消息。
也可以修改 Zabbix Server 的配置文件，将 alertscripts 目录指向/usr/lib/zabbix/alertscripts/

vi zabbix_server.conf

```
AlertScriptsPath=/usr/lib/zabbix/alertscripts
```

修改后重启 Zabbix Server 生效

#### 配置文件

/etc/ms-agent/app.ini 为程序配置文件，默认内容如下

```
[app]
Debug = 1
LogSavePath = /tmp
Host = http://192.168.10.10:8088/v1/receive
Token = ec573cf7388da56916f75ba9bbe46a69
```

Debug 为程序日志级别 0 是 debug，1 为 info

LogSavePath 为日志目录，默认为/tmp 目录

Host 为 ZbxTable 系统地址，默认为 http 服务器 IP+/v1/receive

Token 与 ZbxTable 通信的 Token,可自行修改,需要与 ZbxTable 平台配置保持一致即可，否则无法接收告警。

#### Debug

可修改配置文件打开 Debug 模式，查看日志文件名格式如下/tmp/ms-agent_yyyymmdd.log
