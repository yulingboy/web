# css引入的三种方法

- 概念：

  ​	CSS(Cascading Style Sheets)  ，通常称为CSS样式表或层叠样式表（级联样式表）

- 作用：

  - 主要用于**设置** HTML页面中的文本内容（字体、大小、对齐方式等）、图片的外形（宽高、边框样式、边距等）以及**版面的布局和外观显示样式。**
  - CSS以HTML为基础，提供了丰富的功能，如字体、颜色、背景的控制及整体排版等，而且还可以针对不同的浏览器设置不同的样式。

## 1.行内式（内联样式）

- 概念：

  ​	称行内样式、行间样式.

  ​	是通过标签的style属性来设置元素的样式

- 其基本语法格式如下：

```html
<标签名 style="属性1:属性值1; 属性2:属性值2; 属性3:属性值3;"> 内容 </标签名>
```

实际上任何HTML标签都拥有style属性，用来设置行内式。

- 案例：

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>index</title>
</head>
<body>
        <div style="color: red; font-size: 12px;">hello world</div>
</body>
</html>
```

- 注意：
  - style其实就是标签的属性
  - 样式属性和值中间是`:`
  - 多组属性值之间用`;`隔开。
  - 只能控制当前的标签和以及嵌套在其中的字标签，造成代码冗余
- 缺点：
  - 没有实现样式和结构相分离



## 2.内部样式表（内嵌样式表）

- 概念：

  ​	称内嵌式

  ​	是将CSS代码集中写在HTML文档的head头部标签中，并且用style标签定义

- 其基本语法格式如下：

```html
<head>
<style type="text/CSS">
    选择器（选择的标签） { 
      属性1: 属性值1;
      属性2: 属性值2; 
      属性3: 属性值3;
    }
</style>
</head>
```

```css
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>index</title>
</head>
<style>
    div {
        color: red;
        font-size: 12px;
    }
</style>

<body>
    <div>hello world</div>
</body>

</html>
```

- 注意：

  - style标签一般位于head标签中，当然理论上他可以放在HTML文档的任何地方。
  - type="text/css"  在html5中可以省略。
  - 只能控制当前的页面

- 缺点：

  没有彻底分离



## 3.外部样式表（外链式）

- 概念：

  ​	称链入式

  ​	是将所有的样式放在一个或多个以**.CSS**为扩展名的外部样式表文件中，

  ​	通过link标签将外部样式表文件链接到HTML文档中

- 其基本语法格式如下：

```html
<head>
  <link rel="stylesheet" type="text/css" href="css文件路径">
</head>
```

- 注意：  
  - link 是个单标签
  - link标签需要放在head头部标签中，并且指定link标签的三个属性

| 属性 | 作用                                                         |
| ---- | :----------------------------------------------------------- |
| rel  | 定义当前文档与被链接文档之间的关系，在这里需要指定为“stylesheet”，表示被链接的文档是一个样式表文件。 |
| type | 定义所链接文档的类型，在这里需要指定为“text/CSS”，表示链接的外部文件为CSS样式表。我们都可以省略 |
| href | 定义所链接外部样式表文件的URL，可以是相对路径，也可以是绝对路径。 |



## 4. 三种样式表总结（位置）

| 样式表     | 优点                     | 缺点                     | 使用情况       | 控制范围           |
| ---------- | ------------------------ | ------------------------ | -------------- | ------------------ |
| 行内样式表 | 书写方便，权重高         | 没有实现样式和结构相分离 | 较少           | 控制一个标签（少） |
| 内部样式表 | 部分结构和样式相分离     | 没有彻底分离             | 较多           | 控制一个页面（中） |
| 外部样式表 | 完全实现结构和样式相分离 | 需要引入                 | 最多，强烈推荐 | 控制整个站点（多） |

**代码风格**

样式书写一般有两种：

- 一种是紧凑格式 (Compact)

```css
h3 { color: deeppink;font-size: 20px;}
```

- 一种是展开格式（推荐）

```css
h3 {
	color: deeppink;
    font-size: 20px;    
}
```

**代码大小写**

样式选择器，属性名，属性值关键字全部使用小写字母书写，属性字符串允许使用大小写。

```css
/* 推荐 */
h3{
	color: pink;
}
	
/* 不推荐 */
H3{
	COLOR: PINK;
}
```



## 5. 总结CSS样式规则

1. 选择器用于指定CSS样式作用的HTML标签，花括号内是对该对象设置的具体样式。
2. 属性和属性值以“键值对”的形式出现。
3. 属性是对指定的对象设置的样式属性，例如字体大小、文本颜色等。
4. 属性和属性值之间用英文“:”连接。
5. 多个“键值对”之间用英文“;”进行区分。