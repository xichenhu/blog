# CSS 

# CSS基础
##  CSS选择器及其优先级
|选择器         |格式           |优先级权重|
|:---         |:---:        |---:         |
|id选择器       |#id                    |100|
|类选择器        |#classname            |10|
|属性选择器      |a[ref=“eee”]          |10|
|伪类选择器      |li:last-child         |10|
|标签选择器      |div                   |1|
|伪元素选择器    |li:after              |1|
|相邻兄弟选择器  |h1+p                  |0|
|子选择器       |ul>li                 |0|
|后代选择器     |li a                  |0|
|通配符选择器   |*                     |0|
### 对于选择器的优先级：
* 标签选择器、伪元素选择器：1
* 类选择器、伪类选择器、属性选择器：10
* id 选择器：100
* 内联样式：1000
### 注意事项：
* !important声明的样式的优先级最高；
* 如果优先级相同，则最后出现的样式生效；
* 继承得到的样式的优先级最低；
* 通用选择器（*）、子选择器（>）和相邻同胞选择器（+）并不在这四个等级中，所以它们的权值都为 0 ；
* 样式表的来源不同时，优先级顺序为：内联样式 > 内部样式 > 外部样式 > 浏览器用户自定义样式 > 浏览器默认样式。

# display的属性值及其作用
* none：元素不显示，并且会从文档流中移除。
* blocke：块类型。默认宽度为父元素宽度，可设置宽高，换行显示。
* inlinee：行内元素类型。默认宽度为内容宽度，不可设置宽高，同行显示。
* inline-blocke：默认宽度为内容宽度，可以设置宽高，同行显示。
* list-iteme：像块类型元素一样显示，并添加样式列表标记。
* tablee：此元素会作为块级表格来显示。
* inherite：规定应该从父元素继承display属性的值。

# display的block、inline和inline-block的区别
* block： 会独占一行，多个元素会另起一行，可以设置width、height、margin和padding属性；
* inline： 元素不会独占一行，设置width、height属性无效。但可以设置水平方向的margin和padding属性，不能设置垂直方向的padding和margin；
* inline-block： 将对象设置为inline对象，但对象的内容作为block对象呈现，之后的内联对象会被排列在同一行内。
* 对于行内元素和块级元素，其特点如下：
## 行内元素
* 设置宽高无效；
* 可以设置水平方向的margin和padding属性，不能设置垂直方向的padding和margin；
* 不会自动换行；
## 块级元素
* 可以设置宽高；
* 设置margin和padding都有效；
* 可以自动换行；
* 多个块状，默认排列从上到下。

# 隐藏元素的方法有哪些
* display: none：渲染树不会包含该渲染对象，因此该元素不会在页面中占据位置，也不会响应绑定的监听事件。
* visibility: hidden：元素在页面中仍占据空间，但是不会响应绑定的监听事件。
* opacity: 0：将元素的透明度设置为 0，以此来实现元素的隐藏。元素在页面中仍然占据空间，并且能够响应元素绑定的监听事件。
* position: absolute：通过使用绝对定位将元素移除可视区域内，以此来实现元素的隐藏。
* z-index: 负值：来使其他元素遮盖住该元素，以此来实现隐藏。
* clip/clip-path ：使用元素裁剪的方法来实现元素的隐藏，这种方法下，元素仍在页面中占据位置，但是不会响应绑定的监听事件。
* transform: scale(0,0)：将元素缩放为 0，来实现元素的隐藏。这种方法下，元素仍在页面中占据位置，但是不会响应绑定的监听事件。

# 对盒模型的理解
CSS3中的盒模型有以下两种：标准盒子模型、IE盒子模型
盒模型都是由四个部分组成的，分别是margin、border、padding和content。
标准盒模型和IE盒模型的区别在于设置width和height时，所对应的范围不同：
* 标准盒模型的width和height属性的范围只包含了content，
* IE盒模型的width和height属性的范围包含了border、padding和content。
可以通过修改元素的box-sizing属性来改变元素的盒模型：
box-sizeing: content-box表示标准盒模型（默认值）
box-sizeing: border-box表示IE盒模型（怪异盒模型）

