##	Position & Measurement

#####	screen

	width：返回显示器屏幕的宽度；
	height：返回显示屏幕的高度。
	availWidth：返回显示屏幕的宽度 (除 Windows 任务栏之外)；
	availHeight：返回显示屏幕的高度 (除 Windows 任务栏之外)。

---

#####	元素

######	offset有四个（只读）：

	offsetHeight：元素垂直高度（包括content、padding、border）
	offsetWidth：元素水平宽度（包括content、padding、border）
	offsetTop：元素上外边框和包含元素的上内边框之间距离
	offsetLeft：元素左外边框和包含元素的左内边框之间距离

	offsetParent：包含元素的父元素；

######	client只有两个（只读）：

	clientHeight（包括content、padding）
	clientWidth（包括content、padding）

######	scroll有四个（只读）：
	scrollHeight（无滚动条下元素内容总高度）（包括content、padding）
	scrollWidth（无滚动条下元素内容总宽度）（包括content、padding）
可以设置或读取

	scrollTop（被隐藏在滚动条上方内容的像素数）
	scrollLeft（被隐藏在滚动条左侧内容的像素数）

---

#####	鼠标

相对于浏览器视口

	clientX, clientY, 

相对于页面（包括滚动）

	pageX, pageY, 

相对于屏幕

	screenX, screenY

浏览器（少用）

	innerWidth、innerHeight、outerHeight、outerWidth

直接使用

	location, navigator, screen

---
