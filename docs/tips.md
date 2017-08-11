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

*	(jQuery)具有 true 和 false 两个属性的属性，如 checked, selected 或者 disabled 使用prop()，其他的使用 attr()

###	css
---

*	float不脱离文本流，可以撑开父元素（使用clear、或者父元素也float、或者可以设置父元素overflow属性任意都行），尤其注意父元素里只有float元素的要注意collapse；position：absolute脱离文本流，不会撑开父元素，不能通过css方法实现撑开父元素，设置z-index:-1才能被float浮动在上方，否则都是position:absolute在上面。position:relative;仍然占据原来的空间，只是其实际位置可能改变，但空间仍是原来的空间。

*	A Space between Inline-Block List Items<br>
display:inline-block的li元素间有空格，解决方法：每个li的开元素紧跟上一个li闭元素；或者ul的font-size:0；因为默认了ul的font-size为4px。

*	ul li中去掉多余的白边空位置：li{font-size：0;}然后其它需要用到字体大小再设置。因为默认li中有4px的位置空出来。

*	display: inline-block里面子元素和父元素之间存在间隙，使用vertical-align:middle消除（font-size: 0也可以）

*	content属性可以这样用：<br>
content: attr(data-content)<br>
使用元素里面的data-content属性值来赋值。伪类里是读取伪类绑定元素的属性值。然后使用js脚本设置data-content属性值就可以了，IE低版本不支持。

*	margin collapse：(bottom)可以设置父元素overflow属性

*	animation属性0s要加上秒的单位s

*	父元素overflow: hidden，子元素要突破父元素界限，可以设置子元素position: absolute，但是父元素不能position: relative;