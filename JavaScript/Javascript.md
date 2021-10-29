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

## map和Object的区别
[map和Object的区别](https://juejin.cn/post/6940945178899251230#heading-37)

## JavaScript脚本延迟加载的方式有哪些？
延迟加载就是等页面加载完成之后再加载 JavaScript 文件。 js 延迟加载有助于提高页面加载速度。
* defer 属性：这个属性会让脚本的加载与文档的解析同步解析,设置多个按顺序执行
* async 属性：这个属性会使脚本异步加载，不会阻塞页面的解析过程，多个 async 属性执行顺序不可预测
* 动态创建 DOM 方式：可以对文档的加载事件进行监听，当文档加载完成后再动态的创建 script 标签来引入 js 脚本。
* 使用 setTimeout 延迟方法：设置一个定时器来延迟加载js脚本文件
* 让 JS 最后加载：将 js 脚本放在文档的底部，来使 js 脚本尽可能的在最后来加载执行。

## JavaScript 类数组对象的定义？
一个拥有 length 属性和若干索引属性的对象就可以被称为类数组对象。【但是不能调用数组的方法】

## 为什么函数的 arguments 参数是类数组而不是数组？如何遍历类数组?
arguments是一个对象，它的属性是从 0 开始依次递增的数字，有length等属性，但是它却没有数组常见的方法属性，如forEach, reduce等，所以叫它们类数组。
要遍历类数组，有三个方法：
* 将数组的方法应用到类数组上，这时候就可以使用call和apply方法，如：
``` Java
function foo(){ 
  Array.prototype.forEach.call(arguments, a => console.log(a))
}
```
* 使用Array.from方法将类数组转化成数组：‌
``` Java
function foo(){ 
  const arrArgs = Array.from(arguments) 
  arrArgs.forEach(a => console.log(a))
}
```
* 使用展开运算符将类数组转化成数组
``` Java
function foo(){ 
    const arrArgs = [...arguments] 
    arrArgs.forEach(a => console.log(a)) 
}
```

## ES6模块与CommonJS模块有什么异同？
* 区别
    * CommonJS是对模块的浅拷⻉
    * ES6 Module是对模块的引⽤，即ES6 Module只存只读，不能改变其值，也就是指针指向不能变，类似const；

* 共同点
    * CommonJS和ES6 Module都可以对引⼊的对象进⾏赋值，即对对象内部属性的值进⾏改变。

## 如何判断一个对象是否属于某个类？
* 第一种方式，使用 instanceof 运算符来判断构造函数的 prototype 属性是否出现在对象的原型链中的任何位置。
* 第二种方式，通过对象的 constructor 属性来判断，对象的 constructor 属性指向该对象的构造函数，但是这种方式不是很安全，因为 constructor 属性可以被改写。
* 第三种方式，如果需要判断的是某个内置的引用类型的话，可以使用 Object.prototype.toString() 方法来打印对象的[[Class]] 属性来进行判断。

## for...in和for...of的区别
for…of 是ES6新增的遍历方式，允许遍历一个含有iterator接口的数据结构（数组、对象等）并且返回各项的值，和ES3中的for…in的区别如下
* for…of 遍历获取的是对象的键值，for…in 获取的是对象的键名；
* 对于数组的遍历，for…in 会返回数组中所有可枚举的属性(包括原型链上可枚举的属性，性能非常差不推荐使用)，for…of 只返回数组的下标对应的属性值（不会遍历原型链）；
for...in 循环主要是为了遍历对象而生，不适用于遍历数组；for...of 循环可以用来遍历数组、类数组对象，字符串、Set、Map 以及 Generator 对象。

## 数组的遍历方法有哪些
forEach()
map()
filter()
for...of..：for...of遍历具有Iterator迭代器的对象的属性，返回的是数组的元素、对象的属性值，不能遍历普通的obj对象，将异步循环变成同步循环
every() 
some()
find()
findIndex()
reduce()
reduceRight()

## forEach和map方法有什么区别
* forEach()方法会针对每一个元素执行提供的函数，对数据的操作会改变原数组，该方法没有返回值；
* map()方法不会改变原数组的值，返回一个新数组，新数组中的值为原数组调用函数处理之后的值；

# ES6
## let、const、var的区别
* 块级作用域：块作用域由 { }包括，let和const具有块级作用域，var不存在块级作用域。
    * 块级作用域解决了ES5中的两个问题：
        * 内层变量可能覆盖外层变量
        * 用来计数的循环变量泄露为全局变量
* 变量提升：var存在变量提升，let和const不存在变量提升，即在变量只能在声明之后使用，否在会报错。
* 给全局添加属性：浏览器的全局对象是window，Node的全局对象是global。var声明的变量为全局变量，并且会将该变量添加为全局对象的属性，但是let和const不会。
* 重复声明：var声明变量时，可以重复声明变量，后声明的同名变量会覆盖之前声明的遍历。const和let不允许重复声明变量。
* 暂时性死区：在使用let、const命令声明变量之前，该变量都是不可用的。这在语法上，称为暂时性死区。使用var声明的变量不存在暂时性死区。
* 初始值设置：在变量声明时，var 和 let 可以不用设置初始值。而const声明变量必须设置初始值。
* 指针指向：let和const都是ES6新增的用于创建变量的语法。 let创建的变量是可以更改指针指向（可以重新赋值）。但const声明的变量是不允许改变指针的指向。

## 箭头函数与普通函数的区别
* 箭头函数比普通函数更加简洁
    * 如果没有参数，就直接写一个空括号即可
    * 如果只有一个参数，可以省去参数的括号
    * 如果有多个参数，用逗号分割
    * 如果函数体的返回值只有一句，可以省略大括号
    * 如果函数体不需要返回值，且只有一句话，可以给这个语句前面加一个void关键字。最常见的就是调用一个函数：
        ``` Java
            let fn = () => void doesNotReturn();
        ```
* 箭头函数没有自己的this    
    箭头函数不会创建自己的this， 所以它没有自己的this，它只会在自己作用域的上一层继承this。所以箭头函数中this的指向在它在定义时已经确定了，之后不会改变。
* 箭头函数继承来的this指向永远不会改变
* call()、apply()、bind()等方法不能改变箭头函数中this的指向
* 箭头函数不能作为构造函数使用
    构造函数在new的步骤在上面已经说过了，实际上第二步就是将函数中的this指向该对象。 但是由于箭头函数时没有自己的this的，且this指向外层的执行环境，且不能改变指向，所以不能当做构造函数使用。
* 箭头函数没有自己的arguments
    箭头函数没有自己的arguments对象。在箭头函数中访问arguments实际上获得的是它外层函数的arguments值。
* 箭头函数没有prototype
* 箭头函数不能用作Generator函数，不能使用yeild关键字    

## const对象的属性可以修改吗
const保证的并不是变量的值不能改动，而是变量指向的那个内存地址不能改动。对于基本类型的数据（数值、字符串、布尔值），其值就保存在变量指向的那个内存地址，因此等同于常量。
但对于引用类型的数据（主要是对象和数组）来说，变量指向数据的内存地址，保存的只是一个指针，const只能保证这个指针是固定不变的，至于它指向的数据结构是不是可变的，就完全不能控制了。

## 如果new一个箭头函数的会怎么样
箭头函数是ES6中的提出来的，它没有prototype，也没有自己的this指向，更不可以使用arguments参数，所以不能New一个箭头函数。

## 箭头函数的this指向哪⾥？
箭头函数不同于传统JavaScript中的函数，箭头函数并没有属于⾃⼰的this，它所谓的this是捕获其所在上下⽂的 this 值，作为⾃⼰的 this 值，并且由于没有属于⾃⼰的this，所以是不会被new调⽤的，这个所谓的this也不会被改变。
``` Java
// ES6 
const obj = { 
  getArrow() { 
    return () => { 
      console.log(this === obj); 
    }; 
  } 
}

// ES5，由 Babel 转译
var obj = { 
   getArrow: function getArrow() { 
     var _this = this; 
     return function () { 
        console.log(_this === obj); 
     }; 
   } 
};
```

## 对 rest 参数的理解
扩展运算符被用在函数形参上时，它还可以把一个分离的参数序列整合成一个数组。
``` Java
function mutiple(...args) {
  console.log(args)
}
mutiple(1, 2, 3, 4) // [1, 2, 3, 4]
```
这就是 … rest运算符的又一层威力了，它可以把函数的多个入参收敛进一个数组里。这一点经常用于获取函数的多余参数，或者像上面这样处理函数参数个数不确定的情况。

## ES6中模板语法与字符串处理
* 允许用${}的方式嵌入变量
* 在模板字符串中，空格、缩进、换行都会被保留 【可以在模板字符串里无障碍地直接写 html 代码】
* 模板字符串完全支持“运算”式的表达式，可以在${}里完成一些计算
除了模板语法外， ES6中还新增了一系列的字符串方法用于提升开发效率：
* 存在性判定
    * includes、 startsWith【判断字符串是否以某个/某串字符开头】、startsWith【判断字符串是否以某个/某串字符结尾】 它们都会返回一个布尔值来告诉你是否存在。
* 自动重复
    * 可以使用 repeat 方法来使同一个字符串输出多次（被连续复制多次）

# 原型
##  对原型、原型链的理解
什么是构造函数：
	任何函数只要通过new操作符来调用，那么他就可以作为构造函数。
什么是实例：
	只要是被new关键字调用构造函数所生成的对象就叫对象实例。
什么是原型：
	所有生成的函数都会有一个prototype原型的属性，这个原型属性指向的是原型对象
原型对象的作用：
	共享对象的所有属性和方法，该原型有个属性为constructor（构造函数），这个属性指向的是它的构造函数。
__proto__属性
	指向原型对象（也可以理解为父对象）
prototype 属性
	1、是函数独有的
	2、从一个函数指向一个对象
	3、用来共享属性和方法
	4、任何函数创建的时候都会默认同时创建该函数的prototype对象。
constructor属性
	1、是对象才拥有的属性
	2、它是从一个对象指向一个函数（该对象的构造函数）
	3、单从constructor这个属性来讲，只有prototype对象才有。

函数创建的对象.__proto__ === 该函数.prototype
该函数.prototype.constructor===该函数本身

原型链：当访问一个对象的属性时，如果这个对象内部不存在这个属性，那么它就会去它的原型对象里找这个属性，这个原型对象又会有自己的原型，于是就这样一直找下去，也就是原型链的概念。原型链的尽头一般来说都是 Object.prototype 所以这就是新建的对象为什么能够使用 toString() 等方法的原因。

总结一下
	我们需要牢记两点：
	1、__proto__和constructor属性是对象所独有的；② prototype属性是函数所独有的，因为函数也是一种对象，所以函数也拥有__proto__和constructor属性。
	2、__proto__属性的作用就是当访问一个对象的属性时，如果该对象内部不存在这个属性，那么就会去它的__proto__属性所指向的那个对象（父对象）里找，一直找，直到__proto__属性的终点null，然后返回undefined，通过__proto__属性将对象连接起来的这条链路即我们所谓的原型链。
	3、prototype属性的作用就是让该函数所实例化的对象们都可以找到公用的属性和方法，即f1.__proto__ === Foo.prototype。
	4、constructor属性的含义就是指向该对象的构造函数，所有函数（此时看成对象了）最终的构造函数都指向Function。

``` Java
f.__proto__ === Fn.prototype
f.__proto__ === f.constructor.prototype
Fn.prototype.constructor === Fn
f.constructor === Fn
Fn.prototype.__proto__ === Object.prototype
```
## 原型链指向
``` Java
p.__proto__  // Person.prototype
Person.prototype.__proto__  // Object.prototype
p.__proto__.__proto__ //Object.prototype
p.__proto__.constructor.prototype.__proto__ // Object.prototype
Person.prototype.constructor.prototype.__proto__ // Object.prototype
p1.__proto__.constructor // Person
Person.prototype.constructor  // Person
```
## 原型修改、重写

