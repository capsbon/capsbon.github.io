# 新电脑下使用hexo
这是我的hexo博客里所有文件的备份
其中a.sh是用来远程push到hexo分支上的shell脚本

新电脑下使用hexo

1.安装git
在[git](https://git-scm.com/)下载并安装git

2.生产SSH密钥
打开git bash，输入 

ssh-keygen -t rsa -C "youremail@example.com" 

其中youremail@example.com是你自己的邮件地址

然后一直回车。

登陆github，

找到Settings,点击 SSH and GPG keys 

然后点击new SSH key

Title任意

Key内容粘贴公钥id_rsa.pub文件里的内容

点击Add SSH key，输入密码确认完即可

3.克隆自己的库到本地

git clone git@github.com:capsbon/capsbon.github.io.git

切换分支到hexo

git checkout hexo

4.安装nodejs

去[nodejs](https://nodejs.org/en/)下载并安装node.js

5.安装hexo，

依次执行

npm install -g hexo-cli

npm install hexo-deployer-git –save

因为我的主题[maupassant-hexo](https://github.com/tufu9441/maupassant-hexo)的原因，还需要运行以下命令

npm install hexo-renderer-jade@0.3.0 --save

npm install hexo-renderer-sass --save

6.远程部署

执行hexo s -g 启动本地服务，查看效果

hexo d -g 部署到github上

注意！！！

hexo--d部署失败 出现
fatal: in unpopulated submodule ‘.deploy_git’
将.deploy_git文件夹删掉重新hexo g;hexo d即可

终极解决办法：
在所建的hexo分支下新建一个.gitignore文件
在里面添加.deploy_*
在上传的时候就会自动忽略deplot_git文件夹


