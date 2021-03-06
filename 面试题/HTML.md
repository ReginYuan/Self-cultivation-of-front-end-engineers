# HTML和HTML5的区别

1. 旧版本的HTML比较依赖浏览器的插件，如播放视频需要安装flash插件
2. HTML5不再基于SGML，所以文档声明类型（DOCTYPE）只有一种
3. HTML5消除了过时或冗余的元素，如font、center
4. HTML5新增了许多语义化的元素（article、header）和新功能（video、canvas）
5. HTML5制定了新的全局属性（draggable,contenteditable）和元素属性(accept,placeholder)

# HTML实体的应用场景有哪些

1. 在HTML文档显示特殊字符("<"、">")
2. 预防XSS(跨站脚本攻击)攻击，XSS通常会将脚本代码注入到HTML文档中，再解析执行，使用了HTML实体后，就可以让相关代码只打印，而不执行

# 什么是Shdow DOM

​	Shadow DOM是浏览器的一种功能，能够自动添加子元素，如audio元素，其相关的进度条、音量控制都是由浏览器自动生成

# 元素属性`src`和`href`的区别

​	功能不同

- href能够建立一条通道，将当前文档和定义的资源连接起来
- src是将定义的资源嵌入到当前文档中

# img元素中的title和alt属性有何区别

- title是全局属性，显示定义的提示信息，link和style中的title表示样式表的名称
- alt是局部属性，仅可用在img、input(其type属性为image时可用)

# meta元素可以定义文档的哪些元数据？

1. 声明HTML文档内容所用的字符编码
2. 完善文档描述信息，让搜索引擎更容易解析索引，提升SEO
3. 适配移动设备，使页面在各种尺寸的屏幕中显示正确
4. 指定首选样式表、执行重载或重定向

# a元素除了可以用于导航外，还有什么其他功能

​	href属性中的URL可以是浏览器支持的任何协议，所有a元素也可用于**手机拨号、发送短信、发送邮件**等功能

```html
<a href="tel:10086">拨打电话</a>
<a href="sms:10086?body=test">发送短信</a>	可将内容作为参数直接带过去
<a href="mailto:strick@pw.org?cc=jane@pw.com">发送邮件</a>	可将收件人、抄送人、主题和内容作为参数直接带过去
```

------

# 用什么方法可以防止Cookie被盗取？

Cookie是先由浏览器向服务器发起请求，再由服务器响应后回传Set-Cookie首部（此时可设置HttpOnly属性）向客户端浏览器写入Cookie。在给Cookie设置HttpOnly属性后，就能禁止页面的JS访问该Cookie，从而避免被盗取。

------

# HTML的含义是什么？

-HML( Hyper Text Markup Language)即超文本标记语言,是一种用于创建网页的标记语言。

HTML经历过多个版本,包括HTML20、HTML3x、HTML4x以及最新的HML5。HIML源于标准通用标记语言( Standard Generalized Markup Language,sGML)
遵循SGML指定的语法和规则,但从HIML5开始,将不再基于SGML

------

# 什么是XHTML

HTML的格式比较松散,这会导致一些问题,如兼容性差、移植性差等。为了解决上述所列的种种问题,W3C在2000年发布了XHML1.0。

- XHTML是XML的一种应用，作为HTML的一个子集，它完全兼容HTML，但格式更严谨。 XHTML有过三个版本,分别是10、1.1和20。
- XHTML10与HTML4.01的不同之处在于语法规则，前者需要按照**XML(可扩展标记语言)**的要求来规范HTML,其中，XML是**SGML(标准通用标记语言)**的一个子集。

------

# 什么是CSS预处理器

CSS预处理器( CSS Preprocessor)能为CSs增加编程特性,通过编译器将使
用新语法的文件输出为一个普通的CSS文件,解决CSS难以复用、代码冗余、可维护性低的
问题。对CSS来说,它不是锦上添花而是雪中送炭,常用的预处理器有 Less Sass和Syus

------

# 什么是盒模型？

盒模型( Box Model,也称为框模型)就是从盒子顶部俯视所得的一张平面图,用于描述元素所占用的空间。它有两种盒模型:W3C盒模型和I盒模型(IE6以下,不包含IE6以及怪异模式下的E55+)。两者不同之处是对元素尺寸的计算方式。当用CSS给某个元素定义宽或高时,盒模型中内容的宽或高将会包含内边距和边框,而W3C盒模型并不会
包含。

------

# 什么是互联网？

互联网一词现在已经家喻户晓,它是由许多网络互联构成的一个巨型网络。早期的网络仅仅是连接计算机,而现代的互联网连接的却是全世界的人。互联网已经不再是单纯的以数据为核心,而是以人为中心,它已经渗透到了生活中的方方面面,颠覆了许多传统模式,例如是不出户就能购物、社交或娱乐。

------

# 请简单介绍一下HTTP

HTTP( Hypertext Trans fer Protocol)即超文本传输协议,是一种获取网络资源(例如图像、HTML文档)的应用层协议,它是互联网数据通信的基础,由请求和响应构成。
通常,首先客户端会发起HTp请求(在请求报文中会指定资源的URL),然后用传输层的TCP建立连接,最后服务器响应请求,做出应答,回传数据报文。HTTP自问世到现在,经历了几次版本选代,目前主流的版本是HTTP11,新一代HTTP2.0是HTTP/11的升级版,各方面都超越了前者,但新技术要做到软硬件兼容还需要时间。

# 请阐述对W3C的理解与认识

W3C是一个制定各种标准的非营利性组织,标准包括HTML、CSS、 XHTML和XML等。Web标准制定后,有以下几个方面的优点

