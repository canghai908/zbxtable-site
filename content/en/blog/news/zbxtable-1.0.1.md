---
author: "canghai809"
date: 2020-07-24 19:00:32
title: "zbxtable 1.0"
linkTitle: "zbxtable 1.0"
---

## Introduction

ZbxTable is an open source Zabbix reporting system developed using Go language. The basic features are as follows:

- 导出监控指标特定时间段内的详情数据与趋势数据到 xlsx
- 导出特定时间段内 Zabbix 的告警消息到 xlsx
- 对特定时间段研内的告警消息进行分析，告警 Top10 等
- 按照主机组导出巡检报告
- 对 Zabbix 图形按照数类型进行显示和查看并支持导出到 pdf
- 主机未恢复告警显示和查询

## Architecture

![1](https://img.cactifans.com/wp-content/uploads/2020/07/zbxtable.png)

## Component

ZbxTable: Back-end program written using beego framework

ZbxTable-Web: Frontend written in React

MS-Agent: Installed on Zabbix Server, used to receive alarms generated by Zabbix Server and send them to ZbxTable platform

## Documentation

[Documentation](/en/docs/)

## Demo

[https://zbx.cactifans.com](https://zbx.cactifans.com)

## Compatibility

| zabbix version | Compatibility           |
| :---------- | :---------------- |
| 5.0.x LTS   | ✅                |
| 4.4.x       | ✅                |
| 4.2.x       | ✅                |
| 4.0.x LTS   | ✅                |
| 3.4.x       | ❓ 理论支持未测试 |
| 3.2.x       | ❓ 理论支持未测试 |
| 3.0.x LTS   | ❓ 理论支持未测试 |

## Source code and RPM package

## 1.Source code

ZbxTable: [https://github.com/canghai908/zbxtable](https://github.com/canghai908/zbxtable)

ZbxTable-Web: [https://github.com/canghai908/zbxtable-web](https://github.com/canghai908/zbxtable-web)

MS-Agent: [https://github.com/canghai908/ms-agent](https://github.com/canghai908/ms-agent)

## 2.RPM

ZbxTable: [https://dl.cactifans.com/zabbix/zbxtable-1.0.0-1.el7.x86_64.rpm](https://dl.cactifans.com/zabbix/zbxtable-1.0.0-1.el7.x86_64.rpm)

ZbxTable-Web: [https://dl.cactifans.com/zabbix/zbxtable-web-1.0.0-1.el7.x86_64.rpm](https://dl.cactifans.com/zabbix/zbxtable-web-1.0.0-1.el7.x86_64.rpm)

MS-Agent: [https://dl.cactifans.com/zabbix/ms-agent-1.0.0-1.el7.x86_64.rpm](https://dl.cactifans.com/zabbix/ms-agent-1.0.0-1.el7.x86_64.rpm)

System default account: admin Password: Zbxtable

## Team

Back-end development

[canghai908](https://github.com/canghai908)

Front-end development

[ahyiru](https://github.com/ahyiru)

## Screenshot

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
