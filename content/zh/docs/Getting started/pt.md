---
title: "111"
linkTitle: "111"
weight: 3
---

{{% pageinfo %}}
This is a placeholder page that shows you how to use this template site.
{{% /pageinfo %}}

Information in this section helps your user try your project themselves.

- What do your users need to do to start using your project? This could include downloading/installation instructions, including any prerequisites or system requirements.

- Introductory “Hello World” example, if appropriate. More complex tutorials should live in the Tutorials section.

Consider using the headings below for your getting started page. You can delete any that are not applicable to your project.

## Prerequisites

Are there any system requirements for using your project? What languages are supported (if any)? Do users need to already have any software or tools installed?

## Installation

Where can your user find your project code? How can they install it (binaries, installable package, build from source)? Are there multiple options/versions they can install and how should they choose the right one for them?

## Setup

Is there any initial setup users need to do after installation to try your project?

## Try it out!

Can your users test their installation, for example by running a command or deploying a Hello World example?

CactiFans 中文版 V1.0 的小 Tips，帮大家更好的使用。

### 一.修改系统密码

ssh 登录上去执行

```shell
passwd root
```

根据提示输入新密码就可以修改系统密码

### 二.修改 Nagios 密码

Nagios 的登录地址为：http://192.168.1.10/nagios/ （系统默认 Ip 地址为：192.168.1.10）  
登录的用户名为：nagiosadmin

执行以下命令修改 nagios 登录密码

```shell
cd /etc/nagios
htpasswd -bc passwd nagiosadmin XXXXXX
```

根据提示输入新密码就可以修改系统密码  
XXXXXX 是你要设置的密码

### 三.修改 nconf 密码

nconf 的登录地址为：http://192.168.1.10/nconf/  
nconf 的登录用户名为：admin  
执行以下命令修改 nconf 的登录密码<!--more-->

```shell
cd /usr/share/nconf/config
vi .file_accounts.php
```

就可以看到 admin 的密码，是明文的，修改为你要的密码保存退出就生效了。  
<a href="https://www.cactifans.org/index.php/2012/12/cactifans-v1-0%e4%b8%ad%e6%96%87%e7%89%88tips/2012-12-13_203522/" rel="attachment wp-att-712"><img class="alignleft size-full wp-image-712" alt="2012-12-13_203522" src="https://img.cactifans.com/wp-content/uploads/2012/12/2012-12-13_203522.png" width="905" height="426" srcset="https://img.cactifans.com/wp-content/uploads/2012/12/2012-12-13_203522.png 905w, https://img.cactifans.com/wp-content/uploads/2012/12/2012-12-13_203522-300x141.png 300w" sizes="(max-width: 905px) 100vw, 905px" /></a>

###

### 四.修改 weathermap 编辑密码

由于 Weathermap 没有对编辑拓扑图的 editor.php 做验证，而导致任何人都可以编辑拓扑图，这个问题在 weathermap 官网是提到过的, 传送门：<http://www.network-weathermap.com/manual/latest/pages/install-cacti-editor.html>容易被忽视，网上也有很多没做限制的 weathmaper 图。在 CactiFans 中文版 v1.0 中，已经对 editor.php 这个文件的访问权限做了限制，访问此文件会提示输入用户名和密码  
地址：http://192.168.1.10/plugins/weathermap/editor.php   (IP 根据你自己的具体设定)  
用户名：cactifans  
执行以下命令修改 weathermap 修改密码

```shell
htpasswd -b /var/www/html/plugins/weathermap/.htpasswd cactifans XXX

```

XXX 为你要修改成的新密码

### 五. 关于字体太小的问题

由于从英文版到中文版，CactiFans 中文版 v1.0 的字体有点小，看起来不是很舒服，这是 由于 css 问题造成。我已经做好一个补丁包，只要 Patch 下就可以使字体恢复到正常大小。  
ssh 登录到 CactiFans 服务器执行如下命令

```shell
wget https://dl.cactifans.com/cactifans/patches/FixFontsize.patch
patch -p0 < FixFontsize.patch
```

再打开浏览器登录到 cacti，用 Ctrl+F5 强制刷新就可以看到字体已经恢复到正常的大小。  
好了，今天就先写到这里，以后在使用中有任何问题都可以给我留言。

### 六.关于查看图形出现 2 个周问题

由于翻译错误，导致查看图形时出 2 个周的图片，其实一个是月的，纯属翻译错误，大家可以通过以下命令修复。

```sql
mysql -uroot -pcactifansdb
use cacti;
update rra set name='月 (2小时平均)' where id='3';
exit;
```

就可以了，刷新查看图形已经更新了。

[<img class="alignleft size-full wp-image-824" alt="11" src="https://img.cactifans.com/wp-content/uploads/2013/03/11.png" width="645" height="481" srcset="https://img.cactifans.com/wp-content/uploads/2013/03/11.png 645w, https://img.cactifans.com/wp-content/uploads/2013/03/11-300x223.png 300w" sizes="(max-width: 645px) 100vw, 645px" />](https://img.cactifans.com/wp-content/uploads/2013/03/11.png)
