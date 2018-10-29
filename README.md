### 1. AJAX是一套API,核心提供的类型：XMLHttpRequest
* new安装浏览器（用户代理）xhr对象已创建,readyState = 0
* open打开浏览器输入网址 readyState = 1 
* 注册响应函数
* send发送，等待响应 readyState = 2
* 处理数据
### 2. test11 xhr.response === xhr.responseText //true,但是存在不同之处
* responseText获取的是字符串形式的响应体typeof this.responseText 返回string
* response获取到的结果会根据客户端自动设置的this.responseType的变化而变化
### 3. test13 line39 ajax封装
* 不应该在封装的函数中主观地处理结果
* 无法通过在内部包含函数中直接return给外部函数的调用返回结果
* 由于异步模式下此处代码最后执行，这里的代码最后执行，不可能返回在外部通过返回值的方式返回
* 应使用委托的方式（传递处理函数进去），拿到数据告诉它怎么做，而不是想办法传递出来接收
### 4. 同源（同协议同域名同端口）策略
* 不同源地址之间，默认不能发送AJAX请求
* 不同源地址之间相互请求，必须服务端跟客户端配合才行
* 跨域请求:请求一个不同源的地址
* link 、img可以发出请求，无法拿到响应结果
* iframe
* script 可以发送，无法拿到响应结果，借助于执行返回的js
### 5. josnp(json with padding)
* 只能使用GET请求
### 6. test20. CORS 
* 设置header('Access-Control-Allow-Origin: *');
### 7. readyState描述
* 0 UNSENT xhr对象被创建，尚未调用open()
* 1 OPENED 使用了open(),建立了连接
* 2 HEADER_RECEIVED 调用了send(),已经可以访问状态行和响应头
* 3 LOADING 响应体下载中，已经可以拿到部分数据(视网络情况而定)
* 4 DONE 响应体下载完成，可以使用responseText
### 8. 获取响应头
* getAllResponseHeaders()获取全部响应头
* getResponseHeader(name)获取指定的响应头
### 9. 请求参数
* get参数通过url地址中的?传递，无需设置响应体，可以传null或者不传
* post参数可以写在send里面，需设置Content-Type
### 10. open()的第三参数可以传布尔值，是否异步，默认为true
* 同步方式必须先注册事件再调用send()
### 11. 兼容ie5/6
* 创建对象使用let xhr = windows.XMLHttpRequest?new XMLHttpRequest():new ActiveXObject()
### 12. Jquery中的ajax
* url type dataType data(发送到服务端的数据) contentType请求体类型
* success(成功时调用)
* error请求失败是触发
* complete完成时触发
* $.post
* $.get()
* $.getJSON 返回类型为json格式的get请求
* $.ajaxStart请求开始
* $.ajaxEnd请求结束
* beforeSend请求发送之前，readyState=0"# ajax-learning" 
