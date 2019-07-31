`JavaScript`是运行在浏览器端的脚本语言，`JavaScript`主要解决的是前端与用户交互的问题，包括使用交互与数据交互，`JavaScript`是浏览器解释执行的。

1. `JavaScript`是一种客户端脚本语言
2. `JavaScript`通常被直接嵌入`html`页面
3. `JavaScript`是一种解释性语言

## `<script>`元素

属性

`async`：可选，值为`async`。表示应该立即下载脚本，但不应妨碍页面中的其他操作，比如下载其他资源或等待加载其他脚本。只对外部脚本文件有效。

`defer`：可选，值为`defer`。表示脚本可以延迟到文档完全被解析和显示之后再执行。只对外部脚本文件有效。

无论如何包含代码，只要不存在`defer`和`async`属性，浏览器都会按照`<script>`元素在页面中出现的先后顺序对它们依次进行解析。

使用`<noscript>`元素可以指定在不支持脚本的浏览器中显示的替代内容。但在启用了脚本的情况下，浏览器不会显示`<noscript>`元素的内容。

### `XHTML`

在`XHTML`中，`CData`片段是文档中的一个特殊区域，这个区域中可以包含不需要解析的任意格式的文本内容。这种格式在所有现代浏览器中都可以正常使用，它能通过`XHTML`验证，而且对`XHTML`之前的浏览器也会平稳退化。

```XHTML
<script>//<![CDATA[
        function compare(a,b){
            if(a<b)
                alert("A is less than B");
            else if(a>b)
                alert("A is greater than B");
            else
                alert("A is equal to B");
        }
   // ]]>
</script>
```

### 嵌入页面的方式

**1、script标签嵌入**

```html
<script type="text/javascript">
    var a='NIHAO';
	alert(a);
</script>
```

**2、外链式**

通过`script`标签的`src`属性来引入外部js文件，如果使用`script`标签外部引入js文件，那此标签中就不能再写js程序，会不执行。

```html
<body>
    <script src="./1.js"></script>
</body>
```

**3、行间样式**

```html
<body>
    <!--单击div触发事件-->
    <div onclick="alert('行间')">
    </div>
    <a href="javascript:void(0)" onclick="alert('')"></a>
</body>
```

### 数据类型

定义变量需要用关键字   `'var'`

布尔类型：true、false

数据类型：二进制数以0b开头，八进制数以0开头，十六进制数以0x开头，NaN

**字符串类型：只要是用单引号或双引号引起来的字符都是字符串类型，单双引号可以嵌套使用**

**方法**

`trim()`创建一个字符串的副本，删除前置及后缀的所有空格，返回结果，原始字符串中的前置及后缀空格会保持不变。

`toLowerCase()  toLocaleLowerCase() toUpperCase() toLocaleUpperCase() `字符串大小写转换方法。

**`match()`**只接受一个参数，要么是一个正则表达式，要么是一个`RegeExp`对象。

**`search()`**的唯一参数与**`match()`**方法的参数相同。返回字符串中第一个匹配项的索引，如果没有找到匹配项，则返回-1。始终从字符串开头向后查找模式。

**`replace()`**接受两个参数：第一个参数可以是一个字符串或一个函数。如果第一个参数是字符串，那么只会替换第一个子字符串，要想替换所有子字符串，唯一的方法就是提供一个正则表达式，而且要指定全局`(g)`标志。

~~~javascript
//match()
var text = "cat,bat,sat,fat";
var pattern = /.at/;
var matches = text.match(pattern);
alert(matches.index);		//0
alert(matches[0]);		    //"cat"
alert(pattern.lastIndex);	//0

//search()
var pos = text.search(/at/);
alert(pos);				   //1

//replace
var result = text.replace("at","ond");
alert(result);			   //"cond,bat,sat,fat"
result = text.replace(/at/g,"ond");
alert(result);			   //"cond,bond,sond,fond"
~~~

**`split()`**可以基于指定的分隔符将一个字符串分隔成多个子字符串，并将结果放在一个数组中。可以接受可选的第二个参数，用于指定数组的大小，以便确保返回的数组不会超过既定大小。

~~~javascript
var colorText = "red,blue,green,yelow";
var colors1 = colorText.split(",");		//["red","blue","green","yellow"]
var colors2 = colorText.split(",",2);	//["red","blue"]
var colors3 = colorText.split(/[^\,]+/);	//["",",",",",",",""]
~~~

