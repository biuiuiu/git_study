git study


====================git 本地仓库 =============================

#初始化文件夹，使其成为能够被git管理的仓库，会生成.git的隐藏文件供git跟踪和管理版本变动
git init 

#在文件夹下新建readme.txt文件，添加到暂存区，等待commit
git add readme.txt 

此时可以用git status 查看git状态

#提交改动到本地仓库，等待push
git commit -m "注释"  


#查看git提交记录 ，找到想回退的commit_id。
git log --pretty=oneline 
#命令可以看到分支合并图
git log --graph
#版本回退 -- 回退到对应的版本
git reset --hard commit_id 

如果还想回到之后的版本，只需要知道commit_id即可。对于git而言，版本回退非常快，因为git是靠head指针来记录版本，修改版本只需要移动指针即可。


=======================git remote 操作================

#显示当前git有哪些远程仓库，-v显示全部信息
git remote -v 

git remote add 远程仓库名（一般是origin主线） url （git仓库地址）
eg：git remote add origin https://github.com/biuiuiu/git_study.git

#删除跟本地仓库有关联的远程仓库
git remote remove 远程仓库名 

git push -u 远程仓库名 本地仓库名 ：（分支） #-u是讲远程仓库与本地设置默认关联，以后可以不用指定远程仓库
#分支名不写的话，git会关联查找与当前分支名字相同的分支
eg: git push -u origin master  

#右键在文件夹从远程仓库获取代码到本地仓库
git clone 


============================git branch 分支操作=====================
#查看git所有分支，当前分支会显示绿色，-a显示本地和远程分支
git branch -a 

#创建test_dev分支，但不会切换，还在master分支
git branch test_dev 
#此时分支只在本地仓库，如果要在远程也有分支，则需要 
git push origin test_dev 

#切换到test_dev分支
git checkout test_dev 

#切回master分支
git checkout master 

#创建并切换新分支
git checkout -b test_second 

#删除分支-针对以及合并到master的分支
git branch -d test_dev

#删除分支-对于还没合并到master的分支，强行删除
git branch -D test_dev

#删除远程分支
git push origin --delete test_dev

#合并test_dev分支到master
git checkout master #切换master
git merge test_dev  #merge test_dev到本地仓库
git push origin master #推送远程仓库


==================================tags操作==========================
稳定的版本可以打tag做记录，在GitHub上可以直接下载这个版本的代码

#新建tag
git tag tag_name (一般在最新的commit上打tag，如果指定某个commit_id，git tag tag_name commit_id)

#查询tag
git tag 

#删除tag
git tag -d tag_name

#以上操作都是操作本地仓库，把tagpush到远程
git push origin tag_name 

#如果tag已经推送到远程，删除tag
#先删除本地
git tag -d tag_name 
#删除远程
git push origin :refs/tags/tag_name



====================================================================
一个仓库下的几个分支同步代码，但是不想同步A分支所有的代码，只同步某次提交的改动的功能。
git log --pretty=oneline获取commit_id，
git cherry-pick commit_id 获取某次提交代码到本地仓库
git push 推送到远程仓库


