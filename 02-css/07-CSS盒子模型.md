# 盒子模型（CSS重点）

- 所谓盒子模型：

  - 就是把HTML页面中的布局元素看作是一个矩形的盒子，也就是一个盛装内容的容器。

  * 盒子模型有元素的内容、边框（border）、内边距（padding）、和外边距（margin）组成。
  * 盒子里面的文字和图片等元素是 内容区域
  * 盒子的厚度 我们成为 盒子的边框 
  * 盒子内容与边框的距离是内边距（类似单元格的 cellpadding)
  * 盒子与盒子之间的距离是外边距（类似单元格的 cellspacing）

## 1. 盒子边框（border）



- 语法：

~~~css
border : border-width || border-style || border-color 
~~~

| 属性         |          作用          |
| ------------ | :--------------------: |
| border-width | 定义边框粗细，单位是px |
| border-style |       边框的样式       |
| border-color |        边框颜色        |

- 边框的样式：
  - none：没有边框即忽略所有边框的宽度（默认值）
  - solid：边框为单实线(最为常用的)
  - dashed：边框为虚线  
  - dotted：边框为点线

### 1.1 边框综合设置

```
border : border-width || border-style || border-color 
```

例如：

~~~css
 border: 1px solid red;  没有顺序  
~~~



### 1.2 盒子边框写法总结表

很多情况下，我们不需要指定4个边框，我们是可以单独给4个边框分别指定的。

| 上边框                     | 下边框                        | 左边框                      | 右边框                       |
| :------------------------- | :---------------------------- | :-------------------------- | :--------------------------- |
| border-top-style:样式;     | border-bottom-style:样式;     | border-left-style:样式;     | border-right-style:样式;     |
| border-top-width:宽度;     | border- bottom-width:宽度;    | border-left-width:宽度;     | border-right-width:宽度;     |
| border-top-color:颜色;     | border- bottom-color:颜色;    | border-left-color:颜色;     | border-right-color:颜色;     |
| border-top:宽度 样式 颜色; | border-bottom:宽度 样式 颜色; | border-left:宽度 样式 颜色; | border-right:宽度 样式 颜色; |

**案例**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>边框的练习</title>
    <style>
        /* 请给一个 200*200 的盒子，设置上边框为红色，其余边框为蓝色 */
        div {
            width: 200px;
            height: 200px;
            /* border-top: 1px solid red;
            border-bottom: 1px solid blue;
            border-left: 1px solid blue;
            border-right: 1px solid blue; */
            /* border包含四条边 */
            border: 1px solid blue;
            /* 层叠性 只是层叠了 上边框啊 */
            border-top: 1px solid red;
        }
    </style>
</head>
<body>
    <div></div>
</body>
</html>
```

![image-20200724153122871](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200724153124.png)

### 1.3 表格的细线边框

- 通过表格的`cellspacing="0"`,将单元格与单元格之间的距离设置为0，

- 但是两个单元格之间的边框会出现重叠，从而使边框变粗

- 通过css属性：

  ~~~
  table{ border-collapse:collapse; }  
  ~~~

  - collapse 单词是合并的意思
  - border-collapse:collapse; 表示相邻边框合并在一起。

~~~css
<style>
	table {
		width: 500px;
		height: 300px;
		border: 1px solid red;
	}
	td {
		border: 1px solid red;
		text-align: center;
	}
	table, td {
		border-collapse: collapse;  /*合并相邻边框*/
	}
</style>
~~~

**案例**

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>今日小说排行榜</title>
    <style>
        table {
            width: 500px;
            height: 249px;
        }
        th {
            height: 35px;
        }
        table,
        td, th {
            border: 1px solid pink;
            /* 合并相邻的边框 */
            border-collapse: collapse;
            font-size: 14px;
            text-align: center;
        }
    </style>
</head>
<body>
    <table align="center" cellspacing="0">
    <thead>
        <tr>
            <th>排名</th>
            <th>关键词</th>
            <th>趋势</th>
            <th>进入搜索</th>
            <th>最近七日</th>
            <th>相关链接</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>鬼吹灯</td>
            <td><img src="down.jpg"></td>
            <td>456</td>
            <td>123</td>
            <td> <a href="#">贴吧</a> <a href="#">图片</a> <a href="#">百科</a> </td>
        </tr>

        <tr>
                <td>1</td>
                <td>鬼吹灯</td>
                <td><img src="down.jpg"></td>
                <td>456</td>
                <td>123</td>
                <td> <a href="#">贴吧</a> <a href="#">图片</a> <a href="#">百科</a> </td>
        </tr>
        <tr>
                <td>3</td>
                <td>西游记</td>
                <td><img src="up.jpg"></td>
                <td>456</td>
                <td>123</td>
                <td> <a href="#">贴吧</a> <a href="#">图片</a> <a href="#">百科</a> </td>
        </tr>
        <tr>
                <td>1</td>
                <td>鬼吹灯</td>
                <td><img src="down.jpg"></td>
                <td>456</td>
                <td>123</td>
                <td> <a href="#">贴吧</a> <a href="#">图片</a> <a href="#">百科</a> </td>
        </tr>
        <tr>
                <td>1</td>
                <td>鬼吹灯</td>
                <td><img src="down.jpg"></td>
                <td>456</td>
                <td>123</td>
                <td> <a href="#">贴吧</a> <a href="#">图片</a> <a href="#">百科</a> </td>
        </tr>
        <tr>
                <td>1</td>
                <td>鬼吹灯</td>
                <td><img src="down.jpg"></td>
                <td>456</td>
                <td>123</td>
                <td> <a href="#">贴吧</a> <a href="#">图片</a> <a href="#">百科</a> </td>
        </tr>
    </tbody>           
    </table>
</body>
</html>
```