**`localeCompare()`**比较两个字符串。如果字符串在字母表中应该排在字符串参数之前，则返回一个负数，以此类推。

~~~javascript
var stringValue = "yellow";
alert(stringValue.localeCompare("brick"));	//1
alert(stringValue.localeCompare("yellow"));		//0
alert(stringValue.localeCompare("zoo"));	//-1
//推荐使用以下函数使用这个方法
function determineOrder(value){
    var result = stringValue.localeCompare(value);
    if(result<0){
        alert("The string 'yellow' comes before the string")
    }else if(reslut>0){
    }
}
~~~

### 单体内置对象

**`global`对象**  `isNaN()、isFinite()、parseInt()、parseFloat()`都是`global`对象

**`URI`编码方法**

**`encoodeURI()和encodeURIComponent()`**方法可以对`URI`进行编码，以便发送给浏览器。

与`encoodeURI()和encodeURIComponent()`方法对应的两个方法分别是**`decodeURI()和decodeURIComponent()`**。其中，`decodeURI()`只能对使用`encodeURI()`替换的字符进行解码。

**`eval()`方法**

就像是一个完整的`ECMAScript`解析器，它只接受一个参数，即要执行的`ECMAScript`字符串。当解析器发现代码中调用`eval()`方法时，它会将传入的参数当作世纪的`ECMAScript`语句来解析，然后把执行结果插入到原位置。通过`eval()`执行的代码被认为是包含该次调用的执行环境的一部分，因此被执行的代码具有与该执行环境相同的作用域链。

**`window`对象**

`ECMAScript`虽然没有指出如何直接访问`Global`对象，但`Web`浏览器都是将这个全局对象作为`window`对象的一部分加以实现的。因此，在全局作用域中声明的所有变量和函数，就都成了`window`对象的属性。

对象类型：对象 `obj={name:'zs',age:18};`

   		数组   `list=[1,2,3,4]; `

  		 null

函数数据类型：

```
var Func=function(){
    console.log('这是一个函数')
}
```

`alert()`通过弹窗显示()中的内容，`console.log()`将结果打印到控制台

### 数据类型转换

`Number()`、`parseInt()`、`parseFloat()`

当字符串中包含任意一个非数值表示的字符时，`Number()`返回NaN，`parseInt()`,`parseFloat()`返回从头开始如果碰到非数值类型表示的字符时，后面的内容就舍去，当字符串一开始就是非数值的字符串，都返回NaN。

`isNaN()`   检测一个数据是否是一个数，如果是数，返回false，如果不是数，返回true

`Boolean()`  当空字符串时，结果为false；当数值为0时，结果为false；当对象为null时，结果为false。

`toString()` 转换成字符串，可以将进制作为参数，输出该进制下的字符串类型

`toFixed()`按照指定的小数位返回数值的字符串表示，传递的参数意思是显示几位小数，可以四舍五入。

`toExponential()`返回以指数表示法（e表示法）表示的数值的字符串形式。

```javascript
var num = 10;
alert(num.toExponential(1));		//"1.0e+1"
```

`toPrecision()`可能会返回固定大小格式，也可能返回指数格式。

```javascript
var num = 99;
alert(num.toPrecision(1));			//"1e+2"
alert(num.toPrecision(2));			//"99"
alert(num.toPrecision(3));			//"99.0"
```

===   全等。在比较时，除了值相等，两边的类型也必须相同

！==   全不等。也比较两边的类型

### 循环

for循环

```
for(var i=0;i<len;i++){}
```

for...in循环

是严格的迭代语句，用于枚举对象的属性。

```javascript
var a = [10,20,30,40,50];
for(i in a){
    document.write(a[i]);
}
```

### 元素获取与操作

可以使用内置对象document上的getElementByld方法来获取页面上设置了id属性的元素，获取到的是一个html对象，然后将它赋值给一个变量

```html
<body>
    <div id="item1">
        <script>
            var oDiv=document.getElementById("item1");
            //oDiv的值是<div id="item1"></div>
        </script>
    </div>
</body>
```

如果将JavaScript写在元素的上面，就会出错，因为页面上从上往下加载执行的，要么将JavaScript放在页面最下边，要么将JavaScript语句放在window.onload触发的函数里面，获取元素的语句会在页面加载完成后才执行

