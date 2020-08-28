# git 命令练习

## master分支：C1 -> C2 -> C3

```cmd
# 初始化.git 仓库
$ git init
$ git status
# 创建 C1
$ git add index.hmtl
$ git commit index.html "C1: the 1st init."
# 创建 C2
$ git add .
$ git commit -m "C2: the 2nd modified."
# 创建 C3 版本
$ git add.
$ git commit -m "C3: the 3th modified."
```

## dev分支：C4(dev new functions)

```cmd
# 开发新功能，创建dev分支
$ git branch
$ git branch dev
$ git branch
$ git checkout dev
$ git branch
# 一条命令创建dev分支，并切换过去；
$ git checkout -b dev
$ git branch
# 现在C3版本出现bug了，我们需要开启一个bug修复分支，并进行bug修复工作
```



## bug分支：C3(fixbug)

```cmd
# 现在C3版本出现bug了，我们需要开启一个bug修复分支，并进行bug修复工作
# 切换回master分支
$ git checkout master
# 创建bug新分支
$ git checkout -b bug
$ git branch
# bug 修复完成，我们合并bug会master主分支
$ git checkout master
$ git merge bug
# master主分支C3 bug已经修复完成，删除bug临时分支
$ git branch -d bug
$ git branch
```

## dev 分支：合并到master分支

```cmd
# 新功能开发完，切换到主分支并进行版本合并
# 切换回master
$ git checkout master
$ git branch
$ git merge dev
# 版本合并冲突，需要手动修复，然后在重新做版本提交
$ git add .
$ git commit -m "C4: new function merge ok"
```



```cmd
$ git init
$ git add 
$ git commit 
$ git branch
$ git branch dev
$ git checkout dev
$ git checkout -b dev
$ git merge 
```

