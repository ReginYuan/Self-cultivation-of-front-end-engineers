# HTML基础

## HTML

- 超文本标记语言，用于创建和描述网页的标记语言
- 超文本，即可以加入图片、声音、动画、多媒体等内容，不仅如此，它还可以从一个文件跳转到另一个文件，与世界各地主机的文件连接。
- HTML源于**SGML（标准通用标记语言）**，HTML5后不再基于SGML

##### 基本文档结构

​	包括四个HTML元素`DOCTYPE`、`html`、`head`、`body`

| 元素     | 说明                                     |
| -------- | ---------------------------------------- |
| DOCOTYPE | 文档类型说明，有助于确定浏览器的渲染模式 |
| html     | 根元素，HTML部分的开始                   |
| head     | 包含文档的元数据                         |
| body     | 包含文档的内容                           |

## DOCTYPE

- 用于声明文档类型和DTD规范，确保不同浏览器以相同的方式解析文档，以及执行相同的渲染模式。
- **DTD文档类型定义**，保证SGML和XML文档格式的合法性

注意：  一些老网站可能用的还是老版本的文档类型比如 XHTML之类的，但是我们学的是HTML5,而且HTML5的文档类型兼容很好(向下兼容的原则)，所以大家放心的使用HTML5的文档类型就好了。

### 常用声明

**1. HTML5**

​	HTML5不再基于SGML，所以不需对DTD进行引用、但是需要DOCTYPE来规范浏览器的行为（让浏览器按照它们的方式来运行）

```html
<!DOCTYPE html>
```

**2. HTML 4.01**

​	基于SGML，需要对DTD进行引用，才能告知浏览器文档所使用的类型。

DTD分为三种

- 严格(Strict)：包含所有的HTML元素和属性，不包括已废弃的元素（font、center）和框架元素（frameset、frame）
- 过渡(Transitional)：不包含框架相关的元素
- 框架集(Frameset)：包含所有HTML元素和属性

**3. XHTML 1.0**

​	DTD也分三种

## XHTML

### XHTML规范

- XHTML按照XML(可扩展标记语言)的要求来规范HTML
- XML是SGML的一个子集

### HTML与XHTML的区别

- 需要良好的文档结构，不能随意嵌套
- 元素名称区分大小写，且元素名称和属性要小写
- 所有元素都要有结束标签
- 注释会被忽略
- 元素的属性值需要用引号包裹

## HTML实体

### HTML实体的定义

三种方式

1. **名称方式**

   ```html
   以"&"开头
   &name;
   &lt;
   ```

2. **十进制方式**

   ```html
   以"&#"开头，后紧跟数字
   &#60;	十进制"<"
   ```

3. **十六进制方式**

   ```html
   以"&#x"开头，后紧跟数字
   &#x0003C
   ```

   

## 元素基础

### 元素的分类

1. **基本类型**

| 类型                 | 描述                                                         |
| -------------------- | ------------------------------------------------------------ |
| 虚元素               | 既没有内容，也没有结束标签，如br、input、img                 |
| 原始文本元素         | 包含开始内容和结束标签，单内容只能是文本，必能有元素，如script、style |
| 可转义的原始文本元素 | 含开始内容和结束标签。内容可以是文本或元素，对于特殊字符会自动执行HTML实体，如textarea、title |
| 外部元素             | MathML(数学标记语言)、svg                                    |
| 普通元素             | 不包含再前4类的元素都是普通元素。这类元素可以为空，为空时也叫空元素，虚元素包含在空元素中 |

2. **按盒类型分**

   > 替换元素：内容不包含在文档中，如img、object、video，表单元素（input、textrear）
   >
   > 非替换元素

   - 块级元素
   - 行内元素

### 元素属性

1. **属性的分类**
   - 全局属性
     - ARIA(无障碍网页应用属性)
     - 事件属性，一般以on开头，如onclick
     - 自定义属性，一般以"data-"为前缀
   - 局部属性，如form中的action、textrear中的row

2. **布尔属性**

   设置值时，只能是 属性=”属性值“ 或空值

   ```html
   单选框的3种方式选中
   <input type="radio" checked/>
   <input type="radio" checked="checked"/>
   <input type="radio" checked=""/>
   ```

   取消选中时，只能将该属性从标签中移除，不能设置false或空值

## CSS样式应用

> ###### 三种方式：内连、内嵌、外部样式

### 内联样式

```html
<p style="color:red">内联样式</p>
```

- 特殊性（权重）最高
- 不能定义伪类，伪元素

### 内嵌样式

```html
<style type="text/css">
    p{
        color:red;
    }
</style>
```

**style的四个属性**

| 属性      | 说明                                                         |
| --------- | ------------------------------------------------------------ |
| **type**  | 指定MIME类型，默认text/css                                   |
| **media** | 指定媒体类型，默认all，设置多个则逗号隔开。如设置print(打印机) |
| **title** | 为样式表命名，用于设置首选样式，如下例                       |

