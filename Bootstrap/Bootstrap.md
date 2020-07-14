# Bootstrap

前端：跟用户打交道的一端

框架：库 lib

alpha版：内部测试版

beta版：公开测试版

rc版：Release Candidate(候选版本 )

如jQuqery作为一个框架，提供了一套比较便捷的操作DOM的方式

- 当下最流行的前端框架（界面工具集）、移动优先的前端框架
- 特点：灵活简洁、代码优雅、美观大方
- 目的：为了让Web开发更敏捷

+ 
  + 

### 栅格系统（列布局）

### 布局容器

**.container**用于固定宽度且支持响应式布局

```html
<div class="container"> 
    ...
</div>
```

**.container-fluid**用于100%宽度，占据全部视口viewport的容器

<div class="container">
    ...
</div>

Bootstrap框架中使用任何标签元素都可以实现按钮风格，但为了避免浏览器兼容性问题，建议使用**button**或**a**标签来制作按钮。

.btn-block：块状按钮

按钮的活动状态（悬浮：hover、点击：active、焦点：focus）
	- button元素通过:active伪类实现
	- a标签元素通过添加.active类型名实现
按钮的禁用状态
	- 方法1：在标签中添加disabled属性（disabled=“disabled"）[推荐使用属性的方式]
	- 方法2：在元素标签中添加类.disabled(该方式不能禁用按钮的默认行为，如提交、重置、如a的默认链接跳转，即链接行为是无法禁止的，)

##### img

1. **img-responsive**：响应式图片

2. **img-rounded：**圆角图片

3. **img-circle：**圆形图片

4. **img-thumbnail：**缩略图片

> 不能通过css样式直接修改img的大小，可通过控制图片容器的大小来控制图片大小

##### 图标

------

元素添加**.glyphicon**类名

- 所有icon都是以”glyphicon-”前缀的类名开始，然后后缀表示图标的名称

列偏移

​	.col-md-offset-number

列排序

​	.col-md-push-number和.col-md-pull-number互换两列的位置

列嵌套

```html
<div class="container">
    <div class="row">
        <div class="col-md-8">
        我的里面嵌套了一个网格
            <div class="row">
            <div class="col-md-6">col-md-6</div>
            <div class="col-md-6">col-md-6</div>
          </div>
        </div>
    <div class="col-md-4">col-md-4</div>
    </div>
</div>
```

#### 下拉菜单

------

##### 基本用法

1、使用一个名为“**dropdown**”的容器包裹了整个下拉菜单元素，示例中为:

```html
<div class="dropdown"></div>
上拉菜单
<div class="dropdown dropup"></div>
```

2、使用了一个**<button>**按钮做为父菜单，并且定义类名“**dropdown-toggle**”和自定义“**data-toggle**”属性，且值必须和最外容器类名一致，此示例为:

`**data-toggle="dropdown"**`

3、下拉菜单项使用一个**ul**列表，并且定义一个类名为“**dropdown-menu**”，此示例为:

`<ul class="**dropdown-menu**">`

##### 下拉分隔线

​	设置空的<li>标签，添加.divider类名

##### 菜单标题

```html
<li class="dropdown-header">
```

##### 对齐方式

默认**左对齐**

在"dropdown-menu"上添加“pull-right”或"dropdown-menu-right"类名

```html
<ul class="dropdown-menu pull-right">
<ul class="dropdown-menu dropdown-menu-right">
```

##### 菜单项状态

###### active和disabled状态需要菜单项用a标签包裹

```html
<li class="active"><a href="#">电脑</a></li>
<li class="disabled"><a href="#">手机</a></li>
```

#### 按钮

------

##### 按钮组

1. 使用一个类名为**btn-group**的容器
2. 容器内标签元素可以是任意（button、a、span），但必须带有**.btn**类名

```html
<div class="btn-group">
    <button type="button" class="btn btn-default"><span class="glyphicon glyphicon-step-backward"></span></button>
    <button type="button" class="btn btn-default"><span class="glyphicon glyphicon-fast-backward"></span></button>
</div>
```

