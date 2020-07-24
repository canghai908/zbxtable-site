---
title: "安装部署"
linkTitle: "安装部署"
weight: 1
---

用 iso 引导后将会出现如下画面:<br/>
<a href="https://img.cactifans.com/wp-content/uploads/2012/06/1.png"><img class="size-full wp-image-648 aligncenter" title="1" src="https://img.cactifans.com/wp-content/uploads/2012/06/1.png" alt="" width="640" height="480" srcset="https://img.cactifans.com/wp-content/uploads/2012/06/1.png 640w, https://img.cactifans.com/wp-content/uploads/2012/06/1-300x225.png 300w" sizes="(max-width: 640px) 100vw, 640px" /></a>

直接按回车开始自动安装：<br/> <a href="https://img.cactifans.com/wp-content/uploads/2012/06/5.png"><img class="size-full wp-image-649 aligncenter" title="5" src="https://img.cactifans.com/wp-content/uploads/2012/06/5.png" alt="" width="720" height="400" srcset="https://img.cactifans.com/wp-content/uploads/2012/06/5.png 720w, https://img.cactifans.com/wp-content/uploads/2012/06/5-300x166.png 300w" sizes="(max-width: 720px) 100vw, 720px" /></a>

安装过程需要 5 分钟左右，安装好之后（启动到进度条那里会卡以下，是由于网络 ip 问题，等待，会过去的）<br/><a href="https://img.cactifans.com/wp-content/uploads/2012/06/21.png"><img class="size-full wp-image-650 aligncenter" title="21" src="https://img.cactifans.com/wp-content/uploads/2012/06/21.png" alt="" width="720" height="400" srcset="https://img.cactifans.com/wp-content/uploads/2012/06/21.png 720w, https://img.cactifans.com/wp-content/uploads/2012/06/21-300x166.png 300w" sizes="(max-width: 720px) 100vw, 720px" /></a>

安装后，默认使用静态 ip，ip 地址为 192.168.1.10，安装好之后要根据你自己的网络情况设定 IP。按一下步骤更改服务器 IP。登录系统，用户名:root 密码：cactifans.org  
登录后输入

```
system-config-network
```

回车，出现如图修改 ip<br/> <a href="https://img.cactifans.com/wp-content/uploads/2012/06/8.png"><img class="size-full wp-image-651 aligncenter" title="8" src="https://img.cactifans.com/wp-content/uploads/2012/06/8.png" alt="" width="720" height="400" srcset="https://img.cactifans.com/wp-content/uploads/2012/06/8.png 720w, https://img.cactifans.com/wp-content/uploads/2012/06/8-300x166.png 300w" sizes="(max-width: 720px) 100vw, 720px" /></a>

<a href="https://img.cactifans.com/wp-content/uploads/2012/06/10.png"><img class="size-full wp-image-653 aligncenter" title="10" src="https://img.cactifans.com/wp-content/uploads/2012/06/10.png" alt="" width="720" height="400" srcset="https://img.cactifans.com/wp-content/uploads/2012/06/10.png 720w, https://img.cactifans.com/wp-content/uploads/2012/06/10-300x166.png 300w" sizes="(max-width: 720px) 100vw, 720px" /></a>

修改完，选 ok，保存并退出
输入

```
etc/init.d/network restart
```

重启网卡
打开浏览器http://xxx.xxx.xxx.xxx/
用户名：admin 密码：admin 登录后要强制修改密码，输入要设置的密码点 ok，就进入系统了.
