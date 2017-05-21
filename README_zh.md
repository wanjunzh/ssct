# ShadowSocks ConnecTion

[![ssct](https://img.shields.io/badge/Platform-%20Linux%20%7C%20MACOS-brightgreen.svg)](ssct)
[![Documentation Status](https://img.shields.io/badge/English-latest-brightgreen.svg)](README.md)

`ssct`是封装了 [shadowsocks](https://github.com/shadowsocks/shadowsocks) 更易用的代理工具。

## 快速开始

### 自动连接

直接在终端执行`ssct`，`ssct`会自动从 [ishadowsocks](http://ss.ishadowx.com) 获取服务器信息并自动连接。

### 连接特定服务器

首先获取可用的服务器信息。

```
ssct --list
```

然后连接特定服务器。

```
ssct -n 5
```

另外，也可以连接已有的其它服务器。

```
ssct -s <server_addr> -p <server_port> -l <local_port> -k <password> -m <method>
```

## 使用指南

### 依赖解决

1 安装 shadowsocks

```
# for python2
pip install shadowsocks
# for python3
pip3 install shadowsocks
```

**Note:** shadowsocks 也可以通过系统包管理器安装 (apt, yum, dnf, etc) 或者安装 chrome app 版本 [shadowsocks](https://chrome.google.com/webstore/detail/shadowsocks/fnhhahhihediajgefcnlpdmnogndblbi?utm_source=chrome-app-launcher-info-dialog)。但 chrome app 版本需手动填写服务器信息。

2 安装 python3 模块

```
pip3 install requests
pip3 install prettytable
```

**Note:** `prettytable`模块不是必须，但会使`--list`显示结果更友好。

### 谷歌浏览器配置

1. 安装扩展程序 [SwitchyOmega](https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif)。
2. 打开 SwitchyOmega 选项并作如下配置。
![set switchyomega proxy](img/config-swithyomega.png)
3. 获取所有服务器信息并连接，也可以通过`ssct`自动连接。
![start ssct](img/start-ssct.png)
4. 在谷歌浏览器中选择 proxy 代理。  
![select proxy option](img/chrome-proxy.png)

### 火狐浏览器配置

1. 安装扩展程序 [AutoProxy](https://addons.mozilla.org/en-us/firefox/addon/autoproxy)。
2. 打开 AotoProxy 选项，编辑服务器信息并添加 shadowsocks。
![edit proxy server](img/edit-autoproxy-server.png)
3. 启动 ssct 并选择 shadowsocks 代理。

**Note:** 关于 AutoProxy，[更多帮助信息](https://autoproxy.org/getting_started)。

## 更多参数

```
optional arguments:
  -h, --help         show this help message and exit

ssct options:
  -n <num>           connect server number
  --ss <ss>          path to shadowsocks, assumed in the PATH
  --list             list all ss servers
  --stop             stop running servers
  --version          show program's version number and exit
  --morehelp         show this help message and exit

shadowsocks options:
  -c <config>        path to config file
  -s <addr>          server address, auto crawl online
  -p <port>          server port, auto crawl online
  -b <addr>          local binding address [default: 127.0.0.1]
  -l <port>          local port [default: 1080]
  -k <password>      password, auto crawl online
  -m <method>        encryption method, auto crawl online
  -t <timeout>       timeout in seconds [default: 300]
  --fast-open        use TCP_FASTOPEN, requires Linux 3.7+
  -d <daemon>        daemon mode, one of start, stop and restart
  --pid-file <file>  pid file for daemon mode
  --log-file <file>  log file for daemon mode
  --user <user>      username to run as
  -v, -vv            verbose mode
  -q, -qq            quiet mode, only show warnings/errors
```

如不使用参数，`ssct`会自动获取并连接可用服务器。

## 许可

无任何版权限制，随意使用。