> MIME：多用途互联网邮件扩展类型；一个互联网标准，给在网络中传输的内容赋予类型，当终端接收的时候，可根据类型执行相应的处理。

```html
<!--将titile为red的样式表设置为首选样式表-->
<meta http-equiv="Default-Style" content="red" />
<style title="red">
</style>
<style title="blue">
</style>
```

### 外部样式

通过<link>元素引用

```html
<link rel="stylesheet" type="text/css" href="css/style.css"/>
```

包含5个特殊属性，type、media、title（作用与style元素中的相同），href和rel

| 属性 | 作用                                                         |
| ---- | ------------------------------------------------------------ |
| href | 超文本引用，定义要链接的资源的URL，可以是相对或绝对的URL（用于link 和 a 元素） |
| rel  | relation定义当前文档与目标资源的关系。有多个关键字可选（alernate、tag、stylesheet），stylesheet表示文档的外部样式表 |

> scr：表示源地址，用在img、script、iframe

## 嵌入JS

> 三种方式：内联脚本，外部脚本，元素属性

### 外部脚本

```html
<script src="" type="text/javascript"></script>
```

- 通过定义script元素的src属性来引用外部脚本
- type定义MIME类型，不设置，则默认是text/javascript类型

**script元素的默认运行机制**

1. HTM解析遇到script元素，会先执行脚本，再恢复文档的解析和渲染
2. 默认情况脚本的执行是同步和阻塞的（推荐将脚本放置body结束前）

#### script元素解决阻塞新增的两个属性

| 属性  | 作用                           | 执行顺序 |
| ----- | ------------------------------ | -------- |
| defer | 延迟脚本执行，直到文档解析完成 | 有序     |
| async | 尽快执行脚本，不会阻塞文档解析 | 无序     |

两者都不会阻塞HTML文档的解析

### 元素属性

> 通过元素的事件属性和与链接相关的属性（href、action）来定义脚本

1. **事件属性**

   事件属性都以on为前缀

   ```html
   <input type="button" onclick="print()"
   ```

2. **特殊协议**

   javascript:伪协议，只能用于a的href，form的action

   ```html
   <a href="javascript:alert('test')">点击</a>
   ```

## meta元素

> 四属性：charset、name、http-equiv、content

- 每个meta元素只能有一个用途
- 使用meta，则必须定义charset、name、http-equiv三个属性之一
- 定义了name、http-equiv，则必须定义content
- content不能单独出现

### charset

> HTML5新增属性，表示HTML文档中的内容所用的字符编码（不区分大小写）

```html
<meta charset="uft-8"/>
过去的声明方式
<meta http-equiv="content-type" content="text/html";charset="utf-8"/>
```

### name

- 用来表示文档级元数据，每个name属性值对应特定的content值
- name主要服务于计算机SEO，让计算机能更好地理解当前文档

```html
<meta name="application-name" content="web应用程序的名字"/>
<meta name="author" content="作者"/>
<meta name="description" content="对文档内容的描述"/>
<meta name="keywords" content="文档关键字，多个逗号分隔"/>
<meta name="viewport" content="主要用于移动设备，可设置浏览器中的视口"/>
```

### http-equiv

- 用于模拟HTTP首部，每个http-equiv属性值对应特定的content值

1. content-type:定义MIME类型与字符编码（已不推荐使用）
2. default-style：指定首选样式表，定义的名称要与link或style元素中的title值匹配

```html
<meta http-equiv="default-style" content="red"/>
```

3. refresh：执行重载（只需定义秒数），重定向（需定义秒数和URL）

```html
<meta http-equiv="refresh" content="2"/>	重载
<meta http-equiv="refresh" content="2;url=绝对或相对URL"/>	重定向
```

## 数据存储

本地存储

会话存储

### Cookie

> 用来保持请求的状态

用户访问网站时，会发起大量请求，大部分是基本HTTP协议的HTTP请求，而HTTP协议是无状态的（每个请求都是独立的，前后没有联系），会严重阻碍交互式Web的实现

**缺点**

1. 不适合存储隐私和敏感信息，因为cookie会在网络中传递容易被劫持，劫持后可伪造请求。如CSRF(跨站点请求伪造)
2. 大小限制在4KB左右

### Web存储

- 存储容量2.5~10MB之间
- 比较容易实网页或应用的离线话 
- 不会作为请求报文中的额外信息传递给服务器
- 本地存储永不过期
- 会话存储只存在于页面会话期间

```javascript
//通过javascript的全局属性localStorage和sessionStorage来访问
localStorage.setItem("local","local data")	//设置本地存储
sessionStorage.setItem("session","session data")	//设置会话存储

var local=localStorage.getItem("local"),	//获取本地存储
    session=sessionStorage.getItem("session")	//获取会话存储
```

