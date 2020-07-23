# 标签显示模式（display）

## 1. 什么是标签显示模式

- 什么是标签的显示模式？

  标签以什么方式进行显示，比如div 自己占一行， 比如span 一行可以放很多个

- 作用： 

  我们网页的标签非常多，再不同地方会用到不同类型的标签，以便更好的完成我们的网页。

- 标签的类型(分类)

  HTML标签一般分为块标签和行内标签两种类型，它们也称块元素和行内元素。

## 2. 块级元素(block-level)

- 例：

```
常见的块元素有<h1>~<h6>、<p>、<div>、<ul>、<ol>、<li>等，其中<div>标签是最典型的块元素。
```

- 案例

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>index</title>
</head>

<body>
    <h1>hello world</h1>
    <h2>hello world</h2>
    <h3>hello world</h3>
    <h4>hello world</h4>
    <h5>hello world</h5>
    <h6>hello world</h6>
    <div>hello world</div>
    <ul>hello world</ul>
    <li>hello world</li>
    <ol>hello world</ol>
</body>

</html>
```

![1572600231281](https://yulingimg.oss-cn-beijing.aliyuncs.com/img/20200426210739.png)

- 块级元素的特点

（1）比较霸道，自己独占一行

（2）高度，宽度、外边距以及内边距都可以控制。

（3）宽度默认是容器（父级宽度）的100%

（4）是一个容器及盒子，里面可以放行内或者块级元素。

- 注意：
  - 只有 文字才 能组成段落  因此 p  里面不能放块级元素，特别是 p 不能放div 
  - 同理还有这些标签h1,h2,h3,h4,h5,h6,dt，他们都是文字类块级标签，里面不能放其他块级元素。

## 3. 行内元素(inline-level)

- 例：

```
常见的行内元素有<a>、<strong>、<b>、<em>、<i>、<del>、<s>、<ins>、<u>、<span>等，其中<span>标签最典型的行内元素。有的地方也成内联元素
```

- 案例

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>index</title>
</head>

<body>
    <a href="#">hello world</a>
    <b>hello world</b>
    <s>hello world</s>
    <u>hello world</u>
    <strong>hello world</strong>
    <em>hello world</em>
    <del>hello world</del>
    <ins>hello world</ins>
    <span>hello world</span>
</body>

</html>
```

![1572600381002](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154429.png)

- 行内元素的特点：

（1）相邻行内元素在一行上，一行可以显示多个。

（2）高、宽直接设置是无效的。

（3）默认宽度就是它本身内容的宽度。

（4）**行内元素只能容纳文本或则其他行内元素。**

-  注意：

- 链接里面不能再放链接。
- 特殊情况a里面可以放块级元素，但是给a转换一下块级模式最安全。

## 4. 行内块元素（inline-block）

- 例：

```
在行内元素中有几个特殊的标签——<img />、<input />、<td>，可以对它们设置宽高和对齐属性，有些资料可能会称它们为行内块元素。
```

- 行内块元素的特点：

  （1）和相邻行内元素（行内块）在一行上,但是之间会有空白缝隙。一行可以显示多个
  （2）默认宽度就是它本身内容的宽度。
  （3）高度，行高、外边距以及内边距都可以控制。

  

## 5. 三种模式总结区别

| 元素模式   | 元素排列               | 设置样式               | 默认宽度         | 包含                     |
| ---------- | ---------------------- | ---------------------- | ---------------- | ------------------------ |
| 块级元素   | 一行只能放一个块级元素 | 可以设置宽度高度       | 容器的100%       | 容器级可以包含任何标签   |
| 行内元素   | 一行可以放多个行内元素 | 不可以直接设置宽度高度 | 它本身内容的宽度 | 容纳文本或则其他行内元素 |
| 行内块元素 | 一行放多个行内块元素   | 可以设置宽度和高度     | 它本身内容的宽度 |                          |

## 6. 标签显示模式转换 display

- 块转行内：display:inline;
- 行内转块：display:block;
- 块、行内元素转换为行内块： display: inline-block;