# Canvas

- HTML5新引进标签

#### HTML

```html
<canvas id="canvas"></canvas>
```



#### Javascript初始化

```javascript
var canvas=document.getElementById('canvas');
//canvas的三个接口：width,height,getContext()
canvas.width=1024;
canvas.height=768;
var context=canvas.getContext('2d')//绘图的上下文环境，提供真正的绘图接口
```

#### 兼容性处理

1. canvas标签控制

```html
<canvas id="canvas" style="display: block;border: 1px solid #aaa; margin: 50px auto;">
    当前浏览器不支持canvas，请更换浏览器后再尝试
</canvas>
```

2. js控制

```javascript
if(canvas.getContext('2d')){
    var context=canvas.getContext('2d');
}else{
    alert("当前浏览器不支持canvas，请更换浏览器后再尝试");
}
```

#### 画直线

基于状态绘制，即先定义的状态会被后定义的状态在执行绘图时所代替

```javascript
//绘图的状态设置
context.moveTo(100,100)//从哪画
context.lineTo(700,700)//画到哪

//绘图的样式设置
context.lineWidth=5//线宽
context.strokeStyle=""//颜色颜色
context.fillStyle=""//填充的颜色

//调用绘图的具体方法
context.stroke()//执行画直线
context.fill()//色块填充执行
```

#### 多状态分开处理

```js
context.beginPath()//重新规划一条路径
context.closePatch()//结束当前路径，如果当前路径没有形成封闭则自动封闭路径（对于fill()无效果）
```

- 不一定要成对出现

#### 画弧画圆

```javascript
context.arc(x,y,r,sAng,eAng,anticlock=false)
```

找到当前上下文所在的画布

context.canvas

context.clearRect(x,y,width,height)

#### Canvas动画的基本方法

```javascript
setInterval(
    function(){
        render();//数据渲染
        update();//数据修正
    },
    50
)
```

