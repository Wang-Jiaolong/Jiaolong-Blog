---
layout: wikis
title: Git
description: Git 是一个开源的分布式版本控制系统,用于敏捷高效地处理任何或小或大的项目。
header-img: "img/about-bg.jpg"
catalog: true
hidden: false
---

# 使用现有仓库提交代码

1. 克隆仓库

```cmd
$ git clone git@192.168.xxx.xxx:xxx.git
```



# 修改分支名

> TODO：将分支名称为 `oldbranch` 改为 `newbranch` 

1. 将本地分支oldbranch切一个分支到本地

   ```cmd
   git branch -m oldbranch newbranch
   ```
   
2. 删除远程分支

   ```cmd
   git push --delete origin oldbranch
   ```

3. 将本地新分支推送到远程

   ```cmd
   git push origin newbranch
   ```

4. Finished

- 查看所有分支：`git branch -a`
- 查看当前分支：`git branch`
- 切换分支：`git checkout branchName`

# 新建分支

1. 新建：

   ~~~git
   git checkout newName	 --新建新分支
   git checkout -b newName	 --新建并切换分支
   ~~~

2. 提交该分支到远程仓库

   ~~~cmd
   git push origin newName
   ~~~

3. 链接分支

   ~~~cmd
   git branch --set-upstream-to=origin/newName
   ~~~

4. 取消对master的跟踪

   ~~~cmd
   git branch --unset-upstream master
   ~~~



人有悲欢离合，月有阴晴圆缺.[^1]

[^1]: 《水调歌头》

