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
	
*	自动类型转换


	1.	转换为数字类型
	
		Number原始类型值的转换规则
	
		数值：	转换后还是原来的值。
		字符串：	如果可以被解析为数值，则转换为相应的数值，否则得到NaN。空字符串转为0。
		布尔值：	true转成1，false转成0。
		undefined：	转成NaN。
		null：	转成0（因为c++中NULL即空指针值为0）。
		对象	:	valueOf()方法先试图被调用，如果调用返回的结果为基础类型，则再将其转为数字，如果返回结果**不是基础类型**，则会再试图调用toString()方法，最后试图将返回结果转为数字，如果这个返回结果是基础类型，则会得到一个数字或NaN，如果不是基础类型，则会抛出一个异常。
	
		二元运算符'-', '+', '*', '/'会把运算子自动转为数值（'+'号特殊一点儿，如下面2所述）。

		'-', '+', '*', '/'作为一元操作符时，引擎会试图将操作数转换为数字类型，如果转型失败，则会返回NaN

		tips:	parseInt会从左到右逐个解析数字直到遇到非数字，如果第一个是非数字或者是空字符串，那么返回NaN

	2.	转换为字符串类型

		当加号“+”作为二元操作符(binary)并且**其中一个操作数为字符串类型**时，另一个操作数将会被无条件转为字符串类型

		对于基础类型（boolean、number、null、string、undefined），会直接转为与字面量相一致的字符串类型，而对于复合类型（object、function），会先试图调用对象的valueOf()方法，如果此方法返回值是引用类型，则接着再调用其toString()方法，最后将返回值转为字符串类型。

	3.	转换为布尔类型

		数字：	0和NaN会自动转为false，其余数字都被认为是true。

		字符串：	空字符串会被转为false，其它字符串都会转为true

		undefined和null: undefined和null在逻辑环境中执行时，都被认为是false

		对象（函数）:	当对象在逻辑环境中执行时，只要当前引用的对象不为空(null)，都会被认为是true。

		注意：	new Boolean(false) == true
				Boolean(false) == false

	4.	比较操作符
		
		比较操作符有以下几种：>, >=, <, <=, ==, ===

		1). 当两个操作数都为字符串类型时，不进行数据类型转换，直接比较每个字符（数字类型也是直接比较，凡是有NAN的全是false）

		2). 当两个操作数不同时为字符串时，将操作数转为数字类型，然后进行比较（包括字符串和数字类型比较）

		3). 如果操作数中存在对象类型，先将对象转为基础类型（valueOf和toString()），然后再根据上面两条进行值的比较。

		4).	null和undefined在比较时不进行数据转换，null和自身比较、null和undefined比较都会返回true，和其他值比较都会返回false；undefined和自身比较、undefined和null比较都会返回true，和其他值比较都会返回false。

	5.	一些例子：	
	
		var foo = +[];            // 0 ( [] -> '' -> 0 )，先调用valueOf后调用toString，[].toString() == ''

		var foo = {} + 0;        // '[object Object]0'

		{} + 0;        // 0（命令行直接输入，{}被解释成代码块）
		