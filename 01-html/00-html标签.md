# HTML学习笔记

## 1. HTML基础

### 1.1 什么是HTML?

HTML 是用来描述网页的一种语言。

*   HTML 指的是超文本标记语言: **H**yper**T**ext **M**arkup **L**anguage
*   HTML 不是一种编程语言，而是一种**标记**语言 (markup language)
*   标记语言是一套**标记标签** (markup tag)
*   HTML 使用标记标签来**描述**网页
*   HTML 文档包含了HTML **标签**及**文本**内容
*   HTML文档也叫做 **web 页面**
*   “超文本”就是指页面内可以包含图片、链接，甚至音乐、程序等非文字元素
*   HTML文件后缀为.html或者.htm（推荐使用.html）

### 1.2 基本骨架

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
	</body>
</html>

```

#### 解析

* **`<!DOCTYPE html>`** 声明为 HTML5 文档。<!DOCTYPE>位于文档的最前面，用于向浏览器说明当前.html文件使用的是哪种HTML或者XHTML标准规范。浏览器会按照此处指定的规范对html文件进行解析。

  HTML5可以向下兼容，所以，现在直接指定为`<!DOCTYPE html>`即可。

* **`<html>`** 元素是 HTML 页面的根元素

* **`<head>`** 元素包含了文档的元（meta）数据，如 `<meta charset="utf-8"> `定义网页编码格式为 **utf\-8**。

* **`<title>`** 元素描述了文档的标题

* **`<body>`** 元素包含了可见的页面内容

* charset（字符编码集）

  *   GB2312：简体中文字符集，含6763个常用汉字
  *   BIG5：繁体中文，港澳台地区使用
  *   GBK：含全部中文字符，是对GB2312的扩展，支持繁体字
  *   UTF\-8：支持中文和英文等，是最常用的字符集

## 2. HTML标签

HTML 标记标签通常被称为 HTML 标签 (HTML tag)。

*   HTML 标签是由*尖括号*包围的关键词，比如 `<html>`
*   HTML 标签通常是*成对出现*的，比如` <p> `和` </p>`
*   HTML标签也有单个出现的，比如`<br>` 
*   标签对中的第一个标签是*开始标签*，第二个标签是*结束标签*
*   开始和结束标签也被称为`开放标签`和`闭合标签`

### 2.1 标题标签

`<h1> - <h6>` 标签可定义标题。`<h1>` 定义最大的标题。`<h6> `定义最小的标题。

```html
	<h1>这是一级标题</h1>
	<h2>这是二级标题</h2>
	<h3>这是三级标题</h3>
	<h4>这是四级标题</h4>
	<h5>这是五级标题</h5>
	<h6>这是六级标题</h6>
```

![1565877295932](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723153815.png)

### 2.2 p标签

*   p 即 paragraph 的简写
*   p标签用于定义段落
*   段落中的文本内容超出浏览器宽度之后会执行自动换行
*   基本格式

```html
		<p>这是一个段落</p>
```

### 2.3 img标签

在 HTML 中，图像由`<img> `标签定义。

`<img>` 是空标签，意思是说，它只包含属性，并且没有闭合标签。

要在页面上显示图像，你需要使用源属性（src）。src 指 "source"。源属性的值是图像的 URL 地址。​	

浏览器将图像显示在文档中图像标签出现的地方。如果你将图像标签置于两个段落之间，那么浏览器会首先显示第一个段落，然后显示图片，最后显示第二段。

```html
<img src="图片路径" alt="">
```

常用属性

| 属性   | 属性值                               | 属性含义                     |
| ------ | ------------------------------------ | ---------------------------- |
| src    | URI/URL                              | 图像的路径                   |
| alt    | 文本                                 | 图像无法正常显示时的提示文本 |
| title  | 文本                                 | 鼠标悬停于图像时显示的文本   |
| width  | 像素（XHTML 不支持按页面百分比显示） | 图像的宽度                   |
| height | 像素（XHTML 不支持按页面百分比显示） | 图像的高度                   |
| border | 数字                                 | 设置图像边框的宽度           |

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
		<img src="https://www.runoob.com/images/pulpit.jpg" alt="图片" title="这是一张图片">
	</body>
</html>

```

![image-20200723154111775](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154113.png)

### 2.4 超链接标签

* anchor 的缩写

* 基本格式 `<a href="跳转目标url" target="目标窗口的弹出方式">超链接文本或图像</a>`
  *   href 即 HyperText Reference , 指定要跳转的URL地址
  *   target , 指定目标窗口的打开方式。取值为 self / blank , self 为默认值，blank 表示新窗口打开

