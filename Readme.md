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


Vue生命周期

beforeCreate（创建前）: 在数据观测和初始化事件还未开始,data、watcher、methods都还不存在，但是$route已存在，可以根据路由信息进行重定向等操作。

created(创建后)：在实例创建之后被调用，该阶段可以访问data，使用watcher、events、methods，也就是说 数据观测(data observer) 和event/watcher 事件配置 已完成。但是此时dom还没有被挂载。该阶段允许执行http请求操作。

beforeMount （挂载前）：将HTML解析生成AST节点，再根据AST节点动态生成渲染函数。相关render函数首次被调用(划重点)。

mounted (挂载后)：在挂载完成之后被调用，执行render函数生成虚拟dom，创建真实dom替换虚拟dom，并挂载到实例。可以操作dom，比如事件监听

beforeUpdate：vm.data更新之后，虚拟dom重新渲染之前被调用。在这个钩子可以修改vm.data更新之后，虚拟dom重新渲染之前被调用。在这个钩子可以修改vm.data更新之后，虚拟dom重新渲染之前被调用。在这个钩子可以修改vm.data，并不会触发附加的冲渲染过程。

updated：虚拟dom重新渲染后调用，若再次修改$vm.data，会再次触发beforeUpdate、updated，进入死循环。

beforeDestroy：实例被销毁前调用，也就是说在这个阶段还是可以调用实例的。

destroyed：实例被销毁后调用，所有的事件监听器已被移除，子实例被销毁



第一次是写一个表单页面，写了大概80%~90%，但有地方没有注意到。

input的宽度自适应

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <style>       
            div{
                width: 1200px;
                margin: 0 auto;
                display: flex;
                flex: 1;
            }  
            #name{
                width: 100%;
            }
        </style>
    </head>
    <body>
        <div>
            <label for="name">企业名称</label>
            <input id='name' type="text" placeholder="请输入企业名称">
        </div>
    </body>
    
    </html>



2个select之间的绑定和按钮的margin值不生效，放大缩小页面input框和label位置会变。

select二级地点绑定

第一个select中的option是使用v-for绑定在数组place中。

第二个select中的option也是使用v-for绑定在数组childrenOptions中，而childrenOptions的值则是在第一个select变化（触发@change='change'时）才能获取到。

    change:function(e){
        const placeIndex = e.target.options.selectedIndex
        this.$data.childrenOptions = this.$data.palace[placeIndex - 1].children
        }

获取方法：获取当前选择省在place中的索引值，再将这个索引值对应的children数组赋值给市所绑定的数组中。

-1是因为设置了默认值

             <option selected>
                 请选择省
             </option>



    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
        <link rel="stylesheet" href="./normalize.css">
        <script src="./vue.min.js"></script>
    
    </head>
    <body>
        <div id="app">
            <select name="sheng" id="sheng" @change='change' >
                <option selected>
                    请选择省
                </option>
                <option 
                    v-for="(item,index) in palace"
                    :key="index"
                    :value="item.value" 
                    >{{item.value}}
                </option>
            </select>
            <select name="shi" id="shi">
                <option selected>
                    请选择市
                </option>
                <option
                    v-for="(item,index) in childrenOptions"
                    :key="index"
                    :value="item.value"
                >
                    {{item.value}}
                </option>
            </select>
        </div>
    </body>
    </html>
    <script>
        var vue = new Vue({
            el:'#app',
            data() {
                return {
                    palace:[{
                    label: "11",
                    value: "北京市",
                    children: [{
                            label: "110101",
                            value: "东城区"
                        }, {
                            label: "110102",
                            value: "西城区"
                        }, {
                            label: "110105",
                            value: "朝阳区"
                        }, {
                            label: "110106",
                            value: "丰台区"
                    }]
                }, {
                    label: "12",
                    value: "天津市",
                    children: [{
                            label: "120101",
                            value: "和平区"
                        }, {
                            label: "120102",
                            value: "河东区"
                        }]
                }],
                childrenOptions:[]
                }
            },
            methods: {
                change:function(e){
                    const placeIndex = e.target.options.selectedIndex
                    this.$data.childrenOptions = this.$data.palace[placeIndex - 1].children
                }
            }
        })
    </script>
    <style scoped>
        #app{
            margin: 100px 100px;
        }
    </style>

