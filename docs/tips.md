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

*	事件触发的先后顺序<br>
	blur > click <br>
	mousedown > mouseup > blur

	只使用mousedown不能阻止事件冒泡，要阻止事件冒泡还需要在click事件里面调用stopPropagation
	

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

*	animation属性0s要加上秒的单位s

*	**前提**父元素overflow: hidden，子元素要突破父元素界限，可以设置子元素position: absolute来使子元素相对第一个非static的祖先元素定位;但是如果该子元素超出第一个非static的祖先元素的范围，超出部分会被隐藏，即不能突破第一个非static的祖先元素的范围。

*	border-radius: 左上角水平圆角半径大小	右上角水平圆角半径大小	右下角水平圆角半径大小	左下角水平圆角半径大小/左上角垂直圆角半径大小	右上角垂直圆角半径大小	右下角垂直圆角半径大小	左下角垂直圆角半径大小;百分比水平取的是宽，垂直取的是高。

*	BFC（块格式化上下文：它是块级盒布局的区域，也是浮动元素进行交互的区域）。
	由以下之一创建：<br>
	根元素或其它包含它的元素<br>
	浮动元素 (元素的 float 不是 none)<br>
	绝对定位元素 (元素的 position 为 absolute 或 fixed)<br>
	内联块 (元素具有 display: inline-block)<br>
	具有overflow 且值不是 visible 的块元素<br><br>
	应用：<br>
	防止margin重叠，即不会发生margin collapse<br>
	浮动相关问题<br>

*	IFC

	IFC(Inline Formatting Contexts)直译为"内联格式化上下文"，IFC的line box（线框）高度由其包含行内元素中**最高**（可能包含多个line box）的实际高度计算而来（不受到竖直方向的padding/margin影响)

	IFC中的line box一般左右都贴紧整个IFC，但是会因为float元素而扰乱。**float元素会位于IFC与line box之间，使得line box宽度变窄。** 同个IFC下的多个line box高度会不同。 IFC中是不可能有块级元素的，当插入块级元素时（如p中插入div）会产生两个匿名块与div分隔开，即产生两个IFC，每个IFC对外表现为块级元素，与div垂直排列（可以理解为块级元素单独占一行）。
	
	那么IFC一般有什么用呢？
	
	水平居中：当一个块要在环境中水平居中时，设置其为inline-block则会在外层产生IFC，通过text-align则可以使其水平居中。
	
	垂直居中：创建一个IFC，用其中一个元素撑开父元素的高度，然后设置其vertical-align:middle，其他行内元素则可以在此父元素下垂直居中。

*	先浮动的元素会影响后面行内元素的起始位置（即IFC中所述的，float元素会位于IFC与与line box之间，使得line box宽度变窄。），但不影响块级元素的位置。

*	怪异模式（Quirks Mode）和标准模式（又称严格模式）

	标准模式是指浏览器按W3C标准解析执行代码；
	声明DOCTYPE来决定浏览器使用标准模式。

	怪异模式是使用浏览器各自的方式解析执行代码；
	不加DOCTYPE，浏览器使用怪异模式。

*	纯函数

	相同的输入，永远会得到相同的输出，而且没有任何可观察的副作用。