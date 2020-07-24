# CSS 背景(background)

## 1. 背景颜色(color)

- background-color 属性为元素设置一种纯色。这种颜色会填充元素的内容、内边距和边框区域，扩展到元素边框的外边界（但不包括外边距）。如果边框有透明部分（如虚线边框），会透过这些透明部分显示出背景色。

- 语法：

  ```
  background-color:颜色值;   默认的值是 transparent  透明的
  ```

- 属性值

  | 值          | 描述                               |
  | ----------- | ---------------------------------- |
  | *color*     | 指定背景颜色。                     |
  | transparent | 指定背景颜色应该是透明的。这是默认 |
  | inherit     | 指定背景颜色，应该从父元素继承     |

- color值

  | 值         | 描述                                                   |
  | ---------- | ------------------------------------------------------ |
  | color_name | 规定颜色值为颜色名称的背景颜色（比如 red）。           |
  | hex_number | 规定颜色值为十六进制值的背景颜色（比如 #ff0000）。     |
  | rgb_number | 规定颜色值为 rgb 代码的背景颜色（比如 rgb(255,0,0)）。 |

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
      .txt1 {
          width: 500px;
          height: 100px;
          background-color: red;
      }
      .txt2 {
          width: 500px;
          height: 100px;
          background-color: #00ff00;
      }
      .txt3 {
          width: 500px;
          height: 100px;
          background-color: rgb(0,0,255);
      }
  </style>
  <body>
    <div class="txt1"></div>
    <div class="txt2"></div>
    <div class="txt3"></div>
  </body>
  
  </html>
  ```

  ![1572854124441](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154947.png)

## 2. 背景图片(image)

- background-image 属性为元素设置背景图像。元素的背景占据了元素的全部尺寸，包括内边距和边框，但不包括外边距。默认地，背景图像位于元素的左上角，并在水平和垂直方向上重复。

- 语法： 

  ```html
  background-image : none | url (url) 
  ```

- 参数值

  | 参数 |              作用              |
  | ---- | :----------------------------: |
  | none |       无背景图（默认的）       |
  | url  | 使用绝对或相对地址指定背景图像 |

- 案例

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
      div[class^="txt"] {
          float: left;
      }
      .txt1 {
          width: 500px;
          height: 300px;
          background-image: url(test1.png);
      }
      .txt2 {
          width: 500px;
          height: 300px;
          background-image: url(test2.png);
      }
      .txt3 {
          width: 500px;
          height: 300px;
          background-image: url(test3.png);
      }
  </style>
  <body>
    <div class="txt1"></div>
    <div class="txt2"></div>
    <div class="txt3"></div>
  </body>
  
  </html>
  ```

  ![1572855225969](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723154953.png)

  小技巧：  我们提倡 背景图片后面的地址，url不要加引号。

## 3. 背景平铺（repeat）

- background-repeat 属性设置是否及如何重复背景图像。

  默认地，背景图像在水平和垂直方向上重复。

- 语法： 

```css
background-repeat : repeat | no-repeat | repeat-x | repeat-y 
```

- 参数值

  | 参数      | 作用                                 |
  | --------- | ------------------------------------ |
  | repeat    | 背景图像在纵向和横向上平铺（默认的） |
  | no-repeat | 背景图像不平铺                       |
  | repeat-x  | 背景图像在横向上平铺                 |
  | repeat-y  | 背景图像在纵向平铺                   |

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
      div[class^="txt"] {
          float: left;
          margin: 0 50px;
          border: 1px solid #cccccc;
      }
      /* 不平铺 */
      .txt1 {
          width: 200px;
          height: 200px;
          background-image: url(test3_1.jpg);
          background-repeat: no-repeat;
      }
      /* 平铺 */
      .txt2 {
          width: 200px;
          height: 200px;
          background-image: url(test3_1.jpg);
          background-repeat: repeat;
      }
      /* 沿X轴方向平铺 */
      .txt3 {
          width: 200px;
          height: 200px;
          background-image: url(test3_1.jpg);
          background-repeat: repeat-x;
      }
      /* 沿Y轴方向平铺 */
      .txt4 {
          width: 200px;
          height: 200px;
          background-image: url(test3_1.jpg);
          background-repeat: repeat-y;
      }
  </style>
  <body>
​    <div class="txt1"></div>
​    <div class="txt2"></div>
​    <div class="txt3"></div>
​    <div class="txt4"></div>
  </body>

  </html>
​```

  ```

![1572856185399](I:\桌面\前端笔记\02-css\upload\20200723155013.png)

## 4. 背景位置(position) 重点

- background-position 属性设置背景图像的起始位置。这个属性设置背景原图像的位置，背景图像如果要重复，将从这一点开始。

- 语法： 

  ```html
    background-position : length || length
  ```

  background-position : position || position 

   ```
  
   ```

