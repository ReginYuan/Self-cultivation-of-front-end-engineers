一个解决方案可以包含多个项目

SqlHelper工具类

> 工具类是指可以重复使用的功能代码,如数据库的增删改查



CodeFile：后置代码文件

Inherits：前置代码和后置代码共同生成的页面类文件名称

##### SiteMapPath站点地图

必须放在网站的根目录下

实现页面导航功能

**站点地图文件**

- 文件名：Web.sitemap，一个XML文件
- 用来表示一个网站各个页面之间的层次结构关系
- 要实现页面导航，应该先在Web.Sitemap文件中以XML的形式，提供出整个网站的页面结构层次

```xml
<?xml version="1.0" encoding="utf-8">
//siteMap:根节点元素
<siteMap xmlns="URL地址">
	//siteMap下有且仅有一个siteMapNode节点，siteMapNode对应于页面的节点，一个节点描述一个页面
	<siteMapNode url="" title="" description="">
	//siteMapNode下可以包含多个新的siteMapNode节点
        <siteMapNode url="" title="" description="">
		<siteMapNode url="" title="" description="">
 	</siteMapNode>
</siteMap>
```

- url：用于设置节点导航的URL地址，站点地图中，同一个URL只能出现一次
- title：提供链接的文本描述，指定这个节的标题
- description：设置节点说明性文本，提供光标停留时显示的内容

##### SiteMapPath

- 显示一个导航路径（面包屑式）
- 该导航显示了从站点的根节点到当前页面之间的路径

- 必须与站点地图文件相结合（前置条件），拖到页面即可，不需额外编写代码
- 站点地图中必须有当前页的URL，否则该站点导航控件将不会显示



## Request

```c#
//当前网页跳转，get传值
Response.Redirect("a.aspx?x=11&y=22");
//目标网页使用Request对象的QueryString属性接收
string x=Request.QueryString["参数"]
```



### session

- 存储在服务器端的数据

`session的赋值：Session["变量名"]=变量、常量、字符串;`

`Session值的获取：变量名=Session["变量名"]`

```c#


```

### Application对象

- 用于保存所有用户的公共数据信息

- 记录整个网络的信息，如上线人数
