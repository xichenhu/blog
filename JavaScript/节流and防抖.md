# 节流and防抖
## 节流
``` Java
function throttle (func, wait) {
	let previrous = 0;
	return () => {
		var now = Date.now();
		var args = arguments;
		if (now - previrous > wait) {
			func.apply(this, args);
			previrous = now
		}
	} 
}

function throttle (func, wait) {
	var timeout;
	return function() {
		var args = arguments;
		var context = this;
		if (!timeout) {
			timeout = setTimeout(function() {
				timeout = null;
				func.apply(context, args);
			}, wait)
		}
	}
}
```
## 防抖
``` Java
function debounce(fn, delay) {
  var timer = null
  return function () {
    var context = this
    var args = arguments
    clearTimeout(timer)
    timer = setTimeout(function () {
      fn.apply(context, args)
    }, delay)
  }
}

// 防抖（输入框输入时调用API）
function debounce(fn, delay = 200) {
	let timer;
	return function () {
		timer && clearTimeout(timer);
		timer = setTimeout(fn.bind(this), delay, ...arguments)
	}

}

const handlerChange = debounce(function() {alert("触发更新")});
document.querySelector('input').addEventListener('input', handlerChange);
```

# 参考资料
[彻底弄懂节流和防抖](https://www.lagou.com/lgeduarticle/120749.html)
[好文档](https://www.jianshu.com/p/566c66aafa22)