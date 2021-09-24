# Symbol
Symbol是 JavaScript 语言的第七种数据类型，前六种是：undefined、null、布尔值（Boolean）、字符串（String）、数值（Number）、对象（Object）。
> 注意，Symbol函数前不能使用new命令，否则会报错。这是因为生成的 Symbol 是一个原始类型的值，不是对象。也就是说，由于 Symbol 值不是对象，所以不能添加属性。基本上，它是一种类似于字符串的数据类型。

## 为什么出现Symbol
1. Symbol 值可以作为标识符，用于对象的属性名，可以保证不会与其他属性名产生冲突
2. Symbol 类型还可以用于定义一组常量，保证这组常量的值都是不相等的。



## Symbol.for()
创建或获取全局的Symbol

## Symbol.keyFor()
根据全局symbol获取注册的key

## 内置的symbols
Symbol.prototype.description：返回 Symbol 的描述
Symbol.iterator： 对象默认迭代器
Symbol.toPrimitive： 将对象转化为基本数据类型的方法
Symbol.toStringTag： 用于对象的默认描述的字符串值。被 Object.prototype.toString() 使用。