```html
<script type="text/javascript">
    window.onload=function(){
        var oDiv=document.getElementById('div1');
    }
</script>
```

### 样式操作

在设置样式的时候，如果有些属性是双拼词，要把横杠去掉，第二个单词大写

```html
<body>
    <div id="item1">
        <script>
            var oDiv=document.getElementById("item1");
            //oDiv的值是<div id="item1"></div>
            oDiv.style.width="200px";
            oDiv.style.background="red";
            oDiv.style.fontSize="30px";
        </script>
    </div>
</body>
```

### 文本操作

操作元素的文本内容     innerHTML，会覆盖原来的内容

innerHTML   一般用来设置内容，可以解析标签，获取内容时连同标签一起获取。`oDiv.innerHTML='222';    oDiv.innerHTML='<p>222</p>';`

innerText      解析不了标签，一般只用来获取文本

### 表单操作

通过id获取表单元素对象，获取表单的值，元素对象.value

```html
<script>
    vl=document.getElementById('uname');
    vl.value='888';
</script>
<input type="text" value="123" name="username" id="uname">
```

### 定时器

在一个设定的时间间隔之后来执行代码，而不是在函数被调用后立即执行。

作用：1、制作动画

​	   2、异步操作

**1、单次定时器**

`setTimeout(function(){},1000)`，第一个参数是回调函数，第二个参数是时间。指定时间之后执行特定的功能

清除定时器：`clearTimeout()`

`setTimeout`的方式(注册事件)：有两个参数，第一个参数是函数，第二参数是时间值。调用`setTimeout`时，把函数参数，放到事件队列中。等主程序运行完，再调用。

```html
<script>
    setTimeout(function(){
        console.log('单次定时器启动了')
    },3000)
    //在执行之后3秒在控制台显示引号里的内容
</script>
```

**2、循环定时器**

`setInterval(function(){},time)`，间隔指定时间执行一次特定的功能

清除定时器：启动定时器之后，会返回一个标识符，通过这个标识符来清除定时器   clearInterval()

```html
<script>
    var set=setInterval(function(){
        console.log('');
    },2000);
    setTimeout(function(){//清除定时器
        clearInterval(set);
    },6000);
</script>
```

定时器的简单使用

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>动画</title>
	<style>
		#item1{
			width: 50px;
			height: 50px;
			background: pink;
		}
	</style>
</head>
<body>
	<div id="item1"></div>
	<script>
		var oDiv=document.getElementById('item1');
		var i=0;
		var set=setInterval(function(){
			oDiv.style.width=i+'px';
			oDiv.style.height=i+'px';
			i++;
			if(i==200)
				clearInterval(set);
		},33);
	</script>
</body>
</html>
```

### 函数

**两种定义方式**

1、`function demo(){}   `        调用：`demo();`	==可以把函数声明放在调用它的语句后面==

2、`var demo=function(){}  `  调用：`demo();`	==匿名函数==

函数在调用的时候，不传实参函数依然可以执行，形参返回`undefined`，多传参数，多余的参数会被省略。当形参个数与实参个数不相等时，可以通过遍历`argument`属性来获取实参。

```html
<script>
    function demo(){
        for(i in arguments){
            console.log(argument[i]);
        }
    }
    demo(1,2,3,4);
