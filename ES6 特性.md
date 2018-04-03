# ES6 特性

- 结构赋值
- 箭头函数
- Set和Map
- 异步操作
- 类与对象
- 模块化

# ES6基本技能

- 源码
- 业务
- 面试

![fbfa6b7e897f6d8a6c4ec1b03baa962](C:\Users\ADMINI~1\AppData\Local\Temp\WeChat Files\fbfa6b7e897f6d8a6c4ec1b03baa962.png)

##  构建工具

- gulp
- babel
- webpack
- npm

##  基础语法

##  实战演练
- express
- mockjs

# 预备知识

1. 模块化概念

2. 工程构建
3. 编程经验

## ES6 项目构建

- 基础架构
- 任务自动化（glup）
- 编译工具（babel、webpack）
1. babel  专门编译ES6 代码，编译成ES5 ，让浏览器识别的功能
2. webpack  处理模块化项目依赖的关系的
- 代码实现

### 基础架构

业务逻辑 （页面 、 交互）
自动构建（编译 、 辅助 （自动刷新 、文件合并 、资源压缩））
服务接口（数据 、接口）

### 任务自动化 gulp

什么是任务自动化？
减少人工操作，让机器自动监听所有的操作，自动的响应
什么是gulp？
就是一个工具，用来解决自动化构建工具的，增强工作流程的一个工具
glup 的作用？
就是完成任务自动化，帮助工作流顺畅工作

### 编辑工具 babel 、 webpack

什么是babel、webpack？

babel 的核心用法？

了解webpack 及 webpack-stream 的作用？



### 安装 node

网址：https://nodejs.org/zh/cn

点击下载  
windows installer(.msi)  下载自己电脑响应的版本
macOS installer(.pkg)  的安装包

node -v 查看是否安装成功



### 代码实现

创建一个ES6 前端工程
完成目录结构、自动构建、服务器搭建

使用命令行
创建项目根目录
进入目录
创建三个并行的目录 （app 存放前端代码、server 存放服务器目录、tasks 存放构建工具的目录）
进入app目录
创建存放文件目录（css  存放css文件，js 存放js文件、views 存放模板html目录）
查看文件目录
创建一个类目录专门放类文件（创建在js目录下）
初始化类文件（创建空的类文件）
在类文件中初始化一个入口文件
初始化模板文件（两个，一个错误的模板，一个是入口模板）
清楚目录
回到server 目录
执行脚手架命令
执行安装命令（ npm install  依赖于nodejs，所有要先装nodejs，安装服务器）
回到构建目录
创建js任务（util 存放常见脚本）
初始化文件 args.js
回到 根目录
查看目录

```
mkdir es6 
cd es6
mkdir app
mkdir server
mkdir tasks 
cd app
mkdir css
mkdir js
mkdir views
ls
mkdir js/class
touch js/class/test.js
touch js/class/index.js
touch views/error.ejs
touch views/index.ejs
clear
cd ../server/
express -e .
npm install
clear
cd ../tasks/
mkdir util
touch util/args.js
cd ../
ls
```
执行 express -e .  命令需要先安装

```
npm install -g express
npm install -g express-generator 
```

然后在执行

```
express -e .
```



创建 项目依赖包必须要有的文件 package.json （有这个之后，我们可以使用对应的npm命令装依赖包）

```
npm init
```
输入项目的名称，版本号等，不想定义一路回车就行，最后：y
查看文件
创建文件（文件名不能改是.babellrc）
创建gulp文件 （gulpfile.babel.js 名称是固定的，如果是用“es6“编写脚本，没有“.babel”是会报错的）
```
ls
clear
touch .babellrc
touch gulpfile.babel.js
```






