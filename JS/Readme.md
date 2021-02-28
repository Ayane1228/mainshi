#### 错题：

```js
var foo = {n:1};
(function(foo){
    var foo
	console.log(foo.n)
	foo.n = 3;
	var foo = {n:2};
	console.log(f00.n)
	})(foo)
	console.log(f00.n)
```

结果：

```js
var foo = {n:1};
(function(foo){ //形参foo和实参foo指向同一批内存空间，这个内存空间中的n为1
    var foo // 重新赋值，无效
	console.log(foo.n) //输出1
	foo.n = 3; //形参与实参foo共同指向的内存空间里的n的值被改为3
	var foo = {n:2}; //形参foo指向了新的内存空间，里面n的值为2.
	console.log(f00.n)//输出形参中新的内存空间的n的值
	})(foo)
	console.log(f00.n) //实参foo的指向还是原来的内存空间，里面的n的值为3.
```

#### 题目

```js
function test(){
	var n =4399;
	function add(){
	n++;
	console.log(n)
	}
	return {n:n,add:add}
}
var result = test()
var result2 = test()
result.add() //4400
result.add() //4401
console.log(result.n) 
result2.add()
```

> 结果：4400，4401，4399，4400
>
> 定义了一个test的函数，函数中定义了一个值n和函数add，因此可以将test看作一个对象。外部调用了2次,所以result和r2都是4399。
>
> result:
>
> ​		`result.add()`
>
> ```js
> n = 4399
> n++ ,n = 4400;
> console.log(n) 4400
> ```
>
> ​		`result.add()`
>
> ```js
> n = 4400
> n++, n = 4401
> console.log(4401)
> ```
>
> 第三个`console.log(result.n) `实际相当于输出的是`console.log(test().n)`并没有执行`add()`函数所以还是4399.
>
> 第四个`result2.add()`对result执行了add()函数，所以为4400(4399 + 1)
>



#### 题目

```js
var x = new Boolean(false);
if (x) // 相当于if(new Boolean(false)) => if(true) 
{
  alert('hi');
}
var y = Boolean(0);
if (y) {
  alert('hello'); 
}
```

> 如果Boolean构造函数的参数不是一个布尔值,则该参数会被转换成一个布尔值.**如果参数是0, -0 ,null , false ,NaN , undefined ,或者空字符串(""),生成的Boolean对象的值为false.**其他任何值,包括任何对象或者字符串"false"，,都会创建一个**值为true的Boolean对象**.

X：new调用构造函数,构造了一个boolean对象,所以x 的布尔值应为true，而会输出`hi`。下面直接定义布尔原始值则有效

```js
var x = false
if (x) // 相当于if(false) 
{
	//此处不会输出
}
```

y:

```js
var y = Boolean(0) // 将0转换为布尔值  => var y = false
if (y) {
	//不会输出
}
```



#### 对于代码 var a = 10.42; 取出 a 的整数部分，以下代码哪些是正确的？

> parseInt(a);
>
> Math.floor(a);
>
> Math.ceil(a);
>
> a.split('.')[0];



答案：A,B

ceil：天花板。floor：地板。

> A:	parseInt(a);将数字转为整数，与B相同直接去掉小数部分
>
> B：Math.floor(a);向下取整，直接去掉小数部分
>
> c：Math.ceil(a);向上取整，去掉小数部分后加1
>
> D:将**字符串**`‘.’`前后进行分割，分割为2个数组,但a位数字，没有`split`方法,可修改为
>
> ```js
> var a = '10.42';
> console.log(a.split('.')[0])
> ```
>
> Math.round(a): 对a进行四舍五入，输出整数，结果为10.



问题：

#### 以下哪些对象是Javascript内置的可迭代对象？

> Array
>
> Map
>
> String
>
> Object

答案：A,B,C

> ES6 规定，默认的 Iterator 接口部署在数据结构的Symbol.iterator属性，或者说，一个数据结构只要具有Symbol.iterator属性，就可以认为是“可遍历的”（iterable）。
>
> 遍历器（Iterator）它是一种借口，为各种不同的数据结构提供统一的访问机制。 任何数据结构只要部署Iterator接口，就可以完成遍历操作（即依次处理该数据结构的所有成员）。
>
> 原生具备 Iterator 接口的数据结构如下。
>
> 1. Array
>
> 2. Map
>
> 3. Set
>
> 4. String
>
> 5. TypedArray
>
> 6. 函数的 arguments 对象
>
>    **`arguments`** 是一个对应于传递给函数的参数的类数组对象。
>
>    ```js
>    function func1(a, b, c) {
>      console.log(arguments[0]);
>      // expected output: 1
>    
>      console.log(arguments[1]);
>      // expected output: 2
>    
>      console.log(arguments[2]);
>      // expected output: 3
>    }
>    
>    func1(1, 2, 3);
>    // 结果
>    /*
>            1
>            2
>            3
>    */
>    ```
>
> 7. NodeList 对象



