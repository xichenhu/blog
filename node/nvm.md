# 使用 nvm 管理多版本 node
### 卸载已安装到全局的 node/npm
> ### 查看已经安装在全局的模块，以便删除这些全局模块后再按照不同的 node 版本重新进行全局安装
> npm ls -g --depth=0 
> ### 删除全局 node_modules 目录
> sudo rm -rf /usr/local/lib/node_modules 
> ### 删除 node
> sudo rm /usr/local/bin/node 
> ### 删除全局 node 模块注册的软链
> cd  /usr/local/bin && ls -l | grep "../lib/node_modules/" | awk '{print $9}'| xargs rm
> 

### 安装nvm
``` DOS
$ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash
```
### 查看当前系统node版本
```
nvm ls
```
### 用“nvm install”安装指定版本的node
```
nvm install v8.0.0
```
### "nvm uninstall"删除已安装的指定版本，语法与install类似

```
nvm uninstall v8.0.0
```
### 使用"nvm use"可以切换node版本
```
nvm use v6.10.0
```

### 设置系统用户默认的node版本，可以用"nvm alias default"
```
nvm alias default v8.0.0
```