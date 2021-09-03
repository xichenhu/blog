<u>注意：Markdown使用#、+、*等符号来标记， 符号后面必须跟上 至少1个 空格才有效！</u>
## 《markdown的常用方法》
## 标题————————————————————————
# 一级标题
## 二级标题
### 三级标题
……………
###### 六级标题

一级标题【在标题底下加上任意个=表示一级标题】
==========
二级标题【-表示二级标题】
二级标题
-----------

## 列表————————————————————————
- 无序列表
- Green

* 无序列表
* Green

+ 无序列表
+ Green

1. 有序列表
2. Red
3. Green

## 引用————————————————————————
> 这是一段引用
>
> 这是引用的代码块
> 
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
> 一级引用
>> 二级引用
>>> 三级引用

## 强调————————————————————————
**加粗文本** 或者 __加粗文本__

*斜体* 或者 _斜体_

~~删除文本~~

## 链接————————————————————————
这是行内式链接：[ConnorLin's Blog](http://connorlin.github.io)。

这是参考式链接：[ConnorLin's Blog][url]，其中url为链接标记，可置于文中任意位置。
[url]: http://connorlin.github.io/ "ConnorLin's Blog"

这是自动链接：直接使用`<>`括起来<http://connorlin.github.io>

[avatar]: https://github.com/Hxiaotong/blog/blob/master/git/img/5.png

## 代码————————————————————————
```
这里是代码
```
``` Java
//注意Java前面有空格【代码语法高亮在 ```后面加上空格和语言名称即可】
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);
}
```

## 表格————————————————————————
|标题          |标题         |标题          |
|:---         |:---:        |---:         |
|居左测试文本   |居中测试文本   |居右测试文本   |
|居左测试文本1  |居中测试文本2  |居右测试文本3  |
|居左测试文本11 |居中测试文本22 |居右测试文本33 |
|居左测试文本111|居中测试文本222|居右测试文本333|

## 分割线————————————————————————
***
---
___
* * *
<u>下划线文本</u>

## 换行————————————————————————
在行尾添加两个空格加回车表示换行：  
这是一行后面加两个空格  
换行
使用html标签`<br/>`<br/>换行

## 注脚————————————————————————
这是一个脚注的例子 [^1]
[^1]: xxxxxxxxxxxx



<p align="left">居左文本</p>
<p align="center">居中文本</p>
<p align="right">居右文本</p>

<font face="微软雅黑" color="red" size="6">字体及字体颜色和大小</font>
<font color="#0000ff">字体颜色</font>

## 插入图片——————————————————————
![avatar](./example.png)
<img src="./example.png" alt="图片替换文本" width="300" align="bottom" />