![image-20200724153309551](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200724153310.png)

## 2. 内边距（padding）

### 2.1 内边距：

​	padding属性用于设置内边距。 **是指 边框与内容之间的距离。**

### 2.2 设置

| 属性          | 作用     |
| ------------- | :------- |
| padding-left  | 左内边距 |
| padding-right | 右内边距 |
| padding-top   | 上内边距 |
| padding-bottom   | 下内边距 |

当我们给盒子指定padding值之后， 发生了2件事情：

1. 内容和边框 有了距离，添加了内边距。
2. 盒子会变大了。

 **注意：  后面跟几个数值表示的意思是不一样的。**

我们分开写有点麻烦，我们可以不可以简写呢？

| 值的个数 | 表达意思                                        |
| -------- | ----------------------------------------------- |
| 1个值    | padding：上下左右内边距;                        |
| 2个值    | padding: 上下内边距    左右内边距 ；            |
| 3个值    | padding：上内边距   左右内边距   下内边距；     |
| 4个值    | padding: 上内边距 右内边距 下内边距 左内边距 ； |

### 2.3 内盒尺寸计算（元素实际大小）

- 宽度

  Element Height = content height + padding + border （Height为内容高度）

- 高度

   Element Width = content width + padding + border （Width为内容宽度）

-  盒子的实际的大小 =   内容的宽度和高度 +  内边距   +  边框   

### 2.4 内边距产生的问题

- 问题

  会撑大原来的盒子

- 解决：

  通过给设置了宽高的盒子，减去相应的内边距的值，维持盒子原有的大小




### 2.5 padding不影响盒子大小情况

> 如果没有给一个盒子指定宽度， 此时，如果给这个盒子指定padding， 则不会撑开盒子。

**案例**

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>新浪导航</title>
    <style>
        .nav {
            height: 41px;
            border-top: 3px solid #ff8500;
            border-bottom: 1px solid #edeef0;
            background-color: #fcfcfc;
            line-height: 41px;
        }
        .nav a {
            /* a属于行内元素 此时必须要转换 行内块元素 */
            display: inline-block;
            height: 41px;
            padding: 0 20px;
            font-size: 12px;
            color: #4c4c4c;
            text-decoration: none;
        }
        .nav a:hover {
            background-color: #eee;
            color: #ff8500;
        }
    </style>
</head>
<body>
    <div class="nav">
        <a href="#">新浪导航</a>
        <a href="#">手机新浪网</a>
        <a href="#">移动客户端</a>
        <a href="#">微博</a>
        <a href="#">三个字</a>
    </div>
</body>
</html>
```

![image-20200724153425509](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200724153426.png)

## 3. 外边距（margin）

### 3.1 外边距

​	margin属性用于设置外边距。  margin就是控制**盒子和盒子之间的距离**

### 3.2 设置：

| 属性          | 作用     |
| ------------- | :------- |
| margin-left   | 左外边距 |
| margin-right  | 右外边距 |
| margin-top    | 上外边距 |
| margin-bottom | 下外边距 |

margin值的简写 （复合写法）代表意思  跟 padding 完全相同。

**案例**

```html

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>简单版小米侧边栏</title>
    <style>
        /* 1. 把a转换为块级元素 */
        a {
            display: block;
            width: 200px;
            height: 40px;
            background-color: #55585a;
            font-size: 14px;
            color: #fff;
            text-decoration: none;
            padding-left: 30px;
            line-height: 40px;
        }

        /* 2 鼠标经过链接变换背景颜色 */
        a:hover {
            background-color: #ff6700;
        }
    </style>
</head>

<body>

    <a href="#">手机 电话卡</a>
    <a href="#">电视 盒子</a>
    <a href="#">笔记本 平板</a>
    <a href="#">出行 穿戴</a>
    <a href="#">智能 路由器</a>
    <a href="#">健康 儿童</a>
    <a href="#">耳机 音响</a>
</body>

