---
title: "升级"
linkTitle: "升级"
weight: 5
date: 2020-07-24 19:00:32
description: >
  zbxtable版本升级
---

{{% pageinfo %}}
ZbxTable 目前最新版本 1.1.5
{{% /pageinfo %}}
## 升级ZbxTable

使用yum升级zbxtable
```
yum makecache -y
yum update zbxtable -y
```
升级完成。

### 生成配置文件

按引导生成配置文件即可
```
cd /usr/local/zbxtable/
./zbxtable init
```

#### 升级Action告警内容
如果你的版本小于1.1.3版本之前需要升级,
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
即可完成ZbxTable平台的升级
# Zbxtable-Web升级
新版本web已包含在zbxtable里，启动时自动释放到程序所谓目录的web目录下。
前端更新后强制刷新浏览器即可。
# MS-Asgent升级
```
yum makecache -y
yum update ms-agent -y
```