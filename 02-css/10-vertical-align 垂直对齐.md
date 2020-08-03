## vertical-align 垂直对齐

- 有宽度的块级元素居中对齐，是margin: 0 auto;
- 让文字居中对齐，是 text-align: center;

但是我们从来没有讲过有垂直居中的属性。

vertical-align 垂直对齐，它只针对于**行内元素**或者**行内块元素**，

```css
vertical-align : baseline |top |middle |bottom 
```

设置或检索对象内容的垂直对其方式。

- 注意：

  vertical-align 不影响块级元素中的内容对齐，它只针对于**行内元素**或者**行内块元素**，

  特别是行内块元素， **通常用来控制图片/表单与文字的对齐**。

### 3.1 图片、表单和文字对齐

所以我们知道，我们可以通过vertical-align 控制图片和文字的垂直关系了。 默认的图片会和文字基线对齐。

### 3.2 去除图片底侧空白缝隙

- 原因：

  图片或者表单等行内块元素，他的底线会和父级盒子的基线对齐。

  就是图片底侧会有一个空白缝隙。

- 解决的方法就是：  

  - 给img vertical-align:middle | top| bottom等等。  让图片不要和基线对齐。

  - 给img 添加 display：block; 转换为块级元素就不会存在问题了。