</html>
```

![image-20200724153648430](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200724153651.png)

### 3.3 块级盒子水平居中

- 可以让一个块级盒子实现水平居中必须：
  - 盒子必须指定了宽度（width）
  - 然后就给**左右的外边距都设置为auto**，

实际工作中常用这种方式进行网页布局，示例代码如下：

~~~css
.header{ width:960px; margin:0 auto;}
~~~

常见的写法，以下下三种都可以。

* margin-left: auto;   margin-right: auto;
* margin: auto;
* margin: 0 auto;

### 3.4 文字居中和盒子居中区别

1.  盒子内的文字水平居中是  text-align: center,  而且还可以让 行内元素和行内块居中对齐
2.  块级盒子水平居中  左右margin 改为 auto 

~~~css
text-align: center; /*  文字 行内元素 行内块元素水平居中 */
margin: 10px auto;  /* 块级盒子水平居中  左右margin 改为 auto 就阔以了 上下margin都可以 */
~~~

### 3.5 插入图片和背景图片区别

1. 插入图片 我们用的最多 比如产品展示类  移动位置只能靠盒模型 padding margin
4. 背景图片我们一般用于小图标背景 或者 超大背景图片  背景图片 只能通过  background-position

~~~css
 img {  
		width: 200px;/* 插入图片更改大小 width 和 height */
		height: 210px;
		margin-top: 30px;  /* 插入图片更改位置 可以用margin 或padding  盒模型 */
		margin-left: 50px; /* 插入当图片也是一个盒子 */
	}

 div {
		width: 400px;
		height: 400px;
		border: 1px solid purple;
		background: #fff url(images/sun.jpg) no-repeat;
		background-position: 30px 50px; /* 背景图片更改位置 我用 background-position */
	}
~~~

### 3.6 清除元素的默认内外边距(重要)

为了更灵活方便地控制网页中的元素，制作网页时，我们需要将元素的默认内外边距清除

代码： 

~~~css
* {
   padding:0;         /* 清除内边距 */
   margin:0;          /* 清除外边距 */
}
~~~

注意：  

* 行内元素为了照顾兼容性， 尽量只设置左右内外边距， 不要设置上下内外边距。

### 3.7 外边距合并

使用margin定义块元素的**垂直外边距**时，可能会出现外边距的合并。

#### (1). 相邻块元素垂直外边距的合并

- 当上下相邻的两个块元素相遇时，如果上面的元素有下外边距margin-bottom
- 下面的元素有上外边距margin-top，则他们之间的垂直间距不是margin-bottom与margin-top之和
- **取两个值中的较大者**这种现象被称为相邻块元素垂直外边距的合并（也称外边距塌陷）。

**解决方案：尽量给只给一个盒子添加margin值**。

#### (2). 嵌套块元素垂直外边距的合并（塌陷）

- 对于两个嵌套关系的块元素，如果父元素没有上内边距及边框
- 父元素的上外边距会与子元素的上外边距发生合并
- 合并后的外边距为两者中的较大者

**解决方案：**

1. 可以为父元素定义上边框。
2. 可以为父元素定义上内边距
2. 可以为父元素添加overflow:hidden。

还有其他方法，比如浮动、固定、绝对定位的盒子不会有问题，后面咱们再总结。。。

## 4. 盒子模型布局稳定性

按照 优先使用  宽度 （width）  其次 使用内边距（padding）    再次  外边距（margin）。   

```
  width >  padding  >   margin   
```

- 原因：
  - margin 会有外边距合并 还有 ie6下面margin 加倍的bug（讨厌）所以最后使用。
  - padding  会影响盒子大小， 需要进行加减计算（麻烦） 其次使用。
  - width   没有问题（嗨皮）我们经常使用宽度剩余法 高度剩余法来做。

**综合案例**

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>综合案例-产品模块</title>
    <style>
      * {
          margin: 0;
          padding: 0;
      }
      body {
          background-color: #f5f5f5;
      }
      a {
          color: #333;
          text-decoration: none;
      }
      .box {
          width: 298px;
          height: 415px;
          background-color:#fff;
          /* 让块级的盒子水平居中对齐 */
          margin: 100px auto;
      }
      .box img {
          /* 图片的宽度和父亲一样宽 */
          width: 100%;
      }
      .review {
          height: 70px;
          font-size: 14px;
          /* 因为这个段落没有 width属性 所有 padding不会撑开盒子的宽度 */
          padding: 0 28px;
          margin-top: 30px;
      }
      .appraise {
          font-size: 12px;
          color: #b0b0b0;
          margin-top: 20px;
          padding: 0 28px;
      }
      .info {
          font-size: 14px;
          margin-top: 15px;
          padding: 0 28px;
      }
      .info h4 {
          display: inline-block;
          font-weight: 400;
        
      }
      .info span {
          color: #ff6700;    
      }
      .info em {
          font-style: normal;
          color: #ebe4e0;
          margin: 0 6px 0 15px;
      }
    </style>
</head>
<body>
    <div class="box">
        <img src="images/img.jpg" alt="">
        <p class="review">快递牛，整体不错蓝牙可以说秒连。红米给力</p>
        <div class="appraise">来自于 117384232 的评价</div>
        <div class="info">
               <h4> <a href="#">Redmi AirDots真无线蓝...</a></h4>
               <em>|</em>
               <span> 99.9元</span>
        </div>
    </div>
</body>
</html>
```

![image-20200724153828244](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200724153829.png)