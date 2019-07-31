### css页面引入方法

#### 1、外联式

通过link标签，链接到外部样式表到页面中。要在head标签中引入

```html
<!--day1.html-->
<head>
    <title>css的使用</title>
    <link rel="stylesheet" href="./day1.css">
</head>
<body>
    <div></div>
</body>
```

```css
/*day1.css*/
div{
    width:200px;
    height:200px;
    background-color:red;
}
```

#### 2、嵌入式

通过style标签，在网页上创建嵌入的样式表。要写在head标签中

```html
<head>
 <style>
    div{
        width:200px;
        height:200px;
        background-color:yellow;
    }
</style>
</head>
<body>
    <div></div>
</body>
```

#### 3、内联式

通过标签的style属性，在标签上直接写样式

```html
<body>
    <div style="width:200px;height:200px;background:green">
    </div>
</body>
```

*三种使用方式存在优先级问题，离元素越近优先级越高

#### 4、导入样式

`@import url("css/style.css")`

### css选择器

在style标签中的注释是css的注释/*     */，html的注释不起作用

#### 优先级

第一等：代表内联样式，如: style=””，权值为1000。
第二等：代表ID选择器，如：#content，权值为0100。
第三等：代表类，伪类和属性选择器，如.content，权值为0010。
第四等：代表类型选择器和伪元素选择器，如div p，权值为0001。
通配符、子选择器、相邻选择器等的。如 、>、+,权值为0000。 

#### 1、标签选择器

通过标签来设置元素的样式，代码中所有同名标签都会改变样式，如嵌入式

#### 2、id选择器

通过id属性的值来设置元素的样式，id在html中具有唯一性，不能重名

```html
<head>
    <style>
        #box1{
            width:200px;
            height:200px;
            background-color:green;
        }
    </style>
</head>
<body>
    <div id="box1"></div>
</body>
```

#### 3、类选择器

通过class类名设置元素的样式，如下，class=item的标签都设置了样式，class可重名，一个class可使用多个类名

```html
<head>
    <style>
        .item{
            width:200px;
            height:200px;
            background-color:green;
        }
    </style>
</head>
<body>
    <div class="item"></div>
</body>
```

*影响范围最大，优先级最小

#### 4、层级选择器

主要应用在选择父元素下的子元素，或者子元素下的子元素，可与标签元素结合使用，减少命名，同时也可通过层级，减少命名冲突

可以和多种选择器混合使用

```html
<head>
    <style>
        .wrap{
            width:500px;
            height:500px;
            border:1px solid red;
        }
        .wrap div{
            width:200px;
            height:200px;
            background-color:green;
        }
    </style>
</head>
<body>
    <div class="wrap">
        <div></div>
    </div>
</body>
```

#### 5、组选择器

可以给多个设置相同的样式

```html
<head>
    <style>
        .box1,.box2,.box3{
            width:200px;
            height:200px;
        }
    </style>
</head>
```

#### 6、伪类选择器

```html
<head>
    <style>
        .box{
            width:200px;
            height:200px;
            background-color:green;
        }
        .box:hover{
            /*鼠标悬停上之后的样式*/
            background-color:red;
        }
        .box:after{/*在元素的尾部插入*/
            content:'l';
        }
        .box:before{ /*在元素的头部插入*/
            content:'I';
        }
    </style>
</head>
```

### css颜色表示法

#### 1、颜色名表示

比如：red红色，gold金色

#### 2、16进制数值表示

比如：##ff0000红色

#### 3、RGB颜色

rgb(0,0,0);

#### 4、RGBA颜色

最后一位是透明程度，0-1。rgba(0,0,0,0);

### css文本设置

| 属性            | 描述                                          |
| --------------- | --------------------------------------------- |
| font-size       | 设置文字的大小，如font-size:12px;             |
| font-family     | 设置文字的字体                                |
| font-style      | 设置字体是否倾斜,normal,italic                |
| font-weight     | 设置字体是否粗体，bold,normal                 |
| line-height     | 设置字体的行高                                |
| text-align      | 设置水平对齐方式，属性值：center，right，left |
| text-decoration | 设置文字的下划线，text-decoration:null        |
| text-indent     | 首行缩进，一个字符为30px                      |
| text-shadow     | 设置阴影效果                                  |
| work-wrap       | 自动换行                                      |

### css边框设置

边框设置有三个属性，一个都不能少，但没有先后顺序，颜色样式粗细

border-top：上边框     border-bottom：下边框    border-left：左边框    border-right：右边框

border-radius：设置边框圆角，如果给四个值就是单独给每个角顺时针方向设置，如果给两个值，设置的是对角，如果给一个值每个角都设置

box-shadow：设置阴影，第一个值设置水平方向位移，正值往右偏移，负值往左偏移。第二个值设置垂直方向位移，正值向下，负值向上。第三个值设置模糊程度。第四个值设置扩散范围。第五个值设置阴影颜色。第六个之设置是否为内阴影，如果为内阴影就设置insert，如果不设置内阴影可以不写

### css背景设置

background-image：设置背景图片，background-image：url()      ==这里注意路径问题==

background-size：设置背景图片大小

background-position：设置背景图片位置

### css间距设置

#### 1、内间距

padding-top，padding-left，padding-right，padding-bottom

