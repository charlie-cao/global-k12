---
title: "如何使用git."
date: 2019-01-04T15:04:10.000Z
description: 如何使用git
image: /img/manager_screenshot@2x.png
---

## git 常用方法

- clone到本地

git clone

- 本地创建库并提交到远程(远程为空)

- 本地已存在代码提交到远程(远程也有文件)

git remote -v   查看本地仓库有没有远程库.

```
[root@centos-s-2vcpu-4gb-sfo2-01 lapro-services]# git remote -v
origin	https://altalabs.visualstudio.com/lapro-services/_git/lapro-services (fetch)
origin	https://altalabs.visualstudio.com/lapro-services/_git/lapro-services (push)
```

$ git remote
origin
$ git remote add origin https://altalabs.visualstudio.com/lapro-blog/_git/lapro-blog
$ git remote -v
origin  git://github.com/schacon/ticgit.git
pb  git://github.com/paulboone/ticgit.git


1 git init
2 git remote add origin [remote url]
echo "vendor/" >.gitignore
3 git add .
4 git commit -m "Containerized deployment"
[root@centos-s-2vcpu-4gb-sfo2-01 grav-online]# git commit -m "Containerized deployment"

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'root@centos-s-2vcpu-4gb-sfo2-01.(none)')


如果不想全局设置怎么做
1.git init
2.git config user.name "someone"
3.git config user.email "someone@someplace.com"
4.git add *
5.git commit -m "some init msg"

这样应该是可以的.

user.name 是提交的用户名
user.email 是提交的账户


git push origin
----
git add -A和 git add .   git add -u在功能上看似很相近，但还是存在一点差别

git add . ：他会监控工作区的状态树，使用它会把工作时的所有变化提交到暂存区，包括文件内容修改(modified)以及新文件(new)，但不包括被删除的文件。

git add -u ：他仅监控已经被add的文件（即tracked file），他会将被修改的文件提交到暂存区。add -u 不会提交新文件（untracked file）。（git add --update的缩写）

git add -A ：是上面两个功能的合集（git add --all的缩写）


git remote show origin

git push origin master --force

提交是成功了,但是.. 之前的版本被冲掉了.

git branch --set-upstream-to=origin/master master
设置git pull时的默认仓库.

对于grav来说必须把所有的库内容都提交上去之后git clone下来才能用.


## git 子模块.
```
$ git submodule add https://github.com/chaconinc/DbConnector
Cloning into 'DbConnector'...
remote: Counting objects: 11, done.
remote: Compressing objects: 100% (10/10), done.
remote: Total 11 (delta 0), reused 11 (delta 0)
Unpacking objects: 100% (11/11), done.
Checking connectivity... done.
```
这种方法可以带来什么好处呢.

重新Clone下来的仓库没有包含子模块
可以通过

$ git submodule init
$ git submodule update

或者
如果给 git clone 命令传递 --recursive 选项，它就会自动初始化并更新仓库中的每一个子模块。

## 两个文件夹中文件比较工具 linux

diff 是文件比较




## git 常用命令