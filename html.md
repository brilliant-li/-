![1554082123929](C:\Users\liguiru\AppData\Roaming\Typora\typora-user-images\1554082123929.png)

参考网站：http://www.w3school.com.cn/html/html_jianjie.asp

完整的HTML参考手册：http://www.w3school.com.cn/tags/index.asp

### 标签



### 常见的块级元素标签

独占一行

标题：h1-h6            

段落标签：p

列表标签：无序列表(ul li)  有序列表(ol li) 自定义标签(dl dt dd)

表格标签：table tr td(th)   合并表格....

无语义的块元素：div一般用于网页布局 配合css使用

### 常用的行级元素标签

不独占一行

#### 1、HTML链接   

a标签   双标签

属性target="_blank"在新窗口打开    

​       href="链接地址"

路径问题    在实际开发中建议使用相对路径  ./当前目录   ../上级目录

绝对路径    在Windows中绝对路径的根是文件的盘符

#### 2、图像标签   

img    单标签，不需要闭合

属性  src：图片的地址(网络资源或者本地资源)

​         alt：用于图片加载失败后的替代文字

​         title：鼠标选题在图片上的提示信息

​         width、height：设置图片的大小，只设置一个属性时会等比例放大缩小

#### 3、文本标签

1. b标签    加粗
2. br标签   换行
3. i标签      斜体
4. strong    又加粗又倾斜
5. em标签   斜体

无语义的行内元素   span标签

#### html中的实体字符

1. 大写符号

### 表单标签

form标签来划定一个表单区域

action：提交地址

method：提交方式    get/post

表单控件 必须要填写name属性

​               type属性   表单属性

​                                text    普通文本

​                                radio   单选框

​                                checkbox     多选框

​                                password     密码框

select 标签      下拉选项框     配合option标签使用

~~~html
<form action="" method="">
    用户名：<input type="text" name=""><br>
    密码：<input type="password" name="">
    性别：<input type="radio" name="sex" value="1"> 男   
         <input type="radio" name="sex" value="0"> 女
    <!--单选框 type="radio" 必须有name属性，并且有一组单选框name属性的值必须相同-->
    爱好：<input type="checkbox" name="love" value=""> ***
    <input type="checkbox" name="love" value=""> ***     <input type="checkbox" name="love" value=""> ***
</form>
~~~

### `html`语义化

1、`html`语义化概念
<基本上都是围绕着几个主要的标签，像标题、列表、强调等>
根据内容的结构化(内容语义化)，选择合适的标签(代码语义化)便于开发者阅读和写出更优雅的代码的同时让浏览器的爬虫和机器很好地解析。

2、为什么要语义化

- 为了在没有css的情况下，页面也能呈现出很好的内容结构、代码结构
- 用户体验：例如`title、alt`用于解释名词或解释图片信息、`label`标签的活用
- 有利于`SEO`：和搜索引擎建立良好沟通，有助于爬虫爬取更多的有效信息：爬虫依赖于标签来确定上下文和各个关键字的权重
- 方便其他设备解析（如屏幕阅读器、盲人阅读器、移动设备）以意义的方式来渲染网页；
- 便于团队开发和维护，语义化更具可读性，是下一步把网页的重要动向，遵循W3C标准的团队都遵循这个标准，可以减少差异化

3、写`html`代码时应注意什么

- 尽可能少的使用无语义的标签`div和span`
- 在语义不明显时，既可以使用`div`或者`p`时，尽量用`p`，因为p在默认情况下有上下间距，对兼容特殊终端有利
- 不要使用纯样式标签，如：`b、font、u`等，改用`css`设置
- 需要强调的文本，可以包含在`strong`或者`em`标签中（浏览器预设样式，能用`css`指定就不用他们），`strong`默认样式是加粗，`em`是斜体
- 使用表格时，标题要用`caption`，表头用`thead`，主体部分用`tbody`包围，尾部用`tfoot`包围。表头和一般单元格要区分开，表头用`th`，单元格用`td`
- 表单域要用`fieldset`标签包起来，并用`legend`标签说明表单的用途
- 每个`input`标签对应的说明文本都需要使用`label`标签，并且通过为`input`设置`id`属性，在`label`标签中设置`for=someld`来让说明文本和相对应的`input`关联起来。

### 编码

1、GBK通常指GB2312编码 只支持简体中文字 

2、utf通常指UTF-8，支持简体中文字、繁体中文字、英文、日文、韩文等语言（支持文字更广） 

3、通常国内使用utf-8和gb2312，看自己需求选择

## 五、Ajax

与服务器交换数据并更新部分网页的艺术，在不重新加载整个页面的清空下

~~~
$('button').click(function(){
    $.get('./cgi-bin/1.py',{username:'zhangsan',age:18},function(data){
        console.log(data);
    },'json')
})
~~~

`$.get()`中第一个参数是请求地址，第二个参数是要发送的数据（可选），第三个参数：请求成功后执行的函数，data形参用来接收后端给我们返回的数据，第四个参数指定返回数据的类型

`$.post()`同`$.get()`

`$.ajax()`       简单例子

~~~javascript
$('button').eq(2).click(function(){
			$.ajax({
				url:'./cgi-bin/1.py',				//请求的地址
				type:'get',						   //指定请求方式  get  post
				data:{username:'wangwu',age:18},     //请求时携带的数据
				dataType:'json',                     //指定返回的数据类型
				success:function(da){                //请求成功后调用的函数
					console.log(da);
				},
				error: function () {                 //请求失败时指定的函数
	           		console.log('请求失败');
	        	},
				timeout:2000,                        //设置请求响应的超时时间
				async:true                       //true代表异步，false代表同步
			})
		})
~~~

如果后台返回的数据不是指定的数据类型就不接收

**上述代码测试步骤**

1、在终端运行server.py       D:\software\sublime\Sublime Text3\project

2、输入的网址是127.0.0.1/4.html

3、控制台会显示函数中的第二个参数

## 六、bootstrap框架

## 七、vue js

**官网：cn.vuejs.org**

模板语法：{{}}

​		  可以写数值类型，字符串，对象，数组，运算，不能写表达式

文本指令：以v-开头，对html元素的功能拓展

​		v-html	可以解析标签

​		v-text	 不能解析标签

属性操作：

​		v-bind：属性名=""	简写：    ：属性名=""

类名操作：

​		数组语法

​		v-bind:class=[变量名，变量名]

​		data{      变量名：类名

​		}

​		对象语法

​		v-bind:class={类名：true/false}

style操作：

​		数组语法

~~~
:style=[obj1,obj2]
data:{
    obj1:{
        width:'200px',
        background:'red'
    },
    obj2:{
        border:'1px solid green'
    }
}
~~~

​		对象语法

~~~
:style={width:w}
data:{
    w:'200px'
}
~~~

v-model	一般用于表单的命令，将表单的value值和数据模型当中的变量进行绑定，通常用来实现数据的双向绑定







