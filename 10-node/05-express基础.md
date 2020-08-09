## express

Express 是基于 Node.js 平台，快速、开放、极简的 Web 开发框架。

通俗的理解：Express 的作用和 Node.js 内置的 http 模块类似，是专门用来创建 Web 服务器的。

Express 的本质：就是一个 npm 上的第三方包，提供了快速创建 Web 服务器的便捷方法。

### Express 的基本使用

####  创建基本的 Web 服务器

```js
// 1. 导入 express
const express = require('express')
// 2. 创建 web 服务器
const app = express()
// 3. 启动 web 服务器
app.listen(80, () => {
  console.log('express server running at http://127.0.0.1')
})

```

#### 监听 GET 请求

通过 app.get() 方法，可以监听客户端的 GET 请求，具体的语法格式如下：

```js
app.get('请求URL'，function(req,res){
    //处理函数
})
//参数一：客户端请求的URL地址
//参数二：请求对应的处理函数
//req：请求对象（包含了与请求相关的属性和方法）
//res：响应对象（包含了与响应相关的属性和方法）
```

#### 监听POST请求

通过 app.post() 方法，可以监听客户端的 POST 请求，具体的语法格式如下：

```js
app.post('请求URL'，function(req,res){
    //处理函数
})
//参数一：客户端请求的URL地址
//参数二：请求对应的处理函数
//req：请求对象（包含了与请求相关的属性和方法）
//res：响应对象（包含了与响应相关的属性和方法）
```

#### 把内容响应给客户端

通过 res.send() 方法，可以把处理好的内容，发送给客户端：

```js
app.get('/user',(req,res)=>{
    //向客户端发发送JSON对象
    res.send({name:'yuling',age:18,gender:'男'})
})
app.post('/user',(req,res)=>{
    //向客户端发送文本内容
    res.send('请求成功')
})
```

#### 获取 URL 中携带的查询参数 

通过 req.query 对象，可以访问到客户端通过查询字符串的形式，发送到服务器的参数：

```js
app.get('/',(req,res)=>{
    //req.query 默认是一个空对象
    //客户端使用 ?name=yuling&age=18 这种字符串形式，发送给服务器参数
    //可以通过req.query对象访问到
    //req.query.name req.query.age
    console.log(req.query)
})
```

#### 获取 URL 中的动态参数 

通过 req.params 对象，可以访问到 URL 中，通过 : 匹配到的动态参数：

```js
//URL地址中，可以通过 ：参数名的形式，匹配动态参数值
app.get('/user/:id',(req,res)=>{
    //req.params 默认是一个空对象
    //里面存放通过 ： 动态排配到的参数
    console,log(req.params)
})
```

### 托管静态资源

express 提供了一个非常好用的函数，叫做 express.static()，通过它，我们可以非常方便地创建一个静态资源服务器， 例如，通过如下代码就可以将 public 目录下的图片、CSS 文件、JavaScript 文件对外开放访问了：

```js
app.use(express.static('public'))
```

现在，就可以访问 public 目录中的所有文件了：

```js
 http://localhost:3000/images/bg.jpg

 http://localhost:3000/css/style.css

 http://localhost:3000/js/login.js
```

如果要托管多个静态资源目录，请多次调用 express.static() 函数：

```js
app.use(express.static('public'))
app.use(express.static('files'))
```

####  挂载路径前缀 

如果希望在托管的静态资源访问路径之前，挂载路径前缀，则可以使用如下的方式：

```js
app.use('/public', express.static('public'))
```

现在，可以通过带有 /public 前缀地址来访问 public 目录中的文件了：

```js
http://localhost:3000/public/images/kitten.jpg 
http://localhost:3000/public/css/style.css
http://localhost:3000/public/js/app.js
```

### nodemon

在编写调试 Node.js 项目的时候，如果修改了项目的代码，则需要频繁的手动 close 掉，然后再重新启动，非常繁琐。 现在，我们可以使用 nodemon（https://www.npmjs.com/package/nodemon） 这个工具，它能够监听项目文件 的变动，当代码被修改后，nodemon 会自动帮我们重启项目，极大方便了开发和调试。

**安装 nodemon** 

在终端中，运行如下命令，即可将 nodemon 安装为全局可用的工具：

```shell
npm install  -g nodemon
```

**使用 nodemon** 

当基于 Node.js 编写了一个网站应用的时候，传统的方式，是运行 node app.js 命令，来启动项目。这样做的坏处是： 代码被修改之后，需要手动重启项目。

现在，我们可以将 node 命令替换为 nodemon 命令，使用 nodemon app.js 来启动项目。

这样做的好处是：代码 被修改之后，会被 nodemon 监听到，从而实现自动重启项目的效果。