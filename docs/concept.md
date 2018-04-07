##	Concept

####	vertical-align

	[https://segmentfault.com/a/1190000007663895](https://segmentfault.com/a/1190000007663895)

####	Promise

	```
	new Promise(function(resolve, reject) {
	  //do something here
	  //when do something done
	  resolve();
	});


	then(function(){
	  //resolve
	}, function () {
	  //reject
	  //这里如果没有明确返回Promise对象并且reject，那么将把返回结果给到后面then的resolve状态中。
	})

	```

	then可以使用链式调用的写法原因在于，每一次执行该方法时总是会返回一个Promise对象。另外，在then onFulfilled的函数当中的返回值，可以作为后续操作的参数。then里面如果是Promise对象，那么可以通过Promise里面的resolve或者reject来决定后续then的状态,或者return消息传给后面then作为函数参数。

	Promise的抛错具有冒泡性质，能够不断传递，这样就能够在下一个catch()中统一处理这些错误。同时catch()也能够捕获then()中抛出的错误，所以建议不要使用then()的rejected回调，而是统一使用catch()来处理错误。

	可以通过构造函数的方式来建立一个Promise对象new Promise，也可以通过直接调用Promise函数上面的reject、resolve方法来执行。

####	document.domain

	两个文档，只有在 document.domain 都被设定为同一个值时，表明他们打算协作；或者都没有设定 document.domain 属性并且URL的域是一致的 (如何判断一致)，这两种条件下，一个文档才可以去访问另一个文档。
