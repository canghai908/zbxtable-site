---
author: "canghai809"
date: 2020-08-18 10:00:32
title: "zbxtable web 1.0.3"
linkTitle: "zbxtable web 1.0.3"
url: /en/releases/zbxtable-web-1.0.3.html
---

本次主要更新 zbxtable web 版本到 1.0.3 版本

## 更新内容

**Bug 修复**

- 修复首页触发器与问题接口调用错误问题。
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

如果已安装旧的组件则会进行更新。**更新前务必记得备份配置文件**
安装&更新 Zbxtable

```
yum install zbxtable-web -y
```

## 文档

考虑后续文档及问题汇总，后续使用及配置可查看  
帮助文档：[https://zbxtable.cactifans.com/docs/](https://zbxtable.cactifans.com/docs/)  
发布公告：[https://zbxtable.cactifans.com/blog/releases/](https://zbxtable.cactifans.com/blog/releases/)
