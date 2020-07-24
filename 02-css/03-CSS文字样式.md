# CSS字体样式

# 1.font字体

## 1.1 font-size:大小

- 作用：

  font-size属性用于设置字号

~~~css
p {  
    font-size:20px; 
}
~~~

- 单位：

  - 可以使用相对长度单位，也可以使用绝对长度单位。
  - 相对长度单位比较常用，推荐使用像素单位px，绝对长度单位使用较少。

| 相对长度单位     | 说明                           |
| ---------------- | ------------------------------ |
| em               | 相对于当前对象内文本的字体尺寸 |
| px               | 像素（推荐使用）               |
| **绝对长度单位** | **说明**                       |
| in               | 英寸                           |
| cm               | 毫米                           |
| mm               | 厘米                           |
| pt               | 点                             |

**注意：**

* 我们文字大小以后，基本就用px了，其他单位很少使用
* 谷歌浏览器默认的文字大小为16px
* 但是不同浏览器可能默认显示的字号大小不一致，我们尽量给一个明确值大小，不要默认大小。一般给body指定整个页面文字的大小

## 1.2 font-family:字体

- 作用：

  font-family属性用于设置哪一种字体。

~~~
p{ font-family:"微软雅黑";}
~~~

- 网页中常用的字体有宋体、微软雅黑、黑体等，例如将网页中所有段落文本的字体设置为微软雅黑
- 可以同时指定多个字体，中间以逗号隔开，表示如果浏览器不支持第一个字体，则会尝试下一个，直到找到合适的字体， 如果都没有，则以我们电脑默认的字体为准。

~~~
p{font-family: Arial,"Microsoft Yahei", "微软雅黑";}
~~~

> 常用技巧：

```
1. 各种字体之间必须使用英文状态下的逗号隔开。
2. 中文字体需要加英文状态下的引号，英文字体一般不需要加引号。当需要设置英文字体时，英文字体名必须位于中文字体名之前。
3. 如果字体名中包含空格、#、$等符号，则该字体必须加英文状态下的单引号或双引号，例如font-family: "Times New Roman";。
4. 尽量使用系统默认字体，保证在任何用户的浏览器中都能正确显示。
```

## 1.3 CSS Unicode字体

- 为什么使用 Unicode字体

  - 在 CSS 中设置字体名称，直接写中文是可以的。但是在文件编码（GB2312、UTF-8 等）不匹配时会产生乱码的错误。
  - xp 系统不支持 类似微软雅黑的中文。

- 解决：

  - 方案一： 你可以使用英文来替代。 比如` font-family:"Microsoft Yahei"`。

  - 方案二： 在 CSS 直接使用 Unicode 编码来写字体名称可以避免这些错误。使用 Unicode 写中文字体名称，浏览器是可以正确的解析的。

    ~~~
    font-family: "\5FAE\8F6F\96C5\9ED1";   表示设置字体为“微软雅黑”。
    ~~~

| 字体名称      | 英文名称            | Unicode 编码           |
| --------- | --------------- | -------------------- |
| 宋体        | SimSun          | \5B8B\4F53           |
| 新宋体       | NSimSun         | \65B0\5B8B\4F53      |
| 黑体        | SimHei          | \9ED1\4F53           |
| 微软雅黑      | Microsoft YaHei | \5FAE\8F6F\96C5\9ED1 |
| 楷体_GB2312 | KaiTi_GB2312    | \6977\4F53_GB2312    |
| 隶书        | LiSu            | \96B6\4E66           |
| 幼园        | YouYuan         | \5E7C\5706           |
| 华文细黑      | STXihei         | \534E\6587\7EC6\9ED1 |
| 细明体       | MingLiU         | \7EC6\660E\4F53      |
| 新细明体      | PMingLiU        | \65B0\7EC6\660E\4F53 |

为了照顾不同电脑的字体安装问题，我们尽量只使用宋体和微软雅黑中文字体

## 1.4 font-weight:字体粗细

- 在html中如何将字体加粗我们可以用标签来实现
  - 使用 b  和 strong 标签是文本加粗。
- 可以使用CSS 来实现，但是CSS 是没有语义的。

| 属性值  | 描述                                                      |
| ------- | :-------------------------------------------------------- |
| normal  | 默认值（不加粗的）                                        |
| bold    | 定义粗体（加粗的）                                        |
| 100~900 | 400 等同于 normal，而 700 等同于 bold  我们重点记住这句话 |

提倡：

  我们平时更喜欢用数字来表示加粗和不加粗。

## 1.5 font-style:字体风格

