# Promise
一个 Promise 必然处于以下几种状态之一：
1. 待定（pending）: 初始状态，既没有被兑现，也没有被拒绝。 
2. 已兑现（fulfilled）: 意味着操作成功完成。 
3. 已拒绝（rejected）: 意味着操作失败。

Promise 永远返回的都是一个新 Promise 当 Promise 被 reject 且没有 reject 处理器的时候，会触发 unhandledrejection 事件；这可能发生在 window 下

## Promise是什么
Promise 是一个对象，从它可以获取异步操作的消息。

## 有什么特点
（1）对象的状态不受外界影响。
（2）一旦状态改变，就不会再变，任何时候都可以得到这个结果。

## 解决了什么问题
1. 有了Promise对象，就可以将异步操作以同步操作的流程表达出来，避免了层层嵌套的回调函数。
2. Promise对象提供统一的接口，使得控制异步操作更加容易。

## 存在什么缺点
1. 无法取消Promise，一旦新建它就会立即执行，无法中途取消。
2. 如果不设置回调函数，Promise内部抛出的错误，不会反应到外部。
3. 当处于pending状态时，无法得知目前进展到哪一个阶段（刚刚开始还是即将完成）。



JavaScript 的 **Promise** 是处理异步操作的核心机制，它解决了传统回调函数导致的“回调地狱”问题，提供了更优雅、可读性更高的异步代码管理方式。以下是 Promise 的全面介绍：

---

### **1. Promise 的定义**
Promise 是一个表示异步操作最终完成或失败的对象。它有三种状态：
1. **Pending（进行中）**：初始状态，操作尚未完成。
2. **Fulfilled（已成功）**：操作成功完成。
3. **Rejected（已失败）**：操作失败。

**状态流转**：  
`Pending` → `Fulfilled`（通过 `resolve` 触发）  
`Pending` → `Rejected`（通过 `reject` 触发）  
**一旦状态变更，不可逆**。

---

### **2. 创建 Promise**
通过 `new Promise()` 构造函数创建 Promise 实例，接收一个执行器函数（`executor`），该函数包含 `resolve` 和 `reject` 两个参数。

```javascript
const promise = new Promise((resolve, reject) => {
  // 异步操作（如网络请求、定时器等）
  if (/* 成功条件 */) {
    resolve(value); // 将状态变为 Fulfilled，传递结果
  } else {
    reject(error);  // 将状态变为 Rejected，传递错误
  }
});
```

---

### **3. 使用 Promise**
通过 `.then()`、`.catch()` 和 `.finally()` 方法处理 Promise 的结果或错误。

#### **3.1 `.then()`**
- 接收两个回调函数（`onFulfilled` 和 `onRejected`），分别处理成功和失败。
- 返回一个新的 Promise，支持链式调用。

```javascript
promise
  .then(
    (value) => { /* 处理成功结果 */ },
    (error) => { /* 处理失败结果 */ }
  );
```

#### **3.2 `.catch()`**
- 专门处理 Promise 链中的错误。
- 等同于 `.then(null, errorCallback)`。

```javascript
promise
  .then((value) => { /* ... */ })
  .catch((error) => { /* 统一处理错误 */ });
```

#### **3.3 `.finally()`**
- 无论成功或失败都会执行的回调。
- 适合执行清理操作（如关闭加载状态）。

```javascript
promise
  .then((value) => { /* ... */ })
  .catch((error) => { /* ... */ })
  .finally(() => { /* 最终清理 */ });
```

---

### **4. Promise 链式调用**
Promise 的链式调用可以串联多个异步操作，避免回调嵌套。

```javascript
fetchData()
  .then((data) => processData(data))
  .then((result) => saveData(result))
  .catch((error) => console.error(error));
```

---

### **5. Promise 的静态方法**
#### **5.1 `Promise.resolve()`**
- 返回一个已成功的 Promise。

```javascript
Promise.resolve(42).then((value) => console.log(value)); // 输出 42
```

