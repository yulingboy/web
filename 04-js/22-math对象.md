### 1.3 Math对象

- Math 对象不是构造函数，它具有数学常数和函数的属性和方法。跟数学相关的运算（求绝对值，取整、最大值等）可以使用 Math 中的成员。

-  Math数学对象 不是一个构造函数 ，所以我们不需要new 来调用 而是直接使用里面的属性和方法即可

| 属性、方法名          | 功能                                         |
| --------------------- | -------------------------------------------- |
| Math.PI               | 圆周率                                       |
| Math.floor()          | 向下取整                                     |
| Math.ceil()           | 向上取整                                     |
| Math.round()          | 四舍五入版 就近取整   注意 -3.5   结果是  -3 |
| Math.abs()            | 绝对值                                       |
| Math.max()/Math.min() | 求最大和最小值                               |
| Math.random()         | 获取范围在[0,1)内的随机值                    |

​	注意：上面的方法使用时必须带括号

​	**获取指定范围内的随机整数**：

```js
function getRandom(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min; 
}
```



```js
        // 1.绝对值方法
        console.log(Math.abs(1)); // 1
        console.log(Math.abs(-1)); // 1
        console.log(Math.abs('-1')); // 隐式转换 会把字符串型 -1 转换为数字型
        console.log(Math.abs('pink')); // NaN 

        // 2.三个取整方法
        // (1) Math.floor()   地板 向下取整  往最小了取值
        console.log(Math.floor(1.1)); // 1
        console.log(Math.floor(1.9)); // 1
        // (2) Math.ceil()   ceil 天花板 向上取整  往最大了取值
        console.log(Math.ceil(1.1)); // 2
        console.log(Math.ceil(1.9)); // 2
        // (3) Math.round()   四舍五入  其他数字都是四舍五入，但是 .5 特殊 它往大了取  
        console.log(Math.round(1.1)); // 1
        console.log(Math.round(1.5)); // 2
        console.log(Math.round(1.9)); // 2
        console.log(Math.round(-1.1)); // -1
        console.log(Math.round(-1.5)); // 这个结果是 -1
```





```js
        // 猜数字游戏
        // 1.随机生成一个1~10 的整数  我们需要用到 Math.random() 方法。
        // 2.需要一直猜到正确为止，所以需要一直循环。
        // 3.while 循环更简单
        // 4.核心算法：使用 if  else if 多分支语句来判断大于、小于、等于。
        function getRandom(min, max) {
            return Math.floor(Math.random() * (max - min + 1)) + min;
        }
        var random = getRandom(1, 10);
        while (true) { // 死循环
            var num = prompt('你来猜？ 输入1~10之间的一个数字');
            if (num > random) {
                alert('你猜大了');
            } else if (num < random) {
                alert('你猜小了');
            } else {
                alert('你好帅哦，猜对了');
                break; // 退出整个循环结束程序
            }

        }
```

