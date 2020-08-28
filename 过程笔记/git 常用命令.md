# Git 常用命令分类记忆

## 1. 增加类命令

```cmd
$ git add .
$ git commit -m "Description for commit."
$ git branch dev/bug
# 添加仓库远程托管源
$ git remote add origin https://github.com/myles-hub/xxx.git
```



## 2. 删除类命令

```cmd
$ git branch -d dev/bug
```



## 3. 修改类命令

```cmd
# 切换分支位置
$ git checkout master
# 合并分支
$ git merge bug/dev
```



## 4. 查询类命令

```cmd
$ git status
$ git log
$ git reflog
$ git branch
```



## 5. 同步类命令

```cmd
# 添加远程仓库托管源
$ git remote add origin https://github.com/myles-hub/xxx.git
# 本地仓库提交远程仓库托管
$ git push -u origin master
```