项目权限判断

	通过登录时请求后台时，查询当前登录用户的role权限，并根据权限生成相应的路由页面，相应的用户只能看到和访问相应的页面。



cookie

cookie和session

	cookie保存在客户端，session保存在服务器端



cookie和locationStroge、sessionStroge的区别

	cookie可以用来保存用户喜好或者保存用户名密码。

	cookie保存数据较小，session保存数据比较大。

	cookie：只在设置的cookie过期时间之前有效，即使窗口关闭或浏览器关闭 ，用来保存token，每次请求时传递给后台验证是否正确。

	sessionStorage：仅在当前浏览器窗口关闭之前有效，可以用来不同页面之间交互；

	localStorage：始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；	



同步异步的理解

javascript是单线程的语言，不能同时执行多个任务。

同步是在当前的任务会在主线程上一个接一个地执行，

异步是指将任务放入任务队列，等待主线程上任务完成之后再执行。



盒模型

分为标准盒模型box-sizing:content-box和怪异盒模型box-sizing:border-box。

在 标准盒子模型中，width 和 height 指的是内容区域的宽度和高度。

IE盒子模型中，width 和 height 指的是内容区域+border+padding的宽度和高度。



父子组件：如何获取子组件中的方法？

父组件使用import 子组件 from '../url'获得子组件，并在components中注册子组件

    <script>
    	import 子组件 from '../子组件.vue'
    	export deafult{
    		components：{
    			子组件，
    		}
    		data(){
    			return{
    				....
    			}
    		}
    	}
    </script>

子组件获取父组件的数据：

	父组件需要在子组件上绑定一个属性，属性值就是传递给子组件的值。

    <son :data="data"></son>

	子组件用props可以获取父组件传递过来的值。可以在子组件定义传递值的类型、是否必须、默认值等。

    export default{
    	props：{
    		data：{
    			type：Number，
    			required：true,
    			default:'100'
    		}
    	}
    }

子组件向父组件传值

子组件：子组件通过$emit('父组件的方法名'，需传递的数据)向父组件传值

    <!-- 子组件 -->
    <template> 
    <div class="testCom">
        <input type="text" v-model="message" />
        <button @click="click">Send</button>
    </div>
    </template>
    <script>
    export default {
        // ...
        data() {
            return {
              // 默认
              message: '我是来自子组件的消息'
            }
        },
        methods: {
          click() {
                this.$emit('childFn', this.message);
            }
        }    
    }
    </script>

父组件：父组件需要在子组件上绑定事件，@子组件传递的第一个值='父组件中绑定的方法'。

    <!-- 父组件 -->
    <template>
        <div class="test">
          <test-com @childFn="parentFn"></test-com>
          <br/> 
          子组件传来的值 : {{message}}
        </div>
    </template>
    
    <script>
    export default {
        // ...
        data() {
            return {
                 message: ''
            }
        },
        methods: {
           parentFn(payload) {
            this.message = payload;
          }
        }
    }
    </script>

父组件调用子组件中的方法（$ref）

父组件在子组件上绑定ref=子组件vue实例，这样就可以在methods中通过this.$refs.子组件实例.子组件方法()使用子组件中的方法。

    <template>
      <div @click="parentMethod">
        <children ref="c1"></children>
      </div>
    </template>
    
    <script>
      import children from 'components/children/children.vue'
      export default {
        components: {      
          'children': children
        },
        methods:{
          parentMethod() {
            console.log(this.$refs.c1) //返回的是一个vue对象，可以看到所有添加ref属性的元素
            this.$refs.c1.childMethods(); 
          }
        },
        created(){
        }
      }
    </script>

子组件：

    <template>
      <div>
    
      </div>
    </template>
    
    <script>
      export default {
        data(){
          return {
            num:'123'
          }
        },
        computed: {
        },
        methods:{
          childMethods() {
            alert("I am child's methods")
          }
        },
        created(){
        }
      }
    </script>



ajax发生在vue的哪个阶段

	可以放在created()中此时data数据已经实现了双向绑定，速度也会快一点。

flex：flex-wrap属性用于设置当项目在容器中一行无法显示的时候如何处理。

http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html



	

token

	客户端第一次登录发送用户名和密码给服务器端，服务端返回给客户端，客户端保存在cookie或是loacalstorage中，之后在网站中请求接口的时候都从cookie或localstorage将token返回给客户端。