- 参数

  | 参数     |                              值                              |
  | -------- | :----------------------------------------------------------: |
  | length   |         百分数 \| 由浮点数字和单位标识符组成的长度值         |
  | position | top \| center \| bottom \| left \| center \| right   方位名词 |

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
      div[class^="txt"] {
          float: left;
          margin: 0 50px;
          border: 1px solid #cccccc;
      }
      
      .txt1 {
          width: 200px;
          height: 200px;
          background-image: url(test3.jpg);
         background-position: 0 0;
      }
      
      .txt2 {
          width: 200px;
          height: 200px;
          background-image: url(test3.jpg);
          background-position: left top;
      }
      
      .txt3 {
          width: 200px;
          height: 200px;
          background-image: url(test3.jpg);
          background-position: 0% 0%;
      }
      
      .txt4 {
          width: 200px;
          height: 200px;
          background-image: url(test3.jpg);
          background-position: 30% 30%;
      }
  </style>
  <body>
    <div class="txt1"></div>
    <div class="txt2"></div>
    <div class="txt3"></div>
    <div class="txt4"></div>
  </body>
  
  </html>
  ```

  ![1572856631734](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723155206.png)

- 注意：

  - 必须先指定background-image属性
  - position 后面是x坐标和y坐标。 可以使用方位名词或者 精确单位。
  - 如果指定两个值，两个值都是方位名字，则两个值前后顺序无关，比如left  top和top  left效果一致
  - 如果只指定了一个方位名词，另一个值默认居中对齐。
  - 如果position 后面是精确坐标， 那么第一个，肯定是 x  第二的一定是y
  - 如果只指定一个数值,那该数值一定是x坐标，另一个默认垂直居中
  - 如果指定的两个值是 精确单位和方位名字混合使用，则第一个值是x坐标，第二个值是y坐标



## 5. 背景附着

- 背景附着就是解释背景是滚动的还是固定的

- 语法： 

  ```】
  background-attachment : scroll | fixed 
  ```

- 参数

  | 值      | 描述                                                    |
  | ------- | ------------------------------------------------------- |
  | scroll  | 默认值。背景图像会随着页面其余部分的滚动而移动。        |
  | fixed   | 当页面的其余部分滚动时，背景图像不会移动。              |
  | inherit | 规定应该从父元素继承 background-attachment 属性的设置。 |

- 案例

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>Document</title>
  </head>
  <body>
          <style type="text/css">
              body 
              {
              background-image:url(test3.jpg);
              background-repeat:no-repeat;
              background-attachment:scroll;
              }
              </style>
              
              <body>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              <p>图像会随页面的其余部分滚动。</p>
              </body>
  </body>
  </html>
  ```


## 6. 背景简写

- background：属性的值的书写顺序官方并没有强制标准的。

- background: 背景颜色 背景图片地址 背景平铺 背景滚动 背景位置;

- 语法：

  ```html
  background: transparent url(image.jpg) repeat-y  scroll center top ;
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
         div[class^="txt"] {
             float: left;
             margin: 0 50px;
             border: 1px solid #cccccc;
         }
         .txt1 {
            width: 200px;
         	 height: 200px;
            background: url(test3.jpg) no-repeat  scroll center top;  
         }
        .txt2 {
            width: 200px;
            height: 200px;
            background: url(test3.jpg) repeat  fixed 0 0;
        }
        .txt3 {
            width: 200px;
            height: 200px;
            background: url(test3.jpg) repeat-x  scroll 20% 20%; 
        }
        .txt4 {
            width: 200px;
            height: 200px;
            background: url(test3.jpg) repeat-y  inherit 20px 20px；
        }
      </style>
     <body
       <div class="txt1"></div>
       <div class="txt2"></div>
       <div class="txt3"></div>
       <div class="txt4"></div>
     </body>
     </html>
   ```



## 7. 背景尺寸

- 语法

  ```html
  background-size: length|percentage|cover|contain;
  ```

