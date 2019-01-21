---
title: "linux 一些快捷操作"
date: 2019-01-04T15:04:10.000Z
description: 如何使用git
image: /img/manager_screenshot@2x.png
---

```
vi ~/.bash_profile

alias work="cd /Applications/MAMP/htdocs/lapro-services/ && code ./"
alias blog="cd ~/Desktop/myblog/global-k12/ && code ./"
alias space=""

source  ~/.bash_profile
```
```
Linux中修改环境变量及生效方法
方法一：

　　在/etc/profile文件中添加变量【对所有用户生效(永久的)】

　　用VI在文件/etc/profile文件中增加变量，该变量将会对Linux下所有用户有效，并且是“永久的”。

　　要让刚才的修改马上生效，需要执行以下代码

　　# source /etc/profile

　　方法二：

　　在用户目录下的.bash_profile文件中增加变量【对单一用户生效(永久的)】

　　用VI在用户目录下的.bash_profile文件中增加变量，改变量仅会对当前用户有效，并且是“永久的”。

　　要让刚才的修改马上生效，需要在用户目录下执行以下代码

　　# source .bash_profile

　　方法三：

　　直接运行export命令定义变量【只对当前shell(BASH)有效(临时的)】

　　在shell的命令行下直接使用[export变量名=变量值]定义变量，该变量只在当前的shell(BASH)或其子shell(BASH)下是有效的，shell关闭了，变量也就失效了，再打开新shell时就没有这个变量，需要使用的话还需要重新定义。

　　例如：export PATH=/usr/local/webserver/php/bin:$PATH
```