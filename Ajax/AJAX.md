# Ajax异步JS和XML技术

- 一种用脚本发起HTTP请求于服务器进行通信的技术，能够再不刷新窗口（文档重载）的前提下，完成于服务器之间的交互。
- 核心是XMLHttpRequest对象（简称XHR）



### 功能：页面不刷新，但是内容动态更新
### 1.2原理

```
1.官方含义：浏览器创建XMLHttpRequest请求对象，通过XMLHttpRequest请求对象将数据发送到远程的服务器，服务器接受数据并处理，返回结果，再通过互联网将结果返回到浏览器的过程
2.通俗理解：普通URL地址栏输入地址是正大光明访问服务器，而Ajax是偷偷某某的访问服务器，让页面上的内容发生动态更新。虽然使用的是不同形式，但是都是请求服务器。
```
#### 运用场景
1. 表单验证/发布微博消息/评论微博
2. 瀑布流效果

### 1.3前后端数据交互：Json、String、XML
### 1.4原生Ajax请求-get请求

```
//1.创建XMLHttpRequest请求对象
var xmlhttp = new XMLHttpRequest();
//2.状态改变
xmlhttp.onreadystatechange=function(){
    if(xmlhttp.readyState==4&&xmlhttp.status==200){
        //请求成功，成功返回数据(xmlhttp.responseText)
    }
}
//3.设置请求信息
/*
	.open()参数说明
	method:请求的类型：GET/POST
	url:文件在服务器上的位置
	async:true(异步)/false(同步)
*/
xmlhttp.open('GET','/test?username=万人迷',true);
//4.发送
xmlhttp.send();
```
### 1.5状态值理解

```
XMLHttpRequest的readyState状态值理解
0：请求未初始化
1：服务器连接建立
2：请求已接受
3：请求处理中
4：请求已完成，且响应已经就绪

---
HTTP的status状态
200：请求并响应成功
404：请求的URL地址找不到
```
### 1.6原生Ajax请求-post请求

#### 同步异步

```
发送Ajax请求需要消耗时间
	同步：Ajax之后的代码需要等待Ajax请求返回，之后继续执行
	异步：Ajax之后的代码和Ajax同时进行，相互不影响
```



### 跨域处理

Ajax发送请求的url地址与服务地址必须在同一域名下

**浏览器的同源策略**:	

同源：URL协议、域名和端口号相同

域：协议名+主机名+端口号
+ 域：http、https、
+ 主机名：www.baidu.com
+ 端口号：80、23

相同域：域名、主机名、端口号相同
不通域：http://www.baidu.com:80和http://mp3.baidu.com:80

浏览器为了安全问题（CSRF攻击），做了同源(域)策略的限制（没有访问权限，即虽然Ajax发出去了，但是浏览器将其截止了）

是对Ajax的一个主要约束，除非采用认可的跨域通信（CORS、JSONP），否则访问不同源的接口或资源都会引起安全错误。

img、css、js都可以进行跨域处理，但是Ajax不可以跨域

为什么要跨域？
- 大网站有许多子网站，子网站间要进行数据处理，出现跨域问题

解决办法：**JSONP**跨域解决
- 注：区分JSON，JSON是数据的表示格式
- Ajax跨域请求有权限限制
- img,link,script无跨域限制
- 用script请求服务器的JS文件获取数据

编码转换
- encodeURI('文字')
- encodeURI(‘编码’)

核心原理

1. 在当前页面定义函数
2. 通过script标签引入的函数中调用该函数
`在引入的script标签中需要对应的网站提供相关的函数调用，即提供其js文件路径，这样才能做到跨域访问`