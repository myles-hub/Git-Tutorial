# Git 学习

标签（空格分隔）： Git

---

[TOC]

---

# 第1章：Git 基本了解

---

## 1.1 Git 是什么?

- **（1）git 是一个分布式版本控制系统软件**
  - git 是一个**“软件”**
  - git 是一个做**“版本控制”**的**“软件”**
  - git 是一个做**“分布式”“版本控制”**的**“软件”**

- **（2）什么是版本控制**
  - 以版本作为标记，来实现“文件内容的增/删/修进行备份”与“恢复回滚”。
- **（3）什么是分布式**
  - **本地式**：文件内容只存在于本地
  - **集中式**：文件内容只存在于中央服务器；
  - **分布式**：文件内容存在于每一台机器与中心仓库，这样每台主机就可以互为备份，但又相互不影响；

- [**Git 官方说明**][1]

Git是一个免费的开源 分布式版本控制系统，旨在快速高效地处理从小型到大型项目的所有内容。

---

## 1.2 Git 的安装

- （1）git 安装说明

git 的安装可直接参考 “[git - 简明指南][2]”进行不同平台的安装部署。

- （2）git 安装检查
  - 直接右击键盘，出现“Git Bash Here” 与“Git GUI Here”,即安装完成； 
  - 点击“Git Bash Here” 进入 Bash, 测试下命令`git --version` 

---

## 1.3 git 三大区域

现在请注意，如果你希望后面的学习更顺利，请记住下面这些关于 Git 的概念。 Git 有三种状态，你的文件可能处于其中之一：`已修改（modified）` 、`已暂存（staged）` 和 `已提交（committed）`。

### 1.3.1 git 三个状态

- **（1）已修改（modified）**
  - 表示修改了文件，但还没保存到数据库中。

- **（2）已暂存（staged）**
  - 表示对一个已修改文件的当前版本做了标记，使之包含在下次提交的快照中。

- **（3）已提交（committed）：**
  - 表示数据已经安全地保存在本地数据库中。

### 1.3.2 git 三个区域

通过上面三个状态就会让我们的 Git 项目拥有三个区域：

- **（1）工作区**
- **（2）暂存区**
- **（3）Git 目录区**

![此处输入图片的描述][3]


---

## 1.4 git 仓库管理

### 1.4.1 git仓库管理

- 1.进入要管理的目录

> \> cd git_demo 

- 2.初始化仓库管理目录

> $ git init

- 3.管理仓库目录下文件

> \$ git status
> \$ git add index.html
> \$ git status
> \$ git add readme.txt
> \$ git status

红色：未被管理状态，表示还未准备做版本生成提交；
绿色：已被管理状态，表示以及准备做辨别生成提交；
小结：无论是“红色”还是“绿色”都是表示文件内容已被修改或新增，但是还未做版本提交状态；

- 4.向.git目录生成版本

> \$ git commit index.html -m "V1: the 1th init."

### 1.4.2 git 分步提交

git 版本提交，可以先提交暂存区，然后再做版本生成提交。

![三大区域](https://git-scm.com/images/about/index1@2x.png)

### 1.4.3 git 一次提交

git 版本提交也可忽略“staging area”，只需要在commit 命令添加“-a"参考一次完成版本变更提交；

![git 版本控制一次提交](https://git-scm.com/images/about/index2@2x.png)




---

## 1.5 版本回滚

### 1.5.1 版本回滚命令

- 回滚到上一版本

> \> git reset --hard HEAD^  

- 回滚到上一版本的上一个版本

> \> git reset --hard HEAD^^

- **使用commit id 指定版本回滚**

> \> git reset --hard 82a9cbe1

### 1.5.2 版本信息查询

- 查看提交历史

> \> git log

  - 查了命令历史

> \> git reflog

### 1.5.3 版本回滚原理

Git的版本回退速度非常快，因为Git在内部有个指向当前版本的`HEAD`指针，当你回退版本的时候，Git仅仅是把HEAD从指向`append GPL`：

```ascii
┌────┐
│HEAD│
└────┘
   │
   └──> ○ append GPL
        │
        ○ add distributed
        │
        ○ wrote a readme file
```

如版本需要回滚到`add distributed`，就将指针的指向修改为为`add distributed`即刻，随后顺便把工作区的文件更新了。所以你让`HEAD`指向哪个版本号，你就把当前版本定位在哪个位置。：

```ascii
┌────┐
│HEAD│
└────┘
   │
   │    ○ append GPL
   │    │
   └──> ○ add distributed
        │
        ○ wrote a readme file
```

---

## 1.6 git 命令小结

### 1.6.1 git 初始化命令

```cmd 
# （1）初始化git仓库目录
> git init
```

### 1.6.2 working directory 管理命令

```cmd
# （2）working dir 目录状态查询
> git status 
```

```cmd
# （3）staged area 添加
> git add
```

```cmd
# （4）.git dir 提交新版本
> git commit index.html -m "V1: init"
```

### 1.6.3 版本信息查询命令

```cmd
# （5）版本信息查询
> git log  或
> git reflog
```

### 1.6.4 版本回滚命令

```cmd
# （6）回滚上一版本
> git reset --hard HEAD^
# （7）回滚上一个的上一版本
> git reset --hard HEAD ^^
# （8）回滚指定的commit id 版本
> git reset --hard 72a8c1ad
```

# 第2章：Git远程仓库管理

## 2.1 远程托管提交过程

- 第1步：创建一个空的远程仓库

  > （1）登录github；
  >
  > （2）创建一个可供远程托管的仓库（repo）

- 第2步：提交本地代码到远程仓库进行托管

  > （1）add 添加远程仓库源

  ```cmd
  $ git remote origin https://github.com/myles-hub/remote_repo.git
  ```

  > （2）push 本地代码到远程仓库

  ```cmd
  $ git push -u origin master
  ```



## ## 2.2 远程仓库拉取过程



## 远程仓库管理命令小结

- **远程提交(push)**

```cmd
# (1)添加远程仓库，并设置别名origin
$ git remote add origin https://github.com/myles-hub/xxx.git

# (2)提交本地代码到远程仓库(origin)的master分支
$ git push -u origin master
```

> **注意：远程仓库同步提交前，需要先有一个空的远程仓库可以被提交才行。**

- **远程克隆(clone)**

```cmd
# (1)克隆远程仓库到本地
$ git clone https://github.com/myles-hub/xxx.git
# (2)切换下分支
$ git branch
$ git checkout dev/bug
```









# FAQ

## 1. git reset 的3中回滚

- [学习参考](https://www.jianshu.com/p/c2ec5f06cf1a)

# 学习参考

- [动画图解](https://zhuanlan.zhihu.com/p/147356242)



<img src="C:\Users\myles\AppData\Roaming\Typora\typora-user-images\image-20200805162158127.png" alt="image-20200805162158127" style="zoom:80%;" />




[1]: https://git-scm.com/
[2]: https://www.runoob.com/manual/git-guide/
[3]: https://git-scm.com/book/en/v2/images/areas.png