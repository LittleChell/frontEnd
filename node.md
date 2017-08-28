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

###	file