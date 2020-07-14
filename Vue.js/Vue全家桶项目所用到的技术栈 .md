# Vue全家桶项目所用到的技术栈

## 项目构建工具vue-cli

- 官方推荐的脚手架工具，为我们搭建开发所需要的环境和生成目录架构

## 路由Vue-router

- 创建单页应用，我们的单页应用只做路由切换，组件拼凑成的页面映射成路由
- 单页面的核心插件

## 状态管理vuex

- 状态管理库，可理解为全局数据集中地
- 推荐小项目不用，会显得有些繁琐，bus总线机制完全可以处理了
- 通过创建一个集中的数据存储，供程序中所有组件访问

## http请求工具axios

- http库，一个经过封装的ajax，用于http请求
- axios是经过了ES6的promise封装 
- 可用于浏览器和node.js，即可用于客户端和服务端

**Axios特性**

- 支持 Promise API
- 拦截请求和响应（即可在请求前或响应前做一些操作）
- 转换请求数据和相应数据（数据的加密解密）
- 可自动转换 JSON 数据

# 前后端联调必备技术之Mock讲解

**前端自编写开发阶段接口(模拟假数据)，实现前后端开发可并行状态**

- 什么是Mock数据？
  - 处于开发环境模拟接口返回的数据（用于开发状态后端还没给接口，自己去写接口）
  - 不会影响生产环境，只是方便我们还没与后端交互时不阻塞我们开发流程
- Mock数据的好处
  - 团队可以并行工作（后端进度不至于影响前端开发进度）
  - 可以用来演示开发成果，实时反馈开发进度
  - 模拟测试并简单了解接口编写为全栈打基础（要懂后端的数据是怎么来的，方便和后端交流）

# 第二章 搭建vue单页面应用工程架构

## 第一节：对比vue-cli2.x和vue-cli3.x的搭建

**简介：深入了解脚手架vue-cli2.x版本与3.x版本构建项目的区别**

- ##### 搭建前提条件：

  1. ##### node环境

     - ##### node是傻瓜式安装的，直接去官网下载安装不断下一步

     - ##### 命令行输入node -v查询版本号，有版本号即安装成功

     - ##### node自带npm包管理工具（安装好node也可以输入npm -v查看版本号）

     - ##### npm太慢，下载国内淘宝镜像cnpm(npm install -g cnpm --registry=[https://registry.npm.taobao.org](https://registry.npm.taobao.org/))

  2. ##### 安装webpack

     - ##### 运行npm install webpack -g

  3. ##### 安装vue-cli 2.x(最新最稳定版本)                                                                        

     - ##### npm install vue-cli -g

     - 查看版本 vue -V

     - ##### 创建项目：vue init webpack 项目名(不要取中文名字)

       或 vue init (模板名)webpack-simple 项目名

     - 启动：`npm run dev`

  4. ##### 安装vue-cli 3.x

     - **npm install @vue/cli -g**
     - **创建项目：vue create 项目名（英文小写）**
     - 启动：`npm run serve`开发环境
     - `npm run build`生产环境，打包上线时使用
     
     添加插件的方法： `vue add 插件名字`(vuify)

- **不添加指定版本号就是下载最新稳定版本**

## 深入了解vue-cli2.x和3.x版本项目架构的区别

##### vuecli3.x:

1. 基于webpack4打造

2. 去掉了`2.x` `build`和`config`等配置目录 ,大部分配置 都集成到`vue.config.js`这里了

vue.config.js需要自己新建

vue.config.js里大概包括了配置 常用的输出路径名、跟目录、预处理、devServer配置、pwa、dll、第三方插件等等

