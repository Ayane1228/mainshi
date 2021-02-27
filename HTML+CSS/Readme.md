## HTML5 CSS3

- ## HTML5

  ##### 1. Doctype作用，HTML5 为什么只需要写`<!DOCTYPE html>`

  ​	Doctype:W3C规定这声明了该文档的html标准，html5使用了和以前不一样的标准。

  

  ##### 2. 常用元素类型有那些

  ​	行内元素（inline）：

  ​		不能设置宽高，不会自动换行。有：`a`,`img`,`span`,`input`,`i`,`select(下拉标签)`等。

  ​	块级元素（block）：

  ​		最常见的标签，常用作其他元素的容器，会自动换行，多个块元素会自动从上到下自动排列。有：`div`,`ul`,`ol`,`p`,`li`,`header`,`footer`,`h1~h6`等。

  ​	行内块元素（dispaly:inline-block）：

  ​		兼有行内元素和块状元素的特点，能够设置宽高，但不会自动换行。	

  ​	空元素（void）：br（换行符）` `hr（换行线）` `link（锚点）。指没有内容的标签。

  ​	伪元素： `::after`,`::before`,`::first-line`。能够选择当前元素的后、前、和这些元素的第一行的**元素**。该元素不会出现在DOM中，不能通过JS操作。

  ​		例子：
  
  ```html
      <style>
          .boring-text::after {
              content: "<- 无聊!";
              color: red;
              }
      </style>
      <p class="boring-text">这是些无聊的文字</p>
    <p>这是不无聊也不有趣的文字</p>
  ```

  ​	会在类名为`boring-text`的p标签后添加颜色为red，内容为<- 无聊!的`::after`元素。

  

  ##### 3.伪类和伪元素的区别

  ​	两者都用在css中,伪元素会创建一个元素，伪类会对已存在的元素加上伪类的样式。

  ​	`:aftere`，`:before`是`::after`,`::before`的简写。

  ​	伪元素：是一个元素。

  ​	伪类：常见：`:first-child(第一个子元素，要有父元素)`,`:checked`,`:hover`等。
  
  ​	例子：结果1为红。
  
  ```html
      <style>
      li:first-child{
          color: red;
      }           
      </style>
      <ul>
          <li>1</li>
        <li>2</li>
          <li>3</li>
    </ul>
  ```

  

  ##### 4.简述一下你对HTML语义化的理解

  语义化：合适的标签做合适的事情。
  
  语义化标签：`h1`,`header`,`footer`等。
  
  
  
  ##### 5.描述一下 cookie，sessionStorage 和 localStorage 的区别
  
  | 特性         | Cookie                                                       | localStorage                                   | sessionStorage                                       |
  | ------------ | ------------------------------------------------------------ | ---------------------------------------------- | ---------------------------------------------------- |
  | 生命周期     | 可设置失效时间，没有设置的话，默认是关闭浏览器后失效         | 除非被手动清除，否则将会永久保存               | 仅在当前网页会话下有效，关闭页面或浏览器后就会被清除 |
  | 存放数据大小 | 4KB左右                                                      | 可以保存5MB的信息                              |                                                      |
  | http请求     | 每次都会携带在HTTP头中，如果使用cookie保存过多数据会带来性能问题。 | 仅在客户端（即浏览器）中保存，不参与和服务器。 |                                                      |



##### 	6. src与href的区别

​	区别：`src` 用于替代这个元素(`img`标签)，而 `href` 用于建立这个标签与外部资源之间的关系

​	`<link href="style.css" rel="stylesheet" />`浏览器加载到这里的时候，`html` 的渲染和解析不会暂停，`css` 文件的加载是同时进行的。

​	`<script src="script.js"></script>`当浏览器解析到这句代码时，页面的加载和解析都会暂停直到浏览器拿到并执行完这个js文件



##### 	7. 表单提交中Get和Post方式的区别

