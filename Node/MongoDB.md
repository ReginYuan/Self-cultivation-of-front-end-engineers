# Node.js 第5天课堂笔记

回调函数

调用者是上层，封装者是下层，调用一个函数时，传入了一个函数的定义作为参数，而该函数在调用函数的定义中被调用

- 我们现在用的模块化是CMD吧 老师能不能给我们扩展一下AMD
  + PHP 中为什么就可以直接 `require`、`include` 因为 PHP 当初在设计的时候就加入了这个功能
  + PHP 这门语言天生就支持
  + 模块作用域
  + 可以使用 API 来进行文件与文件之间的依赖加载
  + 在 Node 这个环境中对 JavaScript 进行了特殊的模块化支持 CommonJS
  + JavaScript 天生不支持模块化
    * require
    * exports
    * Node.js 才有的
  + 在浏览器中也可以像在 Node 中的模块一样来进行编程
    * `<script>` 标签来引用加载，而且你还必须考虑加载的顺序问题
    * require.js 第三方库 AMD
    * sea.js     第三方库 CMD
  + 无论是 CommonJS、AMD、CMD、UMD、EcmaScript 6 Modules 官方规范
    * 都是为了解决 JavaScript 的模块化问题
    * CommonJS、AMD、CMD 都是民间搞出来的
    * EcmaScript 是官方规范定义
    * 官方看民间都在乱搞，开发人员为了在不同的环境使用不同的 JavaScript 模块化解决方案
    * 所以 EcmaScript 在 2015 年发布了 EcmaScript 2016 官方标准
    * 其中就包含了官方对 JavaScript 模块化的支持
    * 也就是说语言天生就支持了
    * 但是虽然标准已经发布了，但是很多 JavaScript 运行换将还不支持
    * Node 也是只在 8.5 版本之后才对 EcmaScript 6 module 进行了支持
    * 后面学 Vue 的时候会去学习
    * less 编译器 > css
    * EcmaScript 6 -> 编译器 -> EcmaScript 5
    * 目前的前端情况都是使用很多新技术，然后利用编译器工具打包可以在低版本浏览器运行。
    * 使用新技术的目的就是为了提高效率，增加可维护性
-  内心极度脆弱。。。有心杀敌 无力回天，总感觉时间不够用。
  
  +  不要猥琐发育，就得浪
- 虽然比较多 但是因为老师讲的很清晰 还是愿意去写的 对于 node.js 的奥义 封装异步的API 就是需要多练
- 老师讲的很清晰 讲课也很洒脱 老师是不是被夸的已经习惯了 后面讲的回掉函数有点懵了
- 老师讲的很好，思路清晰，项目跟着老师的笔记一步一步敲，so easy
-  觉得老师讲课真的超级棒啊 传智的实力担当 双击没毛病 老铁666
- 都坐下 基本操作 哇,老师,一般敢说这句话的都是大神,我还是个菜鸟,学的那是一脸懵逼
-  有点懵，看着老师的思路做，可是还是不知道从何入手，唉。。。
  +  本着达芬奇画鸡蛋的精神
  +  《使徒行者》三哥
  +  《反黑》陈小春
    *  卧底 8年卧底
    *  文职工作
    *  报了电脑版
    *  吃饭都在看书
    *  学习 -》吃饭也是看书
    *  边角余料
- var router = require('./router') 这一步不是加载router.js并执行该文件吗 为什么还要执行app.use(router) app.use 不是开放静态资源吗 app.use(router)在这里是什么意思，挂载到 app 服务中的意思是？ module.exports = app 也不懂
  + 这里涉及到一个中间件的概念
  + app.use 不仅仅是用来处理静态资源的
  + 还可以做很多工作
  + 配置 body-parse 也是通过 app.use 来配置的
  + 这叫中间件，其中有一套规则
- npm init --yes 生成一个package.json 文件 npm --save 文件名 又生成一个package-lock.json文件,又生成的文件和初始化生成的文件有区别吗?
  
  + 当你安装包的时候，新版的 npm 还会自动生成一个文件：package-lock.json
- 为什么模板引擎在app.js中引入之后在router.js中不引入可以直接使用，而express还需要在router.js中再引入一次 app.js中路由器挂载不是很懂 router.js中为什么要创建一个路由器容器，不知道作用是干什么的 es6中的find方法不是很懂
  + 中间件
  + EcmaScript 6 的 find 方法
  
  
  
  

## 复习

- 文件路径中的 `/` 和模块标识中的 `/`

  操作系统不支持正斜杠`/`

- Express 中配置使用 art-template 模板引擎

- Express 中配置使用 body-parser

- Express 中配置处理静态资源

- CRUD 案例中单独提取路由模块

## 上午总结

- 回调函数
  + 异步编程
  + 如果需要得到一个函数内部异步操作的结果，这是时候必须通过回调函数来获取
  + 在调用的位置传递一个函数进来
  + 在封装的函数内部调用传递进来的函数
- find、findIndex、forEach
  + 数组的遍历方法，都是对函数作为参数一种运用
    + every
  + some
  + includes
  + map
  + reduce
- package-lock.json 文件的作用
  + 下载速度快了
  + 锁定版本
- JavaScript 模块化
  + Node 中的是 CommonJS（模块化的名字，就是API）
  + 浏览器中的
    * AMD require.js
    * CMD sea.js
  + EcmaScript 官方在 EcmaScript 6 中增加了官方支持
  + EcmaScript 6
  + 后面我们会学，编译工具

