---
author: "canghai809"
date: 2020-12-23 11:00:32
title: "ms-agent 1.0.3"
linkTitle: "ms-agent 1.0.3"
url: /releases/ms-agent-1.0.3.html
---
Ms-Agent 是一个开源的zabbix告警消息组件，需要安装到Zabbix Server上，采集Zabbix的告警信息并发送到ZbxTable平台

## V1.0.3版本更新内容
**新特性**

- 支持多台Zabbix告警采集到同一个ZbxTable平台

## 安装方式

为方便后续组件的安装和更新，zbxtable 建立了 yum 源，目前支持 centos6/7/8 系统，rpm 包采用 GPG 签名。添加 yum 源之后，可使用 yum 进行组件的安装与升级。如果你已安装 zbxtable 源可跳过此步骤。MS-Agent必须安装在Zabibx Server所在服务器。

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
在ZabTable上完成配置MS-Agent脚本后，可在Zabbix Serve上按照如下方法安装MS-Agent  
使用yum方式安装zbxtable
```
yum makecache -y
yum install ms-agent -y
```
修改配置文件
```
vi /etc/ms-agent/app.ini
```
配置文件结构如下
```
[app]
Debug = 1
TenantID = zabbix01
LogSavePath = /tmp
Host = http://192.168.10.10:8088/v1/receive
Token = ec573cf7388da56916f75ba9bbe46a69
```
配置文件说明如下
>新版本增加TenantID字段，可配置为唯一值，方便区别多套zabbix。   
>Token字段需要与ZbxTable配置文件里的Token字段保持一致，否则无法采集告警信息。   
>Host为ZbxTable访问地址，根据实际修改   

默认ms-agent二进制文件路径位于
```
/usr/lib/zabbix/alertscripts/ms-agent
```
yum安装的zabbix server默认alertscripts路径为此路径。如果你的zabibx的alertscripts路径不为此，需要拷贝ms-agent二进制文件到alertscripts路径路径下。
### 升级
使用yum方式安装zbxtable
```
yum makecache -y
yum update ms-agent -y
```
升级后注意修改新的配置文件，并移动二进制文件到你的zabibx的alertscripts路径下，覆盖旧的版本。

### 使用
配置完成后，Zabbix产生告警后，Zabbix页面会显示告警已发送到MS-Agent，可在ZbxTable平台查看告警信息。如出现红色Failed，一般为ms-agent二进制文件路径不对，根据提示拷贝到对应路径即可。
### Debug
如Zabbix页面提示已发送，ZbxTable平台未收到。可修改/etc/ms-agent/app.ini配置文件，将Debug模式打开
```
Debug = 0
```
下次告警产生后会在/tmp/目录下生成日志文件，日志文件名称如下ms-agent_yyyymmdd.log 根据日志错误提示修改，一般为Token配置与ZbxTable平台不一致或者ZbxTable平台地址错误导致，修改后即可生效。

## 文档

帮助文档：[https://zbxtable.cactifans.com/docs/](https://zbxtable.cactifans.com/docs/)  
发布公告：[https://zbxtable.cactifans.com/blog/releases/](https://zbxtable.cactifans.com/blog/releases/)
