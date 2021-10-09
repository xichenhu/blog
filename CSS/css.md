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


