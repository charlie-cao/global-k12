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


.gitignore只能忽略那些原来没有被 track 的文件，如果某些文件已经被纳入了版本管理中，则修改 .gitignore 是无效的。
解决方法是先把本地缓存删除，然后再提交。

## 两个文件夹中文件比较工具 linux

diff 是文件比较




## git 常用命令

## 将保存到本地的git仓库清空后提交到其他仓库中

第一个方案,是否能够把这个仓库fock到vsts中..
/var/discourse/shared/standalone


查看当前容器使用的卷
docker inspect 1d0cbba54f84 | grep Mounts

将当前执行代码复制出容器并解压.

git status



git clone --bare git://github.com/username/project.git


git push --mirror git@gitcafe.com/username/newproject.git
git push --mirror https://altalabs.visualstudio.com/lapro-community/_git/lapro-community

git clone --bare https://github.com/discourse/discourse.git distp

 https://altalabs.visualstudio.com/lapro-community/_git/lapro-community


1). 从原地址克隆一份裸版本库，比如原本托管于 GitHub。

git clone --bare git://github.com/username/project.git
--bare 创建的克隆版本库都不包含工作区，直接就是版本库的内容，这样的版本库称为裸版本库。

2). 然后到新的 Git 服务器上创建一个新项目，比如 GitCafe。

3). 以镜像推送的方式上传代码到 GitCafe 服务器上。

cd project.git
git push --mirror git@gitcafe.com/username/newproject.git
-- mirror 克隆出来的裸版本对上游版本库进行了注册，这样可以在裸版本库中使用git fetch命令和上游版本库进行持续同步。

4). 删除本地代码

cd ..
rm -rf project.git
5). 到新服务器 GitCafe 上找到 Clone 地址，直接 Clone 到本地就可以了。

git clone git@gitcafe.com/username/newproject.git
这种方式可以保留原版本库中的所有内容

这是OK的.

但是问题是如果


# On branch tests-passed
nothing to commit, working directory clean


