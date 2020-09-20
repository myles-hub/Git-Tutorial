# Git 免密同步

通过添加 SSH 公钥到远程github，实现git的免密数据同步；

## 1. 生成本地密钥对

```python
$ ssh-keygen
# 通过本命令工具，一路回车直接生成“一对密钥对”；
# 密码默认生成位置在 ~/.ssh/ 中；
```

## 2. 上传 public-key 

- 复制公钥

```cmd
$ ls ~/.ssh/
id_rsa  id_rsa.pub  known_hosts
# id_rsa.pub 就是公钥了

cat ~/.ssh/id_rsa.pub
# 复制公钥内容；
```

- 上传公钥

我登录个人github仓库，将复制的公钥内容粘贴到远程github上，并保存一个名称。

实际操过如下：

> 导航头像 - Setting-SSH and GPG keys - "Add SSH key"

![image-20200920104759403](..\images\image-20200920104759403.png)

## 3. 添加远程免密origin

```python
git remote add origin git@github.com:myles-hub/watchlist.git
```

## 4.  同步本地数据github

```cmd
$ git push origin master
The authenticity of host 'github.com (13.250.177.223)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'github.com,13.250.177.223' (RSA) to the list of known hosts.
Enumerating objects: 33, done.
Counting objects: 100% (33/33), done.
Delta compression using up to 4 threads
Compressing objects: 100% (20/20), done.
Writing objects: 100% (28/28), 62.65 KiB | 291.00 KiB/s, done.
Total 28 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To github.com:myles-hub/watchlist.git
   14ba65e..2cb99d7  master -> master
(env)

```



