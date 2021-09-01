# BFC
具有 BFC 特性的元素可以看作是隔离了的独立容器，容器里面的元素不会在布局上影响到外面的元素，并且 BFC 具有普通容器所没有的一些特性。
>扩展
> <div>1、BFC “块级格式化上下文”，就是页面上的一个隔离的渲染区域，容器里面的子元素不会在布局上影响到外面的元素，反之也是如此。
</div>

> <div>2、IFC “内联格式化上下文”，IFC的line box（线框）高度由其包含行内元素中最高的实际高度计算而来（不受到竖直方向的padding/margin影响)
    作用：
        水平居中：当一个块要在环境中水平居中时，设置其为inline-block则会在外层产生IFC，通过text-align则可以使其水平居中。
        垂直居中：创建一个IFC，用其中一个元素撑开父元素的高度，然后设置其vertical-align:middle，其他行内元素则可以在此父元素下垂直居中。
</div>

> <div>3、FFC：“自适应格式化上下文”，display值为flex或者inline-flex的元素将会生成自适应容器（flex container）。
</div>

## 特性
1. 同一个 BFC 下外边距会发生折叠
2. BFC 可以包含浮动的元素（清除浮动）
3. BFC 可以阻止元素被浮动元素覆盖

## 如何触发 BFC
* body 根元素
* 浮动元素：float 除 none 以外的值
* 绝对定位元素：position (absolute、fixed)
* display 为 inline-block、table-cells、flex
* overflow 除了 visible 以外的值 (hidden、auto、scroll)

## 应用场景
* 避免外边距的重叠
* 清除浮动
* 阻止元素被浮动元素覆盖（两栏布局）

# 资料
* [10 分钟理解 BFC 原理]("https://zhuanlan.zhihu.com/p/25321647")
* [什么是 BFC（Block Formatting Context）]("https://segmentfault.com/a/1190000016226880")