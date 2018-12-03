title: How To GitHub
author: Tim Zhang
tags:
  - GitHub
  - How-To
categories:
  - GitHub
  - How-To
date: 2015-12-03 15:57:00
---
### 第一步：在github上手动创建仓库[name of your repo]

GitHub Url(https://www.github.com)

### 第二步：本地建立git仓库操作

```sh
cd [name of your repo]
git init #初始化本地仓库
git add xxx #添加要push到远程仓库的文件或文件夹
git commit -m ‘first commit’
git remote add origin https://github.com/yourgithubID/gitRepo.git #建立github远程仓库信息
git pull --rebase origin master #通过如下命令将远程代码合并到本地仓库（注：pull=fetch+merge)
```

### 第三步：本地代码上传github仓库

```sh
git push -u origin master #将本地仓库push到远程仓库
```