- `Get` 一般用于从服务器上获取数据，`Post` 向服务器传送数据
- `Get` 传输的数据是拼接在Url之后的，对用户是可见的；`Post` 的传输数据对用户是不可见的
- `Get` 传送的数据量较小，不能大于 `2KB`。`Post` 传送的数据量较大，一般被默认为不受限制
- `Get` 安全性非常低，`Post` 安全性较高
- 在 `FORM` 提交的时候，如果不指定 `Method`，则默认为 `Get` 请求



### CSS3

##### 1. css盒子模型，box-sizing属性的理解

`css` 的盒模型由 `content`(内容)、`padding`(内边距)、`border`(边框)、`margin`(外边距)组成。但盒子的大小由`content+padding+border`这几部分决定

`box-sizing`是一个`CSS3`属性，与盒子模型有着密切联系。即决定元素的宽高如何计算，`box-sizing`有三个属性：

```
box-sizing: content-box|border-box|inherit:
```

- `content-box` 使得元素的宽高即为内容区的宽高(默认模式)
- `border-box`: 计算方式`content + padding + border` = 本身元素大小，即缩小了`content`大小
- `inherit` 指定 `box-sizing` 属性的值，应该从父元素继承

##### 2. 清除浮动，什么时候需要清除浮动，清除浮动都有哪些方法

浮动的元素是脱离文档标准流的，如果我们不清楚浮动，那么就会造成**父元素高度塌陷**，影响页面布局。

清除浮动的方式：

- 为父元素设置高度
- 为父元素添加`overflow:hidden`
- 伪元素

```
.fix::after { 
     content:""; 
     display:block; 
     clear:both;
}
```

使用伪元素的好处：不增加冗余的 `DOM` 节点，符合语义化

> `overflow`: `hidden` 可以触发 `BFC` 机制。

> `BFC`：块级格式化上下文，创建了 `BFC` 的元素就是一个独立的盒子，它规定了内部如何布局，并且与这个独立盒子里的布局不受外部影响，当然它也不会影响到外面的元素，**计算`BFC`的高度时，浮动元素也参与计算**

##### 3. 如何让一个不定宽高的盒子水平垂直居中

> `css3`属性

```
.father {
    position: relative;
}
.son {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```

> `flex`布局

