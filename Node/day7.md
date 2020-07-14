```javascript
funtion extend (source, target) {
  for (var key in source) {
    target[key] = source[key]
  }
}

var obj1 = {
  foo: 'bar'
}

var obj2 = {
  name: 'Jack'
}

// obj2 就拥有了 obj1 的所有成员了
extend(obj1, obj2)
```

- extend还不是很理解
  + 模板继承
  + extend 把复制过来
  + layout
  + index （extend layout）
  + index 就具有了 layout 的内容
  + index 还可以有自己的自定义内容
  
  + 合适的场景用合适的工具，没有高低贵贱之分，只是一个工具
  + EditThisCookie Chrome 浏览器插件
  
- 像router.js中，需要重新引入第三方模块express，但是body-parser在routre页面也使用了呀，但是怎么不用引入

  -  这主要是中间件的原因

##### 文件引入规则

-  模块是独立的，不能因为a加载过了fs了b就不需要加载，应该是谁需要谁加载
-  没有全局作用域，需要每个文件单独引入，
-  如果先启动node服务，再开启数据库，数据库服务开启了，但是数据库并没有连接，这样会出现所有的操作都会失效的情况，必须打开新的命令行使用mongo命令手动连接数据库 反过来，如果先开启数据库，再开启node服务，就不会出现这样的问题，因为user.js代码中mongoose.connect('mongodb://localhost/test', { useMongoClient: true })自动连接了数据库，刚开始以为数据库竟然和node产生了依赖，原来并不是！ 希望老师控制每节课

---

## 复习

- path 模块
- __dirname 和 __filename
  + **动态的** 获取当前文件或者文件所处目录的绝对路径
  + 用来解决文件操作路劲的相对路径问题
  + 因为在文件操作中，相对路径相对于执行 `node` 命令所处的目录
  + 所以为了尽量避免这个问题，都建议文件操作的相对路劲都转为：**动态的绝对路径**
  + 方式：`path.join(__dirname, '文件名')`
- art-template 模板引擎(include、block、extend)
  + include
  + extend
  + block
  + 动手写一写
- 表单同步提交和异步提交区别
  + web本质就是字符串交互
  + 请求（报文、具有一定格式的字符串）
  + HTTP 就是 Web 中的沟通语言
  + 服务器响应（字符串）
  + 01
  + 服务器端重定向针对异步请求无效