在使用padding的时候会改变元素的实际大小。padding设置四个值时，第一个值代表元素顶部的内间距。也可设置两个值，第一个值代表上下对边，第二个值代表左右对边。设置一个值，代表四个边的间距。单独设置时需要指明top，left，right，bottom。

#### 2、外间距

margin设置外间距

margin-top，margin-bottom，margin-left，margin-right。用法和内间距用法一致。

让元素水平居中：margin:0 auto;

### 置换元素

⼀个内容不受CSS视觉格式化模型控制，CSS渲染模型并不考虑对此内容的渲染，且元素本⾝⼀般拥有固有尺⼨（宽度，⾼度，宽⾼⽐）的元素，被称之为置换元素。
除了置换元素其他的都是非置换元素。 
对于⾏内级⾮置换元素，宽度设置是不适⽤的；
对于⾏内级置换元素来说，其宽度的设置需遵循以下⼏点：
1.若宽⾼的计算值都为auto且元素有固有宽度，则width的使⽤值为该固有宽度；典型的例⼦是：拥有默认宽⾼的input当宽度的计算值为auto时，则宽度使⽤值为其默认的固有宽度
2.若宽度的计算值为auto且元素有固有宽度，则width的使⽤值为该固有宽度；例⼦同上
3.若宽度的计算值为auto且⾼度有⾮auto的计算值，并且元素有固有宽⾼⽐，则width的使⽤值为⾼度使⽤值 * 固有宽⾼⽐

### 盒子模型

![img](http://images.cnblogs.com/cnblogs_com/cchyao/%E6%A0%87%E5%87%86W3C%E7%9B%92%E5%AD%90%E6%A8%A1%E5%9E%8B%E5%92%8CIE%E7%9B%92%E5%AD%90%E6%A8%A1%E5%9E%8BCSS%E5%B8%83%E5%B1%80%E7%BB%8F%E5%85%B8%E7%9B%92%E5%AD%90%E6%A8%A1%E5%9E%8B/1.JPG)

### 浮动

#### 文档流

盒子按照html标签编写的顺序依次从上到下，从左到右排列，，块元素占一行，行内元素在一行之内从左到右排列，先写的先排列，后写的排在后面，每个盒子都占据自己的位置。

#### 浮动

float：属性值left、right

1、浮动会让元素脱离文档流，后面不浮动的元素会占据原来的位置

2、停止浮动

​      碰到父级元素的边界会停止

​      碰到前面有浮动的元素会停止

​	碰到没有浮动的元素会停止

3、浮动会把元素转换成行内块元素，让元素并在一行

4、当父级元素没有设置固定的高度时，子元素都浮动，父级元素的高度就无法被撑开

5、当父级元素不够时，浮动元素会换行显示

#### 清除浮动

​	clear：both。left清除左浮动，right清除有浮动，both清除左右两边的浮动

​	父级上增加属性overflow：hidden；

### 定位

position：设置元素的定位

​	relative：相对定位，以元素本身位置为参考点进行偏移，不会脱离文档流

​	absolute：绝对定位，以有定位属性的父级为参考点进行偏移如果父级元素没有定位属性，继续向上一级元素找，如果都没有就以body为参考点进行偏移

​	fixed：绑定定位，以浏览器窗口为参考进行定位，主要用在固定在头部的导航栏

```html
<style>
    .box1{
        width:80px;
        height:30px;
        background:red;
        position:fixed;
        bottom:20px;
        right:20px;
    }
</style>
```

### 页面布局

#### 静态布局

#### 响应式布局

创建多个流体式布局，分别对应一个屏幕分辨率范围

特点：分别为不同的屏幕分辨率定义布局，同时，在每个布局中，应用流式布局的理念，即页面元素宽度随着窗口调整而自动适配。就是使用媒体查询的方式，创建多个元素宽度是相对的布局理想的响应式布局是指对PC/移动各种终端进行响应的

媒体查询

```css
/*当浏览器窗口小于等于960时，重新设置样式*/
@media(max-width:960px){
    div{
    }
}
```

### 动画

通过css3，我们能够创建动画，这可以在许多网页中取代动画图片、Flash动画以及JavaScript。

`@keyframes`规则用于创建动画。规定某项css样式，就能创建由当前样式逐渐改为新样式的动画效果。

```html
<style>
    @keyframes myfirst{
        from{background:red;}
        to{background:yellow;}
    }
    div{
        width:200px;
        height:200px;
        border:1px solid black;
        animation:myfirst 5s;
    }
</style>
```

0%是动画的开始，100%是动画的完成。

```html
@keyframes myfirst{
0%		{background:red;}
25%		{background:yellow;}
50%		{background:blue;}
100%	{background:green;}
}
<!--改变背景色和位置,,,,改变位置没有实验成功-->
<style>
    @keyframes myfrist{
        0%   {background: red; left:0px; top:0px;}
	    25%  {background: yellow; left:200px; top:0px;}
		50%  {background: blue; left:200px; top:200px;}
		75%  {background: green; left:0px; top:200px;}
		100% {background: red; left:0px; top:0px;}
    }
</style>
```

### 制作网页

#### 与ul有关

`list-style:none;`将`ul`前面的圆点删除

#### 与位置有关

将标签设置为`margin:0 auto;`可以自己设置宽和高

将`width`设置为`width:50%`居中于页面