- 在html中如何将字体倾斜我们可以用标签来实现
  - 字体倾斜除了用 i  和 em 标签，
- 可以使用CSS 来实现，但是CSS 是没有语义的

font-style属性用于定义字体风格，如设置斜体、倾斜或正常字体，其可用属性值如下：

| 属性   | 作用                                                    |
| ------ | :------------------------------------------------------ |
| normal | 默认值，浏览器会显示标准的字体样式  font-style: normal; |
| italic | 浏览器会显示斜体的字体样式。                            |

小技巧： 

```
平时我们很少给文字加斜体，反而喜欢给斜体标签（em，i）改为普通模式。
```

## 1.6 font:综合设置字体样式 (重点)

font属性用于对字体样式进行综合设置

- 基本语法格式如下：

```css
选择器 { font: font-style  font-weight  font-size/line-height  font-family;}
```

- 注意：
  - 使用font属性时，必须按上面语法格式中的顺序书写，不能更换顺序，各个属性以**空格**隔开。
  - 其中不需要设置的属性可以省略（取默认值），但必须保留font-size和font-family属性，否则font属性将不起作用。

## 1.7 font总结
| 属性                          |      表示      |      注意点      |
| :---------------------------- | :-------------  | :------------- |
| font-size     | 字号 |我们通常用的单位是px 像素，一定要跟上单位|
| font-family     |    字体    |实际工作中按照团队约定来写字体|
| font-weight |  字体粗细 |记住加粗是 700 或者 bold  不加粗 是 normal 或者  400  记住数字不要跟单位|
| font-style | 字体样式 |记住倾斜是 italic     不倾斜 是 normal  工作中我们最常用 normal|
| font | 字体连写 |1. 字体连写是有顺序的  不能随意换位置 2. 其中字号 和 字体 必须同时出现|

## 1.8 案例

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
    #txt {
        font-size: 20px;
        font-family: 'Courier New', Courier, monospace;
        font-weight: bold;
        font-style: italic;
    }
</style>

<body>
    <div id="txt">你好，世界</div>
    <div>你好，世界</div>
</body>

</html>
```



![1572598222790](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723163125.png)



# 2. CSS外观属性

## 2.1 color:文本颜色

- 作用：

  color属性用于定义文本的颜色，

- 其取值方式有如下3种：

| 表示表示       | 属性值                                  |
| :------------- | :-------------------------------------- |
| 预定义的颜色值 | red，green，blue，还有我们的御用色 pink |
| 十六进制       | #FF0000，#FF6600，#29D794               |
| RGB代码        | rgb(255,0,0)或rgb(100%,0%,0%)           |

- 注意

  我们实际工作中， 用 16进制的写法是最多的，而且我们更喜欢简写方式比如  #f00 代表红色

## 2.2 text-align:文本水平对齐方式

- 作用：

  text-align属性用于设置文本内容的水平对齐，相当于html中的align对齐属性

- 其可用属性值如下：

| 属性   |       解释       |
| ------ | :--------------: |
| left   | 左对齐（默认值） |
| right  |      右对齐      |
| center |     居中对齐     |

- 注意：

  是让盒子里面的内容水平居中， 而不是让盒子居中对齐

## 2.3 line-height:行间距

- 作用：

  line-height属性用于设置行间距，就是行与行之间的距离，即字符的垂直间距，一般称为行高。

- 单位：

  - line-height常用的属性值单位有三种，分别为像素px，相对值em和百分比%，实际工作中使用最多的是像素px

- 技巧：

```
一般情况下，行距比字号大7.8像素左右就可以了。
line-height: 24px;
```

## 2.4 text-indent:首行缩进

- 作用：

  text-indent属性用于设置首行文本的缩进，

- 属性值

  - 其属性值可为不同单位的数值、em字符宽度的倍数、或相对于浏览器窗口宽度的百分比%，允许使用负值,
  - 建议使用em作为设置单位。

**1em 就是一个字的宽度   如果是汉字的段落， 1em 就是一个汉字的宽度**

~~~css
p {
      /*行间距*/
      line-height: 25px;
      /*首行缩进2个字  em  1个em 就是1个字的大小*/
      text-indent: 2em;  
 }
~~~

## 2.5 text-decoration 文本的装饰

text-decoration   通常我们用于给链接修改装饰效果

| 值           | 描述                                                  |
| ------------ | ----------------------------------------------------- |
| none         | 默认。定义标准的文本。 取消下划线（最常用）           |
| underline    | 定义文本下的一条线。下划线 也是我们链接自带的（常用） |
| overline     | 定义文本上的一条线。（不用）                          |
| line-through | 定义穿过文本下的一条线。（不常用）                    |

## 2.6 CSS外观属性总结

| 属性                          |      表示      |      注意点      |
| :---------------------------- | :-------------  | :------------- |
| color | 颜色 |我们通常用  十六进制   比如 而且是简写形式 #fff|
| line-height |    行高    |控制行与行之间的距离|
| text-align | 水平对齐 |可以设定文字水平的对齐方式|
| text-indent | 首行缩进 |通常我们用于段落首行缩进2个字的距离   text-indent: 2em;|
| text-decoration | 文本修饰 |记住 添加 下划线  underline  取消下划线  none|

## 2.7 案例

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
    .txt1 {
       color: pink;
       line-height: 30px;
       text-align: center;
       text-indent: 20px;
       text-decoration: underline;
    }
    .txt3 {   
       text-indent: 20px;
    }
</style>

<body>
    <div class="txt1">你好，世界</div>
    <div class="txt2">你好，世界</div>
    <div class="txt3">你好，世界</div>
</body>

</html>
```

