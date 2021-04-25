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

2. 生成ssh公钥(`ssh-keygen`)









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

   ```
   git push origin newbranch
   ```

4. Finish