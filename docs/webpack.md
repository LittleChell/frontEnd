##	webpack

[webpack介绍](https://www.jianshu.com/p/42e11515c10f)

###	什么是Webpack

WebPack可以看做是模块打包机：它做的事情是，分析你的项目结构，找到JavaScript模块以及其它的一些浏览器不能直接运行的拓展语言（Scss，TypeScript等），并将其转换和打包为合适的格式供浏览器使用。

###	WebPack和Grunt以及Gulp相比有什么特性

其实Webpack和另外两个并没有太多的可比性，Gulp/Grunt是一种能够优化前端的开发流程的工具，而WebPack是一种**模块化**的解决方案，不过Webpack的优点使得Webpack在很多场景下可以替代Gulp/Grunt类的工具。

Grunt和Gulp的工作方式是：在一个配置文件中，指明对某些文件进行类似编译，组合，压缩等任务的具体步骤，工具之后可以自动替你完成这些任务。（即要多步处理）

Webpack的工作方式是：把你的项目当做一个整体，通过一个给定的主文件（如：index.js），Webpack将从这个文件开始找到你的项目的所有依赖文件，使用loaders处理它们，最后打包为一个（或多个）浏览器可识别的JavaScript文件。（一次处理多个）

### webpack的plugin和module的区别

plugin作用于整个项目的构建部分，module作用于项目构建过程中的模块中。

###	webpack配置

*	source map

	sourcemap是为了解决开发代码与实际运行代码不一致时帮助我们debug到原始开发代码的技术。

*	modules的配置

	下载好相应的module后在module中配置相应的rule；其中规则也可以在外部的文件中配置，比如babel可以在.babelrc里面写入相关配置。

###	webpack配置性能优化

1.	unlifyJsPlugin（压缩js）在生产环境中使用
2.	利用 DllPlugin 和 DllReferencePlugin 预编译资源模块

该方式是将不需要改动的第三方插件与自己的业务代码进行分开打包。

DllPlugin的作用是预先编译一些模块，DllReferencePlugin则是把这些预先编译好的模块引用起来。DllPlugin必须要在DllReferencePlugin执行前先执行一次。

Dll优势：

*	DllPlugin的作用是预先编译一些模块，而DllReferencePlugin则是把这些预先编译好的模块引用起来。这边需要注意的是DllPlugin必须要在DllReferencePlugin执行前先执行一次；
*	Dll资源能有效地解决资源循环依赖的问题；
*	通过配置读取，减少维护的成本；

配置方式：

webpack.dll.conf.js：用来生成静态包dll的配置。
	
	const path = require('path')
	const webpack = require('webpack')
	module.exports = {
	  entry: {
	    vendor: ['vue','vue-router']
	  },
	  output: {
	    path: path.join(__dirname, '../static'),
	    filename: 'dll.[name].js',
	    library: '[name]'
	  },
	  plugins: [
	    new webpack.DllPlugin({
	      path: path.join(__dirname, '../', '[name]-manifest.json'),
	      name: '[name]'
	    })
	  ]
	}
	

webpack.base.conf.js：通常的打包的配置。这里引用的是**json文件**
	
	const manifest = require('../vendor-manifest.json')
	......
	这里是其它基本配置
	......
	plugins: [
	    new webpack.DllReferencePlugin({
	      manifest
	    })
	  ]
	

###	webpack生产文件性能优化

1.	代码分割、按需加载；
2.	提取第三方库，减小源代码体积；

###	webpack一些配置参数

vendor：项目打包的时候，把一些公用的库打包到vendor.js中，配合CommonsChunkPlugin插件；

manifest：在vendor的基础上，再抽取出要经常变动的部分，比如关于异步加载js模块部分的内容。

external：把依赖资源声明为一个外部依赖，然后通过script外链脚本引入。通过配置后可以告知webpack遇到此类变量名时就可以不用解析和编译至模块的内部文件中，而改用从外部变量中读取，这样能极大的提升编译速度，同时也能更好的利用CDN来实现缓存。

###	常用插件

*	HtmlWebpackPlugin

	自动生成最终的HTML文件

*	ExtractTextPlugin
	
	样式脚本分开打包

*	HMR

	局部热更新

*	CommonsChunkPlugin

	把一些公用的库打包；这里会整体打包。

	