- 参数值

  | 值         | 描述                                                         |
  | ---------- | ------------------------------------------------------------ |
  | length     | 设置背景图片高度和宽度。第一个值设置宽度，第二个值设置的高度。如果只给出一个值，第二个是设置为 auto(自动) |
  | percentage | 将计算相对于背景定位区域的百分比。第一个值设置宽度，第二个值设置的高度。如果只给出一个值，第二个是设置为"auto(自动)" |
  | cover      | 此时会保持图像的纵横比并将图像缩放成将完全覆盖背景定位区域的最小大小。 |
  | contain    | 此时会保持图像的纵横比并将图像缩放成将适合背景定位区域的最大大小。 |

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
      div[class^="txt"] {
          float: left;
          margin: 0 50px;
          width: 300px;
          height: 300px;
          border: 1px solid #cccccc;
      }
  
      .txt1 {
          background-image: url(test3_1.jpg);
          background-repeat: no-repeat;
          background-size: 200px 200px;
      }
  
      .txt2 {
          background-image: url(test3_1.jpg);
          background-repeat: no-repeat;
          background-size: 50% 50%;
      }
  
      .txt3 {
          background-image: url(test3_1.jpg);
          background-repeat: no-repeat;
          background-size: cover;
      }
  
      .txt4 {
          background-image: url(test3_1.jpg);
          background-repeat: no-repeat;
          background-size: contain;
      }
  </style>
  
  <body>
      <div class="txt1"></div>
      <div class="txt2"></div>
      <div class="txt3"></div>
      <div class="txt4"></div>
  </body>
  
  </html>
  ```

  ![1572859335518](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723155219.png)

## 8. 背景区域(CSS)

- background-origin 属性规定 background-position 属性相对于什么位置来定位。

- 语法

  ```css
  background-origin: padding-box|border-box|content-box;
  ```

- 参数值

  | 值          | 描述                           |
  | ----------- | ------------------------------ |
  | padding-box | 背景图像相对于内边距框来定位。 |
  | border-box  | 背景图像相对于边框盒来定位。   |
  | content-box | 背景图像相对于内容框来定位。   |

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
      div[class^="txt"] {
          float: left;
          margin: 0 50px;
          width: 300px;
          height: 300px;
          padding: 10px;
          border: 10px solid rgba(0, 0, 0, 0.1);
      }
  
      .txt1 {
          background-image: url(test3.jpg);
          background-repeat: no-repeat;
          background-origin: padding-box;
      }
  
      .txt2 {
          background-image: url(test3.jpg);
          background-repeat: no-repeat;
          background-origin: border-box;
      }
  
      .txt3 {
          background-image: url(test3.jpg);
          background-repeat: no-repeat;
          background-origin: content-box;
      }
  
     
  </style>
  
  <body>
      <div class="txt1"></div>
      <div class="txt2"></div>
      <div class="txt3"></div>
      
  </body>
  
  </html>
  ```

  ![1572860162606](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200723155225.png)

## 9. 背景透明(CSS3)

- 语法：

  ```html
  background: rgba(0, 0, 0, 0.3);
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
      .txt1 {
          width: 500px;
          height: 100px;
          background: rgba(255,0,0,0.5);
      }
      .txt2 {
          width: 500px;
          height: 100px;
          background: rgba(0,255,0,0.5);
      }
      .txt3 {
          width: 500px;
          height: 100px;
          background: rgba(0,0,255,0.5);
      }
  </style>
  <body>
    <div class="txt1"></div>
    <div class="txt2"></div>
    <div class="txt3"></div>
  </body>
  
  </html>
  ```

  ![image-20200724151224378](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200724151226.png)

- 我们习惯把0.3 的 0 省略掉  这样写  background: rgba(0, 0, 0, .3);

- 最后一个参数是alpha 透明度  取值范围 0~1之间

- 注意：  背景半透明是指盒子背景半透明， 盒子里面的内容不受影响

- 因为是CSS3 ，所以 低于 ie9 的版本是不支持的。



## 10 综合案例

**五彩导航栏**

```

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>综合案例-五彩导航</title>
    <style>
        .nav a {
            display: inline-block;
            width: 120px;
            height: 58px;
            background-color: pink;
            text-align: center;
            line-height: 48px;
            color: #fff;
            text-decoration: none;
        }

        .nav .bg1 {
            background: url(images/bg1.png) no-repeat;
        }

        .nav .bg1:hover {
            background-image: url(images/bg11.png);
        }

        .nav .bg2 {
            background: url(images/bg2.png) no-repeat;
        }

        .nav .bg2:hover {
            background-image: url(images/bg22.png);
        }
    </style>
</head>

<body>
    <div class="nav">
        <a href="#" class="bg1">五彩导航</a>
        <a href="#" class="bg2">五彩导航</a>
        <a href="#">五彩导航</a>
        <a href="#">五彩导航</a>
        <a href="#">五彩导航</a>
    </div>
</body>

</html>
```

![image-20200724151511128](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200724151513.png)

**百度输入框**

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
    input {
        width: 535px;
        height: 40px;
        background: url(camera_01.png) no-repeat 500px center;
    }
    input:focus {
        width: 535px;
        height: 40px;
        background: url(camera_02.png) no-repeat 500px center;
    }
</style>
<body>
<input type="text"/>
</body>

</html>
```

![](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200724152009.gif)

**导航栏**

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
    a {
        display: inline-block;
        width: 100px;
        height: 40px;
        line-height: 40px;
        background-color: pink;
        text-align: center;
        color: #fff;
        text-decoration: none;
        font-weight: 700;
    }
    a:hover {
        background-color: orange;
        color: black;
    }
</style>
<body>
<a href="#">新闻</a>
<a href="#">体育</a>
<a href="#">汽车</a>
<a href="#">娱乐</a>
</body>

</html>
```

![](https://yulingsimg-1300687702.cos.ap-chengdu.myqcloud.com/20200724152445.gif)