在前端开发中，处理异常是确保应用稳定性和用户体验的关键。以下是 Web 前端处理异常的常见方式：

---

## **1. 全局异常捕获**
### **1.1 `window.onerror`**
- **作用**：捕获全局的 JavaScript 运行时错误。
- **特点**：
  - 可以捕获未被 `try/catch` 捕获的错误。
  - 无法捕获资源加载错误（如图片、脚本加载失败）。
- **示例**：
  ```javascript
  window.onerror = function(message, source, lineno, colno, error) {
    console.error('全局错误:', message, source, lineno, colno, error);
    return true; // 阻止错误继续向上冒泡
  };
  ```

### **1.2 `window.addEventListener('error')`**
- **作用**：捕获全局错误，包括资源加载错误。
- **特点**：
  - 可以捕获资源加载错误。
  - 需要设置 `useCapture` 为 `true`。
- **示例**：
  ```javascript
  window.addEventListener('error', (event) => {
    console.error('捕获到错误:', event.error || event.message);
  }, true);
  ```

### **1.3 `unhandledrejection`**
- **作用**：捕获未处理的 Promise 拒绝（`reject`）。
- **示例**：
  ```javascript
  window.addEventListener('unhandledrejection', (event) => {
    console.error('未处理的 Promise 拒绝:', event.reason);
  });
  ```

---

## **2. 局部异常捕获**
### **2.1 `try/catch`**
- **作用**：捕获同步代码中的异常。
- **特点**：
  - 无法捕获异步代码中的异常（如 `setTimeout`、`Promise`）。
- **示例**：
  ```javascript
  try {
    const data = JSON.parse('无效的 JSON');
  } catch (error) {
    console.error('解析 JSON 失败:', error);
  }
  ```

### **2.2 `try/catch` 与 `async/await`**
- **作用**：捕获异步代码中的异常。
- **示例**：
  ```javascript
  async function fetchData() {
    try {
      const response = await fetch('https://api.example.com/data');
      const data = await response.json();
    } catch (error) {
      console.error('请求失败:', error);
    }
  }
  ```

### **2.3 `.catch()`**
- **作用**：捕获 Promise 的拒绝（`reject`）。
- **示例**：
  ```javascript
  fetch('https://api.example.com/data')
    .then((response) => response.json())
    .catch((error) => {
      console.error('请求失败:', error);
    });
  ```

---

## **3. 资源加载异常捕获**
### **3.1 图片加载失败**
- **示例**：
  ```html
  <img src="image.png" onerror="handleImageError(event)">
  <script>
    function handleImageError(event) {
      console.error('图片加载失败:', event.target.src);
      event.target.src = 'fallback.png'; // 加载备用图片
    }
  </script>
  ```

### **3.2 脚本加载失败**
- **示例**：
  ```html
  <script src="script.js" onerror="handleScriptError(event)"></script>
  <script>
    function handleScriptError(event) {
      console.error('脚本加载失败:', event.target.src);
    }
  </script>
  ```

---

## **4. 框架中的异常处理**
### **4.1 React 错误边界（Error Boundaries）**
- **作用**：捕获组件树中的 JavaScript 错误，并显示降级 UI。
- **示例**：
  ```javascript
  class ErrorBoundary extends React.Component {
    constructor(props) {
      super(props);
      this.state = { hasError: false };
    }

    static getDerivedStateFromError(error) {
      return { hasError: true };
    }

    componentDidCatch(error, errorInfo) {
      console.error('组件错误:', error, errorInfo);
    }

    render() {
      if (this.state.hasError) {
        return <h1>出错了，请稍后重试。</h1>;
      }
      return this.props.children;
    }
  }

  // 使用
  <ErrorBoundary>
    <MyComponent />
  </ErrorBoundary>
  ```

### **4.2 Vue 错误处理**
- **全局错误处理器**：
  ```javascript
  Vue.config.errorHandler = (err, vm, info) => {
    console.error('Vue 错误:', err, info);
  };
  ```
- **生命周期钩子**：
  ```javascript
  export default {
    errorCaptured(err, vm, info) {
      console.error('组件错误:', err, info);
      return false; // 阻止错误继续向上传播
    }
  };
  ```

---

## **5. 日志记录与监控**
### **5.1 日志记录**
- 将错误信息记录到控制台或服务器。
- **示例**：
  ```javascript
  function logError(error) {
    console.error('错误:', error);
    fetch('/log-error', {
      method: 'POST',
      body: JSON.stringify({ error: error.message }),
    });
  }
  ```

### **5.2 错误监控工具**
- 使用第三方工具监控前端错误：
  - **Sentry**：实时错误跟踪。
  - **LogRocket**：记录用户会话和错误。
  - **Bugsnag**：错误监控和报告。

---

## **6. 用户体验优化**
### **6.1 显示友好的错误提示**
- 在捕获错误后，向用户显示友好的提示信息。
- **示例**：
  ```javascript
  try {
    // 业务逻辑
  } catch (error) {
    alert('出错了，请稍后重试。');
  }
  ```

### **6.2 重试机制**
- 对于网络请求等可重试的操作，提供重试按钮或自动重试。
- **示例**：
  ```javascript
  function fetchWithRetry(url, retries = 3) {
    return fetch(url)
      .catch((error) => {
        if (retries > 0) {
          return fetchWithRetry(url, retries - 1);
        }
        throw error;
      });
  }
  ```

---

## **总结**
- **全局捕获**：使用 `window.onerror`、`unhandledrejection` 等捕获全局错误。
- **局部捕获**：使用 `try/catch`、`.catch()` 捕获同步和异步错误。
- **资源加载**：通过 `onerror` 事件捕获资源加载错误。
- **框架支持**：利用 React 错误边界、Vue 错误处理器等框架特性。
- **日志与监控**：记录错误并集成第三方监控工具。
- **用户体验**：显示友好提示并提供重试机制。

通过综合运用这些方法，可以有效提升前端应用的健壮性和用户体验。