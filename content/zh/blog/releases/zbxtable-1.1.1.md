---
author: "canghai809"
date: 2020-12-24 12:00:32
title: "zbxtable 1.1.1"
linkTitle: "zbxtable 1.1.1"
url: /releases/zbxtable-1.1.1.html
---
ZbxTable 是一个开源的 Zabbix 报表系统.本次主要更新 zbxtable 后端程序版本到 1.1.1 版本，主要更新内容如下

**新特性**

- 打包前端文件到二进制文件,初始化时自动释放.不再独立发布ZbxTable-Web的rpm包

**Bug修复**

- 修复告警特殊字符导致告警消入库失败


## 全新安装
配置[RPM 包安装配置](/docs/install/rpm/)

## 升级

如果已安装ZbxTable老版本，则需要按照以下步骤进行升级
```
yum makecache -y
yum update zbxtable -y
```
由于老版本Action格式问题，特殊字符可造成告警无法入库情况，需升级Action。操作如下
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
## 文档

帮助文档：[https://zbxtable.cactifans.com/docs/](https://zbxtable.cactifans.com/docs/)      
发布公告：[https://zbxtable.cactifans.com/blog/releases/](https://zbxtable.cactifans.com/blog/releases/)    

