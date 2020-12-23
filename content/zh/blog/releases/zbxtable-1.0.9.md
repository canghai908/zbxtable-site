---
author: "canghai809"
date: 2020-11-28 01:00:32
title: "zbxtable 1.0.9"
linkTitle: "zbxtable 1.0.9"
url: /releases/zbxtable-1.0.9.html
---

ZbxTable 是一个开源的 Zabbix 报表系统.本次主要更新 zbxtable 后端程序版本到 1.0.9 版本，主要更新内容如下

## 更新内容

**Bug 修复**

- 修复 1.0.8 版本在 zabbix 5.2 版本下 ms-agent 用户权限问题
- 支持 postgresql 作为后端数据库，可在配置文件里进行切换
- 告警历史查询及导出按照发生时间降序输出显示

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

1.0.7 版本开始默认安装后只有一个 zbxtable 可执行文件，安装后需先执行以下命令进行初始化释放配置文件及字体

```
systemctl daemon-reload
systemctl restart zbxtable
```

1.0.8 版本对配置文件进行了修改，zabbix_server 修改为 zabbix_web
恢复之前备份的配置文件，注意修改。
1.0.9 版本支持后端为 postgresql 数据库，可在配置文件里进行指定。
启动 zbxtable

```
systemctl restart zbxtable
```

查看版本信息

```
cd /usr/local/zbxtable/
./zbxtable -v
ZbxTable Version:=1.0.9
Git Commit Hash:=0eefde0edaf893248c9c7bc81613f4c650d523e4
UTC Build Time:=2020-11-28_05:23:21AM
```

确认升级成功

安装&更新 Zbxtable-web

```
yum makecache -y
yum install zbxtable-web -y
```

前端更新后强制刷新浏览器即可。

## 文档

帮助文档：[https://zbxtable.cactifans.com/docs/](https://zbxtable.cactifans.com/docs/)  
发布公告：[https://zbxtable.cactifans.com/blog/releases/](https://zbxtable.cactifans.com/blog/releases/)
