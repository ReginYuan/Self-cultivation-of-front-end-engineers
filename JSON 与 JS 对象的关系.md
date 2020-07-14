### JSON 与 JS 对象的关系

很多人搞不清楚 JSON 和 Js 对象的关系，甚至连谁是谁都不清楚。其实，可以这么理解：

**JSON 是 JS 对象的字符串表示法，它使用文本表示一个 JS 对象的信息，本质是一个字符串。**

如

```
`var` `obj = {a: ``'Hello'``, b: ``'World'``}; ``//这是一个对象，注意键名也是可以使用引号包裹的`
```



### JSON 和 JS 对象互转

要实现从JSON字符串转换为JS对象，使用 JSON.parse() 方法：、

IE8以下不支持parse方法，可使用json2.js框架添加该引用来兼容

```
`var` `obj = JSON.parse(``'{"a": "Hello", "b": "World"}'``); ``//结果是 {a: 'Hello', b: 'World'}`
```

要实现从JS对象转换为JSON字符串，使用 JSON.stringify() 方法：

```
`var` `json = JSON.stringify({a: ``'Hello'``, b: ``'World'``}); ``//结果是 '{"a": "Hello", "b": "World"}'`
```

#### 将非标准的JSON字符串转化为对象

非标准的JSON字符串，即键值对不带引号

`var obj=eval("("+json+")")`，使用eval()方法，但需要在json数据两边加上（）