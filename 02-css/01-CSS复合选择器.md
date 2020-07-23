# CSS复合选择器

## 1. 后代选择器

- 概念：

  后代选择器又称为包含选择器

- 作用：

  用来选择元素或元素组的**子孙后代**

- 其写法就是把外层标签写在前面，内层标签写在后面，中间用**空格**分隔，先写父亲爷爷，在写儿子孙子。 

```
父级 子级{属性:属性值;属性:属性值;}
```

- 语法：

```
.class h3{color:red;font-size:16px;}
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
<style>
   .txt p {
       color: pink;
   }
</style>

<body>
    <div class="txt">
        <p>hello world</p>
    </div>
</body>

</html>
```



- 当标签发生嵌套时，内层标签就成为外层标签的后代。
- 子孙后代都可以这么选择。 或者说，它能选择任何包含在内 的标签。

## 2. 子元素选择器

- 作用：

  子元素选择器只能选择作为某元素**子元素(亲儿子)**的元素。

- 其写法就是把父级标签写在前面，子级标签写在后面，中间跟一个 `>` 进行连接

- 语法：

```
.class>h3{color:red;font-size:14px;}
```



> 这里的子 指的是 亲儿子  不包含孙子 重孙子之类。

白话：  

```
 比如：  .demo > h3 {color: red;}   说明  h3 一定是demo 亲儿子。  demo 元素包含着h3。
```

案例

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>index</title>
</head>
<style>
   .txt>h3 {
       color: pink;
   }
</style>

<body>
    <div class="txt">
        <h3>hello world</h3>
        <div class="txt1">
            <h3>hello world</h3>
            <div class="txt2"><h3>hello world</h3></div>
        </div>
    </div>
</body>

</html>
```



## 3. 交集选择器

- 条件

  交集选择器由两个选择器构成，找到的标签必须满足：既有标签一的特点，也有标签二的特点。


- 其中第一个为标签选择器，第二个为class选择器，两个选择器之间**不能有空格**，如h3.special。

**记忆技巧：**

交集选择器 是 并且的意思。  即...又...的意思

```
比如：   p.one   选择的是： 类名为 .one  的 段落标签。  
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
<style>
   div.txt {
       color: pink;
   }
</style>

<body>
    <div class="txt">hello world</div>
    <div class="txt1">hello world</div>
</body>

</html>
```

![1572599407947](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154841.png)



## 4. 并集选择器

- 应用：
  - 如果某些选择器定义的相同样式，就可以利用并集选择器，可以让代码更简洁。
- 并集选择器（CSS选择器分组）是各个选择器通过`,`连接而成的，通常用于集体声明。

- 任何形式的选择器（包括标签选择器、class类选择器id选择器等），都可以作为并集选择器的一部分。

- 记忆技巧：

  并集选择器通常用于集体声明  ，逗号隔开的，所有选择器都会执行后面样式，逗号可以理解为 和的意思。

```
比如  .one, p , #test {color: #F00;}  
表示   .one 和 p  和 #test 这三个选择器都会执行颜色为红色。 
通常用于集体声明。  
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
<style>
   .txt,h3 {
       color: pink;
   }
</style>

<body>
    <div class="txt">hello world</div>
    <h3>hello world</h3>
    <div class="txt1">hello world</div>
</body>

</html>
```

1. ![1572599503244](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154911.png)

## 5.  链接伪类选择器

 伪类选择器：

 为了和我们刚才学的类选择器相区别
类选择器是一个点 比如 .demo {}   
而我们的伪类 用 2个点 就是 冒号  比如  :link{}    伪娘 

作用：

用于向某些选择器添加特殊的效果。比如给链接添加特殊效果， 比如可以选择 第1个，第n个元素。

因为伪类选择器很多，比如链接伪类，结构伪类等等。我们这里先给大家讲解链接伪类选择器。

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
   a:link {
    color: pink;
   }
   a:visited {
       color: red;
   }
   a:hover {
       color: blueviolet;
   }
   a:active {
       color: chartreuse;
   }
</style>

<body>
    <a href="#">hello world</a>
</body>

</html>
```

- a:link      /* 未访问的链接 */
- a:visited   /* 已访问的链接 */
- a:hover     /* 鼠标移动到链接上 */
- a:active    /* 选定的链接 */

  **注意**

- 写的时候，他们的顺序尽量不要颠倒  按照  lvha 的顺序。否则可能引起错误。  
- 记忆法  
  - **l**o**v**e   **ha**te     爱上了讨厌    
  - **lv **包包   非常 **ha**o   
- 因为叫链接伪类，所以都是 利用交集选择器  a:link    a:hover  
- 因为a链接浏览器具有默认样式，所以我们实际工作中都需要给链接单独指定样式。
- 实际工作开发中，我们很少写全四个状态，一般我们写法如下：

```css
a {   /* a是标签选择器  所有的链接 */
			font-weight: 700;
			font-size: 16px;
			color: gray;
}
a:hover {   /* :hover 是链接伪类选择器 鼠标经过 */
			color: red; /*  鼠标经过的时候，由原来的 灰色 变成了红色 */
}
```

## 6. 复合选择器总结

| 选择器         | 作用                     | 特征                 | 使用情况 | 隔开符号及用法                          |
| -------------- | ------------------------ | -------------------- | -------- | --------------------------------------- |
| 后代选择器     | 用来选择元素后代         | 是选择所有的子孙后代 | 较多     | 符号是**空格** .nav a                   |
| 子代选择器     | 选择 最近一级元素        | 只选亲儿子           | 较少     | 符号是**>**   .nav>p                    |
| 交集选择器     | 选择两个标签交集的部分   | 既是 又是            | 较少     | **没有符号**  p.one                     |
| 并集选择器     | 选择某些相同样式的选择器 | 可以用于集体声明     | 较多     | 符号是**逗号** .nav, .header            |
| 链接伪类选择器 | 给链接更改状态           |                      | 较多     | 重点记住 a{} 和 a:hover  实际开发的写法 |