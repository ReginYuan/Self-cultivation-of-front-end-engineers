1. 响应
- res.render('index',date)：响应一个模板（views/index.html）,date是给模板传递值、
- res.end([])：结束响应（同时还可以返回内容）
-  res.json()：以JSON数据格式来响应客户端
2. get(/<u>参数1</u>,<u>function(req,res){}</u>)方法
    + /参数1：指定的路由名称，如/index
    + req:包含用户的请求信息，如URL传递的参数、POST提交的数据
    + res：服务器的响应信息，返回文本数据：res.send()；返回JSON数据res.json();

##### 服务端获取客户端提交的数据
1. 获取GET请求携带的参数：**req.query**

   get请求可以把向服务器传递的参数放到URL里面去

2. 获取POST提交的数据： **req.body**

