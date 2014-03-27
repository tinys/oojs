oojs
====

这里是我对前端开发的一些思考

面向对象的js开发

	1）模块化开发

	2）单个模块的开发

###模块化开发
	
	模块化开发相关的项目有seajs,requirejs等。

	比较喜欢seajs，名字起得好。同时他符合commonjs的cmd规范。跟nodejs写法差不多。也很好兼容nodejs。

	模块化开发要素:

	定义:define(function(require,exports,module){

		})

	具体见：

	引用：var a = require("../module/a");  参数为相对路径。

	启动：seajs.use

	优化：构建工具(合并-压缩-版本控制)

###单个模块的开发

	1.普通工具类

	普通工具类其实还是面向过程的编程方式

	2.组件

	组件是模块的元素，组件内各个类之间有抽象、继承、多态。这里比较好的可以参照下backbonejs.




