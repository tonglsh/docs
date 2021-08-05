# linux 命令

## 代理：

1. 简单纯粹方式
```
设置
export http_proxy=192.168.10.238:58591
检查
curl cip.cc
```

Linux系统代理配置相关环境变量：

* http_proxy：为 http 设置代理；默认不填开头以 http 协议传输。
* https_proxy：为 https 设置代理。
* ftp_proxy：为 ftp 设置代理。
* all_proxy：全部变量设置代理（设置了此变量，其余变量不需设置）。
* no_proxy 无需配置代理的主机或域名（可以使用通配符，多个主机使用“,”号分隔）。

设置系统代理配置环境变量：

* export http_proxy=server:port
* export https_proxy=user:password@server:port
* export ftp_proxy=socks5://server:port
* export no_proxy=”localhost, 127.0.0.1, ::1″

取消代理配置：

* unset http_proxy
* unset https_proxy
* unset ftp_proxy
* unset no_proxy

2. proxychains
```
apt install proxychains
```
```
vi /etc/proxychains.conf

修改最后一行为自己的配置
http 127.0.0.1 58591
```

使用方式：

```
root@tonglsh-PC:/etc# proxychains curl cip.cc
[proxychains] config file found: /etc/proxychains.conf
[proxychains] preloading /usr/lib/x86_64-linux-gnu/libproxychains.so.4
[proxychains] DLL init: proxychains-ng 4.13
[proxychains] Strict chain  ...  127.0.0.1:58591  ...  cip.cc:80  ...  OK
IP      : 104.245.14.92
地址    : 美国  加利福尼亚州  洛杉矶
运营商  : xtom.com

数据二  : 美国 | 加利福尼亚州洛杉矶xTOM

数据三  : 美国加利福尼亚费利蒙

URL     : http://www.cip.cc/104.245.14.92
```
```
root@tonglsh-PC:/etc# curl cip.cc
IP      : 111.198.54.177
地址    : 中国  北京
运营商  : 联通

数据二  : 北京市 | 联通

数据三  : 中国北京北京 | 联通

URL     : http://www.cip.cc/111.198.54.177

```