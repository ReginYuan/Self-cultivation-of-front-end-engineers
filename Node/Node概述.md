# Node.js 概述

## node.js介绍

- Node.js 是什么
  + 一个能够在服务端运行JS的跨平台运行环境。
  + 不是语言，不是框架，它是一个平台
  + Node.js可以解析和执行JS代码，以前只有浏览器可以
  + 用于搭建自己的后端服务器，即将Node.js当作自己的Web服务器，其语法基于JavaScript(以js为开发语言) 
- Node.js 中的 JavaScript
  + **没有 BOM、DOM**
  + EcmaScript 基本的 JavaScript 语言部分
  + 在 Node 中为 JavaScript 提供了一些服务器级别的 API
    * 文件读写的能力
    * http 服务的能力
    * 网络服务的构建
    * 网络通信

- 构建在Chrome的V8 引擎之上
  - 代码只是具有特定格式的字符串
  - 引擎可以认识，帮助解析和执行
  - Chrome的V8引擎是目前公认的解析执行js代码最快的
  - node.js的作者将Chrome的V8引擎移植出来，开发了一个独立的js运行环境

- 企业需求
  + 具有服务端开发经验更好
  + front-end	前端
  + back-end	后端
  + 全栈工程师
  + 基本的网站开发能力
  	+ 前端
  	+ 服务端
  	+ 运维部署
- Node.js特性
  + 基于事件驱动（event-driven）
  + 非阻塞IO处理(即异步输入和输出操作)(non-blocking I/0 model)
  + 轻量和高效(lightweight and efficient)
  + 单线程
##  Node.js能做什么

- Web服务器后台
- 开发高并发的Web应用
- 命令行工具
  + npm(node开发)
  + git(c开发)
  + hexo(node开发)
- 对前端开发工程师来讲，接触node最多的是其命令行工具
  - 自己写的少，主要使用第三方
  - webpack
  - gulp
  - npm

NPM 

node包管理器，一个在线仓库，用于管理Node程序所需的JS模块

- npm是世界上最大的**开源生态库系统**（open source ecosystem ）

- 绝大多数javascript相关的包都存放在了npm上，方便开发人员下载使用，以命令的方式

通过npm可以方便的获取其他开发人员分享的软件包（即能够复用的类库，也叫模块）

## 可以学到什么

- B/S编程模型
  - 任何bs变成模型都是一样的，和语言无关
  - node只是作为学习bs编程模型的一个工具
- 模块化编程
  - RequireJS、SeaJS
  - 一般Js只能通过script标签加载,node中可以像@import()一样来加载JavaScript脚本文件
- 异步编程
  - 回调函数
  - Promise
  - async
  - generator
- express web开发框架

## 总结

#### Node 中的 JavaScript

+ ##### EcmaScript
  
  * 变量
  * 方法
  * 数据类型
  * 内置对象
  * Array
  * Object
  * Date
  * Math
+ 模块系统
  * 在 Node 中没有全局作用域的概念
  * 在 Node 中，只能通过 require 方法来加载执行多个 JavaScript 脚本文件
  * require 加载只能是执行其中的代码，文件与文件之间由于是模块作用域，所以不会有污染的问题
    - 模块完全是封闭的
    - 外部无法访问内部
    - 内部也无法访问外部
  * 模块作用域固然带来了一些好处，可以加载执行多个文件，可以完全避免变量命名冲突污染的问题
  * 但是某些情况下，模块与模块是需要进行通信的
  * 在每个模块中，都提供了一个对象：`exports`
  * 该对象默认是一个空对象
  * 你要做的就是把需要被外部访问使用的成员手动的挂载到 `exports` 接口对象中
  * 然后谁来 `require` 这个模块，谁就可以得到模块内部的 `exports` 接口对象
  * 还有其它的一些规则，具体后面讲，以及如何在项目中去使用这种编程方式，会通过后面的案例来处理
+ **核心模块**
  
  核心模块是由 Node 提供的一个个的具名的模块，它们都有自己特殊的名称标识，例如
  - `fs` 文件操作模块
  - `http` 网络服务构建模块
  - `os` 操作系统信息模块
  - `path` 路径处理模块
  - 。。。。
  
  所有核心模块在使用的时候都必须手动的先使用 `require` 方法来加载，然后才可以使用，例如：
  
  - `var fs = require('fs')`

- http
  + require
  + 端口号
    * ip 地址定位计算机
    * 端口号定位具体的应用程序
    * 一切需要联网的通信软件都会占用一个端口号
    * 可以同时开启多个服务，但要确保不同服务占用的端口号不同
  + Content-Type
    * 服务器最好把每次响应的数据是什么内容类型都告诉客户端，而且要正确的告诉
    * 不同的资源对应的 Content-Type 是不一样，具体参照：http://tool.oschina.net/commons
    * 对于文本类型的数据，最好都加上编码，目的是为了防止<u>中文解析乱码</u>问题
  + 通过网络发送文件
  * 发送的并不是文件，本质上来讲发送是文件的内容
    * 当浏览器收到服务器响应内容之后，就会根据你的 Content-Type 进行对应的解析处理
- 模块系统
  - 具名的核心模块
  - 用户自己编写的文件模块（即JS文件）
- Node 中的其它的核心模块

## 环境搭建

##### 检查安装结果

- 确认Node环境是否安装成功
  - Win+r输入”cmd”进入命令行`node -v`
  - 或`node --version`
- 环境变量

##### 交互式运行环境——REPL

在终端中输入`node`命令（类似于浏览器中的控制台）

- read
- eval：执行
- print
- loop：循环

该环境的作用只是用来帮助我们做一些辅助测试，如可以直接使用node中的核心模块而不需要require加载

##### 打开cmd方式

- 当前目录：`shift+鼠标右键->在此处打开powershell`
- 当前目录：`右键->Git Bash Here`

node文件名不要用node.js来命名，也最好不要使用中文

##### 一些命令行操作

- `cls`：清屏
- `dir`：列出目录

浏览器的默认请求行为：会默认请求/favicon.ico，（收藏家图标）