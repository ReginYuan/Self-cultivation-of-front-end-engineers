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

