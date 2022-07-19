## git branch -a -vv
> 显示远程和本地所有的分支，并显示各个分支最近的一次提交信息

## git remote prune origin
> 清理远程上不存在的分支

## git tag -l | xargs git tag -d
> 可以先删除所有本地tag
## git fetch --tags
> 然后再拉取远程上的tag

## git push origin --delete branchName
> 删除远程分支
## git branch -D
> 删除本地分支