```
.father {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

##### 4. px和em和rem的区别

> `px`: 像素，相对长度单位。像素`px`是相对于显示器屏幕分辨率而言的

> `em`的值并不是固定的，会继承父级元素的字体大小，代表倍数

> `rem`的值并不是固定的，始终是基于根元素 `<html>` 的，也代表倍数

##### 5. position的值有哪些

> `static`： 默认值。没有定位，元素出现在正常的流中

> `relative`（相对定位）：生成相对定位的元素,相对于其正常（原先本身）位置进行定位

> `absolute`（绝对定位）：生成绝对定位的元素，相对于static定位以外的第一个父元素进行定位

> `fixed`（固定定位）：生成绝对定位的元素，相对于浏览器窗口进行定位

##### 6. display:none与visibility：hidden的区别

| 区别           | display:none                                                 | visibility：hidden的                                         |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 是否占据空间   | 不占据任何空间，在文档渲染时，该元素如同不存在（但依然存在文档对象模型树中） | 该元素空间依旧存在                                           |
| 是否渲染       | 会触发reflow（回流），进行渲染                               | 只会触发repaint（重绘），因为没有发现位置变化，不进行渲染    |
| 是否是继承属性 | 不是继承属性，元素及其子元素都会消失                         | 是继承属性，若子元素使用了visibility:visible，则不继承，这个子孙元素又会显现出 |

##### 7. CSS中link 和@import的区别

> ```
> link`属于`XHTML`标签，`@import`完全是`CSS`提供的一种方式,只能加载`CSS
> ```

> 加载顺序的差别，当一个页面被加载的时候，`link`引用的`CSS`会同时被加载，而`@import`引用的`CSS` 会等到页面全部被下载完再被加载

> 兼容性的差别。由于`@import`是`CSS2.1`提出的所以老的浏览器不支持，而`link`标签无此问题

> 当使用`javascript`控制`dom`去改变样式的时候，只能使用`link`标签，因为`@import`不是`dom`可以控制的

##### 8. 什么是响应式设计，响应式设计的基本原理是什么

> 响应式网站设计是一个网站能够兼容多个终端，而不是为每一个终端做一个特定的版本。基本原理是通过媒体查询检测不同的设备屏幕尺寸做处理

##### 9. ::before 和 :after中双冒号和单冒号有什么区别？解释一下这2个伪元素的作用

> 单冒号(:)用于`CSS3`伪类，双冒号(::)用于`CSS3`伪元素。（伪元素由双冒号和伪元素名称组成）,双冒号是在当前规范中引入的，用于区分伪类和伪元素

##### 10. 重绘和回流

[重绘和回流](https://juejin.im/post/5a9923e9518825558251c96a)

##### 12. flex布局

[flex布局教程--阮一峰](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)

##### 13. css预处理器

提供了一种`css`的书写方式，常见的就是 [SAAS文档](http://sass.bootcss.com/docs/sass-reference/) 和 [LESS文档](https://less.bootcss.com/)



## 盒子水平和垂直居中的五大方案

1. 基于定位(position)的三种方式：子绝父相,`position:absolute`:绝对定位；`position:relative`：相对定位。
               1.子盒子定位到父盒子的50%,50%,再使用transform属性使子盒子沿着X,Y轴偏移自己宽高的50%，需要浏览器支持transform属性
               2.子盒子定位到父盒子的50%,50%，再使用margin值进行偏移：margin-top：-50px；margin-left:-50px,需要知道子盒子的具体宽高
               3.设置top、right、bottom、left均为0，利用margin:auto;设置margin值使得居中,需要子盒子有具体的宽高

2. flex:给父元素设置display：flex，将父盒子变为弹性容器，再设置弹性子元素的对齐方式：

   设置主轴线对齐方式:justify-content：center;设置侧轴对齐方式align-items：center；

3. Javascript方式: 

   ​    获取父盒子、子盒子的宽高，再使用定位，将子盒子定位到到中央:top、left均为(父盒子的宽高减去子盒子的宽高的长度)/2

4. table-cell:将父元素设置为单元格，子元素设置为inline-block
           将父元素设置为table-cell，设置对齐方式；将子元素设置为inline-block
           要求父元素必须要有固定宽高，不常用

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        /* 
            水平垂直居中：
            基于定位(position)的三种方式：
                子绝父相,absolute:绝对；relative：相对
                1.子盒子定位到父盒子的50%,50%,再使用transform属性使子盒子沿着X,Y轴偏移自己宽高的50%，需要浏览器支持transform属性
                2.子盒子定位到父盒子的50%,50%，再使用margin值进行偏移：margin-top：-50px；margin-left:-50px,需要知道子盒子的具体宽高
                3.设置top、right、bottom、left均为0，利用margin:auto;设置margin值使得居中,需要子盒子有具体的宽高
        */

        /* .big{
            width: 500px;
            height: 500px;
            margin: 100px auto;
            background-color: aqua;
            position: relative;
        }
        .small{
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%,-50%);
            width: 100px;
            height: 100px;
            background-color: red;
        } */
        /* .big{
            width: 500px;
            height: 500px;
            margin: 100px auto;
            background-color: aqua;
            position: relative;
        }
        .small{
            position: absolute;
            top: 50%;
            left: 50%;
            margin-top: -50px;
            margin-left: -50px;
            width: 100px;
            height: 100px;
            background-color: red;
        } */
        /* .big{
            width: 500px;
            height: 500px;
            margin: 100px auto;
            background-color: aqua;
            position: relative;
        }
        .small{
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            margin: auto;
            width: 100px;
            height: 100px;
            background-color: red;
        } */
        

        /* flex:
                给父元素设置display：flex，将父盒子变为弹性容器，再设置弹性子元素的对齐方式：
                设置主轴线对齐方式:justify-content：center;设置侧轴对齐方式align-items：center；
            移动端常用,有兼容性问题。
        */
        /* .big{
            width: 500px;
            height: 500px;
            margin: 100px auto;
            background-color: aqua;
            display: flex;
            justify-content: center;
            align-items: center;    
        }
        .small{
            width: 100px;
            height: 100px;
            background-color: red;
        } */
         
        /* 
            Javascript方式: 
            获取父盒子、子盒子的宽高，再使用定位，将子盒子定位到到中央:top、left均为(父盒子的宽高减去子盒子的宽高的长度)/2
        */
         /*
          .big{
            width: 500px;
            height: 500px;
            background-color: aqua;
            position: relative;
        }
        .small{
            position: absolute;
            width: 100px;
            height: 100px;
            background-color: red;
        }        */

        /* table-cell:将父元素设置为单元格，子元素设置为inline-block
            将父元素设置为table-cell，设置对齐方式；将子元素设置为inline-block
            要求父元素必须要有固定宽高，不常用
        */                 
          /* .big{
            width: 500px;
            height: 500px;
            background-color: aqua;
            display: table-cell;
            vertical-align: middle;
            text-align: center;
        }
        .small{
            display: inline-block;
            width: 100px;
            height: 100px;
            background-color: red;
        }        */
    </style>
</head>
<body>
    <div class="big">
        <div class="small">

        </div>
    </div>
    <script>
        /* 
            Javascript方式: 
            获取父盒子、子盒子的宽高，再使用定位，将子盒子定位到到中央:top、left均为(父盒子的宽高减去子盒子的宽高的长度)/2
        */
        // let big = document.querySelector('.big')
        // let small = document.querySelector('.small')

        // let bigW = big.offsetWidth
        // let bigH = big.offsetHeight
        
        // let smallW = small.offsetWidth
        // let smallH = small.offsetHeight

        // small.style.left = ( bigW - smallW)/2 + 'px';
        // small.style.top = ( bigH - smallH)/2 + 'px';
    </script>
</body>

</html>
```



