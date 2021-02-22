## HTML CSS3

- ## HTML

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

  ​	伪元素： `::after`,`::before`,`::first-line`。能够选择当前元素的后、前、和这些元素的第一行的**元素**。

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

  结果：https://github.com/Ayane1228/mainshi/blob/main/HTML%2BCSS/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202021-02-22%20234921.png。

  ​	会在类名为`boring-text`的p标签后添加颜色为red，内容为<- 无聊!的`::after`元素。









































































- ## 盒子水平和垂直居中的五大方案

  1. 基于定位(position)的三种方式：子绝父相,absolute:绝对；relative：相对
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