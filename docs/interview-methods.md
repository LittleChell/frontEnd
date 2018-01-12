##	view * methods

*	深拷贝与浅拷贝

	浅拷贝：只是新增加指针指向原来的内存	。
	直接使用等于号可以实现浅拷贝。

	深拷贝：增加一个指针并且申请一个新的内存，使这个增加的指针指向这个新的内存。

	在js中，可以通过obj = JSON.parse(JSON.stringify(o))来快速高效地实现深复制，但是这个方法**不能复制对象里面的函数**。

	通过for in 方法可以实现全部深复制，但是如果值里面是对象，还需要通过递归来进一步进行深拷贝，否则对象里面的对象会是增加指针而不是拷贝内存。

*	区分是数组还是对象（数组属于对象），附加：判断实例属于哪种类型

	Array.isArray()方法

	也可以使用Object.prototype.toString.call(object)
	1.	Object.prototype.toString.call([]) === '[object Array]'
	2.	Object.prototype.toString.call({}) === '[object Object]'
	3.	Object.prototype.toString.call(null) === "[object Null]"
	4.	Object.prototype.toString.call("") === "[object String]"
	5.	Object.prototype.toString.call(1) === "[object Number]"
	6.	Object.prototype.toString.call(undefined) === "[object Undefined]"
	7.	Object.prototype.toString.call(false) === "[object Boolean]"
	8.	Object.prototype.toString.call(NaN) === "[object Number]"
	9.	Object.prototype.toString.call(function a(){}) === "[object Function]"
	10.	Object.prototype.toString.call(new Date()) === "[object Date]"

*	创建对象经历了怎么样的过程

	JavaScript中的所有对象都来自Object；所有对象从Object.prototype继承方法和属性，尽管它们可能被覆盖。
	
	Object是一个function，是native code

*	Function instanceof Object === true

*	prototype和\_\_proto\_\_

	
	注：使用\_\_proto\_\_是有争议的，也不鼓励使用它。因为它从来没有被包括在EcmaScript语言规范中，但是现代浏览器都实现了它（MDN）
	
	prototype：prototype是**函数**的一个属性（每个函数都有一个prototype属性），这个属性是一个指针，指向一个**对象**。可以这么理解，在当前实例上面没有的方法属性，通过浏览器的内部实现机制（c++等），查看有没有prototype属性，有的话在prototype属性指向的对象上面查找，如果还没有找到，还存在prototype属性的话继续向该对象查找，以此类推。

	\_\_proto\_\_是一个对象拥有的内置属性（请注意：prototype是函数的内置属性，\_\_proto\_\_是对象的内置属性），是JS内部使用寻找原型链的属性，是所有对象(包括函数)都有。

	每个对象的__proto__属性指向自身构造函数的prototype。

*	Array, String, Number, Boolean, Object都是function

*	constructor
	
	constructor元素创建的时候就有的，指向创建该元素的构造函数。
	
	有时候（比如某些继承方式）需要修正constructor的指向，来保证原型链的指向正确（并不会影响prototype的指向，不影响原型链调用，只是影响通过访问constructor来访问prototype的实际元素）。

	作用：使实例可以通过constructor访问prototype
	

