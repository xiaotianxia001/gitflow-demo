# gitflow-demo
A demo for git flow
项目背景：
在接入到集团后，我们进行中的项目使用的git也统一到集团的git flow分支管理应用上。
思考：
git flow相较之前的git分支管理的优势是什么？
知识点汇聚：
0.git的几种工作流方式
1.git flow是什么？较之前的git有什么优势。
2.git flow的使用
3.项目中的使用

0.git的几种工作流方式
git的工作流一般有如下集中：集中式工作流，功能分支工作流，gitflow工作流，forking工作流
集中式工作流：类似svn，它只有一个master分支，开发者会先把远程的仓库克隆到本地，之后的修 改和提交都在本地操作，直到在某个合适的时间点将本地的代码合入到远程master。这种工作流比 较适合小团队，因为小团队可能不会太多的协作和合流的动作。
功能分支工作流：这种工作流关注功能开发，不直接往master提交代码保证它是稳定并且干净的，而是从master拉 取feature分支进行功能开发，团队成员根据分工拉取不同的功能分支来进行不同的功能开发，这样 就可以完全隔离开每个人的工作。当功能开发完成后，会向master分支发起Pull Request，只有审 核通过的代码才真正允许合入master，这样就加强了团队成员之间的代码交流。
gitflow工作流：它会相对复杂一点，但它非常适合用来管理大型项目的发布和维护，后面也会详细讲下这一块。 贯穿整个开发周期，master和develop分支是一直存在的，master分支可以被视为稳定的分支， 而develop分支是相对稳定的分支，特性开发会在feature分支上进行，发布会在release分支上 进行，而bug修复则会在hotfix分支上进行。
forking工作流：Forking工作流对于开源项目贡献者一定不陌生了，它有一个公开的中央仓库，其他贡献 者可以Fork（克隆）这个仓库作为你自己的私有仓库，开源项目维护者可以直接往中央仓库 push代码，而代码贡献者只能将代码push到自己的私有仓库，只有项目维护者接受代码贡献 者往中央仓库发起的pull request才会真正合入。

1.git flow是什么？较之前的git有什么优势。
git flow是一种代码管理方案，适合用来管理大型项目的发布和维护。通过为功能开发、发布准备和维护分配独立的分支，让发布迭代过程更流畅。严格的分支模型也为大型项目提供了一些非常必要的结构。可以并行开发，支持紧急修复（hotfix），可以协同开发，增加发布分支。



2.git flow的使用
利用gitflow操作命令来新建分支管理分支
2.1 git flow的下载和使用 
安装：brew install git flow 
初始化：git flow init
2.2创建feature功能分支
创建：git flow feature start feature-v1
推送到远程： git flow feature publish  feature-v1
获取分支:  git flow feature pull origin feature-v1
完成： git flow feature finish feature-v1
2.3创建release分支
基于develop分支创建：  git flow release start release-v1 develop
推送到远程： git flow release publish release-v1
完成一个release分支： git flow release finish release-v1
利用命令行来新建分支管理分支
feature分支
2.1创建develop分支
git branch develop
git push -u origin develop
2.2创建feature分支
git checkout -b feature-v1 develop
git push -u origin feature-v1
2.3完成feature分支
git pull origin develop
git checkout develop
git merge --no-ff feature-v1
git push origin develop
git branch -d feature-v1
git push origin --delete feture-v1

release分支
2.1创建
git checkout -b release-v1 develop
2.2完成
git checkout master
git merge --no-ff release-v1
git push
git checkout develop
git merge --no-ff release-v1
git push
git branch -d release-v1  
git push origin --delete release-v1  
hotfix分支
2.1创建
git checkout -b hotfix-v1 master
2.2完成
git checkout master 
git merge --no-ff hotfix-v1 
git push
git checkout develop
git merge --no-ff hotfix-v1
git push
git branch -d hotfix-v1
git tag -a tag-v1 master
git push --tags

在sourcetree中使用git flow

3.项目中的使用

