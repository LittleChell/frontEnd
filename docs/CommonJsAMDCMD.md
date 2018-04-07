##	CommonJs AMD CMD

####	CommonJs规范

一个单独的文件就是一个模块，模块内将需要对外暴露的变量放到exports对象里，可以是任意对象，函数，数组等，未放到exports对象里的都是私有的。用require方法加载模块，即读取模块文件获得exports对象。

CommonJS是同步的，意味着你想调用模块里的方法，必须先用require加载模块。


####	AMD规范
requirejs为代表

####	CMD规范
seajs为代表
