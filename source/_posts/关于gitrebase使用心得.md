---
title: 关于gitrebase使用心得
categories:
  - git
tags:
  - rebase
mp3: 'http://domain.com/awesome.mp3'
cover: 'http://domain.com/awesome.jpg'
date: 2021-11-10 20:54:16
---
## 背景
由于公司以master分支为基线，因而每次从master切出，如果想要合入master时，就得rebase master分支。
但是每次合入rebase都会有很多冲突
## 具体原因
![git-rebase示意图](git-rebase示意图.png)
rebase最新的时候，commit 3，4，8节点会有冲突，如果旧的节点很多，你会崩溃的。
## 解决方式
主要分三种阶段
1. 开发提交时
  - git rebase -i HEAD~2 合并重复的commit
2. 合并阶段
  - 用master合并dev分之
3. 解决冲突阶段
  - 使用master分支内容，之后找到变更文件，覆盖现有的文件