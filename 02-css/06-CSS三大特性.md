#  CSS 三大特性

## 1. CSS层叠性

- 概念：

  所谓层叠性是指多种CSS样式的叠加。

  是浏览器处理冲突的一个能力,如果一个属性通过两个相同选择器设置到同一个元素上，那么这个时候一个属性就会将另一个属性层叠掉

- 原则：

  - 样式冲突，遵循的原则是**就近原则。** 那个样式离着结构近，就执行那个样式。
  - 样式不冲突，不会层叠

```
CSS层叠性最后的执行口诀：  长江后浪推前浪，前浪死在沙滩上。
```

## 2. CSS继承性

- 概念：

  子标签会继承父标签的某些样式，如文本颜色和字号。

   想要设置一个可继承的属性，只需将它应用于父元素即可。

简单的理解就是：  子承父业。

- **注意**：
  - 恰当地使用继承可以简化代码，降低CSS样式的复杂性。比如有很多子级孩子都需要某个样式，可以给父级指定一个，这些孩子继承过来就好了。
  - 子元素可以继承父元素的样式（**text-，font-，line-这些元素开头的可以继承，以及color属性**）

```
CSS继承性口诀：  龙生龙，凤生凤，老鼠生的孩子会打洞。
```

## 3. CSS优先级

- 概念：

  定义CSS样式时，经常出现两个或更多规则应用在同一元素上，此时，

  - 选择器相同，则执行层叠性
  - 选择器不同，就会出现优先级的问题。

### 1. 权重计算公式

关于CSS权重，我们需要一套计算公式来去计算，这个就是 CSS Specificity（特殊性）

| 标签选择器             | 计算权重公式 |
| ---------------------- | ------------ |
| 继承或者 *             | 0,0,0,0      |
| 每个元素（标签选择器） | 0,0,0,1      |
| 每个类，伪类           | 0,0,1,0      |
| 每个ID                 | 0,1,0,0      |
| 每个行内样式 style=""  | 1,0,0,0      |
| 每个!important  重要的 | ∞ 无穷大     |

- 值从左到右，左面的最大，一级大于一级，数位之间没有进制，级别之间不可超越。 
- 关于CSS权重，我们需要一套计算公式来去计算，这个就是 CSS Specificity（特殊性）
- div {
  ​    color: pink!important;  
  }

### 2. 权重叠加

我们经常用交集选择器，后代选择器等，是有多个基础选择器组合而成，那么此时，就会出现权重叠加。

就是一个简单的加法计算

- div ul  li   ------>      0,0,0,3
- .nav ul li   ------>      0,0,1,2
- a:hover      -----—>   0,0,1,1
- .nav a       ------>      0,0,1,1

 注意： 

1. 数位之间没有进制 比如说： 0,0,0,5 + 0,0,0,5 =0,0,0,10 而不是 0,0, 1, 0， 所以不会存在10个div能赶上一个类选择器的情况。

### 3. 继承的权重是0

这个不难，但是忽略很容易绕晕。其实，我们修改样式，一定要看该标签有没有被选中。

1） 如果选中了，那么以上面的公式来计权重。谁大听谁的。 
2） 如果没有选中，那么权重是0，因为继承的权重为0.

**案例**

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>CSS权重练习</title>
    <style>
        .nav {
            color: red;
        }
        /* 继承的权重是0 */
        li {
            color: pink;
        }
    
    </style>
</head>
<body>
    
    <ul class="nav">
        <li>人生四大悲</li>
        <li>家里没宽带</li>
        <li>网速不够快</li>
        <li>手机没流量</li>
        <li>学校没wifi</li>
    </ul>
</body>
</html>
```

![image-20200724152709118](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200724152711.png)

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>CSS权重练习</title>
    <style>
        /* .nav li  权重是 11 */
        .nav li {
            color: red;
        }
        /* 需求把第一个小li 颜色改为 粉色加粗 ? */
        /* .pink  权重是 10    .nav .pink  20  */
       .nav .pink {
            color: pink;
            font-weight: 700;
        }
    </style>
</head>
<body>
    
    <ul class="nav">
        <li class="pink">人生四大悲</li>
        <li>家里没宽带</li>
        <li>网速不够快</li>
        <li>手机没流量</li>
        <li>学校没wifi</li>
    </ul>
</body>
</html>
```

![image-20200724152758364](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200724152800.png)