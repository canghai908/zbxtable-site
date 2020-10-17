---
author: "canghai809"
date: 2020-07-27 19:00:32
title: "zbxtable 1.0.2"
linkTitle: "zbxtable 1.0.2"
url: /en/releases/zbxtable-1.0.2.html
---

zbxtable 1.0.2 版本修复编译缓存问题，请大家尽快更新。

## 更新内容

**Bug 修复**

- 修复编译缓存问题

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
安装 Zbxtable

```
yum install zbxtable -y
```

安装 Zbxtable-Web

```
yum install zbxtable-web -y
```

安装 ms-agent

```
yum install ms-agent -y
```

## 文档

考虑后续文档及问题汇总，后续使用及配置可查看 Zbxtable 网站，
[https://zbxtable.cactifans.com/](https://zbxtable.cactifans.com/)
帮助文档：[https://zbxtable.cactifans.com/docs/](https://zbxtable.cactifans.com/docs/)
发布公告：[https://zbxtable.cactifans.com/blog/releases/](https://zbxtable.cactifans.com/blog/releases/)