# CSS3中有哪些新特性
* 新增各种CSS选择器 （: not(.input)：所有 class 不是“input”的节点）
* 圆角 （border-radius:8px）
* 多列布局 （multi-column layout）
* 阴影和反射 （Shadoweflect）
* 文字特效 （text-shadow）
* 文字渲染 （Text-decoration）
* 线性渐变 （gradient）
* 旋转 （transform）
* 增加了旋转,缩放,定位,倾斜,动画,多背景

# 单行、多行文本溢出隐藏
单行文本溢出
``` Java
overflow: hidden;            // 溢出隐藏
text-overflow: ellipsis;      // 溢出用省略号显示
white-space: nowrap;         // 规定段落中的文本不进行换行
```
多行文本溢出
``` Java
overflow: hidden;            // 溢出隐藏
text-overflow: ellipsis;     // 溢出用省略号显示
display:-webkit-box;         // 作为弹性伸缩盒子模型显示。
-webkit-box-orient:vertical; // 设置伸缩盒子的子元素排列方式：从上到下垂直排列
-webkit-line-clamp:3;        // 显示的行数
```
[高频前端面试题汇总之CSS篇](https://juejin.cn/post/6905539198107942919#heading-3)

# CSS中可继承与不可继承属性有哪些
## 无继承性的属性
* display：规定元素应该生成的框的类型
* 文本属性：
    * vertical-align：垂直文本对齐
    * text-decoration：规定添加到文本的装饰
    * text-shadow：文本阴影效果
    * white-space：空白符的处理
    * unicode-bidi：设置文本的方向
* 盒子模型的属性：width、height、margin、border、padding
* 背景属性：background、background-color、background-image、background-repeat、background-position、background-attachment
* 定位属性：float、clear、position、top、right、bottom、left、min-width、min-height、max-width、max-height、overflow、clip、z-index
* 生成内容属性：content、counter-reset、counter-increment
* 轮廓样式属性：outline-style、outline-width、outline-color、outline
* 页面样式属性：size、page-break-before、page-break-after
* 声音样式属性：pause-before、pause-after、pause、cue-before、cue-after、cue、play-during

## 有继承性的属性
* 字体系列属性
    * font-family：字体系列
    * font-weight：字体的粗细
    * font-size：字体的大小
    * font-style：字体的风格
* 文本系列属性
    * text-indent：文本缩进
    * text-align：文本水平对齐
    * line-height：行高
    * word-spacing：单词之间的间距
    * letter-spacing：中文或者字母之间的间距
    * text-transform：控制文本大小写（就是uppercase、lowercase、capitalize这三个）
    * color：文本颜色
* 元素可见性：visibility：控制元素显示隐藏
* 列表布局属性：list-style：列表风格，包括list-style-type、list-style-image等
* 光标属性：cursor：光标显示为何种形态

# link和@import的区别
两者都是外部引用CSS的方式：
* link是XHTML标签,无兼容问题
* @import属于CSS范畴，只能加载CSS，是在CSS2.1提出的，低版本的浏览器不支持。
* link引用CSS时，在页面载入时同时加载；@import需要页面网页完全载入以后加载。
* link支持使用Javascript控制DOM去改变样式；而@import不支持。

# 伪元素和伪类的区别和作用？
伪元素：在内容元素的前后插入额外的元素或样式，但是这些元素实际上并不在文档中生成。它们只在外部显示可见，但不会在文档的源代码中找到它们，因此，称为“伪”元素。【::before、::after、::first-line、::first-letter】
伪类：将特殊的效果添加到特定选择器上。它是已有元素上添加类别的，不会产生新的元素。【:hover、:first-child

# 常见的图片格式及使用场景
* BMP是无损的：BMP格式的图片通常是较大的文件
* GIF是无损的：适用于对色彩要求不高同时需要文件体积较小的场景。
* JPEG是有损的：适合用来存储照片，与GIF相比，JPEG不适合用来存储企业Logo、线框类的图。
* PNG-8是无损的：是非常好的GIF格式替代者
* PNG-24是无损的：图片还是要比JPEG、GIF、PNG-8大得多，比BMP小得多
* SVG是无损的矢量图：适合用来绘制Logo、Icon等

# 对 CSSSprites 的理解
将一个页面涉及到的所有图片都包含到一张大图中去，然后利用CSS的 background-image，background-repeat，background-position属性的组合进行背景定位。
* 优点：
    * 减少网页的http请求，提高了页面的性能。
* 缺点：
    * 要把多张图片有序的、合理的合并成一张图片，还要留好足够的空间，防止板块内出现不必要的背景。在宽屏及高分辨率下的自适应页面，如果背景不够宽，很容易出现背景断裂；
    * 要借助photoshop
    * 维护的时候比较麻烦，页面背景有少许改动时，就要改这张合并的图片

# CSS预处理器/后处理器是什么？为什么要使用它们？
预处理器， 如：less，sass，stylus，用来预编译sass或者less，增加了css代码的复用性。层级，mixin， 变量，循环， 函数等对编写以及开发UI组件都极为方便。
后处理器， 如： postCss，通常是在完成的样式表中根据css规范处理css，让其更加有效。目前最常做的是给css属性添加浏览器私有前缀，实现跨浏览器兼容性的问题。
使用原因：
* 结构清晰， 便于扩展
* 可以很方便的屏蔽浏览器私有语法的差异
* 可以轻松实现多重继承
* 完美的兼容了CSS代码，可以应用到老项目中

# 对line-height 的理解及其赋值方式
line-height的概念：
* line-height 指一行文本的高度，包含了字间距，实际上是下一行基线到上一行基线距离；
* 如果一个标签没有定义 height 属性，那么其最终表现的高度由 line-height 决定；
* 把 line-height 值设置为 height 一样大小的值可以实现单行文字的垂直居中；
line-height 的赋值方式：
带单位：px 是固定值，而 em 会参考父元素 font-size 值计算自身的行高
纯数字：会把比例传递给后代。例如，父级行高为 1.5，子元素字体为 18px，则子元素行高为 1.5 * 18 = 27px
百分比：将计算后的值传递给后代

# Sass、Less 是什么？为什么要使用他们？
他们都是 CSS 预处理器，是 CSS 上的一种抽象层。
为什么要使用它们？
* 结构清晰，便于扩展，减少无意义的机械劳动。
* 可以轻松实现多重继承。


# 页面布局
## 两栏布局的实现
两栏布局指的是左边一栏宽度固定，右边一栏宽度自适应。
* 利用浮动，将左边元素宽度设置为200px，并且设置向左浮动。将右边元素的margin-left设置为200px，宽度设置为auto（默认为auto，撑满整个父元素）。
* 利用浮动，左侧元素设置固定大小，并左浮动，右侧元素设置overflow: hidden; 这样右边就触发了BFC，BFC的区域不会与浮动元素发生重叠，所以两侧就不会发生重叠。
* 利用flex布局，将左边元素设置为固定宽度200px，将右边的元素设置为flex:1。
* 利用绝对定位，将父级元素设置为相对定位。左边元素设置为absolute定位，并且宽度设置为200px。将右边元素的margin-left的值设置为200px。
* 利用绝对定位，将父级元素设置为相对定位。左边元素宽度设置为200px，右边元素设置为绝对定位，左边定位为200px，其余方向定位为0。

## 三栏布局的实现
三栏布局一般指的是页面中一共有三栏，左右两栏宽度固定，中间自适应的布局。
* 利用绝对定位，左右两栏设置为绝对定位，中间设置对应方向大小的margin的值。
* 利用flex布局，左右两栏设置固定大小，中间一栏设置为flex:1。
* 利用浮动，左右两栏设置固定大小，并设置对应方向的浮动。中间一栏设置左右两个方向的margin值，【注意这种方式，中间一栏必须放到最后】
* 圣杯布局，利用浮动和负边距来实现。父级元素设置左右的 padding，三列均设置向左浮动，中间一列放在最前面，宽度设置为父级元素的宽度，因此后面两列都被挤到了下一行，通过设置 margin 负值将其移动到上一行，再利用相对定位，定位到两边。
``` Java
.outer {
  height: 100px;
  padding-left: 100px;
  padding-right: 200px;
}

.left {
  position: relative;
  left: -100px;

  float: left;
  margin-left: -100%;

  width: 100px;
  height: 100px;
  background: tomato;
}

.right {
  position: relative;
  left: 200px;

  float: right;
  margin-left: -200px;

  width: 200px;
  height: 100px;
  background: gold;
}

.center {
  float: left;

  width: 100%;
  height: 100px;
  background: lightgreen;
}
```
* 双飞翼布局，双飞翼布局相对于圣杯布局来说，左右位置的保留是通过中间列的 margin 值来实现的，而不是通过父元素的 padding 来实现的。本质上来说，也是通过浮动和外边距负值来实现的。
``` Java
.outer {
  height: 100px;
}
.left {
  float: left;
  margin-left: -100%;
  width: 100px;
  height: 100px;
  background: tomato;
}
.right {
  float: left;
  margin-left: -200px;
  width: 200px;
  height: 100px;
  background: gold;
}
.wrapper {
  float: left;
  width: 100%;
  height: 100px;
  background: lightgreen;
}
.center {
  margin-left: 100px;
  margin-right: 200px;
  height: 100px;
}
```
## 水平垂直居中的实现
* 利用绝对定位，先将元素的左上角通过top:50%和left:50%定位到页面的中心，然后再通过translate来调整元素的中心点到页面的中心。该方法需要考虑浏览器兼容问题。
* 利用绝对定位，设置四个方向的值都为0，并将margin设置为auto，由于宽高固定，因此对应方向实现平分，可以实现水平和垂直方向上的居中。该方法适用于盒子有宽高的情况.
* 利用绝对定位，先将元素的左上角通过top:50%和left:50%定位到页面的中心，然后再通过margin负值来调整元素的中心点到页面的中心。该方法适用于盒子宽高已知的情况.
* 使用flex布局，通过align-items:center和justify-content:center设置容器的垂直和水平方向上为居中对齐，然后它的子元素也可以实现垂直和水平的居中。该方法要考虑兼容的问题，该方法在移动端用的较多.

## 对Flex布局的理解及其使用场景
"弹性布局"，任何一个容器都可以指定为Flex布局。【注意，设为Flex布局以后，子元素的float、clear和vertical-align属性将失效。】
简单来说：
flex布局是CSS3新增的一种布局方式，可以通过将一个元素的display属性值设置为flex从而使它成为一个flex容器，它的所有子元素都会成为它的项目。一个容器默认有两条轴：一个是水平的主轴，一个是与主轴垂直的交叉轴。可以使用flex-direction来指定主轴的方向。可以使用justify-content来指定元素在主轴上的排列方式，使用align-items来指定元素在交叉轴上的排列方式。还可以使用flex-wrap来规定当一行排列不下时的换行方式。对于容器中的项目，可以使用order属性来指定项目的排列顺序，还可以使用flex-grow来指定当排列空间有剩余的时候，项目的放大比例，还可以使用flex-shrink来指定当排列空间不足时，项目的缩小比例。

[高频前端面试题汇总之CSS篇](https://juejin.cn/post/6905539198107942919#heading-3)
## 常见的CSS布局单位
常用的布局单位包括像素（px），百分比（%），em，rem，vw/vh。
* 像素（px）是页面布局的基础，一个像素表示终端（电脑、手机、平板等）屏幕所能显示的最小的区域，像素分为两种类型：CSS像素和物理像素：
    * CSS像素：为web开发者提供，在CSS中使用的一个抽象单位；
    * 物理像素：只与设备的硬件密度有关，任何设备的物理像素都是固定的。
* 百分比（%），当浏览器的宽度或者高度发生变化时，通过百分比单位可以使得浏览器中的组件的宽和高随着浏览器的变化而变化，从而实现响应式的效果。一般认为子元素的百分比相对于直接父元素。
* em和rem相对于px更具灵活性，它们都是相对长度单位，它们之间的区别：em相对于父元素，rem相对于根元素。
    * em： 文本相对长度单位。相对于当前对象内文本的字体尺寸。如果当前行内文本的字体尺寸未被人为设置，则相对于浏览器的默认字体尺寸(默认16px)。(相对父元素的字体大小倍数)。
    * rem： rem是CSS3新增的一个相对单位，相对于根元素（html元素）的font-size的倍数。作用：利用rem可以实现简单的响应式布局，可以利用html元素中字体的大小与屏幕间的比值来设置font-size的值，以此实现当屏幕分辨率变化时让元素也随之变化。
* vw/vh是与视图窗口有关的单位，vw表示相对于视图窗口的宽度，vh表示相对于视图窗口高度，除了vw和vh外，还有vmin和vmax两个相关的单位。
    * vw：相对于视窗的宽度，视窗宽度是100vw；
    * vh：相对于视窗的高度，视窗高度是100vh；
    * vmin：vw和vh中的较小值；
    * vmax：vw和vh中的较大值；

## px、em、rem的区别及使用场景
三者的区别：
* px是固定的像素，一旦设置了就无法因为适应页面大小而改变。
* em和rem相对于px更具有灵活性，他们是相对长度单位，其长度不是固定的，更适用于响应式布局。
* em是相对于其父元素来设置字体大小，这样就会存在一个问题，进行任何元素设置，都有可能需要知道他父元素的大小。而rem是相对于根元素，这样就意味着，只需要在根元素确定一个参考值。
使用场景：
* 对于只需要适配少部分移动设备，且分辨率对页面影响不大的，使用px即可 。
* 对于需要适配各种移动设备，使用rem，例如需要适配iPhone和iPad等分辨率差别比较挺大的设备。


# 定位与浮动
## 为什么需要清除浮动？清除浮动的方式
浮动的定义： 非IE浏览器下，容器不设高度且子元素浮动时，容器高度不能被内容撑开。 此时，内容会溢出到容器外面而影响布局。这种现象被称为浮动（溢出）。
浮动的工作原理：
* 浮动元素脱离文档流，不占据空间（引起“高度塌陷”现象）
* 浮动元素碰到包含它的边框或者其他浮动元素的边框停留
浮动元素引起的问题？
* 父元素的高度无法被撑开，影响与父元素同级的元素
* 与浮动元素同级的非浮动元素会跟随其后
* 若浮动的元素不是第一个元素，则该元素之前的元素也要浮动，否则会影响页面的显示结构
清除浮动的方式如下：
* 给父级div定义height属性
* 最后一个浮动元素之后添加一个空的div标签，并添加clear:both样式
* 包含浮动元素的父级标签添加overflow:hidden或者overflow:auto
* 使用 :after 伪元素。由于IE6-7不支持 :after，使用 zoom:1 触发 hasLayout**
``` Java
.clearfix:after{
    content: "\200B";
    display: table; 
    height: 0;
    clear: both;
}
.clearfix{
    *zoom: 1;
}
```

## 对BFC的理解，如何创建BFC
BFC是一个独立的布局环境，BFC中的元素布局不受外部影响。
创建BFC的条件：
* 根元素：body；
* 元素设置浮动：float 除 none 以外的值
* 元素设置绝对定位：position (absolute、fixed)；
* display 值为：inline-block、table-cell、table-caption、flex等；
* overflow 值为：hidden、auto、scroll；
BFC的特点：
* 垂直方向上，自上而下排列，和文档流的排列方式一致。
* 在BFC中上下相邻的两个容器的margin会重叠
* 计算BFC的高度时，需要计算浮动元素的高度
* BFC区域不会与浮动的容器发生重叠
* BFC是独立的容器，容器内部元素不会影响外部元素
* 每个元素的左margin值和容器的左border相接触
BFC的作用：
* 解决margin的重叠问题：由于BFC是一个独立的区域，内部的元素和外部的元素互不影响，将两个元素变为两个BFC，就解决了margin重叠的问题。
* 解决高度塌陷的问题：在对子元素设置浮动后，父元素会发生高度塌陷，也就是父元素的高度变为0。解决这个问题，只需要把父元素变成一个BFC。常用的办法是给父元素设置overflow:hidden。
* 创建自适应两栏布局：可以用来创建自适应两栏布局：左边的宽度固定，右边的宽度自适应。
``` Java
.left{
     width: 100px;
     height: 200px;
     background: red;
     float: left;
}
.right{
     height: 300px;
     background: blue;
     overflow: hidden;
}
<div class="left"></div>
<div class="right"></div>

```
左侧设置float:left，右侧设置overflow: hidden。这样右边就触发了BFC，BFC的区域不会与浮动元素发生重叠，所以两侧就不会发生重叠，实现了自适应两栏布局。

## position的属性有哪些，区别是什么
position有以下属性值：
* absolute：绝对定位的元素，相对于static定位以外的一个父元素进行定位。
* relative：生成相对定位的元素，相对于其原来的位置进行定位。
* fixed：生成绝对定位的元素，指定元素相对于屏幕视⼝（viewport）的位置来指定元素位置。
* static：默认值，没有定位，元素出现在正常的文档流中，会忽略 top, bottom, left, right 或者 z-index 声明，块级元素从上往下纵向排布，⾏级元素从左向右排列。
* inherit：规定从父元素继承position属性的值

## 什么是margin重叠问题？如何解决？
两个块级元素的上外边距和下外边距可能会合并（折叠）为一个外边距，其大小会取其中外边距值大的那个，这种行为就是外边距折叠。需要注意的是，浮动的元素和绝对定位这种脱离文档流的元素的外边距不会折叠。重叠只会出现在垂直方向。
计算原则： 折叠合并后外边距的计算原则如下：
* 如果两者都是正数，那么就去最大者
* 如果是一正一负，就会正值减去负值的绝对值
* 两个都是负值时，用0减去两个中绝对值大的那个
解决办法： 对于折叠的情况，主要有两种：兄弟之间重叠和父子之间重叠
* 兄弟之间重叠
    * 底部元素变为行内盒子：display: inline-block
    * 底部元素设置浮动：float
    * 底部元素的position的值为absolute/fixed
* 父子之间重叠
    * 父元素加入：overflow: hidden
    * 父元素添加透明边框：border:1px solid transparent
    * 子元素变为行内盒子：display: inline-block
    * 子元素加入浮动属性或定位

## display、float、position的关系
"position:absolute"和"position:fixed"优先级最高，有它存在的时候，浮动不起作用，'display'的值也需要调整；
其次，元素的'float'特性的值不是"none"的时候或者它是根元素的时候，调整'display'的值；
最后，非根元素，并且非浮动元素，并且非绝对定位的元素，'display'特性值同设置值。

# 场景应用
## 实现一个三角形
``` css
div {
    width: 0;
    height: 0;
    border: 100px solid;
    border-color: orange blue red green; /* 上右下左 */ 
}
```
``` css
div {    
    width: 0;    
    height: 0;    
    border-top: 50px solid red;    
    border-right: 50px solid transparent;    
    border-left: 50px solid transparent;
}
```
## 如何解决 1px 问题？
1px 问题指的是：在一些 Retina屏幕 的机型上，移动端页面的 1px 会变得很粗，呈现出不止 1px 的效果。原因很简单——CSS 中的 1px 并不能和移动设备上的 1px 划等号。它们之间的比例关系有一个专门的属性来描述：
window.devicePixelRatio = 设备的物理像素 / CSS像素。
* 思路一：直接写 0.5px
    可以先在 JS 中拿到 window.devicePixelRatio 的值，然后把这个值通过 JSX 或者模板语法给到 CSS 的 data 里，达到这样的效果（这里用 JSX 语法做示范）：
    <div id="container" data-device={{window.devicePixelRatio}}></div>
    然后就可以在 CSS 中用属性选择器来命中 devicePixelRatio 为某一值的情况，比如说这里尝试命中 devicePixelRatio 为2的情况：

    ``` css
    #container[data-device="2"] {
    border:0.5px solid #333
    }
    ```
    直接把 1px 改成 1/devicePixelRatio 后的值，这是目前为止最简单的一种方法。这种方法的缺陷在于兼容性不行，IOS 系统需要8及以上的版本，安卓系统则直接不兼容。
* 伪元素先放大后缩小
    这个方法的可行性会更高，兼容性也更好。唯一的缺点是代码会变多。
    思路是先放大、后缩小：在目标元素的后面追加一个 ::after 伪元素，让这个元素布局为 absolute 之后、整个伸展开铺在目标元素上，然后把它的宽和高都设置为目标元素的两倍，border值设为 1px。
    接着借助 CSS 动画特效中的放缩能力，把整个伪元素缩小为原来的 50%。此时，伪元素的宽高刚好可以和原有的目标元素对齐，而 border 也缩小为了 1px 的二分之一，间接地实现了 0.5px 的效果。
    ``` Javascript
        #container[data-device="2"] {
            position: relative;
        }
        #container[data-device="2"]::after{
            position:absolute;
            top: 0;
            left: 0;
            width: 200%;
            height: 200%;
            content:"";
            transform: scale(0.5);
            transform-origin: left top;
            box-sizing: border-box;
            border: 1px solid #333;
            }
        }
    ```
* 思路三：viewport 缩放来解决
    这个思路就是对 meta 标签里几个关键属性下手：
    ``` Javascript
    <meta name="viewport" content="initial-scale=0.5, maximum-scale=0.5, minimum-scale=0.5, user-scalable=no">
    ```
    这里针对像素比为2的页面，把整个页面缩放为了原来的1/2大小。这样，本来占用2个物理像素的 1px 样式，现在占用的就是标准的一个物理像素。根据像素比的不同，这个缩放比例可以被计算为不同的值，用 js 代码实现如下：

    ``` Javascript
    const scale = 1 / window.devicePixelRatio;
    // 这里 metaEl 指的是 meta 标签对应的 Dom
    metaEl.setAttribute('content', `width=device-width,user-scalable=no,initial-scale=${scale},maximum-scale=${scale},minimum-scale=${scale}`);
    ```
    这样解决了，但这样做的副作用也很大，整个页面被缩放了。这时 1px 已经被处理成物理像素大小，这样的大小在手机上显示边框很合适。但是，一些原本不需要被缩小的内容，比如文字、图片等，也被无差别缩小掉了。

## 实现一个扇形
用CSS实现扇形的思路和三角形基本一致，就是多了一个圆角的样式，实现一个90°的扇形：
``` css
div{
    border: 100px solid transparent;
    width: 0;
    heigt: 0;
    border-radius: 100px;
    border-top-color: red;
}
```
## 实现一个宽高自适应的正方形
* 利用vw来实现：
``` css
.square {
  width: 10%;
  height: 10vw;
  background: tomato;
}
```
* 利用元素的margin/padding百分比是相对父元素width的性质来实现：
``` css
.square {
  width: 20%;
  height: 0;
  padding-top: 20%;
  background: orange;
}
```
* 利用子元素的margin-top的值来实现：
``` css
.square {
  width: 30%;
  overflow: hidden;
  background: yellow;
}
.square::after {
  content: '';
  display: block;
  margin-top: 100%;
}
```
## 画一条0.5px的线
* 采用transform: scale()的方式，该方法用来定义元素的2D 缩放转换：transform: scale(0.5,0.5);
* 采用meta viewport的方式
``` Java
<meta name="viewport" content="width=device-width, initial-scale=0.5, minimum-scale=0.5, maximum-scale=0.5"/>
```
这样就能缩放到原来的0.5倍，如果是1px那么就会变成0.5px。viewport只针对于移动端，只在移动端上才能看到效果

# 设置小于12px的字体
在谷歌下css设置字体大小为12px及以下时，显示都是一样大小，都是默认12px。
解决办法：
* 使用Webkit的内核的-webkit-text-size-adjust的私有CSS属性来解决，只要加了-webkit-text-size-adjust:none;字体大小就不受限制了。但是chrome更新到27版本之后就不可以用了。所以高版本chrome谷歌浏览器已经不再支持-webkit-text-size-adjust样式，所以要使用时候慎用。
* 使用css3的transform缩放属性-webkit-transform:scale(0.5); 注意-webkit-transform:scale(0.75);收缩的是整个元素的大小，这时候，如果是内联元素，必须要将内联元素转换成块元素，可以使用display：block/inline-block/...；
* 使用图片：如果是内容固定不变情况下，使用将小于12px文字内容切出做图片，这样不影响兼容也不影响美观。