*   `<a> `标签定义超链接，用于从一个页面链接到另一个页面

*   `<a> `元素最重要的属性是 href 属性，它指定链接的目标

*   在所有浏览器中，链接的默认外观如下：

    *   未被访问的链接带有下划线而且是蓝色的
    *   已被访问的链接带有下划线而且是紫色的
    *   活动链接带有下划线而且是红色的

注意：

> *   外链需要添加 http:// 或 https:// 前缀
> *   内部链接 直接链接内部页面名称即可，如 `<a href="index.html">首页</a>`
> *   如果当时没有确定链接目标时，可以为 href 赋值 为 “#” ,即 `href="#"`,表示一个空连接
> *   各种网页元素，如 文本、图像、表格、音频、视频等都可以作为超链接的载体
> *   如果没有使用 href 属性，则不能使用 hreflang、media、rel、target 以及 type 属性
> *   通常在当前浏览器窗口中显示被链接页面，除非规定了其他 target

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
	</head>
	<body>
			<a href="#"></a>
			<a href="https://www.baidu.com/">百度</a>
			<a href="index.html">跳转到index.html页面</a>
	</body>
</html>

```

![image-20200723154030865](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154032.png)

### 2.5 列表标签

#### 2.5.1 有序列表

- 有序列表是一列项目，默认状态下，列表项目使用数字进行标记。

- 有序列表始于` <ol>` 标签。每个列表项始于` <li> `标签。

- 使用type样式来定义列表前的标记样式。  
- 默认以1. 2.3. ··· 进行排列

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
   <ol>
	   <li>有序列表1</li>
	   <li>有序列表2</li>
	   <li>有序列表3</li>
	   <li>有序列表4</li>
	   <li>有序列表5</li>
   </ol>
</body>
</html>
```

![1565940141510](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723153922.png)



#### 2.5.2 无序列表

- 所谓无序列表就是以小圆点或者小方块作为行首标志的列表
- 无序列表的各项之间是并列的，没有顺序级别的区分

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
   <ul>
	   <li>无序列表1</li>
	   <li>无序列表2</li>
	   <li>无序列表3</li>
	   <li>无序列表4</li>
	   <li>无序列表5</li>
   </ul>
</body>
</html>
```

![1565940376705](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154125.png)

注意：

- <ul></ul> 之间只能嵌套 <li></li>,不允许嵌套其他标签
- **`<li></li> `之间相当于一个容器，可以嵌套任意标签**

#### 2.5.3 自定义列表

- <dl></dl>为外层标签、<dt></dt>为内层标签、<dt> 下还可以嵌套 <dd></dd>
- 自定义列表项前不具有任何项目符号，既没有小圆点也没有1234

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
   <dl>
        <dt>自定义列表项1</dt>
            <dd>内容1</dd>
            <dd>内容2</dd>
        <dt>自定义列表项2</dt>
            <dd>内容解释1</dd>
            <dd>内容解释2</dd>
    </dl>
</body>
</html>
```

![1565940551124](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154133.png)

### 2.6 表格标签

* `<table></table> `用来定义表格

* `<tr></tr> `用来定义行，嵌套在 `<table></table> `中

* `<td></td> `用来定义行中的单元格，嵌套在` <tr></tr>` 中

* `<th></th> `用来定义行中的单元格，嵌套在` <tr></tr>` 中

* `<tr></tr>` 中只能嵌套`<td></td>` , 但` <td></td>` 相当于一个容器，可以嵌套任意元素

* `<thead></thead>` 标签定义表格的表头。该标签用于组合 HTML 表格的表头内容

* `<tbody></tbody> `元素用于对 HTML 表格中的主体内容进行分组

*  `<tfoot></tfoot>`元素用于对 HTML 表格中的表注（页脚）内容进行分组


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
   <table border="1">
	   <thead>
		   <tr>
			   <th>表头一</th>
			   <th>表头二</th>
			   <th>表头三</th>
		   </tr>
	   </thead>
	    <tfoot>
	   			<tr>
	   				<td>页脚一</td>
	   				<td>页脚一</td>
	   				<td>页脚三</td>
	   			</tr>
	   </tfoot>
	   <tbody>
		   <tr>
				<td>内容一</td>
				<td>内容一</td>
				<td>表头三</td>
		   </tr>
	   </tbody>
	  
   </table>
