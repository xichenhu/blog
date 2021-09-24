# Set
存储任何类型的唯一值

## 常用方法
* 增 Set.prototype.add(value)
* 删 Set.prototype.delete(value)    [移除Set中与这个值相等的元素，返回Set.prototype.has(value)在这个操作前会返回的值（即如果该元素存在，返回true，否则返回false）。Set.prototype.has(value)在此后会返回false。]
* 清空 Set.prototype.clear()
* 获取迭代器对象 Set.prototype.entries()
* 遍历 Set.prototype.forEach(callbackFn[, thisArg])
* 查询值是否在set中 Set.prototype.has(value)
* 返回Set对象中的值的个数 Set.prototype.size
* keys Set.prototype.keys()
* values Set.prototype.values()

## WeakSet
垃圾回收机制不考虑 WeakSet 对该对象的引用，也就是说，如果其他对象都不再引用该对象，那么垃圾回收机制会自动回收该对象所占用的内存，不考虑该对象还存在于 WeakSet 之中。
    * 不可遍历
    * 没有size

# 参考资料
[MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Set)