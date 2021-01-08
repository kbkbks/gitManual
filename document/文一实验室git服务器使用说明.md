# 文一实验室git服务器使用说明

2021/01/08	韩鑫焱

## 简介

文一实验室git服务器现位于文一校区新教楼404，主要用于代码、文档及资料托管和归档，现可在杭州电子科技大学内网下使用，外网使用需要借助公有IP及外部服务器（购买云服务器可实现）。

此外，另开设Github orgnization用于实验室项目协作研发和代码托管，目前Github大部分功能免费开放，团队协作不限制公开/私有库和协作人数，组织名称：hduorg。

## 文一实验室git服务器

*文一服务器内网IP地址：192.168.1.52，用户名：git，密码：123*

本服务器中项目全部使用git管理，项目本地仓库和远程仓库尽量同名，项目进行需要遵从git使用规范流程。

git基本介绍：https://www.runoob.com/git/git-tutorial.html

git使用规范流程：http://www.ruanyifeng.com/blog/2015/08/git-use-process.html（Github与私有服务器同原理）

git官网：https://git-scm.com/book/zh/v2

git简明指南：https://www.runoob.com/manual/git-guide/

![](/home/hanxinyan/gitManual/figure/gitRemote.jpeg)

git常用操作

- git clone
- git init
- git remote
- git fetch
- git pull
- git commit
- git push

上述常用操作包含了git本地及远程操作大部分内容，下面说明git操作基本流程。

### 1.新建本地仓库

创建一个项目文件夹，进入文件夹，然后执行

```
git init
```

### 2.克隆远程仓库

如果是Github上的远程仓库，执行

```
git clone git@github.com:xxxx/xxxx.git
```

如果是其他人Github上的仓库，建议使用fork，后续可以修改原作者源代码。

如果是文一实验室git服务器，所有远程托管项目均放在/home/git/repository，所有远程归档项目均放在/home/git/archive，执行

```
git clone git@192.168.1.52:/home/git/repository/xxxx.git
```

### 3.添加和提交

若对项目进行更改，使用如下命令，将更改内容添加到暂存区

```
git add <filename>
```

使用如下命令将更改内容进行提交

```
git commit -m "代码提交相关信息"
```

### 4.推送

若是不是克隆来的仓库，需将你的仓库连接到远程服务器，执行

```
git remote add <仓库名比如origin> <server>
```



将更改提交推送到远程仓库











