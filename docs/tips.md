##	Tips

*	判断数组为空<br>

	.length === 0

*	读取样式的问题

	js .style只能获取到元素标签style = ""; 的具体值，而头部定义和外部样式无法获取到具体值（不包括从其它样式表层叠而来并影响到当前元素的样式信息）。一些方法或属性都是只针对style起作用的。
	所以如果要获取所有的CSS对象属性值，使用currentStyle和getComputedStyle。currentStyle是IE的方法，用法和style一样，getComputedStyle（ELEMENT，":after"）是其它浏览器方法，用法document.defaultView.getComputedStyle（）；不过currentStyle和getComputedStyle是只读的，修改CSS样式还是要用style来修改。也有Element.getClientRects()的方法，可以计算出使用百分比的长宽在显示器中的具体px。
	样式的style.left, style.top这些最好用'300px'这种，即最好用px表示而不是直接写数字（有时候不起作用），但是offsetLeft、scrollLeft这种最好直接写数字，用px好像不起作用。

*	引用传递

	对象、数组

*	"", NaN, null, undefined, false, 0 == false

*	一般不能在**本地文件**设置查看cookie

*	appendChild()

	appendChild()只能将新创建的节点加到一个父元素节点末尾或者移动已存在的节点到父元素节点末尾，不能通过循环重复添加节点，最多只能添加一个节点。要不断添加新节点需要不断创建新节点以加入。