##NodeJS笔记
@(nodejs)[刘泽伟, 前端开发]
- setTimeout
- setInterval
- setImmediate
- console
- Process进程管理
- nextTick
    - 下一队列（当前队列的底部）

- 使用PID关闭计算机指定的进程
```
process.kill(PID)
```

- 获取node程序的PID号
```
process.pid
```

- 当前工作目录
```
process.cwd()
```

- 退出Node进程
```
process.exit()
```

##模块系统

#### 核心模块
- uitl
	- ```uilt.inherits(fn1,fn2)``` 实现继承。
	- ```uilt.inspect(obj,[true | flase])```将任意对象转成字符串，通常调试时用到。
	- ```uilt.isArray(数组)``` 检测是否是一个数组
	- ```uilt.isRegExp(正则表达式)``` 检测是否是一个正则
	- ```uilt.isDate(日期对象)```检测是否是一个日期对象
	- ```uilt.isError(错误对象)```检测是否是一个错误对象
	- ```等等其他检测...```
- buffer

####module.exports 与 exports的区别
- 在exports增加属性直接改变module.exports的指向。
- 导出多个模块用exports方式
- 导出单个用module.exports方式
```
module.exports = 模块 或 模块组
exports.模块1 = 模块1
exports.模块2 = 模块2
```

####require方法
- require方法具有文件缓存机制，缓存的文件在该对象下的cache中。
- 因缓存机制，所以当重复引入多次，只会执行一次。
- 删除require引入的文件缓存的方法就是删除该对象下的cache属性。
- 先找到当前目录下node_modules文件夹，找到名字相同的文件夹，找到package.json查看里面的main属性，运行对应的文件，找不到会向上一级查找node_modules文件文件夹中查找，直到找到为止，找不到就会报错
    
####npm全局安装 与 本地安装的区别
- 全局安装（只在命令下使用）
    - nrm工具（切换镜像源地址）
- 本地安装
    - 依赖（开发上线都需要）
    ```npm install jquery --save```
    - 开发依赖（只在开发使用）
    ```npm install jquery --save-dve```
    
####nrm的使用
- ```npm install nrm -g```下载
- ```nrm ls```查看所有源
- ```nrm test```查看源速度
- ```nrm add 源名字 源地址```添加源
- ```nrm del 源名字```删除源
- ```nrm use 源名字```使用源
- 
####bower的使用
- bower安装指令 ```bower install jquery --save ``` 和```npm```用法指令一样
- bower安装的模块路径，默认安装到bower_components文件夹中
- 指定bower的安装路径,新建一个.bowerrc文件 写入 ```{"directory":"目录地址"}``` bower会自动识别该文件。
- bower指令
	- ```cache```:bower缓存管理
	- ```help```:显示Bower命令的帮助信息
	- ```home```:通过浏览器打开一个包的github发布页
	- ```info```:查看包的信息
	- ```init```:创建bower.json文件
	- ```install```:安装包到项目
	- ```link```:在本地bower库建立一个项目链接
	- ```list```:列出项目已安装的包
	- ```lookup```:根据包名查询包的URL
	- ```prune```:删除项目无关的包
	- ```register```:注册一个包
	- ```search```:搜索包
	- ```update```:更新项目的包
	- ```uninstall```:删除项目的包	 

####搭建简单的博客
- ```npm install hexo -g ```安装Hexo
- 