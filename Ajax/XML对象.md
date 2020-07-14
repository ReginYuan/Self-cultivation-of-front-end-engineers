#### Ajax原理

​	通过XMLHttpRequest对象向服务器发起异步请求，从服务器获取数据，然后通过JavaScript操作DOM结点来更新页面数据

#### XMLHttpRequest对象

+ AJax的核心，一种异步请求技术

+ js通过XMLHttpRequest对象向服务器请求数据和处理响应，达到用户看到的页面无刷新效果

#### 创建XMLHttpRequest对象
```js
//兼容性写法
var xmlhttp=null
if(window.XMLHttpRequest){//创建主流浏览器支持的XMLHttpRequest对象
	xmlhttp=new XMLHttpRequest()
}
else if(window.ActiveXObject){//创建IE5/6支持的XMLHttpRequest对象
    xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
}
xmlhttp.open('配置信息')；
xmlhttp.send();
```

##### 原生Ajax-get请求

```js
//1.创建XMLHttpRequest请求对象
var xmlhttp = new XMLHttpRequest();
//2.状态改变
xmlhttp.onreadystatechange=function(){
    if(xmlhttp.readyState==4&&xmlhttp.status==200){
        //请求成功，成功返回数据(xmlhttp.responseText)
    }
}
//3.设置请求信息
xmlhttp.open('GET','/test?username=万人迷',true);
//4.发送
xmlhttp.send();
```

###### open()方法

1. 用来初始化XMLHttpRequest对象，设置请求方式、URL、同步或异步
	`open(method,url,async)`
	- method：GET、POST、PUT、DELETE、HEAD
	- url请求的地址
	- async是否异，,默认**true**(异步请求)，设置false同步请求

