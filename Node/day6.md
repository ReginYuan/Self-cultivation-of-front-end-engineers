# Node.js 第6天课堂笔记

## 知识点

- 多人社区案例

- MongoDB 数据库
  + 灵活
  + 不用设计数据表
  + 业务的改动不需要关心数据表结构
  + DBA 架构师 级别的工程师都需要掌握这项技能
    * 设计
    * 维护
    * 分布式计算
- mongoose
  + mongodb 官方包也可以操作 MongoDB 数据库
  + 第三方包：WordPress 项目开发团队
  + 设计 Schema
  + 发布 Model（得到模型构造函数）
    * 查询
    * 增加
    * 修改
    * 删除
- Promise
  + http://es6.ruanyifeng.com/#docs/promise
  + callback hell 回调地狱
  + 回调函数中套了回调函数
  + Promise(EcmaScript 6 中新增了一个语法 API)
  + 容器
    * 异步任务（pending）
    * resolve
    * reject
  + then 方法获取容器的结果（成功的，失败的）
  + then 方法支持链式调用
  + 可以在 then 方法中返回一个 promise 对象，然后在后面的 then 方法中获取上一个 then 返回的 promise 对象的状态结果

#### path 模块

`__dirname` 和 `__filename`

+ **动态的** 获取当前文件（_filename）或者文件所处目录的绝对路径
+ 用来解决文件操作路劲的相对路径问题
+ 一般在开发命令行工具是很有必要的一个特性

在文件操作中，使用相对路径是不可靠的，因为在node中文件操作的路径被设计为相对于执行node命令所处的路径

为了解决这个问题，需要把相对路径变为**动态的绝对路径**

```javascript
fs.readFile(path.join(__dirname, './a.txt'), 'utf8', function (err, data) {
  if (err) {
    throw err
  }
  console.log(data)
})
```

- `__dirname` 和 `__filename`不受执行node命令所属路径影响

+ 因为在文件操作中，相对路径相对于执行 `node` 命令所处的目录

+ 所以为了尽量避免这个问题，都建议文件操作的相对路劲都转为：**动态的绝对路径**

+ 方式：`path.join(__dirname, '文件名')`

+ 一般fs和path模块是成对引入

+ art-template 模板引擎(include、block、extend)
  + include
  + extend
  + block

+ 表单同步提交和异步提交区别
  + 以前没有 ajax 都是这么干的，甚至有些直接就是渲染了提示信息出来了
  + 异步提交页面不会刷新，交互方式更灵活

  表单具有默认的提交行为，默认是同步的，同步表单提交，浏览器会锁死（转圈儿）等待服务端的响应结果。
        表单的同步提交之后，无论服务端响应的是什么，都会直接把响应的结果覆盖掉当前页面。

        服务端处理会比客户端更安全，但会给服务端带来压力

Express框架默认不支持Session和cookie

Express 中配置使用 `express-session `插件

配置	

```javascript
var session = require('express-session')
```



+ 概述案例中注册-登陆-退出的前后端交互实现流程

## 目录结构

```tex
.
|-- app.js				项目的入口文件
|-- controllers
|-- models				数据库数据模型，存储使用mongoose设计的数据模型
|-- node_modules		第三方包
|-- package.json		包描述文件
|-- package-lock.json	第三播放包锁定版本文件（npm5以后才有）
|-- public				公共的静态资源
|-- REANME.md			项目说明文件
|-- routes				对路由的分类（业务比较多，代码量大时，最好把路由按业务的分类存储到routes目录中）
|-- views				存储目录视图
```

## 模板页

## 路由设计

###### 注册登录相关路由

| 路径      | 请求方法 | get参数 | post参数                 | 是否需要登录(权限) | 备注         |
| --------- | -------- | ------- | ------------------------ | ------------------ | ------------ |
| /         | GET      |         |                          |                    | 渲染首页     |
| /register | GET      |         |                          |                    | 渲染注册页面 |
| /register | POST     |         | email、nickname\password |                    | 处理注册请求 |
| /login    | GET      |         |                          |                    | 渲染登录页面 |
| /login    | POST     |         | email、password          |                    | 处理登录请求 |
| /logout   | GET      |         |                          |                    | 处理退出请求 |

## 模型设计

## 书写步骤

- 创建目录结构
- 整合静态页-模板页
  - include 
  - block
  - extend

- 设计用户登录、退出、注册的路由
- 用户注册
  - 先处理好客户端页面的内容（表单控件的name、收集表单的数据、发起请求）
  - 服务端
    - 先获取客户端表单请求的数据
    - 操作数据库
      - 如果有错，发送500告诉客户端服务器错误
      - 其他的根据业务发送不同的响应数据

- 