</body>
</html>
```

![1566030249159](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154139.png)

常用属性：

| 属性名称    | 含义                                                 | 属性取值              |
| ----------- | ---------------------------------------------------- | --------------------- |
| border      | 表格的边框。默认 border="0",即无边框                 | 像素值                |
| cellspacing | 单元格与单元格边框之间的间距。  默认 cellspacing="2" | 像素值                |
| cellpadding | 单元格内容与单元格边框的间距。  默认 cellpadding="1" | 像素值                |
| width       | 表格的宽度                                           | 像素值                |
| height      | 表格的高度                                           | 像素值                |
| align       | 表格在页面中的水平对齐方式                           | left 、center 、right |
| caption     | 标题                                                 | 文本                  |
| colspan     | 从当前列向后 横跨几列, 应用于td、th                  | 数字                  |
| rowspan     | 从当前行向下 竖跨几行, 应用于td、th                  | 数字                  |

单元格合并：

- 适用于 `<td></td>`、`<th></th>`

- colspan 跨列合并（水平合并）

- rowspan 跨行合并（垂直合并）

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
     <table border="1">
  	   <thead>
  		   <tr>
  			   <th>表头一</th>
  			   <th>表头二</th>
  			   <th colspan="2">向右合并两列</th>
  		   </tr>
  	   </thead>
  	    <tfoot>
  	   			<tr>
  	   				<td>页脚一</td>
  	   				<td>页脚一</td>
  	   				<td>页脚三</td>
  					<td>页脚四</td>
  	   			</tr>
  	   </tfoot>
  	   <tbody>
  		   <tr>
  				<td>内容一</td>
  				<td>内容二</td>
  				<td>表头三</td>
  				<td rowspan="3">向下合并三排</td>
  		   </tr>
  		    <tr>
  		   		<td>内容一</td>
  		   		<td>内容一</td>
  		   		<td>表头三</td>
  		   </tr>
  		    <tr>
  		   		<td>内容一</td>
  		   		<td>内容一</td>
  		   		<td>表头三</td>
  		   </tr>
  	   </tbody>
  	  
     </table>
  </body>
  </html>
  ```




注意：

- thead 元素应该与 tbody 和 tfoot 元素结合起来使用
- 它们的出现次序是：thead、tfoot、tbody
- 必须在 table 元素内部使用这些标签,，在默认情况下这些元素不会影响到表格的布局

### 2.7 表单标签

- <form> 标签用于为用户输入创建 HTML 表单。

- 表单能够包含 input 元素，比如文本字段、复选框、单选框、提交按钮等等。


- 表单还可以包含 menus、textarea、fieldset、legend 和 label 元素。


- 表单用于向服务器传输数据。

![1566032318108](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154146.png)

#### 2.7.1  input标签

- input 为单标签（自闭合标签）
- type 是其基本属性，用来控制输入的类型

| 属性      | 取值     | 含义                                   |
| --------- | -------- | -------------------------------------- |
| type      | text     | **单行**文本输入框（不换行的）         |
| type      | password | 密码输入框                             |
| type      | radio    | 单选框（配合name 可以实现单选效果）    |
| type      | checkbox | 复选框                                 |
| type      | button   | 普通按钮                               |
| type      | submit   | 提交按钮                               |
| type      | reset    | 重置按钮                               |
| type      | image    | 图像形式的提交按钮                     |
| type      | file     | 文件域, 点击之后打开文件选择器         |
| name      | 任意文本 | 控件名称 , name 相同则表示是同一组数据 |
| value     | 任意文本 | 默认文本值                             |
| size      | 正整数   | 显示大小                               |
| checked   | checked  | 默认是否被选中                         |
| maxlength | 正整数   | 控制输入的最大字符数量                 |

注意：

> 多个 radio 使用相同的 name ，则表示这是一组数据，这样可以实现单选效果。如果不加 name 多个 radio 可同时被选中

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
	<form action="">
		<input type="text" value="请输入文本">
		<br>
		<input type="password" value="请输入密码">
		<br>
		<input type="radio" name="1" checked="checked">篮球
		<input type="radio" name="1">足球
		<input type="radio" name="1">排球
		<br>
		<input type="checkbox" checked="checked">篮球
		<input type="checkbox">足球
		<input type="checkbox" checked="checked">排球
		<input type="checkbox">乒乓球
		<br>
		<input type="button" value="这是一个普通按钮">
		<br>
		<input type="reset" value="重置按钮">
		<br>
		<input type="submit" value="提交按钮">
		<br>
		<input type="image" src="图片路径" value="图像形式的提交按钮">
		<br>
		<input type="file">
	</form>
 
