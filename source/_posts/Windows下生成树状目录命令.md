---
title: Windows下生成树状目录命令
date: 2018-03-19 21:54:53
tags:
categories: Ruby
---
将当前目录下的所有子目录及其文件生成树状目录并保存到tree.txt文件中

```
tree /f >tree.txt 
```

顺便比较下Dos和Linux命令的异同吧

| 命令的目的                             | MS-DOS    | Linux                                    | Linux 的简单实例                              |
| --------------------------------- | --------- | ---------------------------------------- | ---------------------------------------- |
| 复制文件                              | `copy`    | `cp`                                     | `cp thisfile.txt /home/thisdirectory`    |
| 转移文件                              | `move`    | `mv`                                     | `mv thisfile.txt /home/thisdirectory`    |
| 列举文件                              | `dir`     | `ls`                                     | `ls`                                     |
| 清除屏幕                              | `cls`     | `clear`                                  | `clear`                                  |
| 关闭 shell 提示                       | `exit`    | `exit`                                   | `exit`                                   |
| 显示或设置日期                           | `date`    | `date`                                   | `date`                                   |
| 删除文件                              | `del`     | `rm`                                     | `rm thisfile.txt`                        |
| 把输出“回响”到屏幕上                       | `echo`    | `echo`                                   | `echo "messageg"`                        |
| 用简单文本编辑器来编辑文件                     | `edit`    | `gedit`([[a\]](http://www.huihoo.org/gnu_linux/ch-doslinux.html#FTN.AEN7986)) | `gedit thisfile.txt`注意Dos部分情况下可能识别不了单引号  |
| 比较文件内容                            | `fc`      | `diff`                                   | `diff file1 file2`                       |
| 在文件中寻找字串                          | `find`    | `grep`                                   | `grep 词或词组 thisfile.txt`·`find "message" a.txt`注意Dos部分情况下可能识别不了单引号 |
| 显示已被使用的内存数量                       | `mem`     | `free`                                   | `free`                                   |
| 显示命令帮助                            | `*命令* /?` | `man`（[[c\]](http://www.huihoo.org/gnu_linux/ch-doslinux.html#FTN.AEN8035)） | `man 命令`                                 |
| 创建目录                              | `mkdir`   | `mkdir`                                  | `mkdir 目录`                               |
| 查看文件                              | `more`    | `less`（[[d\]](http://www.huihoo.org/gnu_linux/ch-doslinux.html#FTN.AEN8056)） | `less thisfile.txt`                      |
| 重新命名文件                            | `ren`     | `mv`（[[e\]](http://www.huihoo.org/gnu_linux/ch-doslinux.html#FTN.AEN8068)） | `mv thisfile.txt thatfile.txt`           |
| 显示你在文件系统中的位置                      | `chdir`   | `pwd`                                    | `pwd`                                    |
| 用指定的路径（*绝对路径，absolute path*）来改换目录 | `cd 路径名`  | `cd 路径名`                                 | `cd /directory/directory`                |
| 用一个*相对路径（relative path）*来改换目录     | `cd ..`   | `cd ..`                                  | `cd ..`                                  |
| 显示时间                              | `time`    | `date`                                   | `date`                                   |