# git分享学习交流会


主持人：朱泽昌

编写日期：2017/12/12

前语：在编辑这个文档的时候，我的内心都很挣扎；结合公司现在实际旧项目SVN都满足当前的使用场景；git虽然现在市面很流行，但到底适不适用；有句话说得好：“==请以解决问题为核心，不要为了用技术而用技术==”，如果大家觉得通过使用git提升工作效率，减少重复工作，更加方便的沟通，那么就可以去推开使用；

摘要：这次交流会我会从git的发展史，git/svn区别，git的命令，git的图形界面推荐，结合项目git使用几方面做简述，以便大家交流学习。

git官网：https://www.atlassian.com/git


---

- ## git的发展史
- #### 定义：
Git是一款免费、开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。
- #### 简史：
到了 2005 年，开发 BitKeeper 的商业公司同 Linux 内核开源社区的合作关系结束，他们收回了 Linux 内核社区免费使用 BitKeeper 的权力。

  这就迫使 Linux 开源社区（特别是 Linux 的缔造者 Linux Torvalds）基于使用 BitKeeper 时的经验教训，开发出自己的版本系统。

他们对新的系统制订了若干目标：
- 速度
- 简单的设计
- 对非线性开发模式的强力支持（允许成千上万个并行开发的分支）
- 完全分布式
- 有能力高效管理类似 Linux 内核一样的超大规模项目（速度和数据量）

  自诞生于 2005 年以来，Git 日臻成熟完善，在高度易用的同时，仍然保留着初期设定的目标。
它的速度飞快，极其适合管理大项目，有着令人难以置信的非线性分支管理系统
 
- #### 发展历程：       
- git：https://www.atlassian.com/git/articles/10-years-of-git
- ## git/svn对比
- #### 区别：
- Git相比SVN，最大的特点也是优点在于提供分布式的代码管理。这不是说SVN等不具有该功能，但就目前来看，Git更完善，而且也越来越多地被人们所接受。
- git在本地就可以用，可以随便保存各种历史痕迹，不用担心污染服务器。svn commit就到服务器了，有时候发现commit错了或不全就得再来一遍（git commit --amend）
- git拉branch和在branch之间切换都非常简单，可以随便折腾。svn一个branch就是一个copy
- git绝对不会有被lock了不能commit的情况
- 方便切换上下文，以及代码间的协作。代码冲突，突然来临的修改任务，代码 review 这些其实都是工程师经常面临的问题。git 在这些方面处理的还是不错的。git 默认的 stash, chekcout, branch, 都提供了一些常用的切换上下文的便利。在一个混乱没有章法的代码管理的情况下，git 这样做，约定了一些使用习惯，实际上是提升了工作效率。
- #### 版本控制：
- svn集中化的版本控制系统

  单一的集中管理的服务器，保存所有文件的修订版本，而协同工作的人们都通过客户端连到这台服务器，取出最新的文件或者提交更新； 而管理员也可以轻松掌控每个开发者的权限。这么做最显而易见的缺点是中央服务器的单点故障。 如果宕机一小时，那么在这一小时内，谁都无法提交更新，也就无法协同工作。 如果中心数据库所在的磁盘发生损坏，又没有做恰当备份，毫无疑问你将丢失所有数据——包括项目的整个变更历史，只剩下人们在各自机器上保留的单独快照。

- git分布式版本控制系统

  客户端并不只提取最新版本的文件快照，而是把代码仓库完整地镜像下来。 这么一来，任何一处协同工作用的服务器发生故障，事后都可以用任何一个镜像出来的本地仓库恢复。 因为每一次的克隆操作，实际上都是一次对代码仓库的完整备份。
 
- SVN的中心式管理模式很简单，学习成本低，Git灵活方便，但是管理起来复杂度高学习成本高”。

- ## git的命令
    - 查看配置
        - git config --list 
    - 配置
        - git config --global user.name "your name"
        - git config --global user.email youremail@mail.com
    - 生成SSH
        - ssh-keygen -t rsa -C "631634325@qq.com"
        - id_rsa(私钥) id_rsa(公钥)
        - cat id_rsa.pub
        - 配置到git服务器中
    - 创建新仓
        - 在桌面建立一个文件夹
        - git init 
        - hello.php新建
    - 克隆仓
        - git clone git@github.com:zekezhu/gittest.git 
    - 检查状态
        - git status
    - 添加文件
        - git add hello.php
        - git add -a//暂存所有文件
        - git status
    - 暂存文件
        - 使用git的时候，我们往往使用branch解决任务切换问题，例如，我们往往会建一个自己的分支去修改和调试代码, 如果别人或者自己发现原有的分支上有个不得不修改的bug，我们往往会把完成一半的代码 commit提交到本地仓库，然后切换分支去修改bug，改好之后再切换回来。这样的话往往log上会有大量不必要的记录。
        - git stash 暂存
        - git stash pop 获取最近暂存
        - git stash list 
        - git stash clear
    - 删除文件
        - git rm [file1][file2]...
    - 停止跟踪文件
        - git rm --cached [file]
    - 改名文件
        - git mv [file-original][file-rename] 
    - 提交
        - git commit -m "hello"
    - 到目前为止，我们的操作都是在本地的，它存在于.git文件中。为了能够协同开发，我们需要把代码发布到远端仓库上。
    - 上传到服务器
        - git push origin master git@github.com:zekezhu/gittest.git 
        - git branch -a
    - 从服务器拉取代码
        - git pull origin master
        - git fetch -a
    - 当你在做一个新功能的时候，最好是在一个独立的区域上开发，通常称之为分支。分支之间相互独立，并且拥有自己的历史记录。这样做的原因是：
        - 稳定版本的代码不会被破坏
        - 不同的功能可以由不同开发者同时开发。
        - 开发者可以专注于自己的分支，不用担心被其他人破坏了环境
        - 在不确定之前，同一个特性可以拥有几个版本，便于比较
        - 创建分支
        - git branch zhuzechang//新分支跟当前分支同一起点
    - 切换分支
        - git checkout zhuzechang
    - 合并分支
        - git checkout master
        - git merge zhuzechang
    - 删除分支
        - git branch -d zhuzechang 
    - 比较
        - git log//查看提交拿出ID
        - git show id
        - git diff id//当前版本与版本ID对比
    - 回滚某个文件到指定版本
        - git checkout 版本ID 文件名
    - 回滚提交
        - 回滚提交时，发生冲突是非常频繁的。当文件被后面的提交修改了以后，git不能正确回滚。
        - git revert b10cc123
    
- ## git的图形界面推荐
    - sourcetree 
- 
- ## 结合项目
- 