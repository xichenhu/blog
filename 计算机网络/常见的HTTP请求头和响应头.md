# 常见的HTTP请求头和响应头
## HTTP Request Header 常见的请求头：
* Accept:浏览器能够处理的内容类型
* Accept-Charset:浏览器能够显示的字符集
* Accept-Encoding：浏览器能够处理的压缩编码
* Accept-Language：浏览器当前设置的语言
* Connection：浏览器与服务器之间连接的类型
* Cookie：当前页面设置的任何Cookie
* Host：发出请求的页面所在的域
* Referer：发出请求的页面的URL
* User-Agent：浏览器的用户代理字符串

## HTTP Responses Header 常见的响应头：
* Date：表示消息发送的时间，时间的描述格式由rfc822定义
* server:服务器名称
* Connection：浏览器与服务器之间连接的类型
* Cache-Control：控制HTTP缓存
* content-type:表示后面的文档属于什么MIME类型
    * 常见的 Content-Type 属性值有以下四种:
        1. application/x-www-form-urlencoded：浏览器的原生 form 表单，如果不设置 enctype 属性，那么最终就会以 application/x-www-form-urlencoded 方式提交数据。该种方式提交的数据放在 body 里面，数据按照 key1=val1&key2=val2 的方式进行编码，key 和 val 都进行了 URL转码。
        2. multipart/form-data：该种方式也是一个常见的 POST 提交方式，通常表单上传文件时使用该种方式。
        3. application/json：服务器消息主体是序列化后的 JSON 字符串。
        4. text/xml：该种方式主要用来提交 XML 格式的数据。

