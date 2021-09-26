# Map
任何值(对象或者原始值) 都可以作为一个键或一个值。能够记住键的原始插入顺序。

## 作用
在频繁增删键值对的场景下表现更好。

# WeakMap
* 垃圾回收机制不考虑 WeakMap 对该对象的引用
* 不可遍历
* 没有size

## Map.prototype.clear() 
移除Map对象的所有键/值对 。
## Map.prototype.delete(key) 
如果 Map 对象中存在该元素，则移除它并返回 true；否则如果该元素不存在则返回 false。随后调用 Map.prototype.has(key) 将返回 false 。
## Map.prototype.entries() 
返回一个新的 Iterator 对象，它按插入顺序包含了Map对象中每个元素的 [key, value] 数组。
## Map.prototype.forEach(callbackFn[, thisArg])
按插入顺序，为 Map对象里的每一键值对调用一次callbackFn函数。如果为forEach提供了thisArg，它将在每次回调中作为this值。
## Map.prototype.get(key)
返回键对应的值，如果不存在，则返回undefined。
## Map.prototype.has(key)
返回一个布尔值，表示Map实例是否包含键对应的值。
## Map.prototype.keys()
返回一个新的 Iterator对象， 它按插入顺序包含了Map对象中每个元素的键 。
## Map.prototype.set(key, value)
设置Map对象中键的值。返回该Map对象。
## Map.prototype.values()
返回一个新的Iterator对象，它按插入顺序包含了Map对象中每个元素的值 。

# 参考资料
[Map](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Map)