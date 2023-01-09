---
sidebar: auto
---

## 集中式版本控制

CVS和SVN都是是属于集中式版本控制系统

**特点**：

- 单一的集中管理的服务器，保存所有文件的修订版本
- 协同开发人员通过客户端连接到这台服务器，取出最新的文件或者提交更新

**核心问题**：

- 中央服务器不能出现故障
- 如果宕机一小时，那么在这一小时内，谁都无法提 交更新，也就无法协同工作
- 如果中心数据库所在的磁盘发生损坏，又没有做恰 当备份，毫无疑问你将丢失所有数据

## 分布式版本控制

Git是属于分布式版本控制系统

**特点**

- 客户端并不只提取最新版本的文件快照， 而是**把代码仓库完整地镜像下 来，包括完整的历史记录**；
- 任何一处协同工作用的服务器发生故障，事后都可以用任何 一个镜像出来的本地仓库恢复
- 每一次的克隆操作，实际上都是一次对代码仓库的完整备份



## git常用的操作

### git配置

Git 安装完成后，需配置代码提交人员的名字（昵称）和联系邮箱，配置成功后，之后提交代码修改时，会记录是谁修改了对应的代码，可以更好的管理和 Code Review。

配置命令如下：

```
# your_name：名字或昵称
git config --global user.name 'your_name'
# your_email@domain.com：邮箱地址
git config --global user.email 'your_email@domain.com'
```

想要查看 `config` 的配置，可使用如下命令：

```
# 查看当前仓库 config
git config --list --local
# 查看当前用户 config
git config --list --global
# 查看当前系统 config
git config --list --system
```

除了设置 `--global`，还可以设置 `--local` 和 `--system`，这三个都有什么区别呢？

- `--local`：只对某个仓库有效。
- `--global`：对当前用户（比如 windows 的 User 环境）所有仓库有效。
- `--system`：对系统所有登录的用户（比如 windows 的 System 环境）有效，此配置不常用。

### 获取git仓库

方式一：

```git
git init //初始化本地git仓库
```

方式二：

```
git clone //克隆远程仓库
```

### 检测文件的状态 

```
git status
```

### 文件添加到暂存区

```
git add .
```

### 文件更新提交

```
git commit -m '提交信息'
```

### 查看提交的历史

```
git log
```

如果提交信息过多，可以按```enter```键查看更多,按```Q```键可以退出

```
git log --pretty=oneline   //提交信息显示在一行
```

```
git reflog  //可以查看更多更全的提交历史信息（回退前后）
```

### 版本回退

```
git reset
```

```
git reset --hard HEAD^  //回退到上个版本
```

```
git reset --hard HEAD^^ //回退到上上版本
```

```
git reset --hard HEAD~1000 //上1000个版本
```

```
git reset --hard 1234 //回退到指定版本
```

### 远程仓库验证-SSH密钥

```
ssh-keygen -t ed25519 -C “your email" //找到自己的密钥
```
![20](/21.png)

然后去gitLab这样的远程仓库，点击设置，ssh，添加上自己的密钥

### 本地连接远程仓库

**查看是否有连接远程仓库**

```
git remote  //如果出现origin就是连接了
```

```
git remote -v //查看连接的具体仓库
```

**连接远程仓库**

```
git init //先初始化仓库
git remote add origin 仓库地址
git remote //查看是否连接成功
```

**移除远程连接**

```
git remote remove origin
```

**本地分支的上游分支（跟踪分支）**

本地仓库和远程仓库连接之后，执行git pull拉取远程分支会报如下的错误

![23](/23.png)

原因是因为当前分支没有和远程的origin/master分支进行跟踪

解决1

```
git pull origin master
```

解决2

```
git branch --set-upstream-to=origin/master
```

### 远程仓库的交互

```
git add .
git commit -m 'XX'
git pull
git push
```

### tag标签

对于重大的版本我们常常会打上一个标签，以表示它的重要性：

- Git 可以给仓库历史中的某一个提交打上标签；

- 比较有代表性的是人们会使用这个功能来标记发布结点（ v1.0 、 v2.0 等等）；

创建标签

```
git tag v1.0 //方式1
git tag -a v1.0 -m '附属信息' //方式2
git tag //查看tag
```

把本地的git标签推到远程

```
git push origin v1.0
```

删除本地tag

```
git tag -d v1.0
```

删除远程tag

```
git push origin –delete <tagname>
```

检出tag

```
git checkout <tagname>
```

### 分支

创建分支

```
git branch 分支名
```

创建分支并切换到新分支

```
git checkout -b 分支名
```

切换分支

```
git checkout 分支名  //可以切换到本地分支也可以直接切换到远程分支
```

合并分支

```
git merge 合并的分支名
```

查看分支

```
git branch //查看分支
git branch -v //查看分支，并可以看到最后一次提交的commit
```

删除分支

```
git branch –d hotfix # 删除当前分支
git branch –D hotfix # 强制删除某一个分支
git push origin --delete <branch> //删除远程分支
```

为什么需要用到分支

让我们来看一个简单的分支新建与分支合并的例子，实际工作中你可能会用到类似的工作流。

-  开发某个项目，在默认分支master上进行开发；
- 实现项目的功能需求，不断提交；
- 并且在一个大的版本完成时，发布版本，打上一个tag v1.0.0；

继续开发后续的新功能，正在此时，你突然接到一个电话说有个很严重的问题需要紧急修补， 你将按照如下方式来处理

- 切换到tag v1.0.0的版本，并且创建一个分支hotfix；

### rebase

和marge差不多，历史记录不同



