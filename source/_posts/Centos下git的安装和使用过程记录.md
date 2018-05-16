---
title: Centos下git的安装和使用过程记录
date: 2018-05-10 08:43:04
tags: git
categories: tools
---

#### 1.安装git 

```
yum install git
```

之后按照提示输入 'y' 开始下载安装

#### 2.生成ssh key连接github

执行

```
 ssh-keygen -t rsa -C "your_email@youremail.com"
```

your_email是你的email，

会在/root/.ssh文件夹下默认生成id_rsa和id_rsa.pub文件，

此时回到github，进入Account Settings，左边选择SSH Keys，Add SSH Key,title随便填，key中粘贴id_rsa.pub的内容即可

##### ps.

如果生成ssh key过程中修改了id_rsa名字，按照上述方法会出现Permission denied (publickey)错误，这是因为github默认使用id_rsa尝试，所以此时需要配置一个onfig文件

cd ~/.ssh/

vi config

```
Host github.com
 HostName github.com
 User git
 IdentityFile ~/.ssh/github_rsa
```

ESC+:wq保存退出

重新尝试ssh -T [git@github.com](mailto:git@github.com)，即可搞定

解决方法参考[github提示Permission denied (publickey)，如何才能解决](https://www.zhihu.com/question/21402411)

问题中 冰海 的回答

#### 3.测试是否连接成功

测试ssh key是否成功，使用命令“ssh -T git@github.com”，如果出现You’ve successfully authenticated, but GitHub does not provide shell access 。这就表示已成功连上github。

#### 4.配置git的username和email

```
git config --global user.name "your name"   //配置用户名 

git config --global user.email "your email"    //配置email 
```



### 克隆github远程仓库到本地

1.创建新建文件夹

```
mkdir git_repo
```

2.初始化

```
cd git_repo

git init
```

3.添加远程仓库地址

```
git remote add origin git@github.com:capsbon/bilibili_score.git
```

github获取远程库时，有**ssh方式和https方式**,使用ssh时保存密钥对以后可以不再输入帐号密码，而https则需要再次输入账户密码，故采用ssh方式

4.克隆远程仓库到本地

```
git clone git@github.com:capsbon/bilibili_score.git
```

ps.拉取更新到本地

- 如果本地的版本不是最新的，可以使用命令 “git fetch origin”


- 把更新的内容合并到本地分支，可以使用命令 “git merge origin/master”


-  如果你不想手动去合并，那么你可以使用： git pull origin master // 这个命令可以拉去最新版本并自动合并

### 利用git从本地上传到github

- 比如你要添加一个文件xxx到本地仓库，使用命令 “git add xxx”，可以使用“git add .”自动判断添加哪些文件


- 然后把这个添加提交到本地的仓库，使用命令 ”git commit -m ”说明这次的提交“ “


-  最后把本地仓库提交到远程的GitHub仓库，使用命令 ”git push origin master“