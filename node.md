#	NodeJs

###	npm

#####	本地安装、全局安装

---

######	本地安装

1. 将安装包放在 ./node_modules 下(运行npm时所在的目录)
2. 可以通过 require() 来引入本地安装的包

######	全局安装	

1. 一般在 \Users\用户名\AppData\Roaming\ 目录下，可以使用npm root -g查看全局安装目录。

2. 可以直接在命令行中使用。

PS：
在模块中使用require()，那么使用本地安装；
在命令行中使用，那么应该全局安装。

#####	dependencies &ensp; devdependencies &ensp; peerdependencies

---

######	dependencies

npm install会安装

npm install $package也会安装

会安装依赖

######	devdependencies

npm install会安装，除非加上--production

npm install $package不会安装除非加上--dev

不会安装依赖

link:	[https://stackoverflow.com/questions/18875674/whats-the-difference-between-dependencies-devdependencies-and-peerdependencies](https://stackoverflow.com/questions/18875674/whats-the-difference-between-dependencies-devdependencies-and-peerdependencies)

#####	--save &ensp;	--save-dev

--save作为应用来run，会把依赖包名称添加到 package.json文件dependencies键下

--save-dev用来开发使用，添加到package.json文件devDependencies 键下

#####	npm常见错误
*	
	node install.js 
	
	...
	
	This is probably not a problem with npm. There is likely additional logging output above
	...
	
	这里是因为在执行安装的过程中需要执行install.js，这里会下载Chromium,官网建议是进行跳过，我们可以执行 —ignore-scripts 忽略这个js执行。也可以通过设置环境变量set PUPPETEER_SKIP_CHROMIUM_DOWNLOAD=1阻止下载 Chromium （因为封网，直接下载会失败）

	解决:npm i --save puppeteer --ignore-scripts

#####	file
#####	setImmediate and process.nextTick

The setTimeout's callback will be called from the event loop.（event loop里面）

The setImmediate callbacks are fired off the event loop.
Use setImmediate if you want to queue the function behind whatever **I/O event** callbacks that are already in the event queue. Use process.nextTick to effectively queue the function at the head of the **event queue** so that it executes immediately after the current function completes.（setImmediate在event loop事件外，process.nextTick在event loop前）

So in a case where you're trying to break up a long running, CPU-bound job using recursion, you would now want to use setImmediate rather than process.nextTick to queue the next iteration as otherwise any I/O event callbacks wouldn't get the chance to run between iterations.