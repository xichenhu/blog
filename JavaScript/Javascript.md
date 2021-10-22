# Javascript
# 数据类型
## JavaScript有哪些数据类型，它们的区别？
JavaScript共有八种数据类型，分别是 Undefined、Null、Boolean、Number、String、Object、Symbol、BigInt。
* Symbol： 代表创建后独一无二且不可变的数据类型，它主要是为了解决可能出现的全局变量冲突的问题。
* BigInt： 是一种数字类型的数据，它可以表示任意精度格式的整数，使用 BigInt 可以安全地存储和操作大整数，即使这个数已经超出了 Number 能够表示的安全整数范围。
分类
* 栈：原始数据类型（Undefined、Null、Boolean、Number、String）
* 堆：引用数据类型（对象、数组和函数）
区别
* 原始数据类型直接存储在栈（stack）中的简单数据段，占据空间小、大小固定，属于被频繁使用数据，所以放入栈中存储；
* 引用数据类型存储在堆（heap）中的对象，占据空间大、大小不固定。如果存储在栈中，将会影响程序运行的性能；引用数据类型在栈中存储了指针，该指针指向堆中该实体的起始地址。当解释器寻找引用值时，会首先检索其在栈中的地址，取得地址后从堆中获得实体。

## 数据类型检测的方式有哪些
* typeof：其中数组、对象、null都会被判断为object，其他判断都正确。
* instanceof：只能正确判断引用数据类型，而不能判断基本数据类型。【其内部运行机制是判断在其原型链中能否找到该类型的原型。】
* constructor：有两个作用，一是判断数据的类型，二是对象实例通过constrcutor 对象访问它的构造函数。
* Object.prototype.toString.call()： 使用 Object 对象的原型方法 toString 来判断数据类型。

## 判断数组的方式有哪些
* 通过Object.prototype.toString.call()做判断：【Object.prototype.toString.call(obj).slice(8,-1) === 'Array';】
* 通过原型链做判断：【obj.__proto__ === Array.prototype;】
* 通过ES6的Array.isArray()做判断：【Array.isArrray(obj);】
* 通过instanceof做判断：【obj instanceof Array】
* 通过Array.prototype.isPrototypeOf：Array.prototype.isPrototypeOf(obj)

## null和undefined区别
undefined 代表的含义是未定义，null 代表的含义是空对象。
一般变量声明了但还没有定义的时候会返回 undefined，null主要用于赋值给一些可能会返回对象的变量，作为初始化。
【当对这两种类型使用 typeof 进行判断时，Null 类型化会返回 “object”，这是一个历史遗留的问题。当使用双等号对两种类型的值进行比较时会返回 true，使用三个等号时会返回 false。】

## intanceof 操作符的实现原理及实现
instanceof 运算符用于判断构造函数的 prototype 属性是否出现在对象的原型链中的任何位置。
``` Java
function myInstanceof(left, right) {
  // 获取对象的原型
  let proto = Object.getPrototypeOf(left)
  // 获取构造函数的 prototype 对象
  let prototype = right.prototype; 
 
  // 判断构造函数的 prototype 对象是否在对象的原型链上
  while (true) {
    if (!proto) return false;
    if (proto === prototype) return true;
    // 如果没有找到，就继续从其原型上找，Object.getPrototypeOf方法用来获取指定对象的原型
    proto = Object.getPrototypeOf(proto);
  }
}
```

## 为什么0.1+0.2 ! == 0.3，如何让其相等  
计算机是通过二进制的方式存储数据的，所以计算机计算0.1+0.2的时候，实际上是计算的两个数的二进制的和，再转化为十进制数。
``` Java 
let n1 = 0.1, n2 = 0.2
console.log(n1 + n2)  // 0.30000000000000004
(n1 + n2).toFixed(2) // 注意，toFixed为四舍五入
```

## == 操作符的强制类型转换规则？
判断流程：
1. 首先会判断两者类型是否**相同，**相同的话就比较两者的大小；
2. 类型不相同的话，就会进行类型转换；
3. 会先判断是否在对比 null 和 undefined，是的话就会返回 true
4. 判断两者类型是否为 string 和 number，是的话就会将字符串转换为 number
5. 判断其中一方是否为 boolean，是的话就会把 boolean 转为 number 再进行判断
6. 判断其中一方是否为 object 且另一方为 string、number 或者 symbol，是的话就会把 object 转为原始类型再进行判断
'1' == { name: 'js' }       '1' == '[object Object]'
![== 操作符的强制类型转换规则](./images/==操作符的强制类型转换规则.awebp)

