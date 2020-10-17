---
author: "canghai809"
date: 2020-09-03 10:00:32
title: "zbxtable 1.0.6"
linkTitle: "zbxtable 1.0.6"
url: /en/releases/zbxtable-1.0.6.html
---

本次主要更新zbxtable后端程序版本到1.0.6版本，解决zabbix 4.4.10及4.4.13版本等特定版本图形显示异常问题。zbxtable前端程序到1.0.4,解决导出PDF问题。建议尽快升级。
## 更新内容
**Bug 修复**

- 修复zabbix特定版本图形显示异常问题
- 修复前端未选中主机而导出图形PDF空白问题


## 安装方式
为方便后续组件的安装和更新，zbxtable建立了yum源，目前支持centos6/7/8系统，rpm包采用GPG签名。添加yum源之后，可使用yum进行组件的安装与升级。如果你已安装zbxtable源可跳过此步骤。
### 添加yum源
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
### 安装&更新组件
如果已安装旧的组件则会进行更新。更新前务必记得备份配置文件(conf/app.conf 文件)

备份配置文件    
```
cp /usr/local/zbxtable/conf/app.conf /opt
```
安装&更新 Zbxtable
```
yum makecache -y
yum install zbxtable -y
```
恢复之前备份的配置文件，重启 zbxtable 服务
```
\cp /opt/app.conf /usr/local/zbxtable/conf/app.conf
systemctl daemon-reload
systemctl restart zbxtable
```
查看版本信息
```
cd /usr/local/zbxtable/
./zbxtable -v
ZbxTable Version:=1.0.6
Git Commit Hash:=1b41cb53efd73bed77b32b3a9c622dbbd60b6d9f
UTC Build Time:=2020-09-03_11:22:45AM
```
确认升级成功.

安装&更新 Zbxtable-web
```
yum makecache -y
yum install zbxtable-web -y
```
前端更新后强制刷新浏览器即可。
## 文档

帮助文档：[https://zbxtable.cactifans.com/docs/](https://zbxtable.cactifans.com/docs/)	    
发布公告：[https://zbxtable.cactifans.com/blog/releases/](https://zbxtable.cactifans.com/blog/releases/)	