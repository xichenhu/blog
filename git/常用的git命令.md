# Git 常用命令
## git branch -a -vv
> 显示远程和本地所有的分支，并显示各个分支最近的一次提交信息

## git remote prune origin
> 清理远程上不存在的分支

## git push -u origin branchName
> 将本地分支和远程分支进行关联

## git tag -l | xargs git tag -d
> 可以先删除所有本地tag

## git fetch --tags
> 然后再拉取远程上的tag

## git push origin --delete branchName
> 删除远程分支
## git branch -D
> 删除本地分支

## git config --global user.name "用户名" 
## git config --global user.email "git账号" 
> 配置全局用户

## git config --global --unset alias.xxx
## git config --global --unset user.xxx
> 删除全局配置

## add和commit的合并，便捷写法（未追踪的文件无法直接提交到暂存区/本地仓库）
git commit -am "本次提交说明" 

# Git流程图
1. Workspace：工作区
2. Index / Stage：暂存区
3. Repository：仓库区（或本地仓库）
4. Remote：远程仓库

# 查看 Git 信息
## 查看系统配置
git config --list

## 查看用户配置
cat ~/.gitconfig 

## 查看当前项目的 git 配置
cat .git/config

## 查看暂存区的文件
git ls-files

## 查看所有 git 命令
git --help -a 

## 查看当前 HEAD 指向
cat .git/HEAD

## git log 点线图 符号解释
``` Javascript
*	表示一个 commit
|	表示分支前进
/	表示分叉
\	表示合入
|/	表示新分支
```

# merge 三种常用合并方法
```
# 默认 fast-forward ，HEAD 指针直接指向被合并的分支
$ git merge 

# 禁止快进式合并
$ git merge --no-ff 

$ git merge --squash 
```

# remote
```
# 查看所有远程主机
$ git remote
# 查看关联的远程仓库的详细信息
$ git remote -v 
# 删除远程仓库的 “关联”
$ git remote rm projectname 
# 设置远程仓库的 “关联”
$ git remote set-url origin <newurl>
```

## 本地新建好 Git 项目，然后关联远程仓库
```
# 初始化一个Git仓库
$ git init 
# 关联远程仓库
$ git remote add <name> <git-repo-url>  
# 例如
$ git remote add origin https://github.com/xxxxxx
```


# 参考
1. https://github.com/xiaodongxier/iWebs/issues/35