## Object.is() 与比较操作符 “===”、“==” 的区别？
* 使用双等号（==）进行相等判断时，如果两边的类型不一致，则会进行强制类型转化后再进行比较。
* 使用三等号（===）进行相等判断时，如果两边的类型不一致时，不会做强制类型准换，直接返回 false。
* 使用 Object.is 来进行相等判断时，一般情况下和三等号的判断相同，它处理了一些特殊的情况，比如 -0 和 +0 不再相等，两个 NaN 是相等的。

## typeof null 的结果是什么，为什么？
typeof null 的结果是Object。

## isNaN 和 Number.isNaN 函数的区别？
函数 isNaN 接收参数后，会尝试将这个参数转换为数值，任何不能被转换为数值的的值都会返回 true，因此非数字值传入也会返回 true ，会影响 NaN 的判断。
函数 Number.isNaN 会首先判断传入参数是否为数字，如果是数字再继续判断是否为 NaN ，不会进行数据类型的转换，这种方法对于 NaN 的判断更为准确。

## 其他值到字符串的转换规则？
* Null 和 Undefined 类型 ，null 转换为 "null"，undefined 转换为 "undefined"
* Boolean 类型，true 转换为 "true"，false 转换为 "false"。
* Number 类型的值直接转换，不过那些极小和极大的数字会使用指数形式。
* Symbol 类型的值直接转换，但是只允许显式强制类型转换，使用隐式强制类型转换会产生错误。
* 对普通对象来说，除非自行定义 toString() 方法，否则会调用 toString()（Object.prototype.toString()）来返回内部属性 [[Class]] 的值，如"[object Object]"。如果对象有自己的 toString() 方法，字符串化时就会调用该方法并使用其返回值。

## 其他值到数字值的转换规则？
* Undefined 类型的值转换为 NaN。
* Null 类型的值转换为 0。
* Boolean 类型的值，true 转换为 1，false 转换为 0。
* String 类型的值转换如同使用 Number() 函数进行转换，如果包含非数字值则转换为 NaN，空字符串为 0。
* Symbol 类型的值不能转换为数字，会报错。
* 对象（包括数组）会首先被转换为相应的基本类型值，如果返回的是非数字的基本类型值，则再遵循以上规则将其强制转换为数字。
PS：
为了将值转换为相应的基本类型值，抽象操作 ToPrimitive 会首先（通过内部操作 DefaultValue）检查该值是否有valueOf()方法。
如果有并且返回基本类型值，就使用该值进行强制类型转换。如果没有就使用 toString() 的返回值（如果存在）来进行强制类型转换。
如果 valueOf() 和 toString() 均不返回基本类型值，会产生 TypeError 错误。

## 其他值到布尔类型的值的转换规则？
以下这些是假值： • undefined • null • false • +0、-0 和 NaN • ""
假值的布尔强制类型转换结果为 false。从逻辑上说，假值列表以外的都应该是真值。

## JavaScript 中如何进行隐式类型转换？
首先要介绍ToPrimitive方法，这是 JavaScript 中每个值隐含的自带的方法，用来将值 （无论是基本类型值还是对象）转换为基本类型值。如果值为基本类型，则直接返回值本身；如果值为对象，其看起来大概是这样：
```Java
/**
* @obj 需要转换的对象
* @type 期望的结果类型
*/
ToPrimitive(obj,type)
```
type的值为number或者string。
* 当type为number时规则如下：
    * 调用obj的valueOf方法，如果为原始值，则返回，否则下一步；
    * 调用obj的toString方法，后续同上；
    * 抛出TypeError 异常。
* 当type为string时规则如下：
    * 调用obj的toString方法，如果为原始值，则返回，否则下一步；
    * 调用obj的valueOf方法，后续同上；
    * 抛出TypeError 异常。
可以看出两者的主要区别在于调用toString和valueOf的先后顺序。默认情况下：
* 如果对象为 Date 对象，则type默认为string；
* 其他情况下，type默认为number。

