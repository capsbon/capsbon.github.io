---
title: shadowsocks多用户访问配置
date: 2018-03-12 23:09:42
tags: shadowsocks
categories: tools
---

刚安装shadowsocks的时候，由于只设置了一个用户密码，

现在因为不止我一个一个人用

所以要设置一下多用户访问，过程如下：

1.修改设置文件

```
vi /etc/ss.json
```


将

```
{
 "server": "::",
 "local_address": "127.0.0.1",
 "local_port": 1080,
 "port_password": {
       "8080": "password"
 },
 "timeout": 300,
 "method": "aes-256-cfb",
 "fast_open": false
}
```


改为

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


2.开放访问端口

```
firewall-cmd --permanent --zone=public --add-port=344/tcp

fire-cmd --reload
```

4.加载配置文件

```
ssserver -c /etc/ss.json -d restart
```

到此设置过程就结束了，可以输入自己刚才设置的端口密码来实验是否成功生效了。