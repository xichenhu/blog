# 如何实现一个 new
## new 的作用
1. 创建一个JavaScript空对象（即{}）；
2. 为步骤1新创建的对象添加属性__proto__，将该属性链接至构造函数的原型对象 ；
3. 将步骤1新创建的对象作为this的上下文 ；
4. 如果该函数没有返回对象，则返回this。

``` Java
function _new(fn, ...arg) {
    const obj = Object.create(fn.prototype); // 创建空对象，并将新对象的__proto__属性指向构造函数的prototype
    const ret = fn.apply(obj, arg); // 执行构造函数，改变构造函数的this指针，指向新创建的对象（新对象也就有了构造函数的所有属性）
    // 根据规范，返回 null 和 undefined 不处理，依然返回obj
    return ret instanceof Object ? ret : obj;
}

function mynew () {
     // 1、创建一个新对象
     const obj = Object.create({});    // 也可以写成 const obj = {}
     // 2、将this指向该对象
     let Fn = [].shift.call(arguments);    // 把构造函数分离出来【把类数组对象转为数组对象，删除并拿到arguments的第一项】
     let returnObj = Fn.apply(obj, arguments);     // 通过apply将this指向由Fn变为obj
     
     // 3、将新对象的原型指向构造函数的原型
     obj.__proto__ = Fn.prototype
     
    // 4、返回对象（如果构造函数有返回对象，那么就返回构造函数的对象，如果没有就返回新对象）
    return Object.prototype.toString.call(returnObj) == '[object Object]' ? returnObj : obj;
}
```

## 验证
``` Java 
function _new(fn, ...arg) {
    const obj = Object.create(fn.prototype); // 创建空对象，并将新对象的__proto__属性指向构造函数的prototype
    const ret = fn.apply(obj, arg); // 执行构造函数，改变构造函数的this指针，指向新创建的对象（新对象也就有了构造函数的所有属性）
    // 根据规范，返回 null 和 undefined 不处理，依然返回obj
    return ret instanceof Object ? ret : obj;
}

function People() {
    this.name = 'paopao'
    this.age = 3
}

const p = _new(People)
console.log(JSON.stringify(p))
// "{"name":"paopao","age":3}"
console.log(p.__proto__ === People.prototype)
// true
console.log(p.name)
// "paopao"
console.log(p.constructor === People)
// true
```

# 扩展
``` Java
[].slice.call( arguments )
//等效于
Array.prototype.slice.call( arguments )
```
* [Object.create](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/create)