---
author: "canghai809"
date: 2020-12-23 12:00:32
title: "zbxtable web 1.0.5"
linkTitle: "zbxtable web 1.0.5"
url: /releases/zbxtable-web-1.0.5.html
---

本次主要更新 zbxtable web 版本到 1.0.5 版本
**Bug修复**

- 首页自动刷新后，页面配置丢失问题

**新特性**

- 支持国际化语言切换

## 安装方式

为方便后续组件的安装和更新，zbxtable 建立了 yum 源，目前支持 centos6/7/8 系统，rpm 包采用 GPG 签名。添加 yum 源之后，可使用 yum 进行组件的安装与升级。如果你已安装 zbxtable 源可跳过此步骤。

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
### 安装 &升级
前端为纯静态页面，使用yum安装即可
```
yum makecache -y
yum install zbxtable-web -y
```
前端更新后强制刷新浏览器即可。
## 文档

帮助文档：[https://zbxtable.cactifans.com/docs/](https://zbxtable.cactifans.com/docs/)  
发布公告：[https://zbxtable.cactifans.com/blog/releases/](https://zbxtable.cactifans.com/blog/releases/)
