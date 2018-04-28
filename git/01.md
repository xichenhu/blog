## 上传本地项目到github
### 1、创建一个本地项目
这是我自己创建的几个文件夹及文件。

![avatar](./img/1.png)
### 2、建立本地仓库

```javascript
> 1. 首先进入text文件夹: cd d:text
```

![avatar](./img/2.png)

```javascript
> 2. 执行指令：git init
```

![avatar](./img/3.png)

初始化成功后你会发现项目里多了一个隐藏文件夹.git

![avatar](./img/4.png)


```javascript
> 3. 执行指令：git add . (将所有文件添加到仓库)
```

![avatar](./img/5.png)

```javascript
> 4. 执行指令：git commit -m "提交文件" (双引号内是提交注释)
```

![avatar](./img/6.png)
### 3、关联github仓库
```javascript
> 1. github text仓库复制仓库地址
```

![avatar](./img/7.png)

```javascript
> 2. 执行指令：git remote add origin https://github.com/hanyuntao/text.git
```

![avatar](./img/8.png)
### 4、上传本地代码
```javascript
> 执行指令：git push -u origin master
```

![avatar](./img/9.png)
### 5、完成了
可以看到我们的本地项目已经上传到了github上了。

![avatar](./img/10.png)
