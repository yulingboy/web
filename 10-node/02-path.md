## path 路径模块

path 模块是 Node.js 官方提供的、用来处理路径的模块。它提供了一系列的方法和属性，用来满足用户对路径的处理 需求。

如果要在 JavaScript 代码中，使用 path 模块来处理路径，则需要使用如下的方式先导入它：

```js
const path = require('path')
```

### join

使用 path.join() 方法，可以把多个路径片段拼接为完整的路径字符串，语法格式如下：

```js
path.join([...paths])
```

**参数解读：** 

...paths  路径片段的序列 

返回值:  < string >

**案例：**

```js
const path = require('path')
const pathStr = path.join('/a','/b/c','../','./d','e')
cobsole.log(pathStr) //a\b\d\e
const pathStr2 = path.join(__dirname,'./file/1.txt')
cobsole.log(pathStr2) //当前目录\file\1.txt
```

**注意：**

今后凡是涉及到路径拼接的操作，都要使用 path.join() 方法进行处理。不要直接使用 + 进行字符串的拼接。

### basename

使用 path.basename() 方法，可以获取路径中的最后一部分，经常通过这个方法获取路径中的文件名，语法格式如下：

```js
path.basename(path[, ext])
```

**参数解读：** 

path< string >  必选参数，表示一个路径的字符串 

ext < string > 可选参数，表示文件扩展名 

返回:  < string >表示路径中的最后一部分

**案例：**

```js
const path = require('path')

// 定义文件的存放路径
const fpath = '/a/b/c/index.html'

// const fullName = path.basename(fpath)
// console.log(fullName)

const nameWithoutExt = path.basename(fpath, '.html')
console.log(nameWithoutExt)

```

### extname

使用 path.extname() 方法，可以获取路径中的扩展名部分：

```js
 const fext = path.extname(fpath)
```

**案例：**

```js
const path = require('path')

// 这是文件的存放路径
const fpath = '/a/b/c/index.html'

const fext = path.extname(fpath)
console.log(fext)

```

