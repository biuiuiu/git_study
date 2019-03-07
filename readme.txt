git study


====================git 本地仓库 =============================
git init 初始化文件夹，使其成为能够被git管理的仓库，会生成.git的隐藏文件供git跟踪和管理版本变动

在文件夹下新建readme.txt文件
git add readme.txt 添加到暂存区，等待commit

此时可以用git status 查看git状态

git commit -m "注释"  提交改动到本地仓库，等待push

版本回退--适用于本地commit但还没有push的情况

git log --pretty=oneline 查看git提交记录 ，找到想回退的commit_id。

git reset --hard commit_id 回退到对应的版本

如果还想回到之后的版本，只需要知道commit_id即可。对于git而言，版本回退非常快，因为git是靠head指针来记录版本，修改版本只需要移动指针即可。


=======================git remote 操作================

git remote -v 显示当前git有哪些远程仓库，-v显示全部信息

git remote add 远程仓库名（一般是origin主线） url （git仓库地址）
eg：git remote add origin https://github.com/biuiuiu/git_study.git

git remote remove 远程仓库名 删除跟此远程的关联

git push -u 远程仓库名 本地仓库名 ：（分支） -u是讲远程仓库与本地设置默认关联，以后可以不用指定远程仓库
分支名不写的话，git会关联查找与当前分支名字相同的分支
eg: git push -u origin master  


git clone 右键在文件夹从远程仓库获取代码到本地仓库


============================git branch 分支操作=====================










====================================================================
一个仓库下的几个分支同步代码，但是不想同步A分支所有的代码，只同步某次提交的改动的功能。
git log --pretty=oneline获取commit_id，
git cherry-pick commit_id 获取某次提交代码到本地仓库
git push 推送到远程仓库