</script>
```

==函数调用过程==

当某个函数被调用时，会创建一个执行环境（`execution context`）及相应的作用域链。然后，使用`arguments`和其他命名参数的值来初始化函数的活动对象（`activation object`）。但在作用域中，外部函数的活动对象始终处于第二位，外部函数的外部函数的活动对象处于第三位，直到作为作用域链终点的全局执行环境。

**属性**

`length`和`prototype`，`length`属性表示函数希望接收的命名参数的个数

**方法**

`apply()，call()`，这两个方法的用途都是在特定的作用域中调用函数，实际上等于设置函数体内`this`对象的值。

`apply()`方法接收两个参数：一个是在其中运行函数的作用域，另一个是参数数组。第二个参数可以是`Array`的实例，也可以是`arguments`对象。

```javascript
function sum(num1,num2){
    return num1+num2;
}
function callSum1(num1,num2){
    return sum.apply(this,arguments);
}
function callSum2(num1,num2){
    return sum.apply(this,[num1,num2]);
}
alert(callSum1(10,10));		//20
alert(callSum2(10,10));		//20
```

`call()`方法与`apply()`方法的作用相同，它们的区别在于接收参数的方式不同。第一个参数是`this`值没有变化，变化的是其余参数都直接传递给函数。在使用`call()`方法时，传递给函数的参数必须逐个列举出来。

```javascript
function(num1,num2){
    return num1+num2;
}
function(num1,num2){
    return sum.call(this,num1,num2);
}
alert(callSum(10,10));		//20
```

这两种方法能够扩充函数赖以运行的作用域。对象不需要与方法有任何耦合关系。

```javascript
window.color = "red";
var o  = {color:"blue"};
function sayColor(){
	alert(this.color);
}
sayColor();					//red
sayColor.call(this);		 //red
sayColor.call(window);	     //red
sayColor.call(o);			//blue
```

为了消除紧密耦合的现象，可以使用**`arguments.callee`**，无论引用函数时使用的是什么名字，都可以保证正常完成递归调用。当函数在严格模式下运行时，访问**`arguments.callee`**会导致错误

```javascript
function factorial(num){
    if(num<=1){
        return 1;
    }else{
        return num * arguments.callee(num-1);
    }
}
```

`bind()`方法会创建一个函数的实例，其`this`值会被绑定到传给`bind()`函数的值。

**递归**

以下对递归函数的调用可能导致出错。

~~~javascript
var anotherFactorial = factorial;
factorial = null;
alert(anotherFactorial(4));
~~~

**`arguments.callee`**是一个指向正在执行的函数的指针，因此可以用它来实现对函数的递归调用。以下代码使用**`arguments.callee`**代替函数名，可以确保无论怎样调用函数都不会出问题。在编写递归函数时，使用这个总比使用函数名更保险。

```javascript
function factorial(num){
    if(num<=1){
        return 1;
    }else{
        return num*arguments.callee(num-1);
    }
}
```

### 闭包

闭包是指有权访问另一个函数作用域中的变量的函数。创建闭包的常见方式，就是在一个函数内部创建另一个函数。

~~~javascript
function createComparisonFunction(propertyName){
    return function(object1,object2){
        var value1 = object1[propertyName];
        var value2 = object2[propertyName];
        if(value1<value2){
            return -1;
        }else if(value1>value2){
            return 1;
        }else {
            return 0;
        }
    };
}
~~~

访问了外部函数中的变量`propertyName`。即使这个内部函数被返回了，而且是在其他地方被调用了，但它仍然可以访问变量。之所以还能够访问这个变量，是因为内部函数的作用域链中包含`createComparisonFunction`的作用域。

~~~javascript
function makeAdder(x){
    return function(y){
        return x+y;
    };
}
var add5 = makeAdder(5);
var add10 = makeAdder(10);
console.log(add5(2));		//7
console.log(add10(2));		//12
~~~

在上面这个示例中，从本质上讲，`makeAdder`是一个函数工厂，他创建了将指定的值和它的参数相加求和的函数。`add5和add10`都是闭包，他们共享相同的函数定义，但是保存了不同的词法环境，在`add5`的环境中，`x`是5。而在`add10`中，`x`为10。

==闭包很有用==，因为它允许将函数与其所操作的某些数据关联起来。这类似于面向对象编程。在面向对象编程中，对象允许我们将某些数据与一个或多个方法相关联。

==用闭包模拟私有方法==

<https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Closures>

~~~
函数表达式不同于函数声明。函数声明要求有名字，但函数表达式不需要。
递归函数应该始终使用arguments.callee来递归地调用自身，不要使用函数名。
当在函数内部定义了其他函数时，就创建了闭包。闭包有权访问包含函数内部的所有变量。
~~~

### 对象

**1、使用原始的方式创建内置函数**

```javascript
var myobject = new Object();
myobject.name = "lijie";
myobject.age=20;
myobject.say=function(){}
```

**2、直接创建自定义对象**

var 对象名 = {属性名1：属性值，属性名2：属性值2...}

**3、使用自定义构造函数创建对象**

```javascript
function pen(name,color,price){
    this.name=name;
    this.color=color;
    this.price=price;
    this.say=function(){};
}
```

### 数组

```
var arr=new Array(1,2,3);
var arr=['1',2,3];
var names = new Array("Greg");			//创建一个包含1项的数组
```

**`push()`**和**`pop()`**从数组最后增加成员或删除成员

**`unshift()`**和**`shift()`**从数组前面增加成员或删除成员

**`splice()`**在数组中增加或删除元素，如果只有一个参数，就是从第一个元素后开始删除所有的元素。如果传了两个参数，就是从指定元素开始删除指定个元素，第二个参数指定删除的个数。第三个参数，用来替换删除之后的元素。第三个参数之后的所有参数都是用来替换删除的元素。始终都会返回一个数组，该数组中包含从原始数组中删除的项==如果没有删除任何项，则返回一个空数组==

**`slice()`**基于当前数组中的一或多个项创建一个新数组。可以接受一或两个参数，即要返回项的起始和结束位置。如果只有一个参数，返回从该参数指定位置开始到当前数组末尾的所有项。有两个参数，返回起始和结束位置之间的项，但不包括结束位置的项。==不会影响原始数组==。

**`join()`**，可以使用不同的分隔符赖构建字符串。`colors.join("||")`   `//red||green||blue`