- ## CSS中的盒模型

  有标准盒子模型、IE盒模型（怪异盒模型）、flex弹性盒模型。

  ​	可以指定盒子的模型：

  ​	标准盒子模型：`box-sizing:content-box`，标准盒模型指的是我们在样式中写的`width`和`height`指的是内容的宽高，真实盒子的宽高则指的是我们写的`width`和`height`+ 填充`padding`的宽高+边框`border`宽高组成的。

  ​	怪异(IE)盒模型:`box-sizing:border-box`:这里我们写的`width`和`height`写的就是盒子的宽高，，当修改`padding`或`border`的大小的时候，系统会去缩放内容保持盒子的大小不变，比较方便，不用每次计算盒子的大小。现在的UI组件大部分也都让盒模型使用这种盒模型。

  ![img](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071004.png)

  ​	

  [阮一峰教程](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)

  ​	在移动端开发时，我们常用flex弹性盒模型，采用 Flex 布局的元素，称为 Flex 容器。它的所有子元素自动成为容器成员。

  ​	容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。主轴的开始位置（与边框的交叉点）叫做`main start`，结束位置叫做`main end`；交叉轴的开始位置叫做`cross start`，结束位置叫做`cross end`。



- ## 经典布局

  左右固定、中间自适应（圣杯布局、双飞翼布局）

  圣杯布局：

  ```html
  <!DOCTYPE html>
  <html lang="en">
  
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>圣杯布局</title>
  </head>
  <style>
      .container {
          padding: 0 100px 0 200px;/* 此段代码是为了摆正中间栏的位置 */
          /* min-width: 600px; 不设置最小宽度  页面容易变形 */
      }
  
      .left {
          width: 200px;
          background: red;
          /* 关键点：会让元素沿文档流向左移动，负数值比较大的话会一直移动到上一行 */
          margin-left: -100%;
          left: -200px;
          /* 中间栏的位置摆正之后，左栏的位置也相应右移，通过相对定位的left恢复到正确位置 */
      }
      .right{
          width: 100px;
          background: blue;
          margin-left: -100px;
          right: -100px;
          /* 中间栏的位置摆正之后，右栏的位置也相应左移，通过相对定位的right恢复到正确位置 */
      }
      .main{
          width: 100%;
          background: yellow;
      }
      .left,.main,.right{
          float: left;
          min-height: 200px;
          position: relative;
      }
  </style>
  
  <body>
      <div class="container">
          <div class="main">main</div>
          <div class="left">left</div>
          <div class="right">right</div>
      </div>
  </body>
  
  </html>
  ```

  双翼布局

  ```html
  <!DOCTYPE html>
  <html lang="en">
  
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>双飞翼</title>
  </head>
  <style>
      .left,.main,.right{
          min-height: 300px;
          float: left;
      }
      .content{
          /* 关键点：用margin把div挤到中间正常展示*/
          margin: 0 100px 0 200px;
      }
      .left{
          width: 200px;
          background: green;
          margin-left: -100%;
      }
      .main{
          width: 100%;
          background: red;
      }
      .right{
          width: 100px;
          background: blue;
          margin-left: -100px;
      }
  </style>
  
  <body>
      <div class="container">
          <div class="main">
              <div class="content">main</div>
          </div>
          <div class="left">left</div>
          <div class="right">right</div>
      </div>
  </body>
  
  </html>
  ```

  flex实现

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>flex</title>
  </head>
  
  <style>
      .container{
          display: flex;
          min-height: 300px;
      }
      .left,.right{
          /* 
              flex 属性是 flex-grow、flex-shrink 和 flex-basis 属性的简写属性。 
              flex-grow：弹性盒子放大的比率。
              flex-shrink：弹性盒子缩小的比率
              flex-basis：弹性盒子初始长度
          */
          flex: 0 0 200px;
          height: 200px;
          background-color: lightgreen;
      }
      .center{
          /*  
              flex：1
              flex-grow、flex-shrink 和 flex-basis分别是1，1，0%
              自动分配剩余空间
           */
          flex: 1;
          min-width: 400px;
          background-color: lightsalmon;
      }
  </style>
  <body>
      <div class="container">
          <div class="left">left</div>
          <div class="center">main</div>
          <div class="right">right</div>
      </div>
  </body>
  </html>
  ```

  border-box方法：

  ```html
  <!DOCTYPE html>
  <html lang="en">
  
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>其他方法实现中间栏div内容不被遮挡</title>
  </head>
  
  <style>
      .container{
          padding: 0 100px 0 200px;
      }
      .left,.main,.right{
          float:left;
          position: relative;
          min-height: 200px;
      }
      .left{
          background: lightgreen;
          width: 200px;
          /* 关键点：会让元素沿文档流向左移动，负数值比较大的话会一直移动到上一行 */
          margin-left: -100%;
          left: -200px;
      }
      .main{
          background: lightpink;
          width: 100%;
          /* 关键点！！！ */
          box-sizing: border-box;
          padding: 0 100px 0 200px;
      }
      .right{
          background: lightseagreen;
          width: 100px;
          margin-left: -100px;
          right: -100px;
      }
  </style>
  
  <body>
      <div class="container">
          <div class="main">main</div>
          <div class="left">left</div>
          <div class="right">right</div>
      </div>
  </body>
  
  </html>
  ```



- ## 移动端响应式布局的方案

  -  media，一个页面，多个样式表

    媒体查询,根据加载页面的宽度不同加载不同的css样式表。

    ```css
        <link rel="stylesheet" href="./index.css">
        <link rel="stylesheet" href="./index_ipad.css" media="screen and (max-width:1200px)">
        <link rel="stylesheet" href="./index_mobile.css" media="screen and (max-width:768px)">
    ```

  - rem，不同终端，不同页面。rem主要用在移动端，通过监测屏幕大小改变html的字体大小，从而实现自适应大小的效果。

  - flex

  - vh/vw

    将视口宽/高度分为100份，1vh/1vw指1/100视口宽度/高度。