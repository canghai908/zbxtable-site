---
title: "常见问题"
linkTitle: "常见问题"
weight: 5
date: 2020-07-24 19:00:32
description: >
  常见问题的处理方式
---
#### Q1:ZbxTable是否必须要安装在Zabbix Server服务器
ZbxTable通过Zabbix API与Zabbix Server进行通信，不需要安装在Zabbix Server服务器上，只需要能访问Zabbix Web页面即可。MS-Agent必须安装在Zabbix Server所在机器。   
#### Q2:ZbxTable里告警查询为空
ZbxTable里告警查询和告警分析里的告警来自于MS-Agent发送，不包含MS-Agent插件安装之前的告警。如已配置MS-Agent，可检查MS-Agent配置文件里的地址及token是否正确，建议配置debug=0，查看日志处理。
#### Q3:ZbxTable密码丢失
ZbxTable默认创建管理员账号为admin，如密码丢失可在数据库中删除admin用户，重启ZbxTable即可重新生成admin用户，默认密码为Zbxtable
#### Q4:巡检报告导出数据为空
目前ZbxTable只能按照组进行巡检，只能导出Linux和Windows服务器的巡检数据。
#### Q5:首页问题统计与告警信息数量不一致
问题统计为平台所有主机问题统计，包含禁用主机等。表格内为为未恢复实时告警，不包含禁用主机。