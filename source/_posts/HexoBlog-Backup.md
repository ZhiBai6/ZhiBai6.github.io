---
title: Hexo博客的备份
date: 2022-06-10 22:24:03
categories:
 - 博客
tags:
 - 备份
 - Hexo
 - 博客
---
# Hexo博客的备份

<!-- more -->
* ### 前提、机制
    前提是你已经初始化好了自己想要备份的那个博客。GIT、GitHub/Gitee环境已经准备好了。

    机制是这样的，由于hexo d上传部署到github的其实是hexo编译后的文件，是用来生成网页的，不包含源文件。

### 备份博客
* #### 创建新分支
    在确保有master分支的情况下创建一个用来备份的新分支Hexo，并且将其设置为默认分支

* #### 获取.git文件
    原始的博客文件夹只有 .deploy_git 文件夹

    没有 .git 文件夹，所以我们需要把新分支 clone 到随便一个文件夹，然后把 .git 文件放入现在的博客文件夹中

* #### .gitignore 文件
```
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
```

**注意，如果你之前克隆过theme中的主题文件，那么应该把主题文件中的.git文件夹删掉，因为git不能嵌套上传，最好是显示隐藏文件，检查一下有没有，否则上传的时候会出错，导致你的主题文件无法上传，这样你的配置在别的电脑上就用不了了。**

* #### 备份
    通过如下命令将本地文件备份到 Github 上。
        
        $ git add .
        $ git commit -m "Backup"
        $ git push origin hexo
    这样就备份完博客了且在Github上能看到两个分支(master和hexo)。

* #### 备份命令
        hexo clean
        git add .
        git commit -m "Backup"
        git push
        hexo g
        hexo d

### 恢复博客
安装git、安装nodejs、安装hexo。
  
* #### 克隆项目到本地
        $ git clone https://github.com/qq825204921/qq825204921.github.io
* #### 恢复博客的命令
        $ npm install hexo-cli
        $ npm install
        $ npm install hexo-deployer-git

    **在此不用执行 hexo init 指令，因为不是从零开始搭建博客。**

### 恢复完成
    hexo clean
    hexo g
    hexo d
    hexo s

查看本地运行状态，可以开始写博客了！