---
title: hexo内容备份到github
date: 2017-11-10 13:15:21
tags: hexo
---
利用git新建一个分支保存源文件，
我这里是新建了一个hexo分支，
切换到根目录下后依次执行以下命令：

git add .;
git commit -m " blog back up"
git push -f origin hexo

可以写一个shell脚本比如backup.sh，包含以上三句话,
运行 ./backup.sh 或者sh backup.sh即可避免麻烦的一句一句敲了