# JavaScript基础
## new操作符的实现原理
new操作符的执行过程：
1. 首先创建了一个新的空对象
2. 设置原型，将对象的原型设置为函数的 prototype 对象。
3. 让函数的 this 指向这个对象，执行构造函数的代码（为这个新对象添加属性）
4. 判断函数的返回值类型，如果是值类型，返回创建的对象。如果是引用类型，就返回这个引用类型的对象。
``` Java
function objectFactory() {
  let newObject = null;
  let constructor = Array.prototype.shift.call(arguments);
  let result = null;
  // 判断参数是否是一个函数
  if (typeof constructor !== "function") {
    console.error("type error");
    return;
  }
  // 新建一个空对象，对象的原型为构造函数的 prototype 对象
  newObject = Object.create(constructor.prototype);
  // 将 this 指向新建对象，并执行函数
  result = constructor.apply(newObject, arguments);
  // 判断返回对象
  let flag = result && (typeof result === "object" || typeof result === "function");
  // 判断返回结果
  return flag ? result : newObject;
}
// 使用方法
objectFactory(构造函数, 初始化参数);

```

## 数组有哪些原生方法？
* 数组和字符串的转换方法：toString()、toLocalString()、join() 其中 join() 方法可以指定转换为字符串时的分隔符
* 数组尾部操作的方法 pop() 和 push()，push 方法可以传入多个参数。
* 数组首部操作的方法 shift() 和 unshift() 重排序的方法 reverse() 和 sort()，sort() 方法可以传入一个函数来进行比较，传入前后两个值，如果返回值为正数，则交换两个参数的位置。
* 数组连接的方法 concat() ，返回的是拼接好的数组，不影响原数组。
* 数组截取办法 slice()，用于截取数组中的一部分返回，不影响原数组。
* 数组插入方法 splice()，影响原数组。查找特定项的索引的方法indexOf() 和 lastIndexOf() 迭代方法 every()、some()、filter()、map() 和 forEach() 方法
* 数组归并方法 reduce() 和 reduceRight() 方法

## 什么是 DOM 和 BOM？
* DOM 指的是文档对象模型，它指的是把文档当做一个对象，这个对象主要定义了处理网页内容的方法和接口。
* BOM 指的是浏览器对象模型，它指的是把浏览器当做一个对象来对待，这个对象主要定义了与浏览器进行交互的法和接口。BOM的核心是 window，而 window 对象具有双重角色，它既是通过 js 访问浏览器窗口的一个接口，又是一个 Global（全局）对象。这意味着在网页中定义的任何对象，变量和函数，都作为全局对象的一个属性或者方法存在。window 对象含有 location 对象、navigator 对象、screen 对象等子对象，并且 DOM 的最根本的对象 document 对象也是 BOM 的 window 对象的子对象。

## 对类数组对象的理解，如何转化为数组
一个拥有 length 属性和若干索引属性的对象就可以被称为类数组对象，类数组对象和数组类似，但是不能调用数组的方法。
常见的类数组对象有 arguments 和 DOM 方法的返回结果，函数参数也可以被看作是类数组对象，因为它含有 length属性值，代表可接收的参数个数。
常见的类数组转换为数组的方法有这样几种：
* 通过 call 调用数组的 slice 方法来实现转换：Array.prototype.slice.call(arrayLike);
* 通过 call 调用数组的 splice 方法来实现转换：Array.prototype.splice.call(arrayLike, 0);
* 通过 apply 调用数组的 concat 方法来实现转换：Array.prototype.concat.apply([], arrayLike);
* 通过 Array.from 方法来实现转换：Array.from(arrayLike);

## 对AJAX的理解，实现一个AJAX请求
指的是通过 JavaScript 的 异步通信，从服务器获取 XML 文档从中提取数据，再更新当前网页的对应部分，而不用刷新整个网页。
[对AJAX的理解，实现一个AJAX请求](https://juejin.cn/post/6940945178899251230#heading-63)


## JavaScript为什么要进行变量提升，它导致了什么问题？
无论在函数中何处位置声明的变量，好像都被提升到了函数的首部，可以在变量声明前访问到而不会报错。

