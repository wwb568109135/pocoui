#IE6 神奇的3px

---

假设建立一个简单的2列布局，左边一列是200像素宽，右边一栏是600像素宽，他们处于一个800像素宽容器内。

HTML是这样：

```html
<div id="main">
	<div id="box1"></div>
	<div id="box2"></div>
</div>
```

CSS是这样：
```css
#main{
	width: 800px;
	background-color: #ff0;
}
#box1{
	float: left;
	display: inline;
	width: 200px;
	height: 100px;
	background-color: #000;	
}
#box2{
	width: 600px;
	height: 100px;
	margin-left: 200px;
	background-color: #ccc;
}
```

200px + 600px = 800px，因此这2列很准确地符合父级容器所设置的宽度。

使用IE7-9、Chrome、Firefox、Safari、Opera浏览会出现下面结果：


但在IE6上，#box1右边额外增加了3px，#box2剩余的位置只有597px，导致#box2掉了下去，如下图：


这是一个异常隐蔽的BUG，我看来