## BOM

### 1.2.1. 什么是BOM

​	BOM（Browser Object Model）即浏览器对象模型，它提供了独立于内容而与浏览器窗口进行交互的对象，其核心对象是 window。

​	BOM 由一系列相关的对象构成，并且每个对象都提供了很多方法与属性。

​	BOM 缺乏标准，JavaScript 语法的标准化组织是 ECMA，DOM 的标准化组织是 W3C，BOM 最初是Netscape 浏览器标准的一部分。

| DOM                                 | BOM                                           |
| ----------------------------------- | --------------------------------------------- |
| 文档对象模型                        | 浏览器对象模型                                |
| DOM就是把 文档 当做一个 对象 来看待 | 把浏览器当做一个对象来看待                    |
| DOM的顶级对象是document             | BOM的顶级对象是window                         |
| DOM主要学习的是操作页面元素         | BOM学习的是浏览器窗口交互的一些对象           |
| DOM是W3C标准规范                    | BOM是浏览器厂商在各自浏览器上定义的兼容性较差 |



### 1.2.2. BOM的构成

BOM 比 DOM 更大，它包含 DOM。

![1551319344183](I:/%E6%A1%8C%E9%9D%A2/2019%E9%BB%91%E9%A9%AC/%E3%80%9000%E3%80%91%E8%B5%84%E6%96%99/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/02-WebAPI%E7%BC%96%E7%A8%8B%E8%B5%84%E6%96%99/Web%20APIs-day04/4-%E7%AC%94%E8%AE%B0/images/1551319344183.png)

### 1.2.3. 顶级对象window

window对象是浏览器的顶级对象，它具有双重角色

1. 他是JS访问浏览器的一个借口
2. 他是一个全局对象。定义在全局作用域中的变量、函数都会变成window对象的属性和方法

在调用的时候可以省略window，前面学习的对话框都属于window对象方法，比如alert()、prompt()等。

**注意**：window下的一个特殊属性window.name



### 1.2.4. window对象的常见事件

#### 页面（窗口）加载事件（2种）

**第1种**

```js
window.onload = function(){};
或者
window.addEventListener("load",function(){})
```



