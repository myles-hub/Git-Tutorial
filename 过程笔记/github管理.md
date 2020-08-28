# git远程仓库（github)		

## 远程仓库管理基本概念

- **git 可以进行远程仓库托管的有哪些？**

  - （1）github 远程仓库托管
  - （2）gitlab 远程仓库托管

- **添加远程仓库**

  ```cmd
  $ git init
  $ echo 'myles_reop_1' > README.md
  $ git add README.md
  $ git commit -m "Create README.md for the 1st time"
  
  # 添加远程参考，并远程提交.
  $ git remote add origin https://github.com/myles-hub/remote_repo.git
  $ git push -u origin master
  ```

## 远程仓库托管提交

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

## 远程仓库数据同步拉取

- 拉取远程仓库到本地

```cmd
$ git clone https://github.com/myles-hub/demo-git.git

# 默认同步克隆下来后，使用命令查看分支会发现仅能看见master默认分支，这个是正常的。
# 如果需要切换到其他分支，我们直接切换过去就可以了。
$ git branch
$ git checkout dev
```



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



