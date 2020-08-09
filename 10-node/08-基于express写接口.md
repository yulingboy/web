## 使用 Express 写接口

### 基本使用

####  创建基本的服务器

```js
//导入express模块
const express = require('express')
//创建express的服务器实例
const app = express()

//调用app.listen方法，指定端口号并启动服务器
app.listen(80,function(){
    console,log('服务器启动成功')
})
```

#### 创建API路由模块

```js
//apiRouter.js [路由模块]
const express = require('express')
const apiRouter = express.Router()

moudle.exports = apiRouter

//app.js [导入并注册路由模块]
const apiRouter = require('./apiRouter.js')
app.use('/api',apiRouter)

```

#### 编写GET接口

```js
apiRouter.get('/get',(req,res)=>{
    //1.获取到客户端通过查询字符串，发送到服务器的数据
    const query = req.query
    //2.调用res.send()方法，把数据响应给客户端
    res.send({
        status:0,  //状态：0表示成功 1表示失败
        msg:'GET请求成功',  //状态描述
        data:query  //需要响应给客户端的具体数据
    })
})
```

#### 编写POST接口

```js
apiRouter.post('/post',(req,res)=>{
    //1.获取到客户端通过查请求体，发送到服务器的URL-encodeds数据
    const body = req.body
    //2.调用res.send()方法，把数据响应给客户端
    res.send({
        status:0,  //状态：0表示成功 1表示失败
        msg:'POST请求成功',  //状态描述
        data:body  //需要响应给客户端的具体数据
    })
})
```

### 跨域

刚才编写的 GET 和 POST接口，存在一个很严重的问题：不支持跨域请求。

 解决接口跨域问题的方案主要有两种： 

① CORS（主流的解决方案，推荐使用） 

② JSONP（有缺陷的解决方案：只支持 GET 请求）

#### 使用 cors 中间件解决跨域问题

cors 是 Express 的一个第三方中间件。通过安装和配置 cors 中间件，可以很方便地解决跨域问题。 

使用步骤分为如下 3 步：

① 运行 npm install cors 安装中间件 

② 使用 const cors = require('cors') 导入中间件 

③ 在路由之前调用 app.use(cors()) 配置中间件

**CORS** （Cross-Origin Resource Sharing，跨域资源共享）由一系列 HTTP 响应头组成，这些 HTTP 响应头决定 浏览器是否阻止前端 JS 代码跨域获取资源。 浏览器的同源安全策略默认会阻止网页“跨域”获取资源。但如果接口服务器配置了 CORS 相关的 HTTP 响应头， 就可以解除浏览器端的跨域访问限制。

**注意事项** 

① CORS 主要在服务器端进行配置。客户端浏览器无须做任何额外的配置，即可请求开启了 CORS 的接口。 

② CORS 在浏览器中有兼容性。只有支持 XMLHttpRequest Level2 的浏览器，才能正常访问开启了 CORS 的服 务端接口（例如：IE10+、Chrome4+、FireFox3.5+）。

#### CORS 响应头部 

##### Access-Control-Allow-Origin 

响应头部中可以携带一个 Access-Control-Allow-Origin 字段，其语法如下:

```js
Access-Control-Allow-Origin: <origin> | * 
```

其中，origin 参数的值指定了允许访问该资源的外域 URL。 例如，下面的字段值将只允许来自 http://yuling.top的请求：

```js
res.setHeader('Access-Control-Allow-Origin': 'http://yuling.top')
```

如果指定了 Access-Control-Allow-Origin 字段的值为通配符 *，表示允许来自任何域的请求，示例代码如下：

```js
res.setHeader('Access-Control-Allow-Origin': '*')
```

##### Access-Control-Allow-Headers 

默认情况下，CORS 仅支持客户端向服务器发送如下的 9 个请求头： Accept、Accept-Language、Content-Language、DPR、Downlink、Save-Data、Viewport-Width、Width 、 Content-Type （值仅限于 text/plain、multipart/form-data、application/x-www-form-urlencoded 三者之一） 如果客户端向服务器发送了额外的请求头信息，则需要在服务器端，通过 Access-Control-Allow-Headers 对额外 的请求头进行声明，否则这次请求会失败！

```ja
//允许客户端向服务器发送Content-Type 请求头和X-CusTom-Header请求头
//注意多个请求头之间用英文逗号分隔
res.setHeader('Access-Control-Allow-Headers', ' Content-Type,application/x-www-form-urlencoded')
```

##### Access-Control-Allow-Methods

默认情况下，CORS 仅支持客户端发起 GET、POST、HEAD 请求。 如果客户端希望通过 PUT、DELETE 等方式请求服务器的资源，则需要在服务器端，通过 Access-Control-Alow-Methods 来指明实际请求所允许使用的 HTTP 方法。 示例代码如下：

#### CORS请求的分类 

客户端在请求 CORS 接口时，根据请求方式和请求头的不同，可以将 CORS 的请求分为两大类，分别是： ① 简单请求 ② 预检请求

同时满足以下两大条件的请求，就属于**简单请求**： ① 请求方式：GET、POST、HEAD 三者之一 ② HTTP 头部信息不超过以下几种字段：无自定义头部字段、Accept、Accept-Language、Content-Language、DPR、 Downlink、Save-Data、Viewport-Width、Width 、Content-Type（只有三个值application/x-www-formurlencoded、multipart/form-data、text/plain）

只要符合以下任何一个条件的请求，都需要进行**预检请求**： ① 请求方式为 GET、POST、HEAD 之外的请求 Method 类型 ② 请求头中包含自定义头部字段 ③ 向服务器发送了 application/json 格式的数据 在浏览器与服务器正式通信之前，浏览器会先发送 OPTION 请求进行预检，以获知服务器是否允许该实际请求，所以这一 次的 OPTION 请求称为“预检请求”。服务器成功响应预检请求后，才会发送真正的请求，并且携带真实数据。

**区别**

简单请求的特点：客户端与服务器之间只会发生一次请求。 

预检请求的特点：客户端与服务器之间会发生两次请求，OPTION 预检请求成功之后，才会发起真正的请求。

#### JSONP 接口

① 获取客户端发送过来的回调函数的名字 

② 得到要通过 JSONP 形式发送给客户端的数据 

③ 根据前两步得到的数据，拼接出一个函数调用的字符串 

④ 把上一步拼接得到的字符串，响应给客户端的 

##### 实现 JSONP 接口的具体代码

```js
app.get('/api/jsonp',(req,res)=>{
    //1.获取客户端发送过来的回调函数的名字
    const funcName = req.query.callback
    //2.得到要通过JSONP形式发送给客户端的数据
    const data = {name:'yuling', age；18}
    //3.根据前两部得到的数据，拼接出一个函数调用的字符串
    const scriptStr = `${funcName}(${JSON.stringify(data)})`
    4.把上一步拼接的字符串，响应给客户端的script标签进行解析
})
```

##### 在网页中使用 jQuery 发起 JSONP 请求 

调用 $.ajax() 函数，提供 JSONP 的配置选项，从而发起 JSONP 请求，示例代码如下：

```js
$('#btnJsonp').on('click',function(){
    $.ajax({
        method:'GET',
        url:'http://127.0.0.1/api/jsonp',
        dataType:'jsonp', // 表示要发起jsonp请求
        success:function(res){
            console.log(res)
        }
    })
})
```

