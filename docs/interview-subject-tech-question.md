##	技术开放性问题

####	React 和 Vue 

相同点：

*	使用 Virtual DOM

*	提供了响应式 (Reactive) 和组件化 (Composable) 的视图组件。

*	将注意力集中保持在核心库，而将其他功能如路由和全局状态管理交给相关的库。

React：
	
*	更丰富的生态系统

Vue：
	
*	能精确知道哪个组件需要被重新渲染

*	gulp和webpack的主要区别

	webpack更擅长模块化处理，项目整体依赖性比较强。

	gulp更擅长任务化处理和管理。

####	预加载

在资源还没有正式使用的时候，先把资源预先加载到浏览器中。有时候这种方式可以提升用户体验。

方式：

1.	脚本指定	
	
	```

		var img = new Image();

		img.src = ...

	```

	或者动态生成img标签

	```

		var img = document.createNode('img');

		img.src = ...

	```

2.	css样式里面可以使用background-image先加载，但是不显示图片
3.	Ajax方式

	推荐使用该方式，更加高效。

	