**`toString()`**返回数组的字符串表示，每个值得字符串表示凭拼接成了一个字符串，中间用逗号分隔。

**`toLocaleString()`**也会创建一个数组值得以都好分隔的字符串。

**`reverse()`**反转数组项的顺序

**`sort()`**可以接收一个比较函数作为参数，以便我们指定哪个值位于哪个值前面。

```javascript
function compare(value1,value2){
    if(value1<value2){
        return -1;
    }else if(value1>value2){
        return 1;
    }else{
        return 0;
    }
}
var values = {0,1,5,10,15};
values.sort(compare);
```

**`indeOf()`**和**`lastIndexOf()`**接收两个参数：要查找的项和（可选的）表示查找起点位置的索引。`indexOf()`方法从数组的开头开始向后查找，`lastIndexOf()`从数组的末尾开始向前查找。都返回要查找的项在数组中的位置，或者在没找到的情况下返回-1。

**`reduce()`和`reduceRight()`**迭代数组的所有项，构建一个最终返回的值。这两个方法都接收两个参数：一个在每一项上调用的函数和（可选的）作为归并基础的初始值。传给这两个函数接收4个参数：前一个值、当前值、项的索引值和数组对象。这个函数返回的任何值都会作为第一个参数自动传给下一项。第一次迭代发生在数组的第二项上，因此第一个参数是数组的第一项，第二个参数是数组的第二项。

```javascript
var values = [1,2,3,4,5];
var sum = values.reduce(function(prev,cur,index,array){
    return prev+cur;
})
alert(sum);		//15
```

`instanceof`操作符可以确定某个对象是不是数组。它假定只有一个全局执行环境，如果网页中包含多个框架，那实际上就存在两个以上不同的全局执行环境，从而存在两个以上不同版本的Array构造函数。

```javascript
if(value instanceof Array){}
```

**`Array.isArray()`**方法可以解决这个问题，目的是最终确定某个值是不是数组，而不管它是在哪个全局执行环境中创造的。`if(Array.isArray()){}`

**`concat()`**返回一个新的数组，该数组是通过把所有 `arrayX` 参数添加到 `arrayObject` 中生成的。如果要进行 `concat()` 操作参数是数组，那么添加的是数组中的元素，而不是数组。

~~~javascript
var numbers=[1,2,3,4];
	var item=10;
	function prepend(arr,item){
		return [item].concat(arr);			//返回一个数组[10,1,2,3,4]
	}
~~~

**迭代**

**`every()、some()`**相似，对`every()`来说，传入的函数必须对每一项都返回`true`，这个方法才返回`true`。`some()`方法则是只要传入的函数对数组中的某一项返回`true`，就会返回`true`。

**`filter()`**创建一个新数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。

**`map()、`**返回函数中操作后的数组。

**`forEach()`**无返回值，本质上与实用`for`循环迭代数组一样。

~~~javascript
<body>
<button onclick="numbers.forEach(myFunction)">点我</button>
	<p id="demo"></p>
	<script>
	demoP = document.getElementById("demo");
	var numbers=[4,9,15,22];
	function myFunction(item,index){
		demoP.innerHTML = demoP.innerHTML+"index["+index+"]:"+item+"<br>";
	}
	</script>
</body>
~~~

![1557729521618](C:\Users\liguiru\AppData\Roaming\Typora\typora-user-images\1557729521618.png)

