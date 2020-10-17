---
title: "Compile"
linkTitle: "Compile"
weight: 6
date: 2020-07-24 19:00:32
description: >
  Introduction to install zbxtable by compiling
---

{{% pageinfo %}}
Introduction to install zbxtable by compiling
{{% /pageinfo %}}

## 说明

zbxtable 及 ms-agent 为 go 语言编写，编译需要配置 go 语言环境。zbxtable-web 为 React 编译需要使用 node 环境。

## go 语言编译环境配置

配置 go 编译环境，下载并配置 go 语言编译环境

```bash
cd /opt
wget https://dl.google.com/go/go1.14.3.linux-amd64.tar.gz
tar zxvf go1.14.3.linux-amd64.tar.gz -C /usr/local/
echo "export PATH=$PATH:/usr/local/go/bin" >>/etc/profile
source /etc/profile
go env
```

最后显示如下，表明 go 语言环境配置成功。

```
GO111MODULE=""
GOARCH="amd64"
GOBIN=""
GOCACHE="/root/.cache/go-build"
GOENV="/root/.config/go/env"
GOEXE=""
GOFLAGS=""
GOHOSTARCH="amd64"
GOHOSTOS="linux"
GOINSECURE=""
GONOPROXY=""
GONOSUMDB=""
GOOS="linux"
GOPATH="/root/go"
GOPRIVATE=""
GOPROXY="https://proxy.golang.org,direct"
GOROOT="/usr/local/go"
GOSUMDB="sum.golang.org"
GOTMPDIR=""
GOTOOLDIR="/usr/local/go/pkg/tool/linux_amd64"
GCCGO="gccgo"
AR="ar"
CC="gcc"
CXX="g++"
CGO_ENABLED="1"
GOMOD=""
CGO_CFLAGS="-g -O2"
CGO_CPPFLAGS=""
CGO_CXXFLAGS="-g -O2"
CGO_FFLAGS="-g -O2"
CGO_LDFLAGS="-g -O2"
PKG_CONFIG="pkg-config"
GOGCCFLAGS="-fPIC -m64 -pthread -fmessage-length=0 -fdebug-prefix-map=/tmp/go-build821720893=/tmp/go-build -gno-record-gcc-switches"
```

开启 go mod，由于编译过程需要联网下载依赖包，配置 go mod 代理

```
go env -w GO111MODULE=on
go env -w GOPROXY=https://goproxy.cn,direct
```

## zbxtable

### 编译

```
mkdir -p $GOPATH/src/github.com/canghai908
cd $GOPATH/src/github.com/canghai908
git clone https://github.com/canghai908/zbxtable.git
cd zbxtable
./control build
./control pack
```

编译后会生成 zbxtable-1.0.1.tar.gz,可用于部署。

### 安装

解压到/usr/local 目录下

```
tar zxvf zbxtable-1.0.1.tar.gz -C /usr/local
mv /usr/local/zbxtable-1.0.1 /usr/local/zbxtable
```

拷贝启动脚本  
如果系统为 centos6

```
cp /usr/local/zbxtable/zbxtable.init /etc/init.d/
```

centos7 及以上

```
cp /usr/local/zbxtable/zbxtable.service /lib/systemd/system/
```

### 配置

配置及启动参考[RPM 包安装配置](/docs/install/rpm/#zbxtable-配置)

## zbxtable-web

此组件编译打包需要 node 环境。  
环境：nodejs>10  
构建

```
git clone https://github.com/canghai908/zbxtable-web.git`
npm i
npm run build
```

此过程较长，请耐心等待，打包后，生成的文件在 app/build 目录下。安装配置 nginx 之后拷贝到 web 目录即可。

## ms-agent

此组件需要安装在 zabbix server 上，建议在其他机器编译好之后，手动拷贝 zabbix 机器。

### 编译

编译需要 go 语言环境

```
mkdir -p $GOPATH/src/github.com/canghai908
cd $GOPATH/src/github.com/canghai908
git clone https://github.com/canghai908/ms-agent.git
cd ms-agent
./control build
./control pack
```

编译之后会生成 ms-agent-1.0.1.tar.gz 打包文件，上传到 zabbix server

### 安装

解压

```
tar zxvf ms-agent-1.0.1.tar.gz
```

解压之后生成一个 ms-agent 二进制文件,一个 app.ini 配置文件。
拷贝 ms-agent 到你的 zabbix server 的 alertscripts 目录下。可通过修改 Zabbix Server 的配置文件，制定 alertscripts 目录。如指向/usr/lib/zabbix/alertscripts/

vi zabbix_server.conf

```
AlertScriptsPath=/usr/lib/zabbix/alertscripts
```

重启 Zabbix Server 生效.拷贝脚本

```
cp ms-agent-1.0.1/ms-agent /usr/lib/zabbix/alertscripts/
```

创建/etc/ms-agent 配置文件目录(目录必须为/etc/ms-agent)，并拷贝配置文件

```
mkdir /etc/ms-agent
cp ms-agent-1.0.1/app.ini /etc/ms-agent/
```

至此完成基本安装

### 配置

配置参考 [RPM 的 ms-agent 配置](/docs/install/rpm/#ms-agent-配置)
