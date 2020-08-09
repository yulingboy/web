##  http 模块

http 模块是 Node.js 官方提供的、用来创建 web 服务器的模块。通过 http 模块提供的 http.createServer() 方法，就 能方便的把一台普通的电脑，变成一台 Web 服务器，从而对外提供 Web 资源服务。 

如果要希望使用 http 模块创建 Web 服务器，则需要先导入它：

```js
const http = require('http')
```

### 创建最基本的 web 服务器

#### 步骤1 - 导入 http 模块

如果希望在自己的电脑上创建一个 web 服务器，从而对外提供 web 服务，则需要导入 http 模块：

```js
const http = require('http')
```

#### 步骤2 - 创建 web 服务器实例

调用 http.createServer() 方法，即可快速创建一个 web 服务器实例：

```js
const server = http.createServer()
```

#### 步骤3 - 为服务器实例绑定 request 事件

为服务器实例绑定 request 事件，即可监听客户端发送过来的网络请求：

```js
server.on('request', function (req, res) {
  console.log('Someone visit our web server.')
})
```

#### 步骤4 - 启动服务器

调用服务器实例的 .listen() 方法，即可启动当前的 web 服务器实例：

```js
server.listen(8080, function () {  
  console.log('server running at http://127.0.0.1:8080')
})
```

### req 请求对象 

只要服务器接收到了客户端的请求，就会调用通过 server.on() 为服务器绑定的 request 事件处理函数。 如果想在事件处理函数中，访问与客户端相关的数据或属性，可以使用如下的方式：

```js
server.on('request', (req, res) => {
  // req是请求对象 它包含了与客户端相关的数据和属性，例如
  // req.url 是客户端请求的 URL 地址
  // req.method 是客户端请求的 method 类型
  const str = `Your request url is ${req.url}, and request method is ${req.method}`
  console.log(str)
})
```

### res 响应对象

在服务器的 request 事件处理函数中，如果想访问与服务器相关的数据或属性，可以使用如下的方式：

```js
server.on('request', (req, res) => {
  // res是相应对象 它包含了与服务器相关的数据和属性，例如	
  // 要发到客户端的字符串
  const str = `Your request url is ${url}, and request method is ${method}`
  res.send(str)
})
```

### 解决中文乱码问题

当调用 res.end() 方法，向客户端发送中文内容的时候，会出现乱码问题，此时，需要手动设置内容的编码格式：

```js
const http = require('http')
const server = http.createServer()

server.on('request', (req, res) => {
  // 定义一个字符串，包含中文的内容
  const str = `您请求的 URL 地址是 ${req.url}，请求的 method 类型为 ${req.method}`
  // 调用 res.setHeader() 方法，设置 Content-Type 响应头，解决中文乱码的问题
  res.setHeader('Content-Type', 'text/html; charset=utf-8')
  // res.end() 将内容响应给客户端
  res.end(str)
})

server.listen(80, () => {
  console.log('server running at http://127.0.0.1')
})

```