##### 按钮分组

1. 为btn-group容器添加带**btn-toolbar**类名的父容器

```html
<div class="btn-toobar">
    <div class="btn-group">
    </div>
    <div class="btn-group">
    </div>
</div>
```

##### 按钮组大小设置

btn-group添加如下类名控制按钮组大小

- [ ] **.btn-group-lg**
- [ ] **.btn-group-sm**
- [ ] **.btn-group-xs**

##### 按钮下拉菜单

> 只需要把当初制作下拉菜单的“dropdown”的容器换成“btn-group”

##### 等分按钮（移动端）

> 自适应按钮分组

按钮组“btn-group”上追加一个“**btn-group-justified**”类名

**特别声明**：在制作等分按钮组时，请<u>尽量使用**<a>**标签元素</u>来制作按钮，因为使用<button>标签元素时，使用display:table在部分浏览器下支持并不友好。

##### 按钮下的向下向上的三角形

通过在<button>标签中添加一个“<span>”标签元素，并且添加类名为“**caret**”

```html	
<button class="btn btn-default dropdown-toggle" data-toggle="dropdown" type="button">按钮下拉菜单<span class="caret"></span></button>
```

## 导航

##### 导航样式

- [ ] nav nav-tabs：标签形tab样式(选项卡导航)
- [ ] nav **nav-pills**：胶囊形导航
- [ ] nav nav-pills nav-stacked：垂直堆叠的导航

```html
<ul class="nav nav-tabs">
     <li><a href="##">Home</a></li>
</ul>
```

##### 自适应导航

1. 导航占据容器全部宽度，而且菜单项可以像表格的单元格一样自适应宽度
2. 使用类名“**nav-justified**
3. 需要和“nav-tabs”或者“nav-pills”配合在一起使用。

##### 二级导航

将li当作父容器，使用类名“dropdown”，同时在li中嵌套另一个列表ul

```html
<ul class="nav nav-pills">
     <li class="active"><a href="##">首页</a></li>
     <li class="dropdown">
        <a href="##" class="dropdown-toggle" data-toggle="dropdown">教程<span class="caret"></span></a>
        <ul class="dropdown-menu">
            <li><a href="##">CSS3</a></li>
            …
       </ul>
     </li>
     <li><a href="##">关于我们</a></li>
</ul>
```

##### 面包屑式导航

​	为ol加入**breadcrumb**类

```html
<ol class="breadcrumb">
  <li><a href="#">首页</a></li>
  <li><a href="#">我的书</a></li>
  <li class="active">《图解CSS3》</li>
</ol> 
```

## 导航条navbar

- navbar有背景色、可以是纯链接（类似导航），可以是表单
- 表单和导航一起结合成多种形式

##### 基础导航条

1. 首先在制作导航的列表(<ul class="nav">)基础上添加类名“**navbar-nav**”
2. 在列表外部添加一个容器（div），并且使用类名“**navbar**”和“navbar-default”

```html
<div class="navbar navbar-default" role="navigation">
    <div class="container">
        <ul class="nav navbar-nav">
            <li class="active"><a href="##">网站首页</a></li>
            <li><a href="##">系列教程</a></li>
            <li><a href="##">名师介绍</a></li>
            <li><a href="##">成功案例</a></li>
            <li><a href="##">关于我们</a></li>
    	</ul>
    </div>
</div>
```

##### 反色导航条

```html
<div class='navbar navbar-inverse'>
    ...
</div>
```



##### 导航条添加标题、二级菜单及状态

1. 添加一个标题容器，其类名为**.navbar-header**
2. 标题容器内添加a标签元素，其类名为**.navbar-brand**

```html
<div class="navbar navbar-default" role="navigation">
    　<div class="navbar-header">
    　    <a href="##" class="navbar-brand">慕课网</a>
    　</div>
    <ul class="nav navbar-nav">
        <li class="active"><a href="##">网站首页</a></li>
        <li><a href="##">系列教程</a></li>
        <li><a href="##">名师介绍</a></li>
        <li><a href="##">成功案例</a></li>
        <li><a href="##">关于我们</a></li>
    </ul>
</div>
```



