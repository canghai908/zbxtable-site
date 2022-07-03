---
author: "canghai809"
date: 2022-07-02 0:00:32
title: "zbxtable 2.0"
linkTitle: "zbxtable 2.0"
---

## 系统介绍
ZbxTable 是使用 Go 语言开发的一个开源的 Zabbix 报表系统，距离上次ZbxTable发布已有2年，随着Zabbix版本的变化，本次推出ZbxTable 2.0版本
主要功能如下：

- 按照主机类型，展示或导出主机资源
- 简单资产管理，资源状态总览
- 主机资源TOP5
- 多套Zabbix资源告警接入、统计、分析、导出
- 自定义绘制拓扑图，拓扑图可实时更新
- 按照主机组导出巡检报告
- 链路流量自动报表输出及邮件通知
- 自定义资产绑定

## 系统架构

![1](https://img.cactifans.com/wp-content/uploads/2020/07/zbxtable.png)

## 组件介绍

ZbxTable: 使用 Beego 框架编写的后端程序

ZbxTable-Web: 使用 Vue 编写的前端

MS-Agent: 安装在 Zabbix Server 上,用于接收 Zabbix Server 产生的告警，并发送到 ZbxTable 平台

## 文档

[文档](/docs/)

## 在线体验

直接点击登录即可

[https://zbx.cactifans.com](https://zbx.cactifans.com)

## 版本兼容


| zabbix 版本  | 兼容性     |
| :---------- |:--------|
| 6.0.x          | ✅       |
| 5.4.x          | ✅       |
| 5.2.x          | ✅       |
| 5.0.x LTS      | ✅       |
| 4.4.x          | ✅       |
| 4.2.x          | ✅       |
| 4.0.x LTS      | ✅       |
| 3.4.x          | 未测试     |
| 3.2.x          | 未测试     |
| 3.0.x LTS      | 未测试     |

## 源码及 RPM 包

## 1.源码

ZbxTable: [https://github.com/canghai908/zbxtable](https://github.com/canghai908/zbxtable)

ZbxTable-Web: [https://github.com/canghai908/zbxtable-web](https://github.com/canghai908/zbxtable-web)

MS-Agent: [https://github.com/canghai908/ms-agent](https://github.com/canghai908/ms-agent)

## 2.二进制包：
二进制包可用于部署在Linux系统，如CentOS，Ubuntu,Debian等Linux系统下

ZbxTable: [http://dl.cactifans.com/zbxtable/zbxtable-2.0.0.tar.gz](http://dl.cactifans.com/zbxtable/zbxtable-2.0.0.tar.gz)

ZbxTable-Web: [http://dl.cactifans.com/zbxtable/web.tar.gz](http://dl.cactifans.com/zbxtable/web.tar.gz)

MS-Agent: [http://dl.cactifans.com/zbxtable/ms-agent-1.0.3.tar.gz](http://dl.cactifans.com/zbxtable/ms-agent-1.0.3.tar.gz)

系统默认账号：admin 密码：Zbxtable

## Team

后端

[canghai908](https://github.com/canghai908)

前端

[ahyiru](https://github.com/ahyiru)

## 系统截图

系统首页
![1](https://img.cactifans.com/wp-content/uploads/2022/07/2022-07-03_192047.png)

资产管理
![1](https://img.cactifans.com/wp-content/uploads/2022/07/2022-07-03_192240.png)

状态总览
![1](https://img.cactifans.com/wp-content/uploads/2022/07/2022-07-03_192240.png)

主机列表
![1](https://img.cactifans.com/wp-content/uploads/2022/07/2022-07-03_192340.png)

主机详情
![1](https://img.cactifans.com/wp-content/uploads/2022/07/2022-07-03_192407.png)

网络设备列表
![1](https://img.cactifans.com/wp-content/uploads/2022/07/2022-07-03_192423.png)

网络设备详情
![1](https://img.cactifans.com/wp-content/uploads/2022/07/2022-07-03_192503.png)

告警分析
![1](https://img.cactifans.com/wp-content/uploads/2022/07/2022-07-03_192524.png)

告警查询
![1](https://img.cactifans.com/wp-content/uploads/2022/07/2022-07-03_192605.png)

自定义拓扑图
![1](https://img.cactifans.com/wp-content/uploads/2022/07/2022-07-03_192738.png)

拓扑图展示
![1](https://img.cactifans.com/wp-content/uploads/2022/07/2022-07-03_192817.png)

链路报表
![1](https://img.cactifans.com/wp-content/uploads/2022/07/2022-07-03_193010.png)