每个方法都接收两个参数：要在每一项上运行的函数和（可选的）运行该函数的作用域对象。传入这些方法中的函数会接收三个参数：数组项的值、该项在数组中的位置和数组对象本身。

```javascript
var numbers = [1,2,3,4,5,4,3,2,1];
var filterResult = numbers.filter(function(item,index,array){
    retrn (item>2);
})
alert(filterResult);		//[3,4,5,4,3]
```



### Date类型

### RegExp类型

是`ECMAScript`支持正则表达式地一个接口，提供了最基本的和一些高级的正则表达式功能。

### 数学对象

```
var res=Math.round(5.1);    四舍五入
var res=Math.max(20,40);    获取最大值
var res=Math.abs(-100);     获取绝对值
var res=Math.floor(1.9);    向下取整
var res=Math.ceil(1.9);     向上取整
var res=Math.pow(2,4);      幂运算
var res=Math.sqrt(9);       开方
var res=Math.random();      取随机数
function rund(m,n){
    return Math.floor(Math.random()*(n-m+1))+(n-m)
}                           指定范围的随机数
```

`selectFrom()`接受两个参数：应该返回的最小值和最大值。利用这个函数，可以方便地从数组中随机取出一项。

~~~javascript
var colors = ["red","green","blue","yeloow"...];
var color = colors[selectFrom(0,colors.length-1)];
alert(color);
~~~

### 垃圾收集

JavaScript具自动垃圾收集机制。执行环境会负责管理代码执行过程中使用的内存。原理：找出哪些不再继续使用的变量，然后释放其占用的内存。垃圾收集器会按照固定的事件间隔（或代码执行中预定的收集时间），周期性地执行这一操作。

### 面向对象

**属性类型**

**1、数据类型**

要修改属性默认的特性，必须使用`ECMAScript5`的`Object.defineProperty()`方法。这个方法接收三个参数：属性所在的对象，属性的名字和一个描述符对象。其中，描述符对象的属性必须是：`configurable、enumerable、writable和value`。设置其中的一或多个值，可以修改对应的特性值。

~~~javascript
var person = {};
Object.defineProperty(person,"name",{
    writable:false;
    value:"Nicholas";
});
alert(person.name);			//"Nicholas
person.name = "Greg";
alert(person.name);			//"Nicholas
~~~

把`writable`设置为`false`，表示只读。把`configurable`设置为`false`，表示不能从对象中删除属性。如果对这个属性调用`delete`，则在非严格模式下什么也不会发生，而在严格模式下会导致错误。而且，一旦把属性定义为不可配置的，就不能再把它变回可配置了。

**2、访问器属性**

访问器属性不能直接定义，必须使用`Object.defineProperty()`来定义。

**`get`**：在读取属性时调用的函数。**`set`**：在写入属性时调用的函数。

~~~javascript
var book = {
    _year:2004;
    edition:1
};
Object.defineProperty(book,"year",{
    get:function(){
        return this._year;
    }
    set:function(newValue){
    if(newValue>2004){
        this._year = newValue;
        this.edtion += newValue - 2004;
    }
}
});
~~~

==`_year`前面的下划线时一种常用的记号，用于表示只能通过对象方法访问的属性。==

**`Object.defineProperties()`**一次定义多个属性。接收两个对象参数：第一个对象是要添加和修改其属性的对象，第二个对象的属性与第一个对象中要添加或修改的属性一一对应。

~~~javascript
var book = {};
Object.defineProperties(book,{
    _year:{
        writable:true,
        value:2004
    },
    edition:{
        writable:true,
        value:1
    },
    year:{
        get:function(){
            return this._year;
        },
        set:function(newValue){
            if(newValue>2004){
                this._year = newValue;
                this.edition += newValue-2004;
            }
        }
    }
});
~~~

**`Object.getOwnPropertyDescriptor()`**方法，可以取得给定属性的描述符，这个方法接收两个参数：属性所在的对象和要读取其描述符的属性名称。如果是访问器属性，这个对象的属性有`configurable、enumerable、get和set`；如果是数据属性，这个对象的属性有`configurable、enumerable、writable和value`。

**构造函数模式**

~~~javascript
function Person(name,age,job){
	this.name = name;
    this.age = age;
    this.job = job;
    this.sayName = function(){
        alert(this.name);
    };
}
var person1 = new Person("Nicholas",29,"Soft");
var person2 = new Person("Greg",27,"Doctor");
~~~

