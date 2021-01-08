

# 文一实验室git服务器使用说明

2021/01/08	韩鑫焱

## 简介

文一实验室git服务器现位于文一校区新教楼404，主要用于代码、文档及资料托管和归档，现可在杭州电子科技大学内网下使用，外网使用需要借助公有IP及外部服务器（购买云服务器可实现）。

此外，另开设Github orgnization用于实验室项目协作研发和代码托管，目前Github大部分功能免费开放，团队协作不限制公开/私有库和协作人数，组织名称：hduorg。

## 文一实验室git服务器

*文一服务器内网IP地址：192.168.1.52，用户名：git，密码：123*

下面所有操作在Linux和Windows下都可执行，Windows建议安装Git客户端。

![](/home/hanxinyan/gitManual/figure/GitClient.png)

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

### 1.新建本地仓库和远程仓库

在本地创建一个项目文件夹，进入文件夹，然后执行

```
git init
```

文一远程服务器开放ssh密码登录，可以内网ssh连接git服务器新建远程库，执行

```
# 连接远程服务器
ssh git@192.168.1.52
# 新建文件夹 所有远程托管项目均放在/home/git/repository
mkdir /home/git/repository/xxxx.git
# 初始化仓库
cd /home/git/repository/xxxx.git
git init --bare ./xxxx.git
```

Github远程仓库直接在网页上创建即可。

### 2.克隆远程仓库

其他人的仓库可以克隆到本地进行修改，而不需要新建本地仓库，如果是Github上的远程仓库，执行

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

若对其他人的仓库内容进行更改，建议开辟新的分支，使仓库所有者了解到你所做的贡献，并决定是否合并分支

```
# 开辟新的分支，并切换至新分支
git checkout -b dev
# 删除分支
git branch -d dev
```

### 4.推送

若不是克隆来的仓库，需将你的仓库连接到远程服务器，执行

```
git remote add <仓库名比如origin> <server>
```

Github上的<server>在网页上复制得到，文一服务器<server>为git@192.168.1.52:/home/git/repository/xxxx.git。

之后将更改提交推送到远程仓库

```
git push origin master
```

### 5.更新与合并

从远程仓库拉取最新的更改，执行

```
git fetch
```

如果觉得某分支的更改可以接受，决定与当前分支合并，执行

```
git merge dev
```

遗憾的是，git会尝试进行分支合并操作，但并不是每次合并都能成功，需要手动对分支中的冲突进行消除，这一部分操作建议在编辑器上完成，多数编辑器冲突消除都比较直观，如vscode，idea等。

### 6.创建ssh公钥和私钥

使用对称密钥连接，可以不再需要ssh密码登录（也更安全），执行

```
ssh-keygen -C "邮箱"

# 此时Windows用户C:\Users\用户名\.ssh 或者 Linux用户 /home/用户名/.ssh 下会多出两个文件 id_rsa和id_rsa.pub，前者是私钥，后者是公钥
# 将该公钥导入git服务器
ssh git@192.68.1.52 'cat >> .ssh/autuorized_keys' < ~/.ssh/id_rsa.pub
```



## Github orgnization

![](/home/hanxinyan/gitManual/figure/Github.png)

Github orgnization现已全面开放团队功能，无项目协作人数和私有库限制，可以在组织中建立私有库进行多人协作项目研发，其pull request功能使得协作更为便利，项目管理者能够直观看见更新的提交并决定是否合并提交。

![](/home/hanxinyan/gitManual/figure/pullrequest.png)













