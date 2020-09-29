

# node.js

## node.js 介绍

### 为什么要学习 node





###  node 是什么

- Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine.
- Node.js 不是一门语言，不是库，不是框架
- Node.js 是一个运行时环境
- 简单说 node 可以解析和执行 JavaScript 代码
- 以前只有浏览器可以解析执行 JavaScript 代码
- 现在的 JavaScript 可以完脱离浏览器来运行
- 浏览器中的 JavaScript
- EcmaScript 
- 基本的语法
- if
- var
- function
- Object
- Array
- BOM
- DOM
- node 中的 JavaScript
- 没有 BOM、DOM
- 有 EcmaScript
- 服务端不处理 DOM
- 在 node 这个 JavaScript 执行环境中为 JavaScript 提供了一些服务器级别的操作 API
- 例如文件读写
- 网络服务的构建
- 网络通信
- htttp 服务器
- 等处理。。。
- 特性：事件驱动、非阻塞 IO 模型（异步）、轻量和高效
- npm 是世界上最大的开源生态系统
- 绝大多数 JavaScript 相关的包得都存放在 npm 上，这样做的目的是为了开发人员更方便的下载使用
- `npm intall jQuery`
- 构建于 chromeV8引擎之上
- 代码只是具有特定格式的字符串
- 引擎可以认识它，引擎可以帮你去解析和执行
- Google Chrome 的V8引擎是目前公认的解析执行 JavaScript 最快最高效的
- node 的作者把 google 中的 V8引擎移植出来，开发了一个独立的 JavaScript 运行是环境

### node 能做什么

- web 服务器后台
- 命令行工具
- npm
- git（c 语言）
- hexo
- 。。。
- 游戏服务器
- 对于前端工程师来讲，接触 node 最多的是它的命令行工具
- 自己写的很少，主要是使用别人第三方的
- webpack
- guip
- nmp



### 预备知识

- html
- css
- JavaScript
- 简单的一命令行操作
- cd
- dir
- mkdir
- rm
- 具有服务端开发经验更佳



### 一些资源

