---
author: "canghai809"
date: 2021-08-15 00:01:32
title: "zbxtable 1.1.5"
linkTitle: "zbxtable 1.1.5"
url: /releases/zbxtable-1.1.5.html
---
ZbxTable 是一个开源的 Zabbix 报表系统.本次主要更新 zbxtable 后端程序版本到 1.1.5 版本,建议尽快更新,主要更新内容如下:    
**新特性**
- 适配zabbix 5.4版本


**Bug修复**

- 修复zabbix 5.4版本主机列表显示异常
- 修复jwt依赖包安全问题

## 全新安装
全新安装可查看安装文档[RPM 包安装配置](https://zbxtable.cactifans.com/docs/install/rpm/)

## 升级

如果已安装ZbxTable老版本，则需要按照以下步骤进行升级
```
yum makecache -y
yum update zbxtable -y
```
前端web为静态页面，删除旧的web目录，后端启动会自动释放最新的前端静态文件到web目录
```
rm -rf /usr/local/zbxtable/web
```
即可完成zbxtable版本升级，重启ZbxTable。
```
systemctl daemon-reload
systemctl restart zbxtable
```
对于启动出现数据库连接失败的，建议使用以下命令，重新初始化生成配置文件（注意备份旧的配置文件conf/app.conf）
```
cd /usr/local/zbxtable/
./zbxtable init
```
**注意：此命令会重新生成配置文件中的token字符串，务必确保与ms-agent配置文件中的token保持一致，否则会影响告警信息发送到ZbxTable。**
## 源码
https://github.com/canghai908/zbxtable

## 文档

帮助文档：[https://zbxtable.cactifans.com/docs/](https://zbxtable.cactifans.com/docs/)      
发布公告：[https://zbxtable.cactifans.com/blog/releases/](https://zbxtable.cactifans.com/blog/releases/)   
FAQ:   [https://zbxtable.cactifans.com/docs/faq/faq/](https://zbxtable.cactifans.com/docs/faq/faq/)

## 反馈
https://github.com/canghai908/zbxtable/issues