## MongoDB 数据库

### 安装配置

2. 配置环境变量，创建存储目录

3. 命令行启动数据库

```shell
#mongdb默认使用执行mongod命令所处c盘目录下的 /data/db作为自己的数据存储目录
#所以在第一次执行该命令之前先手动创建一个目录 /data/db
mongod
```

4. 修改默认的数据存储目录和端口号

```shell
mongod --dpath 数据存储目录路径(绝对) --port 端口号
```

### 基本使用

#### MongoDB 的数据存储结构，基本组成

- 数据库 ——数据库是一个仓库，在仓库中可以存放集合
- 集合（表） ——类似于数组，可存放文档
- 文档（表记录）——文档数据库中的最小单位，存储和操作的内容都是文档

#### 连接退出数据库

```shell
# 该命令默认连接本机的MongoDB服务
mongo
#退出
exit
```

##### 基本命令

```shell
#查看显示所有数据库，默认有[admin,local]系统数据库
show dbs
#创建数据库
#切换到指定数据库（如果没有会新建）
use 数据库名
#查看当前操作的数据库
db
#显示数据库中所有集合
show collections
```

#### 命令行CRUD

```shell
# 插入
db.集合.insert({})
#查集合中的所有数据
db.集合名.find()
```





#### node中操作mongoDB

##### 使用官方的`mongodb`包来操作

##### 使用第三方mongoose来操作MongoDB

第三方包：`moogoose`是基于MongoDB官方的`mongodb`包再一次做了封装

- [moogoose](http://mongoosejs.com/)

#### mongoose

安装

```shell
npm i mongoose
```

连接数据库

```javascript
const mongoose = require('mongoose')
mongoose.connect('mongodb://localhost:27017/element-admin', {
  useFindAndModify: true,
  useNewUrlParser: true,
  useCreateIndex: true
})
```

创建数据库模型

```javascript
const Article = mongoose.model('Article', new mongoose.Schema({
  title: {
    type: String
  },
  context: {
    type: String
  }
}))
```



### 获取数据

app.get请求

```javascript
查所有
Schema.find()
限制查询条数
Schema.find().limit(2)
// 跳过某条数据(假设有3条，则显示2，3数据)
// skip和limit结合作分页
Schema.find().skip(1).limit(2)

//指定查询条件，where({})
Schema.find().where({})
// 排序正
Schema.find().sort({_id: 1})
// 排序倒
Schema.find().sort({_id: -1})

// 通过客户端url中动态传递过来的id(/:id)
Schema.findById(req.parmas.id)
```



### 提交数据

设置express允许解析json数据

```javascript
app.use(express.json)
```

app.post请求

```javascript
app.get('/api/articles', async (req, res) => {
  const article = await Article.find()
  res.send(article)
})
```

vscode 中用代码的方式发起http请求的插件 rest client

使用方法

```javascript
1.创建一个.http文件
2.设置请求
GET http://localhost:3000/api/articles
3.每个请求用 ### 3个#号隔开

//定义变量
@url = http://localhost:3000/
//引用变量
GET {{url}}api/articles

//POST请求
POST {{url}}api/articles	//请求url
Content-Type: application/json	//请求头

{
  "title": "小王",		//请求内容，必须和请求头空一行
  "context": "蛋疼"
}
```

### 修改数据

app.put：完全修改并覆盖

app.patch：部分修改

```javascript
app.put('/api/articles/:id', async (req, res) => {
  const article = await Article.findByIdAndUpdate(req.params.id, req.body)
  res.send(article)
})
```

### 删除数据

```javascript
app.delete('/api/articles/:id', async (req, res) => {
  await Article.findByIdAndDelete(req.params.id)
  //或者
  const article = await Article.findById(req.params.id)
  await article.remove()
  //或者
  await Article.deleteOne({_id:req.params.id})
  res.send({
    status: true
  })
})
```



### 关系型数据库和非关系型数据库

表就是关系

- 关系型数据库都通过`sql`语言来操作
- 关系型数据库在操作之前都需要设计表结构

#### 非关系型数据库

- 没有行，列的概念（表的概念），用JSON来存储数据

- 非关系型数据库非常灵活
- 有的非关系型数据库就是key-value对儿
- MongoDB是长得最像关系型数据库的非关系型数据库
  - 数据库->数据库
  - 数据表->集合（数组）
  - 表记录->文档对象
- MongDB不需要设计表结构

+ MongoDB 官方有一个 mongodb 的包可以用来操作 MongoDB 数据库
  + 这个确实和强大，但是比较原始，麻烦，所以咱们不使用它
+ mongoose
  + 真正在公司进行开发，使用的是 mongoose 这个第三方包
  + 它是基于 MongoDB 官方的 mongodb 包进一步做了封装
  + 可以提高开发效率
  + 让你操作 MongoDB 数据库更方便
+ 掌握使用 mongoose 对数据集合进行基本的 CRUD
+ 把之前的 crud 案例改为了 MongoDB 数据库版本
+ 使用 Node 操作 mysql 数据库

### 异步编程

#### promise

​	callback hell

异步API无法保证函数执行的顺序，要想保证顺序只能通过嵌套的方式，即回调地狱

为了解决嵌套编码方式带来的问题（回调地狱嵌套），es6新增了一个API，`promise`