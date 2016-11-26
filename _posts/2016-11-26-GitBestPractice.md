---
layout: post
title: git 最佳实践
tags: [git, vcs]
---

##### 基本操作  
```  
* git config --global user.name "xxxxx"  
* git config --global user.email "xxxxxxxx@xxxx.com"   
* git init  
* git remote add origin [项目地址(.git/https)]  
* git add .  
* git commit -m "提交说明"  
* git push -u origin master  
```  
 
##### 查看当前更新和提交状态  
```
* git status  
```  

##### 查看本次提交与源代码的区别  
```
* git diff
```  
##### ReInit git项目
```
* rm -rf git
* git init
```

##### 修改最后一次i提交
```
* git commit --amend
```
##### 切换分支
```
* git checkout [分支名]
```
##### 回滚到之前的版本  
注意 reset 是很暴力的，删除回滚那个版本之后的commit，HEAD 向后移动。  
而 revert 是用一次新的提交来回滚版本，HEAD 一直保持向前。  

``` 
* git reset --hard [版本号]
* git revert [版本号]
```

##### 将本次未提交的变动加入暂存区  
```
* git stash
```

### 场景一：在一台主机上同时使用 github 和公司的 gitlab 同时管理多个ssh key  

> 原文地址 http://xuyuan923.github.io/2014/11/04/github-gitlab-ssh/  

在.ssh目录下新建一个config文件配置一下，就能解决gitlab与github的ssh key的冲突。  
##### 生成并添加第一个ssh key  
```
* cd ~/.ssh
* ssh  ssh-keygen -t ras -C "youremail@yourcompany.com"
```

这时可以一路回车，不输入任何字符，将自动生成id_rsa和id_rsa.pub文件。  
##### 生成并添加第二个ssh key  
``` 
* ssh-keygen -t rsa -C "youremail@gmail.com"
```
注意，这时不能一路回车，否则邮箱将覆盖上一次生成的ssh key，给这个文件起一个名字，比如叫 `id_rsa_github`，所以相应的也会生成一个 `id_rsa_github.pub` 文件。

此时查看.ssh下的目录文件，发现多了`id_rsa_github`和`id_rsa_github.pub`两个文件。  

##### 添加私钥  
```
* ssh-add ~/.ssh/id_rsa
* ssh-add ~/.ssh/id_rsa_github
```
##### 修改配置文件
在 ~/.ssh 目录下新建一个config文件，并添加内容。  

```  
* touch config
# gitlab
Host gitlab.com
    HostName gitlab.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa
# github
Host github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa_github
 ```  
 
##### 给 github/gitlab 上添加 ssh key
查看 ssh key 执行`cat id_rsa_github.pub`内容，将文本内容拷贝到https://github.com/settings/ssh。  
生成ssh key的方法可以去看官方教程，这里不再赘述。  