</body>
</html>
```

![1566032597474](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154203.png)

#### 2.7.2 label标签

- label 标签为 input 标签定义标注/标签
- 用来绑定一个表单元素，当点击 label 标签的时候，被绑定的 表单元素就会获取焦点
- 通过 for 属性，可以绑定 label 和 input ; 或者直接用lable 标签将input 包裹起来



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <!--label 中直接包裹 input,可以实现绑定-->
    <label>点击此处文本，用户名输入框会获取焦点 <br> 用户名：<input type="text"/></label>
    <br/>

    <hr/>
    <!--使用 label 的 for 属性绑定input-->
    <label for="#two">点击此处文本，密码输入框会获取焦点</label>
    <br/>
    用户名：<input type="text"/>
    <br/>
    密　码：<input type="text" id="#two"/>
</body>
</html>
```

#### 2.7.3 textarea 文本域标签

- `<textarea></textarea>`用来做大量文本的输入，支持多行
- 有 cols 、rows 属性。cols 限制每行中所输入的文本字数，rows 限制最大行数。（这两个属性通常不被使用，更多使用会使用CSS样式做相关控制）

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    请输入评论内容：
    <br/>
    <textarea placeholder="请输入评论内容"></textarea>
</body>
</html>
```

![1566133651389](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154210.png)

#### 2.7.4 下拉菜单`<select></select>`

- `<select></select> `用来定义下拉菜单
- `<option></option>` 用来定义下拉菜单选项
- `<select></select>` 中至少包含一对` <option></option>`
- 在 option 中定义了属性 selected="selected" 之后，表示该项被默认选中

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title></title>
</head>
<body>
    出生日期
    <select >
		<option>年</option>
        <option selected="selected">2000</option>
        <option>2001</option>
        <option>2002</option>
        <option>2003</option>
        <option>2004</option>
    </select>
    <select>
		<option>月</option>
        <option>01</option>
        <option selected="selected">02</option>
        <option>03</option>
        <option>04</option>
        <option>05</option>
    </select>
	<select>
		<option>日</option>
	    <option>01</option>
	    <option>02</option>
	    <option>03</option>
	    <option>04</option>
	    <option selected="selected">05</option>
	</select>
</body>
</html>
```

![1566133998811](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154233.png)

#### 2.7.5 form表单域

该标签用来定义表单域，以实现用户信息的收集和传递，form 中的内容通常都会被提交到服务器。

```html
 <form action="url地址" method="提交方式" name="表单名称">
     ...各种表单控件...
 </form>
```

| 属性           | 值                                | 描述                                     |
| -------------- | --------------------------------- | ---------------------------------------- |
| accept-charset | *charset_list*                    | 规定服务器可处理的表单数据字符集。       |
| action         | URL                               | 规定当提交表单时向何处发送表单数据。     |
| autocomplete   | onoff                             | 规定是否启用表单的自动完成功能。         |
| enctype        | 见说明                            | 规定在发送表单数据之前如何对其进行编码。 |
| method         | getpost                           | 规定用于发送 form-data 的 HTTP 方法。    |
| name           | form_name                         | 规定表单的名称。                         |
| novalidate     | novalidate                        | 如果使用该属性，则提交表单时不进行验证。 |
| target         | _blank_self_parent_top*framename* | 规定在何处打开 action URL。              |

- 每个表单都应该有自己的表单域

- 使用form 包裹之后点击提交按钮才有提交的动作

### 2.8  容器盒子标签

盒模型

#### 2.8.1 span标签

- `<span>` 用于对文档中的行内元素进行组合。

- `<span> `标签没有固定的格式表现。当对它应用样式时，它才会产生视觉上的变化。如果不对` <span> `应用样式，那么` <span> `元素中的文本与其他文本不会任何视觉上的差异。

- `<span> `标签提供了一种将文本的一部分或者文档的一部分独立出来的方式。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title></title>
</head>
<body>
  <p>我的母亲有 <span style="color:blue">蓝色</span> 的眼睛。</p>
</body>
</html>
```



![1566137153361](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154315.png)

#### 2.8.2 div标签

- 可定义文档中的分区或节（division/section）
- 可以把文档分割为独立的、不同的部分

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title></title>
</head>
<body>
  <div style="color:#0000FF;border:1px #FFC0CB solid;">
  <h3>这是一个在 div 元素中的标题。</h3>
  <p>这是一个在 div 元素中的文本。</p>
</div>
</body>
</html>
```



![1566137048800](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154321.png)



### 2.9 文本格式化标签

