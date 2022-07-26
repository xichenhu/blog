# nodeJS

### 什么是模块化？什么是模块化开发？
模块化是将项目中不同的功能拆分成多个独立的模块，通过模块之间的互相组合完成一定功能的操作过程模块化开发完成模块化拆分和最后的模块化合并的开发模式。

### 简述面相过程和面向对象的联系和区别？

### module.exports和exports有什么区别？

### http模块如何创建并启动一个web服务？

### 什么是IP地址？什么是端口？什么是网络协议？你都知道那些常见的网络协议？

### 什么是NodeJS？NodeJS有哪些特点？

### 简述一个请求从发起到看到了浏览器页面的过程中都发生了什么事

### npm 命令的作用是什么？都有哪些常见的操作命令

### 简述常见的NodeJS模块

### 什么是中间件,Express中有哪些不同的中间件

### 什么是session，什么是cookie，它们有什么联系和区别

### 为什么说NodeJS是事件驱动的，底层实现逻辑是什么样的

### 请介绍一下Node事件循环的流程

### nodejs适合处理高并发的原因

### 为什么引入node中间层

### Promise是属于微任务吗？【不 promise.then属于微任务】 什么是微任务，什么是宏任务

### koa2,koa1和express区别
[koa2,koa1和express区别](https://juejin.cn/post/6844903973065850888)

### 在Node中使用模板引擎
[在Node中使用模板引擎](https://juejin.cn/post/6844903973065850888)

### v8引擎如何解析js代码
* 先转成AST树，再转成机器码，最后转为字节码，执行字节码。浏览器对重复的js代码有优化 即时编译技术，如果发现一段代码经常使用，则不用转字节码 直接执行机器码

### 适用nodejs的场景
* RESTful API
* 统一Web应用的UI层
* 大量Ajax请求的应用
* 开发命令行工具

### nodejs的优缺点
* 优点
    * 处理高并发场景性能更高
    * 适合I/O密集型应用
* 缺点
    * 不适用用CPU密集型
        * CPU使用率较重、IO使用率较轻的应用——如视频编码、人工智能等，Node.js的优势无法发挥
    * nodejs是单线程的，只支持单核CPU，无法充分利用多核 CPU 的性能
    * 可靠性低，一旦代码某个环节崩溃，整个系统都崩溃
* 解决方案
    * Nnigx反向代理，负载均衡，开多个进程，绑定多个端口
    * 单线程变成多线程：开多个进程监听同一个端口，使用cluster模块

### 请谈一下内存泄漏是什么，以及常见内存泄漏的原因，和排查的方法
* 什么是内存泄漏
    > 内存泄漏(Memory Leak)指由于疏忽或错误造成程序未能释放已经不再使用的内存的情况。
    如果内存泄漏的位置比较关键，那么随着处理的进行可能持有越来越多的无用内存，这些无用的内存变多会引起服务器响应速度变慢。
    严重的情况下导致内存达到某个极限(可能是进程的上限，如 v8 的上限;也可能是系统可提供的内存上限)会使得应用程序崩溃。
* 常见内存泄漏的原因内存泄漏的几种情况:
    * 全局变量
        ``` Java
            a = 10; // 未声明对象。
            global.b = 11;  // 全局变量引用
            // 这种比较简单的原因，全局变量直接挂在 root 对象上，不会被清除掉。
        ```
    * 闭包
    * 事件监听： 对同一个事件重复监听，忘记移除(removeListener)，将造成内存泄漏。
* 排查方法
### 什么是错误优先的回调函数？
* 错误优先的回调函数用于传递错误和数据。第一个参数始终应该是一个错误对象， 用于检查程序是否发生了错误。其余的参数用于传递数据。例如：
    ``` Java
        fs.readFile(filePath, function(err, data) {  
            if (err) {
                //handle the error
            }
            // use the data object
        });
    ```
> 解析：这个题目的主要作用在于检查被面试者对于Node中异步操作的一些基本知识的掌握。

### 如何用Node监听80端口
* 这题有陷阱！在类Unix系统中你不应该尝试去监听80端口，因为这需要超级用户权限。 因此不推荐让你的应用直接监听这个端口。
* 目前，如果你一定要让你的应用监听80端口的话，你可以有通过在Node应用的前方再增加一层反向代理 （例如nginx）来实现，如下图所示。否则，建议你直接监听大于1024的端口。
> 解释：这个问题用于检查被面试者是否有实际运行Node应用的经验。

### 什么是Stub？举个使用场景
* Stub是用于模拟一个组件或模块的函数或程序。在测试用例中， 简单的说，你可以用Stub去模拟一个方法，从而避免调用真实的方法， 使用Stub你还可以返回虚构的结果。你可以配合断言使用Stub.
* 举个例子，在一个读取文件的场景中，当你不想读取一个真正的文件时：
``` Java
    var fs = require('fs');
    var readFileStub = sinon.stub(fs, 'readFile', function (path, cb) {  
        return cb(null, 'filecontent');
    });
    expect(readFileStub).to.be.called;  
    readFileStub.restore(); 
```
> 在单元测试中：Stub是完全模拟一个外部依赖，而Mock常用来判断测试通过还是失败。
> 解析：用于测试被面试者是否有测试的经验。如果被面试者知道什么是Stub， 那么可以继续问他是如何做单元测试的。

### 什么是测试金字塔？

## 事件循环机制
### 什么是同步异步
* 同步
    * 等待被调用方执行完毕才能继续执行
    * 会阻塞后面代码的执行
* 异步
    * 不需要一直等待被调用方响应，调用方的主动轮询和被调用方的主动通知
    * 不会阻塞后面代码的执行
* 区别：调用过程中是主动等待还是被动通知，是否阻塞

### 什么是阻塞非阻塞
* 区别：调用状态，调用方在获取结果的过程中是干等还是互不耽误
* 异步非阻塞是节约调用方时间的（nodejs 一大特点）

### 什么是异步IO
* 操作系统所提供的IO能力
* 生活中可见的IO能力：人机交互，数据的进出，鼠标键盘等物理接口为输入，显示器为输出。这些接口再向下会进入操作系统层面，操作系统会提供诸多能力（磁盘读写，DNS查询，数据库连接）+ 上层应用和下层系统之间的交互，同步阻塞则为同步IO，异步非阻塞则为异步IO
* nodejs 中 fs 模块里的 readFile 文件读写就是典型异步IO，readFileSync 就是同步IO

### 什么是单线程
* 同一时间只能做一件事情，两段js代码不能同时执行
* 原因是避免DOM渲染冲突。多行js同时执行时，可能会同时操作DOM，引发冲突
* 异步是js单线程的解决方案，是一种无奈的解决方案，还存在很多问题
    * 没有按照书写方式执行，可读性差
    * callback 中不容易模块化
* 实现方式 event-loop

### 浏览器的事件循环机制 event-loop
* js实现异步的具体解决方案
* 同步代码，在主进程中直接执行
* 异步函数先放在异步队列中
* 待同步函数执行完毕，轮询执行异步队列的任务
    * 宏任务 macrotask
        * script 整体代码
        * setTimeout
        * setInterval
        * setImmediate
        * I/O
        * ui render
    * 微任务 microtask
        * process.nextTick
        * promise.then
        * async/await（实则就是promise）
        * MutationObserver（h5新特性）

### 你见过小程序跨域吗？
* 「没有」那意思就是跨域只在浏览器出现，那么 proxy解决跨域的原理就是启动了node服务 器，转发其他端口的服务到本地，这样就不会跨域了。
[你见过小程序跨域吗](https://juejin.cn/post/6844904167002079239?utm_source=gold_browser_extension)