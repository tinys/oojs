tinkjs
====

一 一套js开发平台。整合开发、测试、发布流程。

#####重复造轮子

网上已经有很多基于commonjs规范的项目，而且构建工具也很多，seajs配套的spm、require也有自己构建工具，grunt，bower。。。。。各有利弊吧。
我的想法是：

+ 不想为了模块化开发引用其他js。这点老东家新浪用的STK以及配套的构建工具做到了，开发、测试、构建都在node编写的一个服务中。对外边不开源吧。

>其实目前要实现js的模块化，要不靠js控制，要不就靠动态语言帮助来实现。新浪以前是python，php各种版本都有。

+ 少点配置。

+ 自己先玩着。

#####面向对象的js开发

###单个模块的开发

其实我们可以把一些工具当成一个组件文件，比如字符串的处理、url的解析、动画的方式等。按照面向对象的思想，每个工具的方法也是对象，也可以分离成一个文件，当然这样分就太细了。不过分得越细，对其他人员使用的时候越清楚。你想想，不用打开文件，直接看文件名就知道这个工具有哪些方法。
我们通常看到页面的功能，都会对这些功能进行抽象，分析出继承以及实现关系。有时候还需要设计接口，来满足不同页面对同样类似功能的不同展示以及差异。有时候文件会分的很细，这样开发起来思路很清晰。

###模块化开发
	
  一个页面上的功能经常不是一个模块就能完成的，需要很多模块组装，但是模块之间有各种依赖关系，这样就需要有模块化的解决方案，如：requirejs,seajs。我更喜欢seajs这样的写法，他是符合cmd规范，写法更优雅,更像nodejs的写法。如果我要做一些其他组件的开发，当然选择seajs。

###项目的开发、测试、发布

开发：自己启一个服务，自己开发就是

测试：需要将代码发布到一台服务器上测试。合并压缩后的

发布：将测试通过后的代码直接扔trunk。


###版本控制

就是js缓存的问题。一般缓存好做。cdn，自己服务器设置age啥的。

版本控制主要有以下几种

+ 后缀加版本号 xxx.js?version=1111.
	> 这个的缺点就是：在集群环境下，新用户能拿到最新的js，但是页面上的dom不一定与最新js版本号一致。会出现短暂的页面错乱。
+ 版本号写在路径上，就是http://xx.com/static/20130102/js/xxx.js
	> 貌似有些地方，还是会使用缓存，但是基本不会出现页面短暂的错乱了，js线上。动态php或者其他的在上。
+ 版本号加载文件名字上。例如xx_10212.js 或者把文件的md5值当后缀名的。
	> 其实如果不怕以后看上线的svn上一个目录里好多文件，也是可以接收到。
+ 还有一种更绝的，就是上线会发两种文件，一个是当前版本的文件，让新用户使用。对于老用户，会用到第二种文件，这个文件是用户的版本和当前版本的对比后的结果。需要程序支持。