window.onload 是窗口 (页面）加载事件，**当文档内容完全加载完成**会触发该事件(包括图像、脚本文件、CSS 文件等), 就调用的处理函数。

**注意：**

- 有了window.onload就可以把JS代码写到页面元素的上方，因为onload是等页面内容完全加载完毕，再去执行处理函数
- window.onload传统注册事件方式只能写一次，如果有多个，会以最后一个window.onload为准
- 如果使用addEventListener则没有限制

![1551319600263](I:/%E6%A1%8C%E9%9D%A2/2019%E9%BB%91%E9%A9%AC/%E3%80%9000%E3%80%91%E8%B5%84%E6%96%99/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/02-WebAPI%E7%BC%96%E7%A8%8B%E8%B5%84%E6%96%99/Web%20APIs-day04/4-%E7%AC%94%E8%AE%B0/images/1551319600263.png)

**第2种**

```js
document.addEvwntListener('DOMContentLoaded',function(){})
```





​	DOMContentLoaded 事件触发时，仅当DOM加载完成，不包括样式表，图片，flash等等。

​	IE9以上才支持！！！

​	如果页面的图片很多的话, 从用户访问到onload触发可能需要较长的时间, 交互效果就不能实现，必然影响用户的体验，此时用 DOMContentLoaded 事件比较合适。

```js
    <script>
        window.addEventListener('load', function() {
            var btn = document.querySelector('button');
            btn.addEventListener('click', function() {
                alert('点击我');
            })
        })
        window.addEventListener('load', function() {
            alert(22);
        })
        document.addEventListener('DOMContentLoaded', function() {
            alert(33);
        })
    </script>
```

#### 调整窗口大小事件

```js
window.onresize = function(){}
window.addEventListener("resize",function(){})
```



​	window.onresize 是调整窗口大小加载事件,  当触发时就调用的处理函数。

注意：

1. 只要窗口大小发生像素变化，就会触发这个事件。
2. 我们经常利用这个事件完成响应式布局。 window.innerWidth 当前屏幕的宽度

```js
    <script>
        // 注册页面加载事件
        window.addEventListener('load', function() {
            var div = document.querySelector('div');
        	// 注册调整窗口大小事件
            window.addEventListener('resize', function() {
                // window.innerWidth 获取窗口大小
                console.log('变化了');
                if (window.innerWidth <= 800) {
                    div.style.display = 'none';
                } else {
                    div.style.display = 'block';
                }
            })
        })
    </script>
    <div></div>
```



### 1.2.5. 定时器（两种）

window 对象给我们提供了 2 个非常好用的方法-定时器。

- setTimeout() 
- setInterval()  

#### setTimeout() 炸弹定时器

##### 开启定时器

```ls
window.setTimeout(调用函数，[延迟的毫秒数]);
```

setTimeout()这个调用函数我们也称为回调函数callback

**注意：**

- window可以省略
- 这个调用函数可以直接写函数，或者写函数名或者采用字符串‘函数名（）’三种形式。第三种不推荐
- 延迟的毫秒数省略默认是0，如果写，必须是毫秒。
- 因为定时器可能有很多，所以我们经常给定时器赋值一个标识符



> ```
> 普通函数是按照代码顺序直接调用。
> 
> 简单理解： 回调，就是回头调用的意思。上一件事干完，再回头再调用这个函数。
> 例如：定时器中的调用函数，事件处理函数，也是回调函数。
> 
> 以前我们讲的   element.onclick = function(){}   或者  element.addEventListener(“click”, fn);   里面的 函数也是回调函数。
> 
> ```



```js
    <script>
        // 回调函数是一个匿名函数
         setTimeout(function() {
             console.log('时间到了');

         }, 2000);
        function callback() {
            console.log('爆炸了');
        }
		// 回调函数是一个有名函数
        var timer1 = setTimeout(callback, 3000);
        var timer2 = setTimeout(callback, 5000);
    </script>
```

##### 案例：5秒后关闭广告

![1551320924828](I:/%E6%A1%8C%E9%9D%A2/2019%E9%BB%91%E9%A9%AC/%E3%80%9000%E3%80%91%E8%B5%84%E6%96%99/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/02-WebAPI%E7%BC%96%E7%A8%8B%E8%B5%84%E6%96%99/Web%20APIs-day04/4-%E7%AC%94%E8%AE%B0/images/1551320924828.png)



![1551320959756](I:/%E6%A1%8C%E9%9D%A2/2019%E9%BB%91%E9%A9%AC/%E3%80%9000%E3%80%91%E8%B5%84%E6%96%99/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/02-WebAPI%E7%BC%96%E7%A8%8B%E8%B5%84%E6%96%99/Web%20APIs-day04/4-%E7%AC%94%E8%AE%B0/images/1551320959756.png)

```js
<body>
    <img src="images/ad.jpg" alt="" class="ad">
    <script>
        // 获取要操作的元素
        var ad = document.querySelector('.ad');
		// 开启定时器
        setTimeout(function() {
            ad.style.display = 'none';
        }, 5000);
    </script>
</body>
```

##### 停止定时器

```js
window.clearTimeout(timoutID)
```

clearTimeout()方法取消了先前通过调用setTimeout()建立的定时器

**注意：**

- window可以省略
- 里面的参数就是定时器的标识符



```js
    <button>点击停止定时器</button>
    <script>
        var btn = document.querySelector('button');
		// 开启定时器
        var timer = setTimeout(function() {
            console.log('爆炸了');
        }, 5000);
		// 给按钮注册单击事件
        btn.addEventListener('click', function() {
            // 停止定时器
            clearTimeout(timer);
        })
    </script>
```



#### setInterval() 闹钟定时器

##### 开启定时器

```js
window.setIntervel(回调函数，[间隔毫秒数]);
```

setIntervel()方法重复调用一个函数，每隔这个时间，就去调用一次函数

**注意：**

- window可以省略
- 这个调用函数可以直接写函数或者写函数名或者采用字符串‘函数名（）’三种形式。第三种不推荐
- 延迟的毫秒数省略默认是0，如果写，必须是毫秒。
- 因为定时器可能有很多，所以我们经常给定时器赋值一个标识符
- 第一次执行也是间隔毫秒数之后执行，之后每隔毫秒数就只想一次



```js
    <script>
        // 1. setInterval 
        setInterval(function() {
            console.log('继续输出');
        }, 1000);
    </script>
```

##### 案例：倒计时

![1551321298787](I:/%E6%A1%8C%E9%9D%A2/2019%E9%BB%91%E9%A9%AC/%E3%80%9000%E3%80%91%E8%B5%84%E6%96%99/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/02-WebAPI%E7%BC%96%E7%A8%8B%E8%B5%84%E6%96%99/Web%20APIs-day04/4-%E7%AC%94%E8%AE%B0/images/1551321298787.png)

![1551321322188](I:/%E6%A1%8C%E9%9D%A2/2019%E9%BB%91%E9%A9%AC/%E3%80%9000%E3%80%91%E8%B5%84%E6%96%99/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/02-WebAPI%E7%BC%96%E7%A8%8B%E8%B5%84%E6%96%99/Web%20APIs-day04/4-%E7%AC%94%E8%AE%B0/images/1551321322188.png)

```js
    <div>
        <span class="hour">1</span>
        <span class="minute">2</span>
        <span class="second">3</span>
    </div>
    <script>
        // 1. 获取元素（时分秒盒子） 
        var hour = document.querySelector('.hour'); // 小时的黑色盒子
        var minute = document.querySelector('.minute'); // 分钟的黑色盒子
        var second = document.querySelector('.second'); // 秒数的黑色盒子
        var inputTime = +new Date('2019-5-1 18:00:00'); // 返回的是用户输入时间总的毫秒数

        countDown(); // 我们先调用一次这个函数，防止第一次刷新页面有空白 

        // 2. 开启定时器
        setInterval(countDown, 1000);
		
        function countDown() {
            var nowTime = +new Date(); // 返回的是当前时间总的毫秒数
            var times = (inputTime - nowTime) / 1000; // times是剩余时间总的秒数 
            var h = parseInt(times / 60 / 60 % 24); //时
            h = h < 10 ? '0' + h : h;
            hour.innerHTML = h; // 把剩余的小时给 小时黑色盒子
            var m = parseInt(times / 60 % 60); // 分
            m = m < 10 ? '0' + m : m;
            minute.innerHTML = m;
            var s = parseInt(times % 60); // 当前的秒
            s = s < 10 ? '0' + s : s;
            second.innerHTML = s;
        }
    </script>
```

##### 停止定时器

```js
window.clearInterval(intervalId);
```

clearInterval()方法取消了先前通过调用setInterval()建立的定时器。

注意：

- window可以省略
- 里面的参数就是定时器的标识符



#### 案例：发送短信倒计时

​	点击按钮后，该按钮60秒之内不能再次点击，防止重复发送短信。

![1551321540676](I:/%E6%A1%8C%E9%9D%A2/2019%E9%BB%91%E9%A9%AC/%E3%80%9000%E3%80%91%E8%B5%84%E6%96%99/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/02-WebAPI%E7%BC%96%E7%A8%8B%E8%B5%84%E6%96%99/Web%20APIs-day04/4-%E7%AC%94%E8%AE%B0/images/1551321540676.png)

**案例分析：**

1. 按钮点击之后，会禁用disabled为true
2. 同时按钮里面的内容会变化，注意button里面的内容通过innerHTML修改 
3. 里面的秒数室友变化的，因此需要用到定时器
4. 定义一个变量，在定时器里面，不断递减
5. 如果变量为0说明到了时间，我们需要停止定时器，并恢复圆按钮出事状态



```js
    手机号码： <input type="number"> <button>发送</button>
    <script>
        var btn = document.querySelector('button');
		// 全局变量，定义剩下的秒数
        var time = 3; 
		// 注册单击事件
        btn.addEventListener('click', function() {
            // 禁用按钮
            btn.disabled = true;
            // 开启定时器
            var timer = setInterval(function() {
                // 判断剩余秒数
                if (time == 0) {
                    // 清除定时器和复原按钮
                    clearInterval(timer);
                    btn.disabled = false;
                    btn.innerHTML = '发送';
                } else {
                    btn.innerHTML = '还剩下' + time + '秒';
                    time--;
                }
            }, 1000);
        });
    </script>
```



### 1.2.6. this指向问题

​	this的指向在函数定义的时候是确定不了的，只有函数执行的时候才能确定this到底指向谁，一般情况下this的最终指向的是那个调用它的对象。

现阶段，我们先了解一下几个this指向

1. 全局作用域或者普通函数中this指向全局对象window（注意定时器里面的this指向window）
2. 方法调用中谁调用this指向谁
3. 构造函数中this指向构造函数的实例

```js
    <button>点击</button>
    <script>
        // this 指向问题 一般情况下this的最终指向的是那个调用它的对象
        // 1. 全局作用域或者普通函数中this指向全局对象window（ 注意定时器里面的this指向window）
        console.log(this);
        function fn() {
            console.log(this);
        }
        window.fn();
        window.setTimeout(function() {
            console.log(this);
        }, 1000);
        // 2. 方法调用中谁调用this指向谁
        var o = {
            sayHi: function() {
                console.log(this); // this指向的是 o 这个对象
            }
        }
        o.sayHi();
        var btn = document.querySelector('button');
        btn.addEventListener('click', function() {
                console.log(this); // 事件处理函数中的this指向的是btn这个按钮对象
            })
        // 3. 构造函数中this指向构造函数的实例
        function Fun() {
            console.log(this); // this 指向的是fun 实例对象
        }
        var fun = new Fun();
    </script>
```



### 1.2.7. location对象

#### 什么是 location 对象

window对象给我们提供了一个location属性用于获取或者设置长提的url，并且可以用于解析url。因为这个属性返回的是一个对象，所以我们将真个属性也称为location对象。

**URL**

统一资源定位符(Uniform Resource Locator,URL)是互联网上标准资源的地址。互联网上的每个文件都有一个唯一的URL，它包含的信息指出文件的位置以及浏览器应该怎么处理它

URL的一般语法格式为

```
protocol://host[:port]/path/[?query]#fragment
http://www.itcast.cn/index.html?name=andy&age=18#link
```

| 组成     | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| protocol | 通信协议 常用的http,ftp,maito等                              |
| host     | 主机（域名）www.itheima.com                                  |
| port     | 端口号 可选 省略时使用方案的默认端口 如http的默认端口为80    |
| path     | 路径 由一个或者多个'/'符号隔开的字符串，一般用来表示主机上的一个目录或文件地址 |
| query    | 参数 以键值对的形式，通过&符号隔开                           |
| fragment | 片段 #后面内容 常见于链接锚点                                |





#### location 对象的属性

| location对象属性  | 返回值                          |
| ----------------- | ------------------------------- |
| location.href     | 获取或者设置 整个URL            |
| location.host     | 返回主机（域名）                |
| location.port     | 返回端口号 如果未写返回空字符串 |
| location.pathname | 返回路径                        |
| location.search   | 返回参数                        |
| location.hash     | 返回片段 #后面内容              |





#### 案例：5分钟自动跳转页面

![1551322496871](I:/%E6%A1%8C%E9%9D%A2/2019%E9%BB%91%E9%A9%AC/%E3%80%9000%E3%80%91%E8%B5%84%E6%96%99/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/02-WebAPI%E7%BC%96%E7%A8%8B%E8%B5%84%E6%96%99/Web%20APIs-day04/4-%E7%AC%94%E8%AE%B0/images/1551322496871.png)

![1551322517605](I:/%E6%A1%8C%E9%9D%A2/2019%E9%BB%91%E9%A9%AC/%E3%80%9000%E3%80%91%E8%B5%84%E6%96%99/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/02-WebAPI%E7%BC%96%E7%A8%8B%E8%B5%84%E6%96%99/Web%20APIs-day04/4-%E7%AC%94%E8%AE%B0/images/1551322517605.png)

```js
    <button>点击</button>
    <div></div>
    <script>
        var btn = document.querySelector('button');
        var div = document.querySelector('div');
        btn.addEventListener('click', function() {
            // console.log(location.href);
            location.href = 'http://www.itcast.cn';
        })
        var timer = 5;
        setInterval(function() {
            if (timer == 0) {
                location.href = 'http://www.itcast.cn';
            } else {
                div.innerHTML = '您将在' + timer + '秒钟之后跳转到首页';
                timer--;
            }
        }, 1000);
    </script>
```

#### 案例：获取URL参数

![1551322622640](I:/%E6%A1%8C%E9%9D%A2/2019%E9%BB%91%E9%A9%AC/%E3%80%9000%E3%80%91%E8%B5%84%E6%96%99/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/02-WebAPI%E7%BC%96%E7%A8%8B%E8%B5%84%E6%96%99/Web%20APIs-day04/4-%E7%AC%94%E8%AE%B0/images/1551322622640.png)

![1551322639241](I:/%E6%A1%8C%E9%9D%A2/2019%E9%BB%91%E9%A9%AC/%E3%80%9000%E3%80%91%E8%B5%84%E6%96%99/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/02-WebAPI%E7%BC%96%E7%A8%8B%E8%B5%84%E6%96%99/Web%20APIs-day04/4-%E7%AC%94%E8%AE%B0/images/1551322639241.png)

```js
    <div></div>
	<script>
        console.log(location.search); // ?uname=andy
        // 1.先去掉？  substr('起始的位置'，截取几个字符);
        var params = location.search.substr(1); // uname=andy
        console.log(params);
        // 2. 利用=把字符串分割为数组 split('=');
        var arr = params.split('=');
        console.log(arr); // ["uname", "ANDY"]
        var div = document.querySelector('div');
        // 3.把数据写入div中
        div.innerHTML = arr[1] + '欢迎您';
    </script>
```

#### location对象的常见方法

| location对象方法   | 返回值                                                       |
| ------------------ | ------------------------------------------------------------ |
| location.assign()  | 跟href一样，可以跳转页面（也称为重定向页面）                 |
| location.replace() | 替换当前页面，应为不记录历史，所以不能后退页面               |
| location.reload()  | 重新加载页面，相当于刷新按钮或者 f5 如果参数为true 强制刷新 ctrl+f5 |



```js
    <button>点击</button>
    <script>
        var btn = document.querySelector('button');
        btn.addEventListener('click', function() {
            // 记录浏览历史，所以可以实现后退功能
            // location.assign('http://www.itcast.cn');
            // 不记录浏览历史，所以不可以实现后退功能
            // location.replace('http://www.itcast.cn');
            location.reload(true);
        })
    </script>
```

### 1.2.8. navigator对象

​	navigator 对象包含有关浏览器的信息，它有很多属性，我们最常用的是 userAgent，该属性可以返回由客户机发送服务器的 user-agent 头部的值。

下面前端代码可以判断用户那个终端打开页面，实现跳转

```js
if((navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i))) {
    window.location.href = "";     //手机
 } else {
    window.location.href = "";     //电脑
 }
```

### 1.2.9 history对象

​	window对象给我们提供了一个 history对象，与浏览器历史记录进行交互。该对象包含用户（在浏览器窗口中）访问过的URL。

| history对象方法 | 作用                                                        |
| --------------- | ----------------------------------------------------------- |
| back()          | 可以后退功能                                                |
| forward()       | 前进功能                                                    |
| go(参数)        | 前进后退功能 参数如果是1 前进一个页面 如果是-1 后退一个页面 |



history对象一般在实际开发中比较少用，但是会在一些 OA 办公系统中见到。

![1551322959148](I:/%E6%A1%8C%E9%9D%A2/2019%E9%BB%91%E9%A9%AC/%E3%80%9000%E3%80%91%E8%B5%84%E6%96%99/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/07-10%20JavaScript%E7%BD%91%E9%A1%B5%E7%BC%96%E7%A8%8B/02-WebAPI%E7%BC%96%E7%A8%8B%E8%B5%84%E6%96%99/Web%20APIs-day04/4-%E7%AC%94%E8%AE%B0/images/1551322959148.png)

## 