**	具体配置可参考(https://www.cnblogs.com/zjhr/p/9472648.html)**

**	因为绝大部分的配置和扩展尤大大已经做好了封装的了，我们常用的开发基本可以满足，不满足的我们自己可以自行去扩展**

3. 移除了static文件夹（cli2中存放静态资源，打包的时候会原封不动的放到dist中）， 新增了public文件夹（也是存放静态资源，原样打包），并将index.html移动到了public中

**	webpack的配置在这个属性里修改configureWebpack（Mock也是在这里面的）**

## 核心技能之ui库选择

**简介：分析市场上各种各样的ui框架及如何选择适合自己项目的ui框架**

- ##### vue是一套渐进式的框架，设计的时候就是自底层向上组层应用的。

  ##### PC端的ui库基本不用做选型了，ElementUI（饿了么）的霸主地位无人能撼动

  ##### 移动端的选型看好几点即可

  - 能否自定义皮肤
  - 是否使用rem控制尺寸，完美适应不同分辨率移动设备
  - 组件类型风格是否与自己的项目相同或类似
  - 单元测试覆盖率
  - 更新频率的快慢(频率越高，社区越庞大)

  用的时候要去想框架的组件是怎么实现的

  #### 移动端的框架有哪些：

  mint-ui（官方停止更新了）

   vux vant cube-ui

  有赞：<https://youzan.github.io/vant/#/zh-CN/intro>

  滴滴：<https://didi.github.io/cube-ui/#/zh-CN/docs/switch>





### Axios 请求方法

```
get: 用于获取数据
post: 用于提交数据（表单提交 + 文件上传）
put: 更新数据（所有数据推送到后端）
patch: 更新数据（只将修改的数据推送到后端）
delete: 删除数据
```

#### get方法

```javascript
axios.get('url',{
    params: { id: id}
}).then()

//axios(config)
axios({
    method: 'get',
    url: 'ur',
    params: {
        id: id
    }
}).then()
```

#### post方法

```javascript
//application/json 数据格式请求
let data = {}
axios.post('url',data).then()

axios({
    method: 'get',
    url: 'ur',
    data: data
}).then()

// form-data请求
let formData = new FormData()
for(let key in data){
	//将data中数据遍历插入到formData中
    formData.append(key,data[key])
}
axios.post('url', formData).then()
```



#### axios并发请求

- axios.all，可以放入多个请求的数组
- axios.all([])返回的结果是一个数组，使用 axios.spread 可以将数组 [res1, res2] 展开为 res1，res2

```javascript
//全局的axios请求
axios.all([
  axios({
  	//请求1  
  }),
  axios({
    //请求2
  })
]).then(results => {
  
})

//使用axios.spread分别拿到响应结果
axios.all([
  axios(),
  axios()
]).then(axios.spread((res1, res2) => {
  console.log(res1)
  console.log(res2)
}))
```

### 全局配置

```javascript
axios.defaults.baseURL = ''
axios.defaults.timeout = 5000（毫秒）
axios.defaults.headers.post['Content-type'] = ''
```

### 创建axios实例

为了应对服务器有可能不在同一个ip地址

```javascript
const instance1 = axios.create({
  baseURL: 'url1'
})
instance1({
   
})
```

### axios拦截器

四种拦截：请求成功or失败的拦截，响应成功or失败的拦截

### 理解MVVM和组件带出来的面试题详解

**简介：详细讲解面试高频出现问题之MVVM开发模式及组件通信**

1. ##### 谈谈你对MVVM开发模式的理解

   - MVVM分为Model、View、ViewModel三者
     - Model：代表数据模型，数据和业务逻辑都是在Model层中定义
     - View：代表UI视图，负责对数据的展示
     - ViewModel：负责监听Model中数据的改变并控制视图的更新，处理用户交互操作

   Model和View并无直接关联，而是通过ViewModel来进行联系的，Model和ViewModel之间有着双向数据绑定的联系。因此当Model中的数据改变时会触发View层的刷新，View中由于用户交互操作而改变的数据也会在Model中同步。

   这种模式实现了Model和View的数据自动同步，因此开发者只需要专注对数据的维护操作即可，而不需要自己操作dom。

2. ##### 对于组件通信你了解多少，请描述一下你是怎么完成组件的通信的

   - 父传子用 props传递
   - 子传父用$emit传递
   - 非父子之间的传值 建立一个空实例进行传值，中央事件总线机制
   - 祖孙之间的传值可以利用provide inject模式

   ##### VUEX可以处理上述的每一个情况

   ### 第四节：修改数据视图试图不更新情况该怎么处理和如何监听数据

   **简介：分析修改数据视图试图不更新情况和讲述如何处理，讲解监听数据面试问题**

   1. ##### 关于修改了数据，视图不更新的理解和处理方式

      1. **Vue中给data中的对象属性添加一个新的属性时会发生什么**

         **经过打印发现数据是已经改变了，但是由于在Vue实例创建时， 新添加的属性并未声明，因此就没有被Vue转换为响应式的属性，自然就不会触发视图的更新，这时就需要使用Vue的全局api——> $set()**

         **$set()使用方法：**

         **$set(需要修改的对象，"对象的属性",值)**

   2. ##### 在vue里面你如何做数据的监听

      1. **watch里面监听**

         - **第一种写法**

           **watch:{** **obj(newval,oldval){** **console.log(newval,oldval)** **},** **}**

         - **第二种写法可设置deep为true对数据进行深层遍历监听**

           **watch:{** **obj:{** **handler(newval,oldval){** **console.log(222)** **	console.log(newval,oldval)** **},** **deep:true** **}** **}**

      2. **computed 里面监听**

         - **computed里面的依赖改变时，所计算的属性或作出事实的改变**

### 第一节：vue全家桶仿京东电商项目总结

**简介：回顾vue全家桶仿京东电商项目所用到的技术栈**

1. ##### 全家桶成员登场及介绍各自的作用（vue-cli、vue-router、axios、vuex）

2. ##### 新知识Mock自己编写本地运行接口返回数据

3. ##### 开始利用脚手架快速构建我们的工程项目（分别介绍了vue-cli2.x和vue-cli3.x构建命令的区别）

4. ##### 讲解vue-cli2.x和vue-cli3.x构建出来的项目架构的区别

5. ##### 面对市场上花样百出的ui库如何选择质量高适合自己项目的ui库

6. ##### 使用cube-ui开始我们的项目之旅（tips：多看api文档就能熟练使用ui库）

7. ##### 使用Mock编写我们的接口并返回我们需要的信息

8. ##### 介绍那种场景下使用嵌套路由以及如何实现

9. ##### 介绍token的用途和编写axios请求的全局拦截和路由守卫（轻易实现权限控制）

10. ##### 利用vuex和本地存储的配合实现购物车的功能

11. ##### 进行项目的性能优化及体验优化(优化首屏加载、路由跳转过渡效果、购物车动画效果)

12. ##### 打包项目及详解面试关于vue的高频面试题

### 第二节：中高级前端工程师学习路线介绍

**简介：介绍中高级前端工程师学习路线，让你进阶的路上不再迷茫**

- #### 中高级前端工程师的学习路线：

  - #### html5→css3→js→es6→ps切图基础→vue→react→angular→小程序生态→webpack→http知识→node.js→express、koa→Linux→mysql、mongoDB、redis→Git和持续集成→Docker→JS高级→前端性能优化→浏览器知识→前端安全性问题→项目实战