题目：

```js
for(let i = 0;i < 12; i++) console.log(i)
```

> `let`有函数作用域，最终会输出`i not defined`

```js
const a = 12;
a = 13;
console.log(a)
```

> 使用`const`定义的`a`是一个常量，不能重复赋值，输出`TypeError`

```js
const g = {b:3};
console.log(g.b);
g.b = 12
console.log(g.b);
```

> 正常输出3，12，因为这里`const`定义的是一个对象，输出的是对象的一个属性。

```js
let [head,...tail] = [1,2,3,4];
console.log(tail)
```

> 结果：[2,3,4]，
>
> ES6语法中的解构赋值，
>
> ```js
> console.log(head)；
> // 结果
> 1；
> ```
>
> ...运算符有两种意义，将一个数组转为用逗号分隔的参数序列。



```js
var str = "Hellllo world";
str = str.replace(/(l)\1/g, '$l);
```

> 正则替换，将正则表达式的值替换.
>
> 正则表达式：`/（l）\1/g`, `/ /g`表示这个正则表达式执行全局匹配。
>
> `()`,表示分组，`\1`表示和括号中内容相同，正则表达式相当于/(ll)/g。
>
> `$1`表示替换为分组中第一个出现的值，即替换为`l`。                                        



在文件/home/somebody/workspace/somemodule.js中第一行引用了一个模块：require(‘othermodule‘)，请问required 的查找模块的顺序
A. /home/somebody/workspace/node_modules/othermodule/index.js
B. /home/somebody/workspace/node_modules/othermodule. Js
C.CORE MODULES named othermodule
D./home/somebody/node_modules/othermodule/index.js

> (1):首先，Node在当前目录下查找package.json(CommonJS包规范定义的包描述文件)，通过JSON.parse()解析出包描述对象，从中取出main属性指定的文件名进行定位。如果文件缺少扩展名，将会进入扩展名分析的步骤。 
>
> (2):而如果main属性制定的文件名错误，或者压根没有package.json文件，Node会将index当做默认文件名，然后依次查找index.js、index.node、index.json. 　　
>
> (3):如果在目录分析的过程中没有定位成功任何文件，则自定义模块进入下一个模块路径进行查找。如果模块路径数组都被遍历完毕，依然没有查找到目标文件，则会抛出查找失败异常。 　　
>
> 按照上面的思路，首先应该查找package.json文件，看看里面有没有核心模块，应该是C最先，othermodule不是核心模块，那么接着应该进入扩展名分析的步骤，就应该是查找othermodule. js，对应B，紧接着就是以index为默认文件名，也就是A，再接下来就是上一个文件目录D了，
> 所以答案是： C B A D



触摸事件包括?

> touchstart、touchmove、touchend 



```js
var a = [1,4,5,2,9];
```

下面求a中最大值正确的是

```
Math.max(a)
Array.max(a)
Math.max.call(null,a)
Math.max.apply(null,a)
以上均不是
```

答案

```js
Math.max.apply(null,a)
```

> A：Math.max(a) 
>  **Math**.max()方法比较的是多个数值参数，**不接受一个数组**作为参数，可用展开符取出数组元素作为参数使用， Math.max(...a) 
>  更多关于Math.max()的用法可以查看： https://developer.mozilla.org/zh-TW/docs/Web/JavaScript/Reference/Global_Objects/Math/max       
>
> ​    B：Array.max(a)
>  Array类型没有定义这个方法。详情可查看：https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array       
>
> ​    C：Math.max.call(null,a)      
>
> ​    D：Math.max.apply(null,a)
>
>  关于C和D的区别其实是.call()方法和.apply()方法的区别:
>  语法格式对比：.call(对象,参数1,参数2)，VS .apply(对象,[参数1,参数2])，
>  它们的第一个对象类型的参数都是用来重定向this的,从第二个参数开始.**call()是直接一个个传入,而.apply()是支持传入一个参数数组**
>  所以D正确而C错误，参考A，将C改为Math.max.call(null,...a)即为正确。
>  详情可看：https://www.runoob.com/w3cnote/js-call-apply-bind.html