![1572598549043](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723163212.png)

```

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
       body {
           font: 16px/28px 'Microsoft YaHei';
       }
       h1 {
        /* 文字不加粗 */
           font-weight: 400; 
           /* 让h1里面的文字水平居中对齐 */
           text-align: center;
       }
       a {
           text-decoration: none;
       }
       .gray {
           color: #888888;
           font-size: 12px;
           text-align: center;
       }
       .search {
           color: #666;
           /* #666666     #666
           #ff00ff    #f0f */
           width: 170px;
       }
       .btn {
           font-weight: 700;
       }
       p {
           /* 首行缩进2个字的距离 */
           text-indent: 2em;
       }
       .pic {
           /* 想要图片居中对齐,则是让它的父亲 p标签添加 水平居中的代码 */
           text-align: center;
       }
       .footer {
           color: #888888;
           font-size: 12px;
       }
    </style>
</head>
<body>
       <h1> 北方高温明日达鼎盛 京津冀多地地表温度将超60℃</h1>
       <div class="gray"> 2019-07-03 16:31:47 来源: <a href="#">中国天气网</a>　 
        <input type="text" value="请输入查询条件..." class="search">  <button class="btn">搜索</button>
    </div>
        <hr> 
        <p>中国天气网讯 今天（3日），华北、黄淮多地出现高温天气，截至下午2点，北京、天津、郑州等地气温突破35℃。预报显示，今后三天（3-5日），这一带的高温天气将继续发酵，高温范围以及强度将在4日达到鼎盛，预计北京、天津、石家庄、济南等地明天的最高气温有望突破38℃，其中北京和石家庄的最高气温还有望创今年以来的新高。</p>
        
        <h4>气温41.4℃！地温66.5！北京强势迎七月首个高温日</h4>
        <p class="pic">
            <img src="images/pic.jpeg" alt="">
        </p>
        <p>今天，华北、黄淮一带的高温持续发酵，截至今天下午2点，陕西北部、山西西南部、河北南部、北京、天津、山东西部、河南北部最高气温已普遍超过35℃。大城市中，北京、天津、郑州均迎来高温日。</p>
        
        
        
        <p>在阳光暴晒下，地表温度也逐渐走高。今天下午2点，华北黄淮大部地区的地表温度都在50℃以上，部分地区地表温度甚至超过60℃。其中，河北衡水地表温度高达68.3℃，天津站和北京站附近的地表温度分别高达66.6℃和66.5℃。</p>
        
        <h4>明日热度再升级！京津冀携手冲击38℃+</h4>
        <p>中国天气网气象分析师王伟跃介绍，明天（4日），华北、黄淮地区35℃以上的高温天气还将继续升级，并进入鼎盛阶段，高温强度和范围都将发展到最强。 明天，北京南部、天津大部、河北中部和南部、山东中部和西部、山西南部局地、河南北部、东北部分地区的最高气温都将达到或超过35℃。</p>
        
       <p> 不过，专家提醒，济南被雨水天气完美绕开，因此未来一周，当地的高温还会天天上岗。在此提醒当地居民注意防暑降温，防范持续高温带来的各种不利影响。（文/张慧 数据支持/王伟跃 胡啸 审核/刘文静 张方丽）</p>
        
       <p class="footer"> 本文来源：中国天气网 责任编辑：刘京_NO5631</p>
</body>
</html>
```

![image-20200724145334359](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200724145336.png)