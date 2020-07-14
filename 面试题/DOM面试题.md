# DOM面试题

1. 多种方式获取下面文本框中的vaule值

```html
<form action="" class="register">
	<input type="text" id="txt" value="">
</form>
<script>
	document.getElementById("txt").value;
	document.forms[0].tet.value;
	document.forms.register.txt.value;
	document.forms[0].elements[0].value;
</script>
```

2. 不使用border模拟边框，利用阴影可模拟边框（无限嵌套）

```html
<style>
    div{
		margin: 50px auto;
		width: 100px;
		height: 100px;
		box-shadow: 0 0 0 5px aqua,
				    0 0 0 10px blue,
				    0 0 0 15px palevioletred;
		}
</style>
<div></div>
```

3. 将元素的display属性设为inline-block后，多个元素在一行显示会存在空隙，如何消除间隙？

- 有间隙是因为格式化文档后，标签间包含换行符和空白符，浏览器会将这些额外的字符合并成一个空白符
- 解决：将多个元素写在一行中

4. 如何用CSS3的媒体查询实现视口宽度大于360px而小于640时，div元素的宽度变成30%

```css
@media only screen and (min-width:360px)and(max-width:640px){
    div{
        width:30%; 
    }
}
```

