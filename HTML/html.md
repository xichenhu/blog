# HTML
# src和href的区别
src和href都是用来引用外部的资源
### src
* 指向的内容会嵌入到当前标签所在的位置
* src会将其指向的资源下载并应⽤到⽂档内，如请求js脚本。
> 当浏览器解析到该元素时，会阻塞页面渲染，所以⼀般js脚本会放在页面底部。
### href
* 表示超文本引用，它指向一些网络资源，建立和当前元素或本文档的链接关系。
> 当浏览器识别到它他指向的⽂件时，就会并⾏下载资源，不会停⽌对当前⽂档的处理。 常用在a、link等标签上。

# 对HTML语义化的理解
根据内容的结构，选择合适的标签
### 语义化的优点
1. 对机器友好，适合搜索引擎的爬虫爬取有效信息，有利于SEO。
2. 对开发者友好，增强了可读性，结构更加清晰，便于团队的开发与维护。
### 常见语义化标签
``` Java
<header></header>  头部
<nav></nav>  导航栏
<section></section>  区块（有语义化的div）
<main></main>  主要区域
<article></article>  主要内容
<aside></aside>  侧边栏
<footer></footer>  底部
```

# script标签中defer和async的区别
如果没有defer或async属性，浏览器会立即加载并执行相应的脚本。读取到就会开始加载和执行，会阻塞后续文档的加载。
> defer 和 async属性都是去异步加载外部的JS脚本文件，它们都不会阻塞页面的解析。
### 区别
* 执行顺序：
    * 多个带async属性的标签，不能保证加载的顺序。
    * 多个带defer属性的标签，按照加载顺序执行。
* 脚本是否并行执行：
    * async属性，表示后续文档的加载和执行与js脚本的加载和执行是并行进行的，即异步执行。
    * defer属性，加载后续文档的过程和js脚本的加载(此时仅加载不执行)是并行进行的(异步)，js脚本需要等到文档所有元素解析完成之后才执行，DOMContentLoaded事件触发执行之前。

# HTML5有哪些更新
### 语义化标签
* header：定义文档的页眉（头部）；
* nav：定义导航链接的部分；
* footer：定义文档或节的页脚（底部）；
* article：定义文章内容；
* section：定义文档中的节（section、区段）；
* aside：定义其所处内容之外的内容（侧边）；
### 媒体标签
* audio：音频
* video：视频
### 表单
* 表单类型
    * email ：能够验证当前输入的邮箱地址是否合法
    * url ： 验证URL
    * number ： 只能输入数字，其他输入不了，而且自带上下增大减小箭头，max属性可以设置为最大值，min可以设置为最小值，value为默认值。
    * search ： 输入框后面会给提供一个小叉，可以删除输入的内容，更加人性化。
    * range ： 可以提供给一个范围，其中可以设置max和min以及value，其中value属性可以设置为默认值
    * color ： 提供了一个颜色拾取器
    * time ： 时分秒
    * data ： 日期选择年月日
    * datatime ： 时间和日期(目前只有Safari支持)
    * datatime-local ：日期时间控件
    * week ：周控件
    * month：月控件
* 表单属性
    * placeholder ：提示信息
    * autofocus ：自动获取焦点
    * autocomplete=“on” 或者 autocomplete=“off” 使用这个属性需要有两个前提：
    * 表单必须提交过
    * 必须有name属性。
    * required：要求输入框不能为空，必须有值才能够提交。
    * pattern=" " 里面写入想要的正则模式，例如手机号patte="^(+86)?\d{10}$"
    * multiple：可以选择多个文件或者多个邮箱
    * form=" form表单的ID"
* 表单事件
    * oninput 每当input里的输入框内容发生变化都会触发此事件。
    * oninvalid 当验证不通过时触发此事件。

# 行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？
* 行内元素有：a b span img input select strong
* 块级元素有：div ul ol li dl dt dd h1 h2 h3 h4 h5 h6 p；
* 空元素，即没有内容的HTML元素。空元素是在开始标签中关闭的，也就是空元素没有闭合标签：
    * 常见的有：<br>、<hr>、<img>、<input>、<link>、<meta>；
    * 鲜见的有：<area>、<base>、<col>、<colgroup>、<command>、<embed>、<param>、<source>、<track>。

# 参考资料
[「2021」高频前端面试题汇总之HTML篇](https://juejin.cn/post/6905294475539513352#heading-15)

# DOCTYPE(⽂档类型) 的作⽤
文档类型声明，
## 作用
告诉浏览器（解析器）应该以什么样（html或xhtml）的文档类型定义来解析文档。
## 原因
不同的渲染模式会影响浏览器对 CSS 代码甚⾄ JavaScript 脚本的解析。
## 使用
它必须声明在HTML⽂档的第⼀⾏。
## 模式分类
1. 标准模式（Strick mode）：在标准模式中，浏览器以其支持的最高标准呈现页面。
2. 怪异模式(混杂模式)(Quick mode)：在怪异模式中，页面以一种比较宽松的向后兼容的方式显示。

# 常⽤的meta标签有哪些
meta 标签由 name 和 content 属性定义，用来描述网页文档的属性，比如网页的作者，网页描述，关键词等，除了HTTP标准固定了一些name作为大家使用的共识，开发者还可以自定义name。
## 常用的meta标签
1. charset，用来描述HTML文档的编码类型
2. keywords，页面关键词
3. description，页面描述
4. refresh，页面重定向和刷新
``` Java
<meta http-equiv="refresh" content="0;url=" />
```
5. viewport，适配移动端，可以控制视口的大小和比例
``` Java
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
```
    * content 参数有以下几种
        * width viewport ：宽度(数值/device-width)
        * height viewport ：高度(数值/device-height)
        * initial-scale ：初始缩放比例
        * maximum-scale ：最大缩放比例
        * minimum-scale ：最小缩放比例
        * user-scalable ：是否允许用户缩放(yes/no）
6. 搜索引擎索引方式
``` Java
<meta name="robots" content="index,follow" />
```
    * content 参数有以下几种
        * all：文件将被检索，且页面上的链接可以被查询
        * none：文件将不被检索，且页面上的链接不可以被查询；
        * index：文件将被检索；
        * follow：页面上的链接可以被查询；
        * noindex：文件将不被检索；
        * nofollow：页面上的链接不可以被查询。

# 说一下 web worker

# head 标签有什么作用，其中什么标签必不可少？
标签用于定义文档的头部，它是所有头部元素的容器。
下面这些标签可用在 head 部分：<base>, <link>, <meta>, <script>, <style>, <title>。
其中 <title> 定义文档的标题，它是 head 部分中唯一必需的元素。

# Canvas和SVG的区别
1. SVG：SVG可缩放矢量图形
    * 不依赖分辨率
    * 支持事件处理器
    * 最适合带有大型渲染区域的应用程序（比如谷歌地图）
    * 复杂度高会减慢渲染速度（任何过度使用 DOM 的应用都不快）
    * 不适合游戏应用
2. Canvas： Canvas是画布，通过Javascript来绘制2D图形，是逐像素进行渲染的。
    * 依赖分辨率
    * 不支持事件处理器
    * 能够以 .png 或 .jpg 格式保存结果图像
    * 最适合图像密集型的游戏，其中的许多对象会被频繁重绘

# title与h1的区别、b与strong的区别、i与em的区别？
* strong标签有语义，是起到加重语气的效果，而b标签是没有的，b标签只是一个简单加粗标签。搜索引擎更侧重strong标签。
* title属性没有明确意义只表示是个标题，H1则表示层次明确的标题，对页面信息的抓取有很大的影响
* i内容展示为斜体，em表示强调的文本