##### 带表单的导航条

1. 在navbar容器中放置一个带有navbar-form类名的表单
2. navbar-left：让表单左浮动
3. navbar-right：让元素在导航条靠右对齐

*只有当浏览器视窗宽度大于768px生效*

```html
<div class="navbar navbar-default" role="navigation">
    <form action="##" class="navbar-form navbar-left" rol="search">
        <div class="form-group">
            <input type="text" class="form-control" placeholder="请输入关键词" />
        </div>
        <button type="submit" class="btn btn-default">搜索</button>
    </form>
</div>
```

##### 导航条中的按钮、文本

.hide-**：在某种屏幕下隐藏

.visible-**：在某种屏幕下显示

.visible-**-xx：最后一个xx决定显示的display属性

### 缩略图

```html
<div class="container">
    <div class="row">
        <div class="col-xs-6 col-md-3">
            <a href="#" class="thumbnail">
                <img src="" alt="">
            </a>
            <!--嵌套“caption”容器添加标题、描述内容、按钮等-->
            <div class="caption">
                <h3>Bootstrap框架系列教程</h3>
                <p>Bootstrap框架是一个优秀的前端框，就算您是一位后端程序员或者你是一位不懂设计的前端人员，你也能依赖于Bootstrap制作做优美的网站...</p>
                <p>
                    <a href="##" class="btn btn-primary">开始学习</a>
                    <a href="##" class="btn btn-info">正在学习</a>
                </p>
            </div>
        </div>
    …
    </div>
</div>
```

#### 警示框

##### 默认警示框

类名：alert

- [ ] alert alert-success
- [ ] alert alert-info
- [ ] alert alert-warning
- [ ] alert alert-danger

##### 可关闭的警示框

1. 需要在基本警示框“alert”的基础上添加“**alert-dismissable**”样式。

2. 在button标签中加入**class="close"**类，实现警示框关闭按钮的样式。

3. 要确保关闭按钮元素上设置了自定义属性：“**data-dismiss="alert"**”（因为可关闭警示框需要借助于Javascript来检测该属性，从而控制警示框的关闭）。

```html
<div class="alert alert-success alert-dismissable" role="alert">
    <button class="close" type="button" data-dismiss="alert">&times;</button>
	恭喜您操作成功！
</div>
```

##### 警示框的链接

通过给警示框加的a链接添加一个名为“**alert-link**”的类名，通过“alert-link”样式给链接提供高亮显示。

#### 进度条

##### 基础进度条

```html
<div class="progress">
     <div class="progress-bar" style="width:40%">
	</div>
</div>
```

##### 彩色进度条

- [ ] **progress-bar-info**：表示信息进度条，进度条颜色为蓝色

- [ ] **progress-bar-success**：表示成功进度条，进度条颜色为绿色

- [ ] **progress-bar-warning**：表示警告进度条，进度条颜色为黄色

- [ ] **progress-bar-danger**：表示错误进度条，进度条颜色为红色

```html
<div class="progress">
    <div class="progress-bar progress-bar-success" style="width:40%"></div>
</div> 
```

##### 条纹进度条

> 在进度条的容器“progress”基础上增加类名“**progress-striped**”

##### 动态条纹进度条

> 进度条“progress progress-striped”两个类的基础上再加入“**active**”类名。

```html
<div class="progress progress-striped active">
    <div class="progress-bar progress-bar-success" style="width:40%"></div>
</div> 
```

##### 层叠进度条

- 将不同状态的进度条放置在一起，按水平方式排列
- 层叠进度条宽度之和不能大于100%

```html
<div class="progress">
	<div class="progress-bar progress-bar-success" style="width:20%"></div>
	<div class="progress-bar progress-bar-info progress-bar-striped" style="width:20%"></div>
	<div class="progress-bar progress-bar-warning" style="width:30%"></div>
	<div class="progress-bar progress-bar-danger progress-bar-striped" style="width:15%"></div>
</div> 
```

