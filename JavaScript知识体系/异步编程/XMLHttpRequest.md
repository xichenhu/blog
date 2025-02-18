`XMLHttpRequest`（简称 XHR）是浏览器提供的 JavaScript API，用于在客户端和服务器之间发送 HTTP 请求。它是实现 AJAX（Asynchronous JavaScript and XML）技术的核心工具。以下是 `XMLHttpRequest` 的详细使用说明：

---

### **1. 创建 XMLHttpRequest 对象**
首先，创建一个 `XMLHttpRequest` 对象：
```javascript
const xhr = new XMLHttpRequest();
```

---

### **2. 初始化请求**
使用 `open()` 方法初始化请求：
```javascript
xhr.open(method, url, async);
```
- **method**：HTTP 请求方法（如 `"GET"`、`"POST"` 等）。
- **url**：请求的目标 URL。
- **async**：是否异步（默认为 `true`，表示异步请求）。

示例：
```javascript
xhr.open("GET", "https://api.example.com/data", true);
```

---

### **3. 设置请求头（可选）**
使用 `setRequestHeader()` 方法设置请求头：
```javascript
xhr.setRequestHeader(header, value);
```
示例：
```javascript
xhr.setRequestHeader("Content-Type", "application/json");
```

---

### **4. 发送请求**
使用 `send()` 方法发送请求：
- 对于 `GET` 请求，`send()` 可以不传参数或传 `null`。
- 对于 `POST` 请求，`send()` 可以传递请求体数据。

示例：
```javascript
xhr.send(); // GET 请求
xhr.send(JSON.stringify({ key: "value" })); // POST 请求
```

---

### **5. 监听请求状态**
通过 `onreadystatechange` 事件监听请求状态的变化：
```javascript
xhr.onreadystatechange = function () {
    if (xhr.readyState === XMLHttpRequest.DONE) {
        if (xhr.status === 200) {
            console.log("请求成功:", xhr.responseText);
        } else {
            console.log("请求失败:", xhr.status);
        }
    }
};
```

#### **readyState 的可能值**：
- `0`：未初始化（`open()` 未调用）。
- `1`：已打开（`open()` 已调用）。
- `2`：已发送（`send()` 已调用，响应头已接收）。
- `3`：接收中（响应体正在接收）。
- `4`：完成（请求完成）。

---

### **6. 处理响应**
通过 `responseText` 或 `response` 属性获取响应数据：
- `responseText`：返回字符串形式的响应数据。
- `response`：根据 `responseType` 返回相应类型的数据（如 JSON、Blob 等）。

示例：
```javascript
xhr.responseType = "json"; // 设置响应类型为 JSON
xhr.onload = function () {
    if (xhr.status === 200) {
        console.log("响应数据:", xhr.response);
    }
};
```

---

### **7. 错误处理**
通过 `onerror` 事件处理网络错误：
```javascript
xhr.onerror = function () {
    console.log("请求出错");
};
```

---

### **8. 超时设置**
通过 `timeout` 属性设置请求超时时间（单位：毫秒）：
```javascript
xhr.timeout = 5000; // 5 秒超时
xhr.ontimeout = function () {
    console.log("请求超时");
};
```

---

### **9. 完整示例**
以下是一个完整的 `GET` 请求示例：
```javascript
const xhr = new XMLHttpRequest();
xhr.open("GET", "https://api.example.com/data", true);
xhr.onreadystatechange = function () {
    if (xhr.readyState === XMLHttpRequest.DONE) {
        if (xhr.status === 200) {
            console.log("响应数据:", xhr.responseText);
        } else {
            console.log("请求失败:", xhr.status);
        }
    }
};
xhr.send();
```

---

### **10. 注意事项**
1. **跨域问题**：如果请求的目标 URL 与当前页面域名不同，需要服务器支持 CORS（跨域资源共享）。
2. **现代替代方案**：推荐使用 `fetch` API，它更现代、更强大。
3. **兼容性**：`XMLHttpRequest` 在所有现代浏览器中都支持。

---