| 标签                           | 效果                          |
| ------------------------------ | ----------------------------- |
| `<b></b>`、`<strong></strong>` | 加粗，XHTML推荐使用`<strong>` |
| `<i></i>`、`<em></em>`         | 斜体，XHTML推荐使用`<em>`     |
| `<s></s>`、`<del></del>`       | 删除线，XHTML推荐使用`<del>`  |
| `<u></u>`、`<ins></ins>`       | 下划线，XHTML推荐使用`<ins>`  |



### 2.10 锚点

在同一个页面可以通过锚点进行跳转

*   通过创建锚点，可以快速定位到目标内容区域
*   创建锚点分为两步
    *   为目标内容（即锚点）创建id 并赋值
    *   将超链接文本与锚点的id 关联，`<a href="#id名称"> 超链接文本 </a>`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <a href="#createAnchor1">点击跳转到锚点位置1</a>
	<a href="#createAnchor2">点击跳转到锚点位置2</a>
	<a href="#createAnchor3">点击跳转到锚点位置3</a>
    <br/>
    
	<div style="height:1000px;background-color:red">
		<p id="createAnchor1">锚点位置1</p>
		<a href="#createAnchor1">点击跳转到锚点位置1</a>
		<a href="#createAnchor2">点击跳转到锚点位置2</a>
		<a href="#createAnchor3">点击跳转到锚点位置3</a>
	</div>
	<div style="height:1000px;background-color:green">
		<p id="createAnchor2">锚点位置2</p>
		<a href="#createAnchor1">点击跳转到锚点位置1</a>
		<a href="#createAnchor2">点击跳转到锚点位置2</a>
		<a href="#createAnchor3">点击跳转到锚点位置3</a>
	</div>
	<div style="height:1000px;background-color:blue">
		<p id="createAnchor3">锚点位置3</p>
		<a href="#createAnchor1">点击跳转到锚点位置1</a>
		<a href="#createAnchor2">点击跳转到锚点位置2</a>
		<a href="#createAnchor3">点击跳转到锚点位置3</a>
	</div>
   
</body>
</html>
```





### 2.11 常见转义字符

| 显示 | 说明           | 实体名称       | 实体编号  |
| ---- | -------------- | -------------- | --------- |
|      | 半方大的空白   | `&ensp;`&ensp; | `&#8194;` |
|      | 全方大的空白   | `&emsp;`       | `&#8195;` |
|      | 不断行的空白格 | `&nbsp;`       | `&#160;`  |
| <    | 小于           | `&lt;`         | `&#60;`   |
| >    | 大于           | `&gt;`         | `&#62;`   |
| &    | &符号          | `&amp;`        | `&#38;`   |
| "    | 双引号         | `&quot;`       | `&#34;`   |
| ©    | 版权           | `&copy;`       | `&#169;`  |
| ®    | 已注册商标     | `&reg;`        | `&#174;`  |
| ™    | 商标（美国）   | `™`            | `&#8482;` |
| ×    | 乘号           | `&times;`      | `&#215;`  |
| ÷    | 除号           | `&divide;`     | `&#247;`  |



## 3.属性

*   基本格式：`<标签名 属性1=”属性值1“ 属性2=”属性值2“></标签名>`
*   标签可以拥有多个属性
*   属性必须写在开始标签中，位于标签名后面
*   属性之间不区分顺序
*   标签名与属性、属性与属性之间使用空格隔开
*   任何属性都有默认值，省略该属性表示使用默认值



| 属性            | 描述                                                   |
| --------------- | ------------------------------------------------------ |
| accesskey       | 规定激活元素的快捷键。                                 |
| class           | 规定元素的一个或多个类名（引用样式表中的类）。         |
| contenteditable | 规定元素内容是否可编辑。                               |
| contextmenu     | 规定元素的上下文菜单。上下文菜单在用户点击元素时显示。 |
| data-*          | 用于存储页面或应用程序的私有定制数据。                 |
| dir             | 规定元素中内容的文本方向。                             |
| draggable       | 规定元素是否可拖动。                                   |
| dropzone        | 规定在拖动被拖动数据时是否进行复制、移动或链接。       |
| hidden          | 规定元素仍未或不再相关。                               |
| id              | 规定元素的唯一 id。                                    |
| lang            | 规定元素内容的语言。                                   |
| spellcheck      | 规定是否对元素进行拼写和语法检查。                     |
| style           | 规定元素的行内 CSS 样式。                              |
| tabindex        | 规定元素的 tab 键次序。                                |
| title           | 规定有关元素的额外信息。                               |
| translate       | 规定是否应该翻译元素内容。                             |



