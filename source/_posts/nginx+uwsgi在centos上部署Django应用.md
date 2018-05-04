---
title: nginx+uwsgi在centos上部署Django应用
date: 2018-03-05 20:46:05
tags: Django
categories: 
---



**背景介绍**：

之前做完一个Django项目，打算部署在自己的centos服务器上，可以远程访问，于是命令行上输入

python manage.py runserver 0:8000

就成功运行了，可惜，django自带的web服务器并不稳定，经常无缘无故断掉，于是想到

使用主流的uwsgi+nginx来部署项目，

至于Nginx+uWSGI+Django原理可参考[Nginx+uWSGI+Django原理](http://www.cnblogs.com/Xjng/p/aa4dd23918359c6414d54e4b972e9081.html)

此处就不赘述了，下面介绍下具体部署步骤

##### 1.安装uwsgi

```
pip install uwsgi
```

此时可以尝试使用uwsgi来启动应用，其中wsgi.py在mysite文件夹下

```
uwsgi --http :8000 --module mysite.wsgi
```

在浏览其中输入127.0.0.1:8080 能够成功访问，说明你的应用服务器部署成功，已经可以对外提供服务。

##### 2.安装nginx

```
yum install nginx
```

在/etc/nginx/conf.d文件夹下新建nginx启动的配置文件mysite.conf，输入以下信息

    server {
      listen 8000;  #启动的nginx进程监听请求的端口
      server_name localhost;   #域名
      location / {
        include /etc/nginx/uwsgi_params;
        uwsgi_pass 127.0.0.1:8001;  #对于动态请求，转发到本机的8001端口，也就是uwsgi监听的端口
      }
    
      location /static/ {
        alias /home/Maximum/vacancy/static/;    #设定静态文件所在目录
      }
    }
##### 3.同步静态文件到nginx设置的目录下

在django项目setting.py中增加

```
BASE_DIR = os.path.dirname(__file__)
STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR,'..','vacancy','static') 
```

然后在命令行行下执行

```
python manage.py collectstatic 
```

##### 4.配置uwsgi

项目根目录下创建uwsgi.ini文件

```
vi uwsgi.ini
```

uwsgi.ini内容

```
[uwsgi]
# Django's wsgi file
module = mysite.wsgi
pythonpath = /usr/local/lib/python3.5/site-packages
socket = 127.0.0.1:8001
pidfile = /home/Maximum/uwsgi.pid    
daemonize = /home/Maximum/uwsgi.log

```

介绍下uwsgi和nginx相关命令

```
启动uwsgi：uwsgi --ini uwsgi.ini
停止uwsgi：uwsgi --stop uwsgi.pid
重新加载配置：uwsgi --reload uwsgi.pid
启动nginx：service nginx start
停止nginx：service nginx stop
重启nginx：service nginx restart
```

接下来启动uwsgi：

```
uwsgi --ini uwsgi.ini
```

启动nginx

```
service nginx start
```

此时没问题的话就大功告成了，访问[173.199.118.8:8000/vacancies]()即可看到我们运行的项目了



#### *遇到的坑

##### 1.启动nginx时出现以下错误，可知端口已被占用

```
[gaarai@linode /etc/nginx]$ service nginx restart
 * Restarting nginx nginx
nginx: [emerg] bind() to [::]:80 failed (98: Address already in use)
nginx: [emerg] bind() to [::]:443 failed (98: Address already in use)
nginx: [emerg] bind() to [::]:80 failed (98: Address already in use)
```

##### 解决方法：

```
netstat -ntpl
```

查看当前运行的端口以及程序，内容类似如下：

```
[root@vultr mysite]# netstat -ntpl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1502/nginx: master
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      461/sshd
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      677/master
tcp        0      0 0.0.0.0:8000            0.0.0.0:*               LISTEN      1502/nginx: master
tcp        0      0 127.0.0.1:8001          0.0.0.0:*               LISTEN      1475/uwsgi
tcp6       0      0 :::3306                 :::*                    LIS
```

将使用进程端口80，8000，8001的进程PID关闭，uwsgi的进程需要强制关闭

```
[root@vultr mysite]# kill -9 1475
[root@vultr mysite]# kill 1502
```

重新启动uwsgi和nginx

```
[root@vultr mysite]# uwsgi --ini uwsgi.ini
[root@vultr mysite]# service nginx start
```



##### 2.访问网站出现Internal Server Error错误

查看uwsgi.log日志文件

```
tail -30 uwsgi.log
```

日志里出现

```
unable to load app 0 (mountpoint='') (callable not found or import error)
```

**错误，**

尝试执行

```
uwsgi --http :8000 --module mysite.wsgi
```

访问[173.199.118.8:8000/vacancies]()运行正常，可知是uwsgi.ini配置文件有误

参考链接[Setting up django with uwsgi and nginx](https://stackoverflow.com/questions/18546299/setting-up-django-with-uwsgi-and-nginx)

##### 解决办法：

修改uwsgi.ini文件为

```
[uwsgi]

# Django's wsgi file

module = mysite.wsgi
pythonpath = /usr/local/lib/python3.5/site-packages
socket = 127.0.0.1:8001
pidfile = /home/Maximum/uwsgi.pid    
daemonize = /home/Maximum/uwsgi.log
```

之前有一些不太懂的设置加了上去，运行错误，去掉之后重启uwsgi和nginx服务即运行正常，

果然自己不太懂的设置还是不能乱加

##### 以上です