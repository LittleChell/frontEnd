#	Scss

###	变量

*	变量声明用$，如$var。
*	变量使用在属性或者选择器上，就需要用#{}包裹起来，变量声明还是用$，如#{var}
*	变量先声明的会被后声明的覆盖，包括import进来的变量
*	变量声明带有!default，那么如果在此声明之外没有这个变量的声明，则用这个值。
*	一个变量可以声明多个值，用空格符分隔值，通过nth($var,index)可以获取第几个值，也可以全部都使用。
*	嵌套变量中对变量重新赋值会影响嵌套里面部分后面该变量的值。

	p{ <br>
		$color:blue; <br>
		color:$color;//blue <br>
		a{ $color:red; color:$color;//red } <br>
		background-color:$color;//red <br>
		span{ color:$color;//red } <br>
	}

###	Mixin

@mixin指令提高代码的重复使用率并简化代码。

*	通过@include来调用mixin模块
		
	@mixin name { 
		font-size: 1em; padding: 0.5em 1.0em; text-decoration: none; color: #fff; 
	}

	.button-green { @include name; background-color: green; }

*	在mixin定义的变量名后增加三个点（...）来使mixin模块接收数量可变的参数。使用@include传递参数的时候，使用逗号将参数分开。


