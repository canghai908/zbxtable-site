---
author: "canghai809"
date: 2020-07-24 19:00:32
title: "zbxtable 1.0"
linkTitle: "zbxtable 1.0"
---

## 系统介绍

ZbxTable 是使用 Go 语言开发的一个开源的 Zabbix 报表系统。基本功能如下：

- 导出监控指标特定时间段内的详情数据与趋势数据到 xlsx
- 导出特定时间段内 Zabbix 的告警消息到 xlsx
- 对特定时间段研内的告警消息进行分析，告警 Top10 等
- 按照主机组导出巡检报告
- 对 Zabbix 图形按照数类型进行显示和查看并支持导出到 pdf
- 主机未恢复告警显示和查询

## 系统架构

![1](https://img.cactifans.com/wp-content/uploads/2020/07/zbxtable.png)

## 组件介绍

ZbxTable: 使用 beego 框架编写的后端程序

ZbxTable-Web: 使用 React 编写的前端

MS-Agent: 安装在 Zabbix Server 上,用于接收 Zabbix Server 产生的告警，并发送到 ZbxTable 平台

## 文档

[文档](/docs/)

## 在线体验

直接点击登录即可

[https://zbx.cactifans.com](https://zbx.cactifans.com)

## 兼容性

| zabbix 版本 | 兼容性            |
| :---------- | :---------------- |
| 5.0.x LTS   | ✅                |
| 4.4.x       | ✅                |
| 4.2.x       | ✅                |
| 4.0.x LTS   | ✅                |
| 3.4.x       | ❓ 理论支持未测试 |
| 3.2.x       | ❓ 理论支持未测试 |
| 3.0.x LTS   | ❓ 理论支持未测试 |

## 源码及 RPM 包

## 1.源码

ZbxTable: [https://github.com/canghai908/zbxtable](https://github.com/canghai908/zbxtable)

ZbxTable-Web: [https://github.com/canghai908/zbxtable-web](https://github.com/canghai908/zbxtable-web)

MS-Agent: [https://github.com/canghai908/ms-agent](https://github.com/canghai908/ms-agent)

## 2.RPM 包：

ZbxTable: [https://dl.cactifans.com/zabbix/zbxtable-1.0.0-1.el7.x86_64.rpm](https://dl.cactifans.com/zabbix/zbxtable-1.0.0-1.el7.x86_64.rpm)

ZbxTable-Web: [https://dl.cactifans.com/zabbix/zbxtable-web-1.0.0-1.el7.x86_64.rpm](https://dl.cactifans.com/zabbix/zbxtable-web-1.0.0-1.el7.x86_64.rpm)

MS-Agent: [https://dl.cactifans.com/zabbix/ms-agent-1.0.0-1.el7.x86_64.rpm](https://dl.cactifans.com/zabbix/ms-agent-1.0.0-1.el7.x86_64.rpm)

系统默认账号：admin 密码：Zbxtable

## Team

后端

[canghai908](https://github.com/canghai908)

前端

[ahyiru](https://github.com/ahyiru)

## 系统截图

系统登录
![1](https://img.cactifans.com/wp-content/uploads/2020/07/C893A6D6-D4BC-4E0F-A087-2826E6D12699.png)

系统首页
![1](https://img.cactifans.com/wp-content/uploads/2020/07/BA043817-6994-44FE-8FC2-36D2561C0C92.png)

主机列表
![1](https://img.cactifans.com/wp-content/uploads/2020/07/7F477F6C-8BB0-4042-A643-0D3902C706E3.png)

图形管理
![1](https://img.cactifans.com/wp-content/uploads/2020/07/6F1BD4F7-B185-4D49-A48C-4E9E0E6900A4.png)

图形导出
![1](https://img.cactifans.com/wp-content/uploads/2020/07/2DE17FD9-320B-4685-BCEF-08BFA834A8F7.png)

指标导出
![1](https://img.cactifans.com/wp-content/uploads/2020/07/99E941CE-0018-4AB3-A8B0-35795FA852FA.png)

巡检报告导出
![1](https://img.cactifans.com/wp-content/uploads/2020/07/88B8D652-183A-4595-ACFD-47157FD230FB.png)

告警分析
![1](https://img.cactifans.com/wp-content/uploads/2020/07/482304D1-FD67-4C09-B6E5-7D0660D69556.png)

告警导出
![1](https://img.cactifans.com/wp-content/uploads/2020/07/D2C82FC2-D6F2-472C-BA32-F8825A12F7CA.png)