- 《深入浅出 Node.js》
- 偏理论，几乎没有实战内容
- 理解原理底层有帮助
- 结合课程学习
- 《Node.js 权威指南》
- API 讲解
- 没有业务，没有实战
- [JavaScript 标准参考教程（alpha）](https://javascript.ruanyifeng.com/)







### 能学到啥

- B/S 编程模型
- Browser - Server
- back-end
- 任何服务端技术这种 BS 编程模型都是一样的，和语言无关
- node 只是作为学习 BS 编程模型的工具
- 模块化编程
- RequireJs
- SeaJs
- `@import('文件路径')`
- 以前认知的 js 只能通过 script 标签来加载
- 在 node 中可以像 `@import()` 一样来加载 js 脚本文件
- Node 常用 API
- 异步编程
- 回调函数
- Promise
- async
- generator
- Express Web 开发框架
- Ecmascript6
- 它是一个新语法
- 学习 node 不仅打开服务端黑盒子，同时会帮助你学习以后的前端框架
-  Vue.js
- React.js
- angular



## 起步

### 安装 node 环境

- 查看当前版本号

`node --version`

- 确认 node 环境是否安装成功
打开命令输入`node --version`

### REPL

- read
- eval
- print
- loop

在终端中输入`node`命令直接回车，进入 node 环境，在这里可以直接运行 node 代码，核心代码可以直接使用

这个环境的作用是用来帮助我们做一些辅助测试，例如在里面可以直接使用 node 中的核心模块而不需要 require 加载

### hello wrold

1. 创建编写 JavaScript 脚本文件
2. 打开终端，定位到脚本文件所属目录
3. 输入 `node 文件名` 执行对应脚本
不要用 node.js 来命名，最好也不要使用中文





- 解析执行 JavaScript

- 读写文件

```javascript
  // fs 是 file-system 的简写，就是文件系统
  // 在 node 中如果想要进行文件的读写操作，就必须引入 js 这个核心模块
  // 在 fs 这个核心模块中，提供了所有的文件操作相关的 API
  // 例如：fs.readFile 就是用来读取文件的
  var fs = require('fs')
```

  

  - http

  ```javascript
  // 使用 node 非常轻松的构建一个web服务器
  // 在 node 中专门提供了一个核心模块：http
  // http 这个模块的职责就是创建编写服务器的。
  
  // 1.加载 htpp 模块
  var http = require('http')
  
  // 2. 使用 http.createServer()方法创建一个 web 服务器
  // 返回一个 server 实例
  var server = http.createServer()
  
  // 3.服务器作用：
  // 	 提供服务：对数据的服务
  // 	 发请求 接收请求
  //   处理请求 发送响应
  
  
  // 注册 request 请求事件
  // 当客户端请求过来，就会自动触发服务器的 request 请求事件，
  // 然后执行第二个参数：处理函数
  server.on('request',function(){
  	console.log('收到客户端的请求了')
  })
  
  // 4.绑定端口号，启动服务器
  server.listen(3000,function(){
  	console.log('服务器启动成功了，可以通过 localhost:3000 访问')
  })
  
  
  
  
  ```

  



  ## node 中的 JavaScript

  - EcmaScript
  - 没有 DOM、BOM
  - 核心模块
  - 第三方模块
  - 用户自定义模块



  ### require

  ```javascript
// require 是一个方法
// 它的作用就是用来加载模块的
// 在 Node 中，模块有三种：
//    具名的核心模块，例如 fs、http
//    用户自己编写的文件模块
//      相对路径必须加 ./
//      可以省略后缀名
//      相对路径中的 ./ 不能省略，否则报错
//    在 Node 中，没有全局作用域，只有模块作用域
//      外部访问不到内部
//      内部也访问不到外部
//      默认都是封闭的
//    既然是模块作用域，那如何让模块与模块之间进行通信
//    有时候，我们加载文件模块的目的不是为了简简单单的执行里面的代码，更重要是为了使用里面的某个成员

var foo = 'aaa'

console.log('a start')

function add(x, y) {
  return x + y
}

// Error: Cannot find module 'b'
// require('b')

// 可以
// require('./b.js')

// 推荐：可以省略后缀名
require('./b')

console.log('a end')

console.log('foo 的值是：', foo)

  ```





```javascript
// require 方法有两个作用：
//    1. 加载文件模块并执行里面的代码
//    2. 拿到被加载文件模块导出的接口对象
//    
//    在每个文件模块中都提供了一个对象：exports
//    exports 默认是一个空对象
//    你要做的就是把所有需要被外部访问的成员挂载到这个 exports 对象中
var bExports = require('./b')
var fs = require('fs')

console.log(bExports.foo)

console.log(bExports.add(10, 30))

console.log(bExports.age)

bExports.readFile('./a.js')

fs.readFile('./a.js', function (err, data) {
  if (err) {
    console.log('读取文件失败')
  } else {
    console.log(data.toString())
  }
})

```



- 模块作用域固然带来了一些好处，可以加载执行多个文件，可以完全避免变量命名冲突污染的问题
- 但是某些情况下，模块与模块是需要通信的
- 在每个模块中，都提供了一个对象 `exports`
- `exports`对象默认是一个空对象
- 你要做的就是把需要外部访问使用的成员手动的添加一到 `exports`接口对象中
- 然后谁来 `require`这个模块，谁就可以使用模块内部的 `exprots`接口对象















### 核心模块

node 为 JavaScript 提供了很多服务器级别的 API，这些 API 绝大多数都包装到一个具名的核心模块中了。

例如文件操作的 `fs` 核心模块，http 服务器模构建的 `http` 模块，`path`路径操作模块，`os`操作系统信息模块。。。

只要提到是核心模块就要想使用它的时候一定要

```javascript
var fs = require('fs')
var http = require('http')
```



### 用户自定义模块







### 第三方模块





## web 服务器开发

### ip 地址和端口号

- ip 地址用来定位计算机
- 端口号用来定位具体的应用程序
- 一切需要联网通信的软件都会占用一个端口号
- 端口号的范围从 0 - 655536 之间
- 在计算机中有一些默认端口号，最好不要去使用
- 例如 http 服务的 80端口
- 我们在开发过程中使用一些简单好记的就可以了，例如 3000，5000 等没什么含义
- 可以同时开启多个服务，但一定要确保不同的服务占用不同的端口号



### Content-type

- http://tool.oschina.net/

### 请求对象 Request







### 响应对象 Response



### 在 node 中使用模板引擎



### 统一处理静态资源





### 服务器渲染



## 留言本





## node 中的模块系统

使用 node 编写应用程序主要就是在使用

- EmacScript
- 和浏览器一样，在 node 中没有 BOM、DOM
- 核心模块
- fs 文件操作
- http 服务
- url 路径操作
- path 路径处理模块
- os 操作系统
- 第三方模块
- art-tamplate
- 必须通过 npm 来下载才可以使用
- 自己写的模块
- 自己创建的文件

### 什么是模块化

- 文件作用域
- 通信规则
- 加载
- 导出

### CommonJs 模块规范

在 node 中的 JavaScript 还有一个重要的概念，模块系统

- 模块作用域
- 使用 require 方法用来加载模块
- 使用 exports 接口对象导出模块成员



#### 加载 `require`

语法：

```javas
var 自定义变量名 = require('模块名称')
```

两个作用：

- 执行被加载模块中的代码
- 得到被加载模块中的 `exports`导出的接口对象

#### 导出 `exprots`

- node 中是模块作用域，默认文件中所有的成员在当前文件模块有效
- 对于希望可以被其他模块访问的成员，我们就需要把这些公开的成员都挂载到`exports`接口对象中就可以了

导出多个成员（必须在对象中）

```javascript 
exports.a = 123
exports.b = 'hello'
exports.c = function(){
	console.log('ccc')
}
exports.d = function(){
	foo:'bar'
}
exports.a = 123

```



导出单个成员（拿到的就是函数，字符串）

```javascript
module.exports = 'hello'

// 以这个为准，后者会覆盖前者
module.exports = function(){
  return x + y
}
```



也可以这样导出多个成员

```javascript
module.exports = {
  add:function (){
    return x + y
  }
  str:'hello'
}
```



#### 原理解析

exports 是 module.exportsr 

```javascript
console.log(exports === module.exports) // true

exports.foo = 'bar'

// 等价于
module.exports.foo = 'bar'
```



```javascript
// 在 Node 中，每个模块内部都有一个自己的 module 对象
// 该 module 对象中，有一个成员叫：exports 也是一个对象
// 也就是说如果你需要对外导出成员，只需要把导出的成员挂载到 module.exports 中

// 我们发现，每次导出接口成员的时候都通过 module.exports.xxx = xxx 的方式很麻烦，点儿的太多了
// 所以，Node 为了简化你的操作，专门提供了一个变量：exports 等于 module.exports

// var module = {
//   exports: {
//     foo: 'bar',
//     add: function
//   }
// }

// 也就是说在模块中还有这么一句代码
// var exports = module.exports

// module.exports.foo = 'bar'

// module.exports.add = function (x, y) {
//   return x + y
// }

// 两者一致，那就说明，我可以使用任意一方来导出内部成员
// console.log(exports === module.exports)

// exports.foo = 'bar'
// module.exports.add = function (x, y) {
//   return x + y
// }

// 当一个模块需要导出单个成员的时候
// 直接给 exports 赋值是不管用的

// exports.a = 123

// exports = {}
// exports.foo = 'bar'

// module.exports.b = 456

// 给 exports 赋值会断开和 module.exports 之间的引用
// 同理，给 module.exports 重新赋值也会断开

// 这里导致 exports !== module.exports
// module.exports = {
//   foo: 'bar'
// }

// // 但是这里又重新建立两者的引用关系
// exports = module.exports

// exports.foo = 'hello'

// {foo: bar}
exports.foo = 'bar'


// {foo: bar, a: 123}
module.exports.a = 123

// exports !== module.exports
// 最终 return 的是 module.exports
// 所以无论你 exports 中的成员是什么都没用
exports = {
  a: 456
}

// {foo: 'haha', a: 123}
module.exports.foo = 'haha'

// 没关系，混淆你的
exports.c = 456

// 重新建立了和 module.exports 之间的引用关系了
exports = module.exports

// 由于在上面建立了引用关系，所以这里是生效的
// {foo: 'haha', a: 789}
exports.a = 789

// 前面再牛逼，在这里都全部推翻了，重新赋值
// 最终得到的是 Function
module.exports = function () {
  console.log('hello')
}

// 真正去使用的时候：
//    导出多个成员：exports.xxx = xxx
//    导出多个成员也可以：module.exports = {
//                        }
//    导出单个成员：module.exports


// 谁来 require 我，谁就得到 module.exports
// 默认在代码的最后有一句：
// 一定要记住，最后 return 的是 module.exports
// 不是 exports
// 所以你给 exports 重新赋值不管用，
// return module.exports

```



#### exports 和 module.exports 的区别

- exports 和 module.exprots 的区别
- 每个模块中都有 module 对象
- module 对象中有一个 exports 对象
- 我们可以把需要导出的成员都挂载到了 module.exports 接口对象中
- 也就是，`module.exports.xxx = xxx` 方式
- 但是每次都 `module.exports.xxx = xxx`太麻烦
- 所以 node 为了方便，同时在每一个模块中都提供了一个成员叫 `exports`
- `expoorts = module.exports` 结果为 ture
- 所以对于：`moudle.exports.xxx = xxx` 的方式 完全可以：`expots.xxx = xxx`
- 当一个模块需要导出单个成员的时候，这个时候必须使用：`module.exports = xxx` 的方式
- 不要使用 `exports = xxx` 不管用
- 因为每个模块最终向外 `return` 的是 `module.exports`
- 而 `exports` 只是 `module.exports` 的一个引用
- 所以即便你为 `exports = xx` 重新赋值，也不会影响 `module.exports`
- 但是有一种赋值方式比较特殊：`exports = module.exports` 这个用来重新建立引用关系的
- 之所以让大家明白这个道理，是希望可以更灵活的去用它



#### require 加载规则

- 核心模块
- 模块名
- 第三方模块
- 模块名
- 用户自己写的
- 路径



- 优先从缓存中加载
- 判断模块标识
- 核心模块
- 第三方模块
- 自己写的模块



**路径形式的模块**：

- ./ 当前目录，不可省略
../ 上一级目录，不可省略
/xxx 几乎不用
d:/a/foo.js 几乎不用
首位的 / 在这里表示的是当前文件模块所属磁盘根路径
.js 后缀名可以省略
require('./foo.js')



**核心模块的本质也是文件**
- 核心模块文件已经被编译到了二进制文件中了，我们只需要按照名字来加载就可以了
require('fs')
require('http')





**第三方模块**
- 凡是第三方模块都必须通过 npm 来下载
使用的时候就可以通过 require('包名') 的方式来进行加载才可以使用
不可能有任何一个第三方包和核心模块的名字是一样的
- 既不是核心模块、也不是路径形式的模块
先找到当前文件所处目录中的 node_modules 目录
node_modules/art-template
node_modules/art-template/package.json 文件
node_modules/art-template/package.json 文件中的 main 属性
main 属性中就记录了 art-template 的入口模块
然后加载使用这个第三方包
实际上最终加载的还是文件



**项目入口模块**

- 如果 package.json 文件不存在或者 main 指定的入口模块是也没有
则 node 会自动找该目录下的 index.js
也就是说 index.js 会作为一个默认备选项

- 如果以上所有任何一个条件都不成立，则会进入上一级目录中的 node_modules 目录查找
- 如果上一级还没有，则继续往上上一级查找
。。。
- 如果直到当前磁盘根目录还找不到，最后报错：
can not find module xxx
var template = require('art-template')

注意：我们一个项目有且只有一个 node_modules，放在项目根目录中，这样的话项目中所有的子目录中的代码都可以加载到第三方包，不会出现有多个 node_modules



**模块查找机制**
优先从缓存加载
核心模块
路径形式的文件模块
第三方模块
node_modules/art-template/
node_modules/art-template/package.json
node_modules/art-template/package.json main
index.js 备选项
进入上一级目录找 node_modules
按照这个规则依次往上找，直到磁盘根目录还找不到，最后报错：Can not find moudle xxx
一个项目有且仅有一个 node_modules 而且是存放到项目的根目录

### npm

- node package manager

#### npm 网站

> npmjs.com

#### npm 命令行工具

npm 是一个命令行工具，只要你安装了node 就已经安装好的 npm

npm 也有版本概念

可以通过在命令行中输入

```shell
npm --version
```

升级 npm（自己升级自己）

```shell
npm install --golbal npm
```

#### 常用命令

- npm init 生成 package.json
- npm init -y 可以跳过向导，快速生成
- npm install
- 一次性把 dependencies 选项中的依赖项全都安装
- npm i （简写）
- npm install 包名
- 只下载
- npm i 包名（简写）
- npm intall --save 包名
- 下载并且保存依赖项（package.json 文件中的 dependencies 选项）
- npm i -S 包名
- npm uninstall 包名
- 只删除，如果有依赖项会依然保存
- npm un 包名
- npm uninstall --save 包名
- 删除包的同时也会把依赖项信息也删除
- npm un -S 包名
- npm help
- 查看使用帮助
- npm 命令 --help
- 查看指定命令的使用帮助

#### 解决 npm 被墙问题

npm 存储包文件的服务器在国外，有时候会被墙，速度很慢

https://developer.aliyun.com/mirror/NPM?from=tnpm 淘宝的印象地址



安装淘宝的 cnpm

```shell
# 在任意目录执行都可以
# --global 表示安装到全局，而非当前目录
# --global 不能省略，否则不管用
npm install --global cnpm
```

接下来你安装包的时候把之前的 `npm` 替换成 `cnpm`

举例例子：

```shell
# 这里是走国外的 npm 服务器
npm install jQuery

# 使用 cnpm 就会通过国内镜像下载
cnpm install jQqery
```

如果不想安装`cnpm`又想使用淘宝的服务器来下载

```shell
npm install jQuery --registry=https://registry.npm.taobao.org
```

但是每次手动这样都很麻烦，所以我们可以把这个选项加入配置文件中

```shell
npm config set registry https://registry.npm.taobao.org

# 查看 npm 配置信息
npm config list
```

只要通过了上面命令的配置，以后所有的 `npm install` 都会默认通过淘宝服务器来下载





### package.json

我们建议每一个项目都要有一个 package.json 文件（包描述文件，就像产品的说明书一样）

这个文件可以通过 `npm init`的方式来自动初始化出来

对于现在来谫，最有用的就是`dependencise`选项，可以用来帮我们保存第三方包的依赖信息

如果项目中的`node_modules`删除了也不用担心，只要执行 `npm install` 就会自动把`package.json` 中的`dependencies` 中所有的依赖项都下载回来



- 建议每个项目的根目录下都有一个 `package.json`	文件
- 建议执行`npm install ` 包名的时候，加上`--save`这个选项，目的是用来右相依赖项信息



####   package.json 和  package-lock.json

Npm 5 以前是不会有 `package-lock.json` 这个文件的

Npm5 以后加入了这个文件

当安装包的时候，npm 会自动生成或者更新 `package-lock.json`  这个文件



- npm 5 以后的版本安装不需要加 --save 参数，也会自动保存依赖信息
- 当安装包的时候，会自动创建或更新 package-lock.json 这个文件
- package.josn 文件会保存 node_modules 中所有包的信息（版本、下载地址）
  - 这样的话重新更新 npm install 的时候速度就可以提升
  - 另一个作用就中锁定版本号，防止自动升级新版

## path 路径操作模块

> 参考文档：官网
- path.basename
+ 获取一个路径的文件名（默认包含扩展名）
- path.dirname
+ 获取一个路径中的目录部分
- path.extname
+ 获取一个路径中的扩展名部分
- path.parse
+ 把一个路径转为对象
* root：根路径
* dir：目录
* base：包含后缀名的文件名
* ext：后缀名
* name ：不包含后缀名的文件名
- path.join
+ 当你需要进行路径拼接的时候，推荐使用这个方法
- path.isAbsolute
+ 判断一个路径是否是绝对路径

## node 中的其他成员

在每个模块中，除了 `require` 、 `exports` 等模块相关的 API 之外，还有两个特殊的成员
- `__dirname` 可以用来动态获取当前文件模块所属目录的绝对路径
- `__filename` 可以用来动态获取当前文件的绝对路径
- `__dirname` 和 `__filename` 是不受执行 node 命令所属路径影响的




在文件操作中，使用相对路径是不可靠的，因为在 node 中文件操作的路径被设计为相对于执行 node 命令所处的路径（不是 bug，是有使用场景的）
所以为了解决这个问题，只需要把相对路径变为绝对路径就可以了
使用 `__dirname`或者 `__filename` 来帮我们解决这个问题了

在拼接路径的过程中，为了避免手动拼接带来的一些低级错误，所以推荐使用 `path.join()` 来辅助拼接

所以为了尽量避免上述问题，在文件操作中使用相对路径统一转换为 **动态的绝对路径**

> 补充：在引用模块时，模块中的路径标识就是相对于当前文件模块，不受执行 node 命令所处路径影响




## Express

原生的 http 在某些方面表现不足以应对我们的开发需求，所以我人需要使用框架来加快我们的开发效率，框架的目的就是提高效率，让我们的代码更高度统一

在 node 中，有很多 web 开发框架，我们这里以`express`为主

- expressjs.com

### 起步

#### 安装

```javascript
npm install --save express
```



#### hello world

```javascript
// 1. 引包
var express = require('express')

// 2. 创建服务器响应程序
//    也就是原来的 http.createServer
var app = express()

// 3. 当服务器收到 get 请求 / 的时候，执行回调处理函数
app.get('/',function(req,res){
	res.end('hello express')
})

// 相当于 server.listen
app.listen(3000,function(){
	console.log('running...')
})
```



#### 基本路由

路由就是一张表，这个表里有具体的映射关系

- 请求方法
- 请求路径
- 请求处理函数

get



```javascript
// 当你以 get 方法请求 / 的时候，执行对应的处理函数
app.get('/',function(req,res){
  res.send('hello world')
})
```



post

```javascript
// 当你以 post 方法请求 / 的时候，执行对应的处理函数
app.post('/',function(req,res){
  res.send('hello world')
})
```

####  静态服务

```javascript

// 当省略第一个参数的时候，则可以通过 省略 /public 的方式来访问
// 这种方式的好处就是可以省略 /public/
// /public中的资源
app.use(express.static('public'))
// /files 中的资源
app.use(express.static('files'))

// 当以 /static/ 开头的时候，去./static/ 目录中查找 对应的资源

// 第一个参数是请求的地址，第二个参数中路径是文件所在的目录
// 所以不第一个参数是什么，请求的时候都是在浏览器中以这个路径开头，后面跟的就是后面路径中的文件名
// /static/static 中的资源
app.use('/static/',express.static('static'))
// /static/public 中的资源
app.use('/static/',express.static('public'))

app.use('/static/',express.static(path_join(_dirname,'public')))
```



### 在 express 中配置使用 art-template 模板引擎

- [art-template 官网地址](https://aui.github.io/art-template/)

安装

```shell
npm install --save art-template
npm install --save express-art-template
```



配置

```javascript
// view engine setup
// 配置使用 art-template 模板引擎
// 第一个参数表示，当渲染以 .art 结尾的文件的时候，使用 art-template 模板引擎
// express-art-template 是专门用来在 express 中把 art-template 整合到 express 中
// 虽然这里不需要加载 art-template 但是也必须安装
// 原因就在于 express-art-template 依赖了 art-template
app.engine('art',require('express-art-template'))
```

使用

```javascript
app.get('/',function(req,res){
  // express 默认会去项目中的 views 目录中找
  res.render('index.html',{
    title:'hello world'
  })
}
```



修改默认的 views 目录

```javascript
// 注意：第一个参数 views 千万不要写错
app.set('views',render函数的默认路径)
```



### 在 express 中获取表单 get 请求参数

express 内置了一个 API，可以直接通过 `req.query`来获取

```javasript	
req.query	
```

###  在 express 获取表单 post 请求体数据

在 expres 中没有内置获取表单 post 请求体的 API，这里需要使用一个第三方包 `body-parser`

安装

```shell
npm install --save body-parser
```

配置

```javascript
var express = require('express')
// 引包
var bodyParser = require('body-parser')

var app = express()

// parse application/x-www-form-urlencoded
// 配置 body-parser
// 只要加入这个配置，则在 req 请求对象上会多出来一个属性：body
// 也就是说你就可以直接通过 req.body 来获取表单 post 请求体数据了
app.use(bodyParser.urlencoded({ extended: false }))

// parse application/json
app.use(bodyParser.json())


```



使用

```javascript
app.use(function (req, res) {
  res.setHeader('Content-Type', 'text/plain')
  res.write('you posted:\n')
  // 可以通过 req.body 来获取表单数据 
    // 在请求的时候，请求体的格式 要设置为 json格式 
  res.end(JSON.stringify(req.body, null, 2))
})
```



### 设置 router 路由 ，提取路由模块





###  CRUD 案例

#### 模块化思想

模块如何划分：

- 模块职责要单一

#### 起步

- 初始化
- 安装依赖
- 模板处理

#### 路由设计

| 请求方法 | 请求路径         | get 参数 | post 参数                      | 备注             |
| -------- | ---------------- | -------- | ------------------------------ | ---------------- |
| get      | /students        |          |                                | 渲染页面         |
| get      | /sutdents/new    |          |                                | 渲染学生页面     |
| post     | /students/new    |          | Name、age、gender、hobbies     | 处理添加请求页面 |
| get      | /students/edit   | id       |                                | 渲染编辑页面     |
| post     | /students/edit   |          | id、name、age、gender、hobbies | 处理编辑请求     |
| get      | /students/delete | id       |                                | 处理删除请求     |

#### 提取路由模块



在开发时遵循模块单一的原则，所以请求的部分会以路由的方式单独出来，作为一个模块，这个时候就需要把 `app.js`中的 `app` 对象，也就是 `express` 对象关联起来。

第一种方法，传统的方法（不推荐使用）：

在 router.js 中

```javascript
// 封装一个函数，把 app 做为参数，在 app.js 中执行
// router = require('./router')
// router(app)
// 这样就把 app 传入到了 router 中
// 但是这种方法不建义使用，express 提供了方法
module.exports = function(app){
	app.get('/students/new', function(req, res){

	})
}
```

第二种方法，express 提供的方法：

Router.js 中

```javascript
var fs = require('fs')
var express = require('express')

// 第二种方法：express 提供的方法，专门用来包装路由
// 1. 创建一个路由容器
var router = express.Router()

// 2. 把路由都挂载到 router 路由容器中
router.get('/students', function(req,res){

	// readFile 的第二个参数是可选的 utf8 与 data.toString() 的功能是一样的
	fs.readFile('./db.json', 'utf8', function(error, data){
		if (error) {
			return res.status(500).send('server error')
		}

		console.log(data)

		res.render('index.html',{
			// 从文件读取出来的数据是字符串，不是对象
			// 这里需要传入的是一个 JSON 对象
			// 所以需要转为 json 对象
			// JSON 需要全都大写
			students: JSON.parse(data).students
		})
	})

})

router.get('/students/new', function(req, res){

})
// 3. 把 router 导出
module.exports = router
```

app.js 中

```javascript
var express = require('express')
var fs = require('fs')
var app = express()
var router = require('./router')

// 4. 把路由容器挂载到 app 服务中
app.use(router)
```








#### 设计操作数据的 API 文件模块

```javascript
/**
 * 职责：只操作文件中的数据，只处理数据，不关心业务
 *
 */

/**
 * 获取所有学生的列表
 */
 exports.find = function(){

 }

/**
 * 添加保存学生
 */

 exports.save = function(){
   
 }
/**
 * 更新学生
 */

 exports.update = function(){
   
 }
/**
 * 删除学生
 */

 exports.delete = function(){
   
 }

```



 #### 自己编写的步骤

 - 处理模板

 - 配置开放静态页面

 - 配置模板引擎

 - 简单路由，渲染静态页面

 - 路由设计

 - 提取路由模块

 - 由于接下来的一系列的操作都需要处理文件数据，所以我们需要封装 students.js 文件专门用来操作文件数据

 

## MongoDB

### 关系型数据库和非关系型数据库

表就是关系

或者说表与表之间存在关系

- 所有的关系型数据库都需要通过 sql 语言来操作
- 所有的关系型数据库在操作之前都需要设计表结构
- 而且数据库表支持约束
  - 唯一的
  - 主键
  - 默认值
  - 非空
- 非关系型数据库非常的灵活
- 有的非关系型数据库就是 key-value
- 但是 MongoDB 是长的最像关系型的非关系型数据库
  - 数据库 --》 数据库
  - 数据表 -- 》 集合（数组）
  - 表记录 -- 》文档对象
- MongoDB 不需要设计表结构
- 也就是说可以任意的往里面存数据，没有结构性这么一说

### 启动和关闭数据库

启动

```shell
# mongodb 默认使用执行 mongod 命令所处盘符根目录下的 /data/db 作为自己的数据存储目录
# 所以在 第一次执行该命令前先自己手动新建一个 /data/db
mongod
```

如果想要修改默认值的数据存储目录，可以

```shell
mongod --dbpath=数据存储的路径
```

停止：

```shell
在开启服务的控制台 ctrl + c
或者关闭控制台
```

### 连接数据库

控制台中

连接

```shell
# 默认连接本机的 mongo 服务
mongo 
```

断开连接

```shell
exit
```

### 基本命令

- `show dbs`
  - 查看显示所有数据库
- `db`
  - 查看当前操作的数据库
- `use数据库名称`
  - 切换到指定的数据（如果没有会新建）
- `show collections`
  - 查看数据库中的集合
- `db.subject`
  - 查看当前集合 subject 中的内容
- 插入数据



### 在 node 中如何操作 mongoDB 数据

#### 使用官方的 mongodb 包来操作

#### 使用第三方 mongoose 来操作 mongoDB 数据库

第三方包是基于 mongodb 包再一次做了封装















## 异步编程

### 回调函数

```javascript
// 一种数据类型
// 参数
// 返回值
// 函数太灵活了，无所不能
// 一般情况下，把函数作为参数的目的就是为了获取函数内部的异步操作结果
// JavaScript 单线程、事件循环

function add(x, y) {
  return x + y
}

// add(10, 20)

// console.log(1)

// // 不会等待
// setTimeout(function () {
//   console.log(2)
//   console.log('hello')
// }, 0)

// console.log(3)

function add(x, y, callback) {
  console.log(1)
  setTimeout(function () {
    var ret = x + y
    callback(ret)
  }, 1000)
}

add(10, 20, function (ret) {
  console.log(ret)
})

// 注意：凡是需要得到一个函数内部异步操作的结果
//    setTimeout
//    readFile
//    writeFile
//    ajax
//   这种情况必须通过：回调函数

```







### promise

为了解决回调地狱方式带来的问题，

promise 本身不是异步，而是在它里面封装一些异步方法

promise 的基础语法

```javascript
var fs = require('fs')


// 创建一个 promise 容器
// function 中的两个参数一个是成功回调， 一个是失败的回调
var p1 = new Promise(function(resolve,reject){
    fs.readFile('./a.txt','utf8',function(err,data){
        if(err){
            // 失败时调用这个方法，把错误信息返回
            // 把容器的 pending 的状态变为 rejected
            // 在调用这个方法是，执行的就是 then 方法中的第二个参数的函数 function(err){}
            reject(err)
        }else{
            // 成功时调用这个方法，数据返回
            // 把容器的 pending 的状态变为 resolved
            // 在调用这个方法是，执行的就是 then 方法中的第二个参数的函数 function(data){} 把 data 传递到then 方法中的第一个函数中
            resolve(data)
        }
    })
})

// p1 就是 promise 对象
// 当p1 成功了然后 （then）做指定的操作
// then 方法接收的第一个 function 就是 promise 容器中的 resolve 函数，第二个 function 就是 promise 容器中的 reject 方法
p1
    .then(function(data){},function(err){})
```



多个 promise 回调

```javascript
// p1 就是 promise 对象
// 当p1 成功了然后 （then）做指定的操作
// then 方法接收的第一个 function 就是 promise 容器中的 resolve 函数，第二个 function 就是 promise 容器中的 reject 方法
p1
    .then(function(data){
        // 当 p1 读取数据成功后
        // 当前函数中 return 的结果就可以传递到后面 then 中的第一个 function 的参数中接收到
        // return 123 后面 then 中的第一个 function 的参数就是123
        // 当 return 一个 promise 对象（p2）的时候，后面的 then 方法中的第一个 function 对应的就是这个 p2 的 resolve 方法中,第二个 function 对应的就是 p2 的 reject 方法
        return p2
    },function(err){

    })
    .then(function(data){

    },function(err){

    })
```



封装 promise 版本的 readFile

```javascript
   // 封装
    function pReadFile(filePath){
        return new Promise(function(resolve,reject){
            fs.readFile(filePath,'utf8',function(err,data){
                if(err){
                    rejected(err)
                } else{
                    resolved(data)
                }
            })
        })
    }

    // 调用

    pReadFile('./a.txt')
        .then(function(data){
            console.log(data)
            return pReadFile('./b.txt')
        },function(err){

        })
        .then(function(data){
            console.log(data)
            return pReadFile('./c.txt')
        },function(err){
            
        })
        .then(function(data){
            console.log(data)
        },function(err){
            
        })
```





### Generator  生成函数的 async 函数



### async/awiat

- async function 是 Promise 的语法糖封闭
- 异步编程的终极方案 -- 以同步的方式写异步
  - await 关键字可以  “暂停” async/function 的执行
  - await 关键字可以以同步的写法获取 Promise 的执行结果
  - try-catch 可以获取 await 所得到的错误
- 一个穿越事件循环的 function







```javascript
(async function(){


    // await 会等待 interview 全部执行完成后，如果 interview 都执行成功则打印下面 smile，
    // 如果不成功则打印 error 信息

    try{
        await interview(1)
        await interview(2)
        await interview(3)
    }catch (e){
        return console.log('error:' + e.round)
    }

    console.log('smile')
})()
```













 ## 扩展

 ### 代码风格

 - 当你采用了无分号的代码风格的时候，只要注意以下情况就不会出现类型错误了

 - 当一行代码是以：

 - (
 - [
 - `

 开头的时候，则在前面补上一个分号用以避免一些语法解析错误

 所以你会发现在一些第三方的代码中看到一上来就是一个分号 `;` 开头。

 - 结论：
 无论你的代码是不是有分号，都建义如果一行代码是以 `(` `[` ` 开头的，最好在前面加上分号。

 - 还有可能会见到一些 `!` `~` 代替 `;` 的

 - 《编写可维护的 JavaScript》



 ### EcmaScript 6 相关

 - 在 DcmaScript6 的 \` 字符串中，可以使用`${}`来引用变量

 ```javascript
 var fun = function(item){
  content = `this is a variable ${item} useage.`
}
 ```



### 服务端渲染与客户端渲染的区别

- 客户端渲染不利于 SEO 搜索引擎优化
- 服务端渲染是可以被爬虫抓取到的，客户端异步渲染是很难被爬虫抓取到的
- 所以你会发现真正的网站既不是纯异步，也不是纯服务端渲染的，而是两者结合来做的
- 例如京东商品列表是服务端渲染的，评论是客户端渲染的



### 修改完代码自动重启

我们这里可以使用一个第三方命名工具，`nodemon` 来帮助我们解决频繁修改代码重启服务器问题

`nodemon` 是一个基于 node 开发的第三方命令工具，我们用不用的时候需要独立安装

```shell
# 在任意目录执行该命令都可以
# 也就是说，所有需要 --global 来安装的包都可以在任意目录执行
npm install --global nodemon
```

安装完毕后，使用

```shell
node app.js

# 改为 
nodemon app.js
```



只要是通过 `nodemon app.js` 启动的服务，它都会监视文件的变化，当文件发生变化后，它会自动重启服务器







### 文件操作路径和模块路径

文件操作路径

```javascript
// 在文件操作的相对路径中
//    ./data/a.txt 相对于当前目录
//    data/a.txt   相对于当前目录
//    /data/a.txt  绝对路径，当前文件模块所处磁盘根目录
//    c:/xx/xx...  绝对路径
// fs.readFile('./data/a.txt', function (err, data) {
//   if (err) {
//     console.log(err)
//     return console.log('读取失败')
//   }
//   console.log(data.toString())
// })
```

模块操作路径

```javascript
// 在模块加载中，相对路径中的 ./ 不能省略
// Error: Cannot find module 'data/foo.js'
// require('data/foo.js')

// 模块操作路径中不能省略 ./
```

