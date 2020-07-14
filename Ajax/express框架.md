# Express框架

目前最流行的node.js后端框架，相当于jq和js之间的关系

三大块：路由、模板引擎、中间件

app.js：入口文件

- “/”：表示public目录

views：模板文件

+ 默认文件后缀名为.ejs

### supervison

*服务器创建成功，如果使用node启动，修改代码之后，刷新页面不会生效*

*因为启动服务器后创建了缓存，再刷新仍然是从缓存拿数据*

*让修改马上生效，需要重启动服务器*

*supervisor工具可以自动检测代码修改，并重新启动*

```shell
#安装
npm install supervisor -g
#启动
supervisor 文件名
```



## Express应用生成器

通过应用生成器工具可以快速创建一个应用的骨架

默认端口号3000

1. 全局安装生成器

```shell
npm i express-generator -g
```



```shell

express 项目名 -e (ejs模板引擎)
npm i

package.json修改
"start": "node ./bin/www" => "start": "supervisor ./bin/www"
```

目录结构

```
|--bin:创建服务器,命令执行目录
|--nodemodules
|--public：公共目录，存放静态资源
|--routes
|--views
|--app.js：项目启动文件

```

app.js文件修改默认视图渲染引擎

```javascript

```

2. 常用操作

```shell
# 查看帮助
express -h 
```

## 基本结构

```javascript
//引包
var express = require('express')
//2.创建服务器应用程序,express()就时原来的http.createServer
// app 即 application
var app = express()

app.listen(3000,function () {
	console.log('app is running at port 3000')
})
```

## 基本路由

路由器：请求方法，请求路径，请求处理函数

get:

```javascript
//以get方法请求'/'的时候，执行对应的处理函数
app.get('/',function(req,res){
    res.send('hello world')
})
```

post:

```javascript
//以post方法请求'/'的时候，执行对应的处理函数
app.get('/',function(req,res){
    res.send('get a post request')
})
```

## 静态服务

访问静态文件

```javascript
//	/public
app.use(express.static('public'))
//	/files
app.use(express.static('files'))

// 通过指定路径访问该路径下的静态文件
//	/public/xxx
app.use('/public',express.static('xxx'))
//	/static/xxx
app.use('/static',express.static('xxx'))
```

## express解决跨域问题

浏览器自带 `fetch`网络请求

1. 装包

```shell
npm i cors
```

2. 使用

```javascript
app.use(require('cors')())
```



## 配置`art-template`模板引擎

> node中有很多第三方模板引擎都可以使用，如ejs、jade(pug)、handlebars、nunjucks

安装

```shell
npm i -S art-template
npm i -S express-art-template
```

配置

```shell
app.engine('html',require('express-art-template'))
```

使用

```javascript
app.get('/',function(){
    //express默认会去项目中的views目录找index.html
    res.render('index.html',{
        title:'标题'
    })
})
```

如果想修改默认的`views`视图渲染存储目录

```javascript
app.set('views',目录路径)
```



## 在Expres获取表单`GET`请求参数

express内置一个API

```javascript
req.query
```

## 在Expres获取表单`POST`请求体数据

在express中没有内置获取表单post请求的api，需要第三包`body-parse`r

安装

```shell
npm install --save body-parser
```

配置

```javascript
//引包
var bodyParser = require('body-parser')

//加入配置后，可以通过req.body来获取表单请求体的数据
//配置到挂在路由（app.use(router)）之前
app.use(bodyParser.urlencoded({ extended: false }))
app.use(bodyParser.json())
```

## 在Express配置使用`express-session`插件

Session是基于cookie的

安装

```shell
npm install express-session
```

配置

```javascript
app.use(session({
    //配置加密字符串，会在原有的加密基础（服务端产生的session有一个加密ID）之上和这个字符串拼接起来去加密，目的是为了增加安全性，防止客户端恶意伪造
	secret: 'keyboard cat',	
	resave: false,
	//设置为false时，只有往session存数据时，才会分配钥匙
    //无论是否启用session,都会分配一个钥匙（ssession）
	saveUninitialized: true 
}))
```

使用

```javascript
//添加 
req.session.wrm = '万人迷'
//访问 
reqsession.wrm
//删除
req.session.xxx = null
delete req.session.xxx //更严谨的删除方式
```

> 默认Session数据时内存存储的，服务器一旦重启就会丢失，真正的生产环境会把session进行持久化存储。