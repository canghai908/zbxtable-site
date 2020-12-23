---
author: "canghai809"
date: 2020-12-23 12:00:32
title: "zbxtable 1.1.0"
linkTitle: "zbxtable 1.1.0"
url: /en/releases/zbxtable-1.1.0.html
---
ZbxTable 是一个开源的 Zabbix 报表系统.本次主要更新 zbxtable 后端程序版本到 1.1.0 版本，主要更新内容如下

## V1.1.0版本更新内容
**新特性**

- 前端国际化支持
- 优化ms-agent安装脚本
- 告警分析支持多zabbix server
- 配置文件响应式生成及连接检查
- 老版本配置文件及Zabbix Action内容升级
- 告警字段增加到16个


**Bug 修复**

- 修复首页问题统计错误
- 修复导出文件名中文乱码问题
- 修复告警统计中文乱码

## 安装方式

为方便后续组件的安装和更新，zbxtable 建立了 yum 源，目前支持 centos6/7/8 系统，rpm 包采用 GPG 签名。添加 yum 源之后，可使用 yum 进行组件的安装与升级。如果你已安装 zbxtable 源可跳过此步骤。ZbxTable可安装在zabibx 服务器上，也可以安装在其他服务器上。

### 添加 yum 源

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
### 全新安装
使用yum方式安装zbxtable
```
yum makecache -y
yum install zbxtable -y
```
新版本配置文件需要手动生成，生成步骤如下:
```
cd /usr/local/zbxtable/
./zbxtable init
```
会进入交互式命令行，根据实际情况输入数据库账号及密码，以及zabbix连接信息，最后确认即可生成配置文件。如数据库及zabbix连接错误，会要求重新输入连接信息，否则无法生成配置文件。
```
✔ mysql
✔ DBHost: localhost
DBName: zbxtable
DBUser: zbxtable
DBPass: zbxtablepwd123
DBPort: 3306
Connected to database zbxtable successfully!
Zabbix Web URL: http://192.168.10.10
✔ Zabbix Username: Admin
Zabbix Password: zabbix
Connected to zabbix web successfully！Zabbix version is  4.2.5
The configuration information is as follows:
ZbxTable dbtype: mysql
ZbxTable dbhost: localhost
ZbxTable dbname: zbxtable
ZbxTable dbuser: zbxtable
ZbxTable dbpass: zbxtablepwd123
ZbxTable dbport: 3306
Zabbix Web URL: http://10.110.200.12
Zabbix Username: Admin
Zabbix Password: zabbix
✔ Yes
The configuration file ./conf/app.conf is generated successfully!
```
### 配置MS-Agent
MS-Agent为告警消息采集客户端，采集zabbix产生的告警信息，并发送到ZbxTable平台，zbxtable需要在zabbix server上配置对应的Action等。配置步骤如下
```
cd /usr/local/zbxtable/
./zbxtable install
```
执行后会根据之前提供的zabbix信息，配置action，输出如下
```
2020/12/23 18:33:46.593 [I] [install.go:109]  Zabbix API Address: http://192.168.10.10/api_jsonrpc.php
2020/12/23 18:33:46.593 [I] [install.go:109]  Zabbix Admin User: Admin
2020/12/23 18:33:46.593 [I] [install.go:109]  Zabbix Admin Password: zabbix
2020/12/23 18:33:46.736 [I] [install.go:109]  Login to zabbix successed
2020/12/23 18:33:46.845 [I] [install.go:109]  Zabbix version is 4.2.5
2020/12/23 18:33:47.007 [I] [app.go:528]  Create media type successfully!
2020/12/23 18:33:47.140 [I] [app.go:528]  Create user group successfully!
2020/12/23 18:33:47.319 [I] [app.go:528]  Create alarm user successfully!
2020/12/23 18:33:47.319 [I] [app.go:528]  Username : ms-agent
2020/12/23 18:33:47.319 [I] [app.go:528]  Password : MtFqqXGaIU
2020/12/23 18:33:47.538 [I] [app.go:528]  Create alarm action successfully!
2020/12/23 18:33:47.538 [I] [app.go:528]  MS-Agent plugin configured successfully!
2020/12/23 18:33:47.538 [I] [app.go:528]  MS-Agent token is fd5d5de55df64ac3b68c5d6a1f796d9a
```
会自动在zabbix上建立一个ms-agent用户，密码为随机，权限为管理员。最后输出MS-Agent token为MS-Agent 与ZbxTable通信的token，需要和MS-Agent 配置文件里的token保持一致，否则无法正常收到告警。    
启动ZbxTable
```
systemctl start zbxtable
```
 至此ZbxTable 后台安装成功，web及nginx配置详见官网安装文档

### 升级ZbxTable

如果已安装ZbxTable老版本，则需要按照以下步骤进行升级
```
yum makecache -y
yum update zbxtable -y
```
安装完成后，新版本配置文件与老版本配置文件有差异，需先升级配置文件到最新版本
#### 升级配置文件
```
cd /usr/local/zbxtable/
./zbxtable uc
```
输入如下，表示配置文件升级成功
```
2020/12/23 19:31:21.349 [I] [app.go:528]  Start upgrading the old configuration file!
2020/12/23 19:31:21.355 [I] [updateconf.go:39]  Connected to database zbxtable successfully!
2020/12/23 19:31:21.617 [I] [updateconf.go:39]  Connected to zabbix web successfully！Zabbix version is : 4.2.5
2020/12/23 19:31:21.617 [I] [app.go:528]  Successfully upgraded the old configuration file!
```
表示升级成功。
#### 升级Action告警内容
由于新版本对告警结构体发生了变化，因此需要更新在zabbix上的action内容，更新步骤如下
```
cd /usr/local/zbxtable/
./zbxtable ua
```
输入如下
```
2020/12/23 18:52:16.232 [I] [updateaction.go:61]  Zabbix API Address: http://192.168.10.10/api_jsonrpc.php
2020/12/23 18:52:16.232 [I] [updateaction.go:61]  Zabbix Admin User: Admin
2020/12/23 18:52:16.232 [I] [updateaction.go:61]  Zabbix Admin Password: zabbix
2020/12/23 18:52:16.366 [I] [updateaction.go:61]  Login to zabbix successed
2020/12/23 18:52:16.476 [I] [updateaction.go:61]  Zabbix version is 4.2.5
2020/12/23 18:52:16.806 [I] [app.go:528]  Update MS-Agent Action successed
```
表示升级成功。
启动ZbxTable
```
systemctl start zbxtable
```

# Zbxtable-Web
Zbxtable-Web为ZbxTable前端页面，新版本已支持国际化，建议升级。
```
yum makecache -y
yum install zbxtable-web -y
```
前端更新后强制刷新浏览器即可。

## 文档

帮助文档：[https://zbxtable.cactifans.com/docs/](https://zbxtable.cactifans.com/docs/)      
发布公告：[https://zbxtable.cactifans.com/blog/releases/](https://zbxtable.cactifans.com/blog/releases/)    