#### **5.2 `Promise.reject()`**
- 返回一个已失败的 Promise。

```javascript
Promise.reject(new Error('失败')).catch((error) => console.error(error));
```

#### **5.3 `Promise.all()`**
- 并行执行多个 Promise，全部成功时返回结果数组，任意失败则立即失败。

```javascript
Promise.all([promise1, promise2, promise3])
  .then((results) => console.log(results))
  .catch((error) => console.error(error));
```

#### **5.4 `Promise.race()`**
- 并行执行多个 Promise，返回第一个完成的 Promise 的结果（无论成功或失败）。

```javascript
Promise.race([promise1, promise2])
  .then((result) => console.log(result))
  .catch((error) => console.error(error));
```

#### **5.5 `Promise.allSettled()`**
- 并行执行多个 Promise，等待所有 Promise 完成（无论成功或失败），返回结果数组。

```javascript
Promise.allSettled([promise1, promise2])
  .then((results) => results.forEach((result) => console.log(result.status)));
```

#### **5.6 `Promise.any()`**
- 并行执行多个 Promise，返回第一个成功的 Promise 的结果，全部失败则抛出错误。

```javascript
Promise.any([promise1, promise2])
  .then((result) => console.log(result))
  .catch((errors) => console.error(errors));
```

---

### **6. Promise 的错误处理**
- **统一捕获错误**：通过 `.catch()` 捕获链中任意位置的错误。
- **局部捕获错误**：在 `.then()` 中定义第二个参数处理错误。
- **穿透性**：如果未定义错误处理函数，错误会一直向下传递，直到被捕获。

```javascript
fetchData()
  .then((data) => {
    // 处理成功
  })
  .then((result) => {
    throw new Error('链中抛出错误');
  })
  .catch((error) => {
    // 捕获所有错误
  });
```

---

### **7. async/await 与 Promise**
`async/await` 是 Promise 的语法糖，使异步代码更接近同步代码的写法。

#### **7.1 `async` 函数**
- 函数前加 `async` 关键字，函数内可以使用 `await`。
- 始终返回一个 Promise。

```javascript
async function fetchData() {
  return '数据';
}
```

#### **7.2 `await` 表达式**
- 等待 Promise 完成，返回结果。
- 只能在 `async` 函数中使用。

```javascript
async function process() {
  try {
    const data = await fetchData(); // 等待 Promise 完成
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}
```

---

### **8. 实际应用场景**
#### **场景 1：替代回调函数**
```javascript
// 传统回调
function fetchData(callback) {
  setTimeout(() => callback('数据'), 1000);
}

// 使用 Promise
function fetchData() {
  return new Promise((resolve) => {
    setTimeout(() => resolve('数据'), 1000);
  });
}
```

#### **场景 2：多个异步请求并行**
```javascript
const [user, posts] = await Promise.all([
  fetch('/api/user'),
  fetch('/api/posts')
]);
```

#### **场景 3：超时控制**
```javascript
function fetchWithTimeout(url, timeout) {
  return Promise.race([
    fetch(url),
    new Promise((_, reject) => 
      setTimeout(() => reject(new Error('超时')), timeout)
    )
  ]);
}
```

---

### **9. Promise 的局限性**
1. **无法取消**：一旦创建 Promise，无法中途取消。
2. **错误处理集中**：需通过 `.catch()` 统一处理，可能掩盖局部错误。
3. **性能开销**：链式调用可能增加内存消耗。

---

### **10. 最佳实践**
1. **优先使用 `async/await`**：提升代码可读性。
2. **始终处理错误**：避免未捕获的 Promise 错误。
3. **合理使用静态方法**：如 `Promise.all` 处理并行任务。
4. **避免嵌套 Promise**：通过链式调用保持代码扁平。

---

### **总结**
Promise 是 JavaScript 异步编程的基石，结合 `async/await` 可以编写出清晰、高效的异步代码。理解其核心概念、方法链和错误处理机制，是掌握现代前端开发的关键。