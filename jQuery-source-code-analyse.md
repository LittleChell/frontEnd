#	jQuery


######	
	全局抛出
	window.jQuery = window.$ = jQuery;

######
	通过noConflict指定别名访问jQuery对象	
	noConflict: function( deep ) {
		if ( window.$ === jQuery ) {
			window.$ = _$;
		}

		if ( deep && window.jQuery === jQuery ) {
			window.jQuery = _jQuery;
		}

		return jQuery;
	}

######
	jQuery是function，每次调用jQuery都产生一个新的实例
	jQuery = function( selector, context ) {
		// The jQuery object is actually just the init constructor 'enhanced'
		return new jQuery.fn.init( selector, context, rootjQuery );
	}

######
	jQuery.fn = jQuery.prototype
	jQuery.fn是jQuery原型的另一种引用
	

######
	jQuery.fn是return this，jQuery是return其它类型

######
	jQuery选择器
	rootjQuery指向$(document)
	$(DOMElement)：
	返回this.context, this.length