`Person()`使用的是大写字母`P`。按照惯例，构造函数始终都以一个大写字母开头，而非构造函数则应该以一个小写字母开头。要创建`Person`的新实例，必须使用`new`操作符。

**1、将构造函数当作函数**

~~~javascript
//当作构造函数使用
var person = new Person("Nicholas",29,"Soft");
person.sayName();		//"Nicholas"
//作为普通函数调用
Person("Greg",27,"Doctor");
window.sayName();		//"Greg"
//在另一个对象的作用域中调用
var o = new Object();
Person.call(o,"Kristen",25,"Nurse");
o.sayName();			//"Kristen"
~~~

**2、构造函数的问题**

主要问题是每个方法都要在每个实例上重新创建一遍。但是没有必要，有`this`对象在，根本不用在执行代码前就把函数绑定到特定对象上面。因此，可以通过把函数定义转移到构造函数外部来解决这个问题。

~~~javascript
function Person(name,age,job){
    this.name = name;
    this.age = age;
    this.job = job;
    this.sayName = sayName;
}
function sayName(){
    alert(this.name);
}
var person1 = new Person("NI",29,"soft");
var person2 = new Person("g",27,"doctor");
~~~

**原型模式**

解决了构造函数的问题，新的问题是：在全局作用域中定义的函数实际上只能被某个对象调用，这让全局作用域有点名不副实。如果对象需要定义很多方法，那么就要定义很多全局函数，于是这个自定义的引用类型就没有封装性可言。

创建的每个函数都有一个`prototype`属性，这个属性是一个指针，指向一个对象，而这个对象的用途是包含可以由特定类型的所有实例共享的属性和方法。原型对象的好处是可以让所有对象实例共享它所包含的属性和方法。

~~~javascript
function Person(){}
Person.prototype.name = "Ni";
Person.prototype.age = 29;
Person.prototype.job = "soft";
Person.prototype.sayName = function(){
    alert(this.name);
}
var person1 = new Person();
person1.sayName();		//"Ni"
var person2 = new Person();
person2.sayName();		//"Ni"
~~~

### 继承

给原型添加方法的代码一定要放在替换原型的语句之后。

在通过原型链实现继承时，不能使用对象字面量创建原型方法，因为这样做就会重写原型链。

实现继承的方式有6种：
原型链继承、借用构造函数继承、组合继承、原型式继承、寄生式继承、寄生组合式继承。

**组合继承**

组合继承避免了原型链和借用构造函数的缺陷，融合了它们的优点。

~~~javascript
function SuperType(name){
    this.name = name;
    this.colors = ["red","blue","green"];
}
SuperType.prototype.sayName = function(){
    alert(this.name);
};
function subType(name,age){
    SuperType.call(this,name);
    this.age = age;
}
SubType.prototype = new SuperType();
SubType.prototype.constructor = SubType;
SubType.prototype.sayAge = function(){
    alert(this.age);
};
var instance1 = new SubType("Ni",29);
instance1.colors.push("black");
alert(instance.colors);				//"red,blue,green,blace"
instance1.sayName();			    //"NI"
instance1.sayAge();					//29
var instance2 = new SubType("Greg",27);
alert(instance2.colors);			//"red,blue,green"
instance2.sayName();				//"Greg"
instance2.sayAge();					//27
~~~

### `window`对象

所有在全局作用域中声明的变量、函数都会变成`window`对象的属性和方法。

**框架**

如果页面中包含框架，则每个框架都拥有自己的`window`对象，并且保存在`frames`集合中。在`frames`集合中，可以通过数值索引（从0开始，从左至右，从上到下）或者框架名称来访问相应的`window`对象。每个`window`对象都有一个`name`属性，其中包含框架的名称。

**窗口位置**

~~~javascript
这个例子运用二元操作符首先确定screenLeft和screenTop属性是否存在,这些属性分别用于表示窗口相对于屏幕左边和上边的位置。
var leftPos = (typeof window.screenLeft=="number")?
			window.screenLeft:window.screenX;
var topPos = (typeof window.screenTop=="number")?
			window.screenTop:window.screenY;
~~~

`moveTo()和moveBy()`可能可以将敞口精确地移动到一个新位置。接收两个参数。但是可能会被浏览器禁用。

