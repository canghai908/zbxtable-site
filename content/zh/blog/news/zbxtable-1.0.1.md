---
author: "canghai809"
date: 2020-07-24 08:40:55
title: "zbxtable 1.0正式发布"
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

可修改配置文件打开 Debug 模式，查看日志文件名格式如下/tmp/ms-agent_yyyymmdd.log
