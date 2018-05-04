---
title: VPS设置SSH密钥登录
date: 2018-03-19 21:08:10
tags: shadowsocks
categories: tools
---

在vultr上买的vps,每天都有人企图暴力破解我的VPS，虽然用了DenyHosts防止暴力破解，但总不能算完全安全，要是能像路由器那般设置白名单不不就万事大吉了吗，于是就找到了使用SSH Key登录这个解决办法。

用以下命令可以查看别人暴力破解你SSH密码登录的情况

```
grep "Failed password for invalid user" /var/log/secure | awk '{print $13}' | sort | uniq -c | sort -nr | more
```

[](http://oevfty3i3.bkt.clouddn.com/20170528149595407252948.jpg?imageView2/0/format/jpg)

原理简略如下：

>用户将自己的公钥储存在远程主机上。登录的时候，远程主机会向用户发送一段随机字符串，用户用自己的私钥加密后，再发回来。远程主机用事先储存的公钥进行解密，如果成功，就证明用户是可信的，直接允许登录shell，不再要求密码。



1.首先生成密钥对

```
[root@host ~]$ ssh-keygen -t rsa <== 建立密钥对，之后一路回车
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa): <== 按 Enter
Created directory '/root/.ssh'.
Enter passphrase (empty for no passphrase): <== 输入密钥锁码，或直接按 Enter 留空
Enter same passphrase again: <== 再输入一遍密钥锁码
Your identification has been saved in /root/.ssh/id_rsa. <== 私钥
Your public key has been saved in /root/.ssh/id_rsa.pub. <== 公钥
```

生成后将立马id_rsa从VPS拖下来到本机中，以免后面设置成只能密钥登录无法密码登录时无法登录

2.修改公钥名

```
[root@host ~]$ cd /root/.ssh
将id_rsa.pub 改名为authorized_keys
[root@host ~]$ mv id_rsa.pub authorized_keys
```

3.修改sshd_config配置文件

```
RSAAuthentication yes #RSA认证
PubkeyAuthentication yes #开启公钥验证
AuthorizedKeysFile .ssh/authorized_keys #验证文件路径
PasswordAuthentication no #禁止密码认证
PermitEmptyPasswords no #禁止空密码
```

若有的配置项找不到（比如RSAAuthentication）就忽略掉

4.重启SSH服务

```
systemctl restart sshd
```

5.登录

> 如果你用的是Window系统要登录VPS需要将私钥下载到客户端，然后转换为 PuTTY 能使用的格式

> 使用 WinSCP、SFTP 等工具将私钥文件 id_rsa 下载到客户端机器上。然后打开 PuTTYGen，单击 Actions 中的 Load 按钮，载入你刚才下载到的私钥文件。如果你刚才设置了密钥锁码，这时则需要输入。

> 载入成功后，PuTTYGen 会显示密钥相关的信息。在 Key comment 中键入对密钥的说明信息，然后单击 Save private key 按钮即可将私钥文件存放为 PuTTY 能使用的格式。

> 今后，当你使用 PuTTY 登录时，可以在左侧的 Connection -> SSH -> Auth 中的 Private key file for authentication: 处选择你的私钥文件，然后即可登录了，过程中只需输入密钥锁码即可。



关于手机远程登录设置SSH key，我使用的是JuiceSSH,版本为2.1.4

导入私钥过程

1. 将私钥传到手机里
2. 打开JuiceSSH, 点击Connections转到其中的 Identities.
3. 创建认证（点击 + 符号）
4. 设置Nickname 和username
5. 点击"Set (Optional)" 设置私钥
6. 选择 "Smart Search" JuiceSSH会自动搜索你手机中的SSH key，搜索到id_rsa（我的私钥）,选中，点击OK
7. 保存这个认证（点击右上方的对勾）

新建连接时将认证方式选为你刚才设置的那个认证即可



参考链接：

[Vultr VPS SSH密钥登录](http://zlxdike.github.io/2017/05/28/Vultr-VPS-SSH%E5%AF%86%E9%92%A5%E7%99%BB%E5%BD%95/)

[JuiceSSH Supported Private Key Formats](https://sonelli.freshdesk.com/support/solutions/articles/139632-juicessh-supported-private-key-formats-openssh-pem-)

[SSH原理与运用（一）：远程登录](http://www.ruanyifeng.com/blog/2011/12/ssh_remote_login.html)