---
title: 科学上网配置shadowsocks
date: 2017-12-19 23:35:12
tags: shadowsocks
categories: tools
---

1.Shadowsocks
更新系统的软件源：

```
yum update
```

安装并更新包管理工具：

```
# CentOS yum源 中默认没有 pip，需要安装 扩展源EPEL
yum -y install epel-release
#安装pip并更新pip
yum install python-pip

pip install --upgrade pip
```

通过pip安装Shadowsocks：

```
pip install shadowsocks
```

编辑配置文件：

```
vi /etc/ss.json
```

内容如下,设置了两个代理端口和密码，都可访问：

```
{
 "server": "::",
 "local_address": "127.0.0.1",
 "local_port": 1080,
 "port_password": {
       "8080": "password",
       "443":"password2"
 },
 "timeout": 300,
 "method": "aes-256-cfb",
 "fast_open": false
}
```

“server”: “::” 同时监听IPv4和IPv6；
“port_passwd” 下是开放的端口和对应的密码，可以开放多个端口，之间用逗号隔开。格式应为：”端口”：”密码”，例如”8080”: “123456”；
“method”为加密方式，可根据需要修改，默认也可以。
防火墙开启相应的端口：

```
firewall-cmd --permanent --zone=public --add-port=8080/tcp

firewall-cmd --reload
```

开机自启前需要先执行

```
chmod +x /etc/rc.local
```

添加开机启动：

```
vi /etc/rc.local
```

插入一行：

```
ssserver -c /etc/ss.json -d start
```



2.使用Google BBR加速

```
wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh

chmod +x bbr.sh

./bbr.sh
```



3.安装DenyHosts阻止SSH暴力攻击

一键安装denyhosts：

```
wget http://soft.vpser.net/lnmp/lnmp1.4beta.tar.gz && tar zxf lnmp1.4beta.tar.gz && cd lnmp1.4/tools/ && ./denyhosts.sh 
```


编辑denyhosts文件

```
nano /etc/denyhosts.conf
```

查看屏蔽ip

```
vi /etc/hosts.deny
```



4.查看shadowsocks连接用户数

显示链接服务器的用户连接  

```
netstat -anp |grep 'ESTABLISHED' |grep 'python' |grep 'tcp6'
```


查看一个SS端口的链接人数/设备数

```
netstat -anp |grep 'ESTABLISHED' |grep 'python' |grep 'tcp6' |grep 173.199.118.8:344 |wc -l 
```

查看一个SS端口的用户连接

```
netstat -anp |grep 'ESTABLISHED' |grep 'python' |grep 'tcp6' |grep 173.199.118.8:344 
```

参考链接:

[CentOS 7安装DenyHosts阻止SSH暴力攻击](http://blog.hlogc.com/20170318/centos-7-install-denyhosts-to-prevent-sshd-explore/)

[一键安装最新内核并开启 BBR 脚本](https://teddysun.com/489.html)
