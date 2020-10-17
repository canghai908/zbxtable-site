---
author: "canghai809"
date: 2020-08-18 16:00:32
title: "zbxtable 1.0.5"
linkTitle: "zbxtable 1.0.5"
url: /en/releases/zbxtable-1.0.5.html
---

本次主要更新 zbxtable 后端程序版本到 1.0.5 版本，主要修复导出 PDF 问题，建议尽快升级。

## 更新内容

**Bug 修复**

- 修复图形导出到 PDF 卡死问题
- 修复导出 PDF 出现空白页的问题
- 修复导出 PDF 表头时间错误问题
- 移除部分冗余代码

## 安装方式

为方便后续组件的安装和更新，zbxtable 建立了 yum 源，目前支持 centos6/7/8 系统，rpm 包采用 GPG 签名。添加 yum 源之后，可使用 yum 进行组件的安装与升级。

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

### 安装&更新组件

如果已安装旧的组件则会进行更新。**更新前务必记得备份配置文件**(conf/app.conf 文件)  
安装&更新 Zbxtable

```
yum makecache -y
yum install zbxtable -y
```

**恢复之前备份的配置文件**，重启 zbxtable 服务

```
systemctl daemon-reload
systemctl restart zbxtable
```

查看版本信息

```
cd /usr/local/zbxtable/
./zbxtable -v
ZbxTable Version:=1.0.5
Git Commit Hash:=f49671b4e85f9eb1c36fc5e448b2c54a9c829bbc
UTC Build Time:=2020-08-18_04:27:38PM
```

确认升级成功

## 文档

帮助文档：[https://zbxtable.cactifans.com/docs/](https://zbxtable.cactifans.com/docs/)  
发布公告：[https://zbxtable.cactifans.com/blog/releases/](https://zbxtable.cactifans.com/blog/releases/)
