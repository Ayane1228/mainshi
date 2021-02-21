# 突击面试

## HTML CSS3

- 盒子水平和垂直居中的五大方案

  1. 基于定位(position)的三种方式：子绝父相,absolute:绝对；relative：相对
                 1.子盒子定位到父盒子的50%,50%,再使用transform属性使子盒子沿着X,Y轴偏移自己宽高的50%，需要浏览器支持transform属性
                 2.子盒子定位到父盒子的50%,50%，再使用margin值进行偏移：margin-top：-50px；margin-left:-50px,需要知道子盒子的具体宽高
                 3.设置top、right、bottom、left均为0，利用margin:auto;设置margin值使得居中,需要子盒子有具体的宽高

  2. flex:给父元素设置display：flex，将父盒子变为弹性容器，再设置弹性子元素的对齐方式：设置主轴线对齐方式:justify-content：center;设置侧轴对齐方式align-items：center；

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

  