冒泡 捕获

	为了解决事件流，例子：多个嵌套的div嵌套绑定了多个相同的点击事件。

    <div id='3'> 3
    	<div id='2'>2
    		<div id='1'>
    			1	
    		</div>
    	</div>	
    </div>
    <script>
    	    var dv1 = document.getElementById('dv1');
            var dv2 = document.getElementById('dv2');
            var dv3 = document.getElementById('dv3');
            dv1.onclick = function () {
                console.log(this.id);
            };
            dv2.onclick = function () {
                console.log(this.id);
            };
            dv3.onclick = function (e) {
                console.log(this.id);
                e.stopPropagation();
            };
    </script>

	1.事件冒泡(event bubbling)：会输出123

	微软提出了名为事件冒泡的事件流。事件按照从最特定的事件目标到最不特定的事件目标(document对象)的顺序触发。可以想象把一颗石头投入水中，泡泡会一直从水底冒出水面。也就是说，事件会从最内层的元素开始发生，一直向上传播，直到document对象。

	2.事件捕获(event capturing)：会输出321。

	网景提出另一种事件流名为事件捕获。事件从最不精确的对象(document 对象)开始触发，然后到最精确(也可以在窗口级别捕获事件，不过必须由开发人员特别指定)，与事件冒泡相反，事件会从最外层开始发生，直到最具体的元素。同样形象的比喻一下可以想象成警察逮捕屋子内的小偷，就要从外面一层层的进入到房子内。

阻止事件冒泡：e.	()

stopDefault()
功能：阻止浏览器的默认行为

清除浮动

1. 	给父元素添加overflow:hidden
2. 在浮动元素最后加一个空div，添加属性clear:both属性
3. 给父元素添加伪元素，给伪元素添加属性。.father:after{clear:both}

js css优化

减少循环，压缩文件，去除无用CSS，减少重复的css，减少改变元素的位置，颜色，类名



如何生成自动生成文件目录结构?

使用命令行；

    cd 对应文件夹
    tree



数组翻转

reverse() 方法用于颠倒数组中元素的顺序。

    arrayObject.reverse()

注释：该方法会改变原来的数组，而不会创建新的数组。



浅拷贝深拷贝

怎么实现对对象的拷贝(浅拷贝与深拷贝)

浅拷贝

- 拷贝原对象引用
- 可以使用Array.prototype.slice()也可以完成对一个数组或者对象的浅拷贝
- Object.assign()方法

深拷贝