1. 学习成本降低,只需按照已定的标准学习一套即可,否则将学习各个浏览器厂商制标准,繁而杂。
2. 统一开发流程,用标准化的工具(如 WebSter、 Sublime等)开发,再用标准化的器(如 Firefox、 Chrome等)测试网页,便于多人协作。
3. 简化网站代码的维护,不会有不同浏览器的多个版本,网页寿命也更长。
4. 跨平台,可方便迁移到不同设备中,例如添加无障碍标准后,能让残障人士更便捷
5. 标准大部分是由使用它们的人决定,例如浏览器制造商、Web开发人员等,这样的
   用设备访问网页。

# 请简单介绍一下HTML5m

- HTML5不仅仅是HTML的最新版本,它还是一系列Web技术的集合，包括CSS3、 JavaScript、多媒体、缓存和无障碍访问等。
- HML5的规范是由两个组织制定的,分别是WHATWG(网页超文本技术工作小组)和W3C。

# 什么叫渐进增强？和优雅降级有哪些区别

**渐进增强( Progressive Enhancement)**并不是一种技术,而是一种**设计思想。**各个览器的染能力各不相同,要做一个每个人都能看到的网页、感受到的体验都一致的网站几乎不可能。但还是得确保网站的可访间性,保证用户在任何环境下都能正常访问核心内容或使用基本功能(避免页面打不开、排版错乱等),并为他们提供当前条件下最好的体验,这是渐进增强的核心思想
**优雅降级( Graceful Degradation)**也是一种设计思想,保证在高版本浏览器中提供最好的体验,碰到低版本测览器再降级进行兼容处理,使其能正常浏览。两种思想的区别如下：

1. 渐进增强是向上兼容,优雅降级是向下兼容。
2. 渐进增强是从简单到复杂,优雅降级是从复杂到简单。
3. 渐进增强关注的是内容,优雅降级关注的是浏览体验。

# CSS预处理器有哪些优缺点

**优点**

1. 用变量存储多次引用的信息(如颜色值、字体、边距等),只需修改一个地方,就能
   让所有引用之处都随之改变。
2. 新语法中的混合( Mixin)能够重用一段样式代码,可用混合将自动截取或列表中的
   小箭头样式组织在一起,需要这段代码的选择器只需简单引入即可。
3. 内置丰富的函数,可处理颜色、字符串、数字和选择器等,也可自定义函数,适应
   特定需求。
4. 可像 JavaScript那样使用数学运算(如加、减、乘、除等),条件判断和循环,几句
   就可描述一大段CSS样式。
5. 选择器可嵌套选择器,沿着嵌套的选择器链向上组合形成最终的选择器,嵌套的形
   式模拟出了HIML的层级结构,同时形成了命名空间,选择器之间的关系更明显,增强了文
   件的可读性。
6. 导入规则可让各部分代码保持独立,模块化管理,各个导入的文件最终被编译生成
   个CSS文件

**缺点**

1. 通过编译生成CSS文件,降低了对CSS文件的控制力,如果书写不当,那么编译出
   的CSS文件将会巨大而复杂。
2. 调试难度增加,在浏览器中调试的是编译后的CSS文件,并不是编译前的源代码。
3. 带来了一定的学习成本,新人需要学习预处理器的语法规则,虽然内容不多,但要
   达到融会贯通,还是需要一定的锤炼。

# 请简单介绍一下网络中的协议

协议可简单理解为计算机之间的一种约定,好比人与人之间对话所使用的语言。在我国,不同地区的人讲的方言都不同,如果要沟通,就要约定一种大家都会的语言,例如全国通用的普通话,普通话就相当于协议,沟通相当于通信,说话内容相当于数据信息。

# 谈谈对TCP/IP的理解

TCPIP是为互联网服务的协议簇,它是网络通信协议的统称,由IP、TCP、HTTP和FTP等协议组成。 TCP/IP将通信过程抽象为4层,被视为简化的OSI参考模型,但负责维护这套协议簇的不是ISO而是互联网工程任务组(IETF),TCP/IP在标准化过程中注重开放性和实用性，需要标准化的协议会被放进RFC( Request For Comment)文档中,RFC文档详细记录了协议的实现、运用和实验等各方面的内容,并且这些文档可在线浏览。

# 什么是严格模式、严格模式有哪些限制

ECMAScript5引入了严格模式( Strict Mode)的概念。严格模式对 JavaScript的语法和行为都做了一些更改,消除了语言中一些不合理、不确定、不安全之处;提供高效严谨的差错机制,保证代码安全运行：禁用在未来版本中可能会使用的语法,为新版本做好铺热。

在脚本文件第一行或函数内第一行引入“ use strict”这条指令(如下代码所示),就能触发严格模式,这是一条没有副作用的指令,旧版本的浏览器会将其作为一行字符串直接忽略。

```javascript
"use strict"
//脚本文件第一行
function sum(x){
    "use strict",
	函数内第一行
	retun x
}
```

严格模式常见的限制有以下几条:
(1)所有的变量要先声明,无法再意外创建全局变量。
(2)函数中this对象的默认值是 undefined,而不是全局对象( window)
(3)试图使用 delete运算符删除不可删除的属性会抛出异常。
(4)函数声明中定义两个或多个同名参数将产生一个语法错误,例如sm(x,x){}
(5)禁止使用以0为前级的八进制数字(例如010),以0x为前缀还是支持的
(6)禁止使用with语句。
(7)不能将eval和 arguments用作变量、函数或参数的名称。
8.答案:当用 typeof运算符检测数据类型时,如果操作数是null,那么返回的不是“mul”
而是“ohje.如果要区分mu和对象,可以用基础对象 Object I的原型方法 toString(对mu
做进一步的检测,如下代码所示

