> 我的NPM网址：https://www.npmjs.com/~xiaotong.hu  
> 用户名：xiaotong.hu  
> 密码：webdevelop  
 
> GitHub的地址：https://github.com/four-leaf-clover  
> 登录名：xiaotong.hu@yahoo.com  
> 密码：0912webdevelop  

 ## 一、npm publish 发布示例
```
初始化 

package.json：npm init
```
```
验证你在 npmjs.org 上的账号

npm adduser
```
# <font size="3" color="red">发布：npm publish .  注意事项</font>
* 如果你以后修改了代码，然后想要同步到npm上的话请修改 package.json中的version然后再次publish。
* 使用 cnpm 的注意报错：  
    > no_perms Private mode enable, only admin can publish this module 
* 设置回原本的就可以了：  
    > npm config set registry http://registry.npmjs.org  

## 二、example
1. 编写模块
``` javascript
exports.sayHello = function () { 
    return 'Hello World'; 
} 

保存为index.js  
```
2. 初始化包描述文件
> $ npm init 
``` json
package.json文件

{ 
    "name": "wu_xx", 
    "version": "1.0.1", 
    "description": "wu_xx first demo", 
    "main": "index.js", 
    "scripts": { 
        "test": "make test" 
    }, 
    "repository": { 
        "type": "Git", 
        "url": "git+https://github.com/blackwuxin/testdemo.git" 
    }, 
    "keywords": ["demo" ], 
    "author": "wu_xx", 
    "license": "ISC", 
    "bugs": { 
        "url": "https://github.com/blackwuxin/testdemo/issues" 
    }, 
    "homepage": "https://github.com/blackwuxin/testdemo#readme", 
} 
```
3. 注册npm仓库账号
> https://www.npmjs.com 上面的账号 
```
$ npm adduser
```
4. 上传包
```
$ npm publish
```
5. 安装包
```
$ npm install wu_xx
```
6. 管理包权限
* 查看模块拥有者 
    > $ npm owner ls <package_name> 
* 添加一个发布者 
    > $ npm owner add <user> <package_name> 
* 删除一个发布者 
    > $ npm owner rm <user> <package_name>
7. 分析包，查看当前项目引用了哪些包 
    > npm ls
8. 使用引入包
``` Javascript
var hello = require('wu_xx'); 

hello.sayHello();
```