- 最常用的方式就是 JSON.parse(JSON.stringify(目标对象)，缺点就是只能拷贝符合JSON数据标准类型的对象。
  

JavaScript中的数据类型分为：

基本数据类型：Null,undefined,string,number,boolean,symbol,

和

引用数据类型:arrya,Object

基本数据类型赋值：

    var a = 1
    var b = a
    console.log(a)
    console.loag(b)

此时两个输出均为1，当修改b的值时不会影响a的值，此时a,b的输出分别为1,2。

    var a = 1
    var b = a
    console.log(a)
    console.loag(b)
    var b = 2
    console.log(a)
    console.loag(b)

引用数据类型赋值：

    var obj = {name:'我是obj'}
    var newobj = obj
    console.log(ob.name)
    console.log(newobj.name)

结果均为  ’我是obj‘。

当修改newobj.name的时候，obj.name也会修改。第二次打印的值均为："我是newobj"。

    var obj = {name:'我是obj'}
    var newobj = obj
    console.log(ob.name)
    console.log(newobj.name)
    newobj.name = '我是newobj'
    console.log(newobj.name)
    console.log(obj.name)

这是因为obj和newobj的name属性指向同一个内存地址，当修改时，修改的是内存地址中的值。



浅拷贝：

语法Object.assign(target, source_1, ···)

用于将源对象的所有可枚举属性复制到目标对象中。

        var obj = {name:'我是obj'}
        var newObj = {}
        Object.assign(newObj,obj)
        console.log(obj.name)
        console.log(newObj.name)
        newObj.name = '我是newobj'
        console.log(obj.name);
        console.log(newObj.name);

第一次输出均为“我是obj”，第二次输出则会分别是“我是obj”和“我是newobj”

浅拷贝的体现 ，当修改newObj.Array的值时，会同时修改obj.Array值。

浅拷贝是指拷贝第一层的基本类型值，以及第一层的引用类型地址。开辟新的内存，使得两者不相互影响。

        var obj = {name:'我是obj',Array:[123]}
        var newObj = {}
        Object.assign(newObj,obj)   
        console.log(obj);
        console.log(newObj);
        newObj.Array[0] = 456
        console.log(obj);
    	/*
    		{name: "我是obj", Array: Array(1)}
            Array: [456]
            name: "我是obj"
    	*/
        console.log(newObj);
    	/*
    		{name: "我是obj", Array: Array(1)}
            Array: [456]
            name: "我是obj"
    	*/

深拷贝：开辟全新的内存空间并将元数据的值（包括后几层的引用数据类型）复制给新元素，两者互不影响。

        var obj = {name:'我是obj',Array:[123]}
        var newObj = {}
        newObj = JSON.parse(JSON.stringify(obj))
        newObj.Array[0] = 456
        console.log(obj);
    	/*
    		{name: "我是obj", Array: Array(1)}
            Array: [123]
            name: "我是obj"
    	*/
        console.log(newObj);
    	/*
    	{name: "我是obj", Array: Array(1)}
        Array: [456]
        name: "我是obj"
    	*/



预编译

    function fn(a,c) {
    	console.log(a)  // function(){}
    	var a = 123
    	console.log(a) // 123
    	console.log(c) // function(){}
    	function a() {}
    	if (false) {
    		var d = 678 // 不会执行
    	}
    	console.log(d) // undefined
    	console.log(b) // undefined
    	var b = function(){}
    	console.log(b) // function(){}
    	function c(){}
    	console.log(c) // function(){}
    }
    fn(1,2)

AO对象

AO对象全称为：activation object （活跃对象/执行期上下文），在函数执行前执行函数预编译，此时会产生一个AO对象，AO对象保存该函数的参数变量。

预编译：指创建作用域时js引擎会做的事：

1. 创建ao对象
2. 找形参和实参的声明，并作为ao对象的属性，值是undefined
   可以用来解释变量声明前输出为undefined的问题
       console.log(a) //	undefined
       var a = 123
3. 实参和形参相统一
4. 找函数声明 覆盖变量声明
    
5. 创建ao对象
       ao：{}
6. 找形参和实参的声明，并作为ao对象的属性，值是undefined
       ao：{
       	a:undefined, 
       	c:undefined, 
       	d:undefined, 
       	b:undefined 
       }
7. 实参和形参相统一,执行fn(1,2)传递实参给了形参
       ao：{
       	a:1, 
       	c:2, 
       	d:undefined, 
       	b:undefined 
       }
8. 找函数声明 覆盖变量声明
   在JavaScript中，有两种方式可以定义一个函数，一个是函数声明，一个是函数表达式。
   函数声明的最重要的一个特征是函数声明提升，意思是在执行代码之前会先读取函数声明，所以函数声明可以放在调用函数语句之后。
   函数声明：
       function fn(){
       	...
       }
   函数表达式：
       var fun = function(){}
       ao：{
       	a:function(){}, 
       	c:function(){}, 
       	d:undefined, 
       	b:undefined 
       }
   JS逐行解释执行。
   

动态增删DOM节点

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>动态增删节点</title>
    </head>
    <body>
        <ul id="myul">
            <li>1</li>
            <li>2</li>
            <li id='deleteLi'>需要删除的li</li>
        </ul>
        <button onclick="addNode()">增加节点</button>
        <button onclick="deleteNode()">删除节点</button>
    </body>
    <script>
        var ul = document.querySelector('#myul')
        function addNode(){
            var newli = document.createElement('li')
            newli.id = '新增类'
            newli.innerHTML = '这是一个新增节点'
            ul.appendChild(newli)
        }
        function deleteNode(){
            var deleteli = document.querySelector('#deleteLi')
            ul.removeChild(deleteli)
        }
    
    </script>
    </html>



VUE数据观察watch

watch

- 类型：{ [key: string]: string | Function | Object | Array }
- 详细：
  一个对象，键是需要观察的表达式，值是对应回调函数。值也可以是方法名，或者包含选项的对象。Vue 实例将会在实例化时调用 $watch()，遍历 watch 对象的每一个 property。
- 示例：
      var vm = new Vue({
        data: {
          a: 1,
          b: 2,
          c: 3,
          d: 4,
          e: {
            f: {
              g: 5
            }
          }
        },
        watch: {
          a: function (val, oldVal) {
            console.log('new: %s, old: %s', val, oldVal)
          },
          // 方法名
          b: 'someMethod',
          // 该回调会在任何被侦听的对象的 property 改变时被调用，不论其被嵌套多深
          c: {
            handler: function (val, oldVal) { /* ... */ },
            deep: true
          },
          // 该回调将会在侦听开始之后被立即调用
          d: {
            handler: 'someMethod',
            immediate: true
          },
          // 你可以传入回调数组，它们会被逐一调用
          e: [
            'handle1',
            function handle2 (val, oldVal) { /* ... */ },
            {
              handler: function handle3 (val, oldVal) { /* ... */ },
              /* ... */
            }
          ],
          // watch vm.e.f's value: {g: 5}
          'e.f': function (val, oldVal) { /* ... */ }
        }
      })
      vm.a = 2 // => new: 2, old: 1
  注意，不应该使用箭头函数来定义 watcher 函数 (例如 searchQuery: newValue => this.updateAutocomplete(newValue))。理由是箭头函数绑定了父级作用域的上下文，所以 this 将不会按照期望指向 Vue 实例，this.updateAutocomplete 将是 undefined。

截取数组

array.splice(startIndex,number)方法

或

array.slice(startIndex,endIndex)

        // `array.splice()`方法:arrayObject.splice(index,howmany,item1,.....,itemX)
        // splice() 方法向在数组中添加/删除项目，然后返回被删除的项目。
        var spliceArray = [1,2,3,4,5,6,7,8]
        var newArr = spliceArray.splice(1,3) // 从1开始，删除3个元素，并将删除的元素作为新数组返回 
        console.log(newArr); // 结果：[2,3,4]
    
        // `slice()` 方法：array：返回一个索引和另一个索引之间的数据(不包括end值,不改变原数组)
        var sliceArray = [1,2,3,4,5,6,7,8]
        var newSliceArray = sliceArray.slice(1,4) // 返回一个index从1到4（不包括4）组成的新数组
        console.log(newSliceArray); // 结果：[2,3,4]



onload

onload 事件会在页面或图像加载完成后立即发生。



块级元素

div、p、h1~h6、ul、ol、li、table

行内元素

span、img、a、input、label、select



call、apply、bind

call()、apply()、bind() 都是用来重定义 this 这个对象的

- call、apply都是立即执行的，bind则不会立即执行。
  call（）、apply（）返回的结果就是函数执行之后的结果。
  bind（）则会返回一个修改过后的函数

        window.onload = function(){
            var obj = {
                name:'我是内部obj',
                age:18,
                fo:function(){
                    console.log('姓名:' + this.name + ',年龄：' + this.age);
                }
            }
            var newObj = {
                name:'我是newObj',
                age:250
            }
            var bindObj = {
                name:'我是bindObj',
                age:249
            }
            // bind修改之后不会立即执行
            obj.fo() // 姓名:我是内部obj,年龄：18
            obj.fo.call(newObj) //  姓名:我是newObj,年龄：250
            obj.fo.apply(newObj) //  姓名:我是newObj,年龄：250
            console.log('------------');
            obj.fo.bind(bindObj) // 不输出,修改之后不会立即执行
            obj.fo.bind(bindObj)() // 添加立即执行函数之后的结果： 姓名:我是bindObj,年龄：249
        }

- call（）函数传递的参数是直接传递，apply（）、bind（）则使用数组传递。
              // 2.apply()传递参数是以数组形式传递的
              var object = {
                  name:'tom',
                  sex:'男',
                  learn:function(subject,secsubject){
                      console.log('姓名：' + this.name + ',性别：' + this.sex + ',正在学' + subject + '和' + secsubject );
                  }
              }
              var elseObject = {
                  name:'Mary',
                  sex:'女'
              }
              object.learn('java') // 姓名:tom,性别：男,正在学java
      
              object.learn.call(elseObject,'javascript','C')  // 姓名：Mary,性别：女,正在学javascript和C
      
              object.learn.apply(elseObject,['微信小程序','Node.js']) // 姓名：Mary,性别：女,正在学微信小程序和Node.js
      
              console.log(object.learn.bind(elseObject,['Go','C#'])); 
              /*
                  ƒ (subject,secsubject){
                      console.log('姓名：' + this.name + ',性别：' + this.sex + ',正在学' + subject + '和' + secsubject 			);
                  }
              */
      
             object.learn.bind(elseObject,['Go','C#'],['还有MySql'])()
             // call、bind、apply.html:45 姓名：Mary,性别：女,正在学Go,C#和还有MySql
  

不定宽高居中

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>不定宽高居中</title>
        <style>
            /* 
                flex布局
             */
            .father{
                width: 500px;
                height: 500px;
                margin: 0 auto;
                background-color: red;
                display: flex;
                justify-content: center;
                align-items: center;
            }
            .son{
                width: 50px;
                height: 50px;
                background-color: pink;
            }
            /* 
                定位    
             */
            .elsefather{
                margin-top: 50px;
                width: 500px;
                height: 500px;
                margin: 50px auto;
                background-color: purple;
                position: relative;
            }
            .elseson{
                width: 50px;
                height: 50px;
                background-color: blue;
                position: absolute;
                top: 50%;
                left: 50%;
                transform: translate(-50%,-50%);
            }        
        </style>
    </head>
    <body>
        <div class="father">
            <div class="son">
                son
            </div>
        </div>
        <div class="elsefather">
            <div class="elseson">
                son
            </div>
        </div>
    </body>
    
    </html>

v-for中为什么要使用key

key目前可以理解为遍历数组或元素中的唯一标识，增加或删减元素时，通过这个唯一标识key判断是否是之前的元素，并且该元素key的值是多少。这个唯一标识是保持不变的。

参见：https://www.zhihu.com/question/61064119

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>v-for问题</title>
    </head>
    <body>
        <div id="app">
            <ul>
                <li v-for="item in arr" :key="item.id">
                    {{item.data}}
                </li>
            </ul>
        </div>
    </body>
    <script src="./vue.min.js"></script>
    <script>
        window.onload = function(){
            var vue = new Vue({
                el:'#app',
                data() {
                    return {
                        arr:[
                            {
                                id:1,
                                data:'happy'
                            },
                            {
                                id:2,
                                data:'sad'
                            },
                            {
                                id:3,
                                data:'bad'
                            },
                            {
                                id:4,
                                data:'good'
                            }
                        ]    
                    }
                },
            })
        }
    </script>
    </html>

请求方式

GET, POST ,HEAD, OPTIONS, PUT, DELETE, TRACE 和 CONNECT 方法



this指向问题，箭头函数的this指向哪里

宏任务 微任务

    try {
        let a = 0;
        setTimeout(() => {
          console.log(a)
        }, 0);
        (async function() {
            a += 1;
            console.log('inner', a);
            throw new Error('123');
            // a()
        })();
        console.log('outer', a);
    } catch(e) {
        console.warn('Error', e);
    }

结果

    innar 1
    outer 1
    Error 123
    1

原因：setTimeout是宏任务，在执行完上一个宏任务（立即执行函数async）之后执行。

解构赋值

    // 解构赋值
    const [a, b, c, ...d] = [1, 2, 3, 11, 999];
    const { e, f: f1, g, ...h } = { f: 4, g: 5, i: 6, j: 7 };
    console.log(a, b, c, d, e, f1, g, h);

结果

    1,2,3,[11,999],undefined,4,5,[i:6,j:7]

展开语法

    let [... arr] = [ 1,2,3,4 ]; // 接收时的效果是收集进数组。
    let [a,b,c,d] = [... arr]; // 赋值时的效果是展开成多个。

Hash和History模式的异同，Hash的API

了解SPA

现代前端项目多为单页Web应用(SPA)，在单页Web应用中路由是其中的重要环节。
SPA 是 single page web application 的简称，译为单页Web应用。
简单的说 SPA 就是一个WEB项目只有一个 HTML 页面，一旦页面加载完成，SPA 不会因为用户的操作而进行页面的重新加载或跳转。 取而代之的是利用 JS 动态的变换 HTML 的内容，从而来模拟多个视图间跳转。

前端路由

简单的说，就是在保证只有一个 HTML 页面，且与用户交互时不刷新和跳转页面的同时，为 SPA 中的每个视图展示形式匹配一个特殊的 url。在刷新、前进、后退和SEO时均通过这个特殊的 url 来实现。
我们需要实现下满两点：

- 改变 url 且不让浏览器像服务器发送请求。
- 可以监听到 url 的变化
- 可以在不刷新页面的前提下动态改变浏览器地址栏中的URL地址

hash 模式和 history 模式，就是用来实现上面功能的

Hash模式

在url后面加上#，如http://127.0.0.1:5500/前端路由/hash.html#/page1这个url后面的#/page1就是hash值

- hash 值的变化不会导致浏览器像服务器发送请求
- location.hash可以获取hash值
- hashchange是hash值发生改变的调用的函数

基于以上三点我们可以写一个路由实例

    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <meta http-equiv="X-UA-Compatible" content="ie=edge" />
        <title>Document</title>
      </head>
      <body>
        <ul>
          <li><a href="#/">/</a></li>
          <li><a href="#/page1">page1</a></li>
          <li><a href="#/page2">page2</a></li>
        </ul>
        <div class="content-div"></div>
      </body>
      <script>
        class RouterClass {
          constructor() {
            this.routes = {}; // 记录路径标识符对应的cb
            this.currentUrl = ""; // 记录hash只为方便执行cb
            window.addEventListener("load", () => this.render());
            window.addEventListener("hashchange", () => this.render());
          }
    
          /* 初始化 */
          static init() {
            window.Router = new RouterClass();
          }
    
          /* 注册路由和回调 */
          route(path, cb) {
            this.routes[path] = cb || function() {};
          }
    
          /* 记录当前hash，执行cb */
          render() {
            this.currentUrl = window.location.hash.slice(1) || "/";
            this.routes[this.currentUrl]();
          }
        }
    
    
        RouterClass.init();
        const ContentDom = document.querySelector(".content-div");
        const changeContent = content => (ContentDom.innerHTML = content);
    
        Router.route("/", () => changeContent("默认页面"));
        Router.route("/page1", () => changeContent("page1页面"));
        Router.route("/page2", () => changeContent("page2页面"));
      </script>
    </html>

History模式

History 接口允许操作浏览器的曾经在标签页或者框架里访问的会话历史记录。可以参考下两篇文章对history的说明
https://css-tricks.com/using-the-html5-history-api/
https://developer.mozilla.org/zh-CN/docs/Web/API/History
下面介绍在这个模式下需要用到的api

history基本api

- history.go(n)：路由跳转几步，n为2往前跳转2个页面，-2往后跳转两个页面
- history.back()：路由后退，相当于 history.go(-1)，用户可点击浏览器左上角的后退按钮模拟此方法
- history.forward()：路由前进，相当于 history.go(1)，用户可点击浏览器左上角的前进按钮模拟此方法
- 

pushState()

history.pushState()：添加一条路由历史记录，如果设置跨域网址则报错

history.pushState用于在浏览历史中添加历史记录,但是并不触发跳转,此方法接受三个参数，依次为：
state:一个与指定网址相关的状态对象，popstate事件触发时，该对象会传入回调函数。如果不需要这个对象，此处可以填null。
title：新页面的标题，但是所有浏览器目前都忽略这个值，因此这里可以填null。
url：新的网址，必须与当前页面处在同一个域。浏览器的地址栏将显示这个网址。

window的popstate事件

当活动历史记录条目更改时，将触发popstate事件。如果被激活的历史记录条目是通过对history.pushState（）的调用创建的，或者受到对history.replaceState（）的调用的影响，popstate事件的state属性包含历史条目的状态对象的副本。
需要注意的是调用history.pushState()或history.replaceState()不会触发popstate事件。只有在做出浏览器动作时，才会触发该事件，如用户点击浏览器的回退按钮（或者在Javascript代码中调用history.back()）

    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <meta http-equiv="X-UA-Compatible" content="ie=edge" />
        <title>Document</title>
      </head>
      <body>
        <ul>
          <li><a href="/">/</a></li>
          <li><a href="/page1">page1</a></li>
          <li><a href="/page2">page2</a></li>
        </ul>
        <div class="content-div"></div>
      </body>
      <script>
        class RouterClass {
          constructor(path) {
            this.routes = {}; // 记录路径标识符对应的cb
            history.replaceState({ path }, null, path); // 进入状态
            this.routes[path] && this.routes[path]();
            window.addEventListener("popstate", e => {// 当用户点击浏览器的前进或者后退触发
                console.log(e.state)
              const path = e.state && e.state.path;
              this.routes[path] && this.routes[path]();
            });
          }
          
          /* 初始化 */
          static init() {
            window.Router = new RouterClass(location.pathname);
          }
    
          /* 注册路由和回调 */
          route(path, cb) {
            this.routes[path] = cb || function() {};
          }
    
          /* 跳转路由，并触发路由对应回调 */
          go(path) {
            
            history.pushState({ path }, null, path);
            console.log(history);
            this.routes[path] && this.routes[path]();
          }
        }
    
        RouterClass.init();
        const ul = document.querySelector("ul");
        const ContentDom = document.querySelector(".content-div");
        const changeContent = content => (ContentDom.innerHTML = content);
    
        Router.route("/", () => changeContent("默认页面"));
        Router.route("/page1", () => changeContent("page1页面"));
        Router.route("/page2", () => changeContent("page2页面"));
    
        ul.addEventListener("click", e => {
          console.log(e.target.tagName);
          if (e.target.tagName === "A") {
            e.preventDefault();
            Router.go(e.target.getAttribute("href"));
          }
        });
      </script>
    </html>

Hash 模式和 History 模式对比

Hash 模式是使用 URL 的 Hash 来模拟一个完整的 URL，因此当 URL 改变的时候页面并不会重载。History 模式则会直接改变 URL，所以在路由跳转的时候会丢失一些地址信息，在刷新或直接访问路由地址的时候会匹配不到静态资源。因此需要在服务器上配置一些信息，让服务器增加一个覆盖所有情况的候选资源，比如跳转 index.html 什么的

hash路由 优缺点

- 优点
  - 实现简单，兼容性好（兼容到ie8）
  - 绝大多数前端框架均提供了给予hash的路由实现
  - 不需要服务器端进行任何设置和开发
  - 除了资源加载和ajax请求以外，不会发起其他请求
- 缺点
  - 对于部分需要重定向的操作，后端无法获取hash部分内容，导致后台无法取得url中的数据，典型的例子就是微信公众号的oauth验证
  - 服务器端无法准确跟踪前端路由信息
  - 对于需要锚点功能的需求会与目前路由机制冲突

History(browser)路由 优缺点

- 优点
  - 对于重定向过程中不会丢失url中的参数。后端可以拿到这部分数据
  - 绝大多数前段框架均提供了browser的路由实现
  - 后端可以准确跟踪路由信息
  - 可以使用history.state来获取当前url对应的状态信息
- 缺点
  - 兼容性不如hash路由(只兼容到IE10)
  - 需要后端支持，每次返回html文档

跨域问题

    app.use(cors())
    // 解决跨域问题
    app.all('*', function(req, res, next) {
      res.header("Access-Control-Allow-Origin", "*");
      res.header("Access-Control-Allow-Headers", "X-Requested-With");
      res.header("Access-Control-Allow-Methods","PUT,POST,GET,DELETE,OPTIONS");
      res.header("X-Powered-By",' 3.2.1')
      res.header("Content-Type", "application/json;charset=utf-8");
      next();
    });



Node

    /**
     * 后端入口文件
     */
    const express = require('express')
    const router = require('./router/index')
    const bodyParser = require('body-parser')
    const cors = require('cors')
    
    // 创建 express 应用
    const app = express()
    
    app.use(cors())
    
    app.use(bodyParser.urlencoded({ extended: true }))
    app.use(bodyParser.json())
    
    app.use(router)
    
    // 解决跨域问题
    app.all('*', function(req, res, next) {
      res.header("Access-Control-Allow-Origin", "*");
      res.header("Access-Control-Allow-Headers", "X-Requested-With");
      res.header("Access-Control-Allow-Methods","PUT,POST,GET,DELETE,OPTIONS");
      res.header("X-Powered-By",' 3.2.1')
      res.header("Content-Type", "application/json;charset=utf-8");
      next();
    });
    // 监听 / 路径的 get 请求
    app.get('/',router)
    
    // express 监听18082
    const server = app.listen(18082, function() {
      console.log('Http Server is running on 18082')
    })


