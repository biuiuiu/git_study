git study

git init 初始化文件夹，使其成为能够被git管理的仓库，会生成.git的隐藏文件供git跟踪和管理版本变动

在文件夹下新建readme.txt文件
git add readme.txt 添加到暂存区，等待commit

此时可以用git status 查看git状态

git commit -m "注释"  提交改动到本地仓库，等待push

版本回退--适用于本地commit但还没有push的情况

git log --pretty=oneline 查看git提交记录 ，找到想回退的commit_id。

git reset --hard commit_id 回退到对应的版本

如果还想回到之后的版本，只需要知道commit_id即可。对于git而言，版本回退非常快，因为git是靠head指针来记录版本，修改版本只需要移动指针即可。