##### 带lable数值的进度条

> 只需要在进度条的div中添加内容，即所需要的值

### 媒体对象

即图片居左（或右），内容居右（或右）排列的布局

##### 默认媒体对象

  ☑   媒体对像的容器：常使用“media”类名表示，用来容纳媒体对象的所有内容

  ☑  媒体对像的对象：常使用“media-object”表示，就是媒体对象中的对象，常常是图片

  ☑  媒体对象的主体：常使用“media-body”表示，就是媒体对像中的主体内容，可以是任何元素，常常是图片侧边内容

  ☑  媒体对象的标题：常使用“media-heading”表示，就是用来描述对象的一个标题，此部分可选

> “pull-left”或者“pull-right”来控制 <u>媒体对象中的对象</u> 浮动方式

##### 嵌套媒体对象

> 将另一个媒体对象结构放置在媒体对象的主体内“media-body”

##### 媒体对象列表

1. 在ul上添加类名“media-list”
2. li上使用“media”

```html
<ul class="media-list">
    <li class="media">
        <a class="pull-left" href="#">
            <img class="media-object" src=" " alt="...">
        </a>
        <div class="media-body">
            <h4 class="media-heading">Media Header</h4>
            <div>…</div>
        </div>
    </li>
    <li class="media">…</li>
    <li class="media">…</li>
</ul>
```

### 列表组

##### 基础列表组

  ☑  **list-group**：列表组容器，常用的是ul元素，当然也可以是ol或者div元素

  ☑  **list-group-item**：列表项，常用的是li元素，当然也可以是div元素

```html
<ul class="list-group">
    <li class="list-group-item"></li>
</ul>
```

##### 带徽章的列表组

> 在“list-group-item”中添加徽章组件“badge”

```html
<ul class="list-group">
    <li class="list-group-item">
        <span class="badge">13</span>揭开CSS3的面
    </li>
</ul>
```

##### 带链接的列表组

> 给列表项的文本添加链接

```html
<ul class="list-group">
    <li class="list-group-item">
        <a href="##">揭开CSS3的面</a>
    </li>
    ...
</ul>
缺点：链接的点击区域只在文本上有效果，且需要处理超链接的样式
```

另一种实现方式div+a标签布局

```html
<div class="list-group">
    <a href="##" class="list-group-item"><span class="badge">220</span>Sass教程</a>
</div>
```

##### 自定义列表组

  ☑  list-group-item-heading：用来定义列表项头部样式

  ☑  list-group-item-text：用来定义列表项主要内容

```html
<div class="list-group">
    <a href="##" class="list-group-item">
        <h4 class="list-group-item-heading">图解CSS3</h4>
        <p class="list-group-item-text">...</p>
    </a>
</div>
```

##### 列表项的状态设置

> 在列表组中只需要在对应的**列表项**中添加类名

  ☑  **active**：表示当前状态

  ☑  **disabled**：表示禁用状态

##### 多彩列表组

> 想给列表项添加什么背景色，只需要在“**list-group-item**”基础上增加对应的类名

  ☑  list-group-item-success：成功，背景色绿色

  ☑  list-group-item-info：信息，背景色蓝色

  ☑  list-group-item-warning：警告，背景色为黄色

  ☑  list-group-item-danger：错误，背景色为红色

### 面板

##### 基础面板

```html
<div class="panel panel-default">
    <div class="panel-body">我是一个基础面板，带有默认主题样式风格</div>
</div>
```

##### 带有头和尾的面板

   ☑  panel-heading：用来设置**面板头部**样式

   ☑ panel-footer：用来设置**面板尾部**样式

```html
<div class="panel panel-default">
    <div class="panel-heading">图解CSS3</div>
    <div class="panel-body">…</div>
    <div class="panel-footer">作者：大漠</div>
</div>
```

