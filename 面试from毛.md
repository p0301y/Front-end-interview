前端面试整理

前端面试知识点总结: 

https://juejin.im/post/5c64d15d6fb9a049d37f9c20#heading-67



前端面试题整理: 

https://juejin.im/post/5e2715f06fb9a02fe34bc73c#heading-21



前端面试算法40题整理: 

https://blog.csdn.net/sinat_17775997/article/details/103549117



前端面试43道JavaScript题目整理: 

https://juejin.im/post/5d0644976fb9a07ed064b0ca



前端面试常考js基础编程题:

http://www.conardli.top/docs/JavaScript/



字节跳动面试部分合集: 

https://www.nowcoder.com/discuss/180861



字节跳动面试问题

介绍一下之前做的项目
Es6,7用过哪些新的特性
介绍一下普通函数和箭头函数的区别
有没有用过promise，手写一个sleep函数
说一下react的事件机制
react在平时用的是什么版本的,react hooks有没有用过，和正常的class组件用下来哪一个觉得好
webpack的loader和plugin的区别
用过哪些plugin
手写promsie.all
考察js的宏观和微观队列
一道算法题


YDB面试问题

一面(差不多一个半小时)

手写redux的compose函数(如果在reduce里面传入的是一个promise数组，咋么实现这个数组的compose)
export default function compose(...funcs) {

  if (funcs.length === 0) {

    return arg => arg

  }



  if (funcs.length === 1) {

    return funcs[0]

  }



  return funcs.reduce((a, b) => (...args) => a(b(...args)))

}

js有哪些继承方式，手写一下，用es5的prototype和apply，es6的继承的super做了什么东西
写一个Map的类
对闭包的理解
在用prototype方法做继承时候，new一个实例对象做了什么
redux的一些主要的步骤(getState，dispatch，createStore，subscriber)，其中subscriber具体是咋么运作的（类比成Angular里面decorator的运作方式）
http://zhenhua-lee.github.io/react/redux.html

react的memoizeOne是咋么实现的，或者是createSelector
设计一个弹窗的受控组件，本身的visible,onCancel，不需要从外面传进来（实现方式是用forwardRef，外面调用组件本身的成员函数）
js是咋么执行的，本身是单线程的，和c++不同
js宏观和微观队列的区别，咋么执行，setTimeout和其他两个的区别
HTML的块级上下文（在项目里面有没有碰到一些对HTML排版进行优化的事情），为了避免HTML层级套的太深，提高性能


二面(差不多三刻钟)

浏览器的缓存是什么（比如前端发请求，正常都是200和304）
localStorage，sessionStorage区别，还有localStorage和cookie的区别
一个npm包发布时候，最后哪些文件会被上传
antd最后是如何打包的
用webpack的按需加载，babel-plugin-import
如果一个项目里面最后用了antd的某几个组件，那么最后应该咋么打包，肯定不是整个npm都打包
为什么用yarn lerna
yarn workspace有没有用过
yarn publish最后做了什么事
npm ignore，fails，package可以用fail指定
react的key，用和不用的区别；key是index和是别的属性的区别，拿消息推送列表作为例子，每次都是固定10个，这种情况应该用index作为组件的key


CISCO面试问题

电话面试（主要考试js和css基础，大部分都是挺基础的，这里罗列一小部分）

用js实现拷贝数据
css画三角形 
https://codepen.io/iamyourfatherlalala/pen/Baozqjr
内存泄漏解决方法
react componentDidMount为什么是从里往外执行的
dangerousInnerHTML


视频面试（面了1小时，上来先是问了一堆问题，然后再写代码）

把一个数组里面的元素，每n个做分割
React.useEffect和class组件里面的哪一个生命周期是等价的
说一下react的生命周期
css居中方式，用flex
响应式布局（媒体查询）
编程题：
页面山有一个按钮，然后给定一个字符串比如”HelloWorld”，当点击按钮之后会每隔一个相同的时间依次输出给定字符串的每一个字符(setInterval)
如果每一次的输出时间间隔是1s, 2s, 3s等，如何处理
用setTimeout实现setInterval（思路是用递归）
实现一个sleep函数
ts的枚举类型


酷家乐面试问题

电话面试（主要考试js基础，react源码和一些浏览器的基础知识）

说一下react的生命周期
react的setState是同步还是异步的
react的fiber更新机制
https://www.jianshu.com/p/bf824722b496

以前react的更新机制是同步的，现在上了fiber之后以render函数为界限，分为了render phase和commit phase,前者用来判断哪些组件需要被更新，后者是用来更新组件的
react的key
说一下什么是受控和非受控组件（这里自己理解的不是很深刻，应该说到createRef这一部分，详细看官网）
受控组件的官网定义
https://react.docschina.org/docs/forms.html#controlled-components

非受控组件的官网定义


https://react.docschina.org/docs/uncontrolled-components.html

说一下面向对象编程的几个特性，以及自己的理解
普通函数和箭头函数的区别，箭头函数的this是否可以被改变
说一下this是什么 
https://www.cnblogs.com/pssp/p/5216085.html



es6中箭头函数this的指向
https://zhuanlan.zhihu.com/p/26475137



说一下原型链
js的解析是否会阻塞css的渲染(js单线程)  
浏览器的dom和render tree 
浏览器的帧，在鼠标hover到一个按钮上面之后，具体发生了什么事情
观察者和发布订阅模式
以上两者的区别 https://www.cnblogs.com/leaf930814/p/9014200.html
redux用的是发布订阅模式


现场面试（一共有4面，前3轮技术面，最后一轮hr面）

平时用过哪些性能优化上面的技术（当时说了webpack的code split & ssr & defer以async,面试官后来说还有一个叫FPS的东西）
浏览器的缓存(300)
手写cloneDeep函数（如何深拷贝一个函数对象）
使用哈希表来解决深拷贝之后对象循环引用的问题
https://github.com/yygmind/blog/issues/29

当时是用递归实现的，最后被追问如何不用递归来实现
手写深搜和广搜
问到调用栈（好像和深拷贝实现有关系）
之前项目是如何设计组件的（以modal举例子）
做了4道数学题。。。
1）求n!末尾0的个数

2）有一个字符串，里面只包含’0’和’1’，求最长的连续子串，使得这个子串里面0和1的个数相同

3）有一个长度为L的木板，i个蚂蚁分布在这个木板上，假设木板的起点为o，末端为p,这些蚂蚁一开始距离o的距离是xi，每一个蚂蚁移动的速度为1，每当两个蚂蚁迎面相遇时候，他们的移动方向会和之前相反，当一个蚂蚁最后走到p的时候，会从木板上掉下来，求从开始到最后木板上没有蚂蚁的最短和最长时间

4）现在有m个0和n个1组成的集合，现在每一次从这些数字中任取两个数字，进行异或的操作，然后把新的数字放进集合中，直到最后集合中只有一个数字，求最后数字是1的概率

第三轮技术面试，面试官推荐了两本书，’重构’，’设计模式’(design pattern)


平安保险面试问题

电话面试（这里只罗列出当时回答的不是很好的问题）

什么时候不能用箭头函数 
箭头函数不能用作构造函数，js是会报错的
https://juejin.im/post/5d4770ecf265da03dd3d5642

React diff算法中是如何比较index的
如何让setState中是同步的，说出多种方式
如何判断一个对象是否是空对象
用for in属性
JSON.stringify(data) === ‘{}’
判断是否是数组
知道哪一些跨域的方式
Morgan Stanley面试准备

LinkedList
A linked list is an ordered collection of data elements. A data element can be represented as a node in a linked list. Each node consists of two parts: data & pointer to the next node.

https://codeburst.io/linked-lists-in-javascript-es6-code-part-1-6dd349c3dcc3

hashMap的底层
https://juejin.im/post/5b3731b36fb9a00e5326f087#heading-18

react diff算法详细
tree diff,  component diff, element diff
建议看第二个链接的东西，讲的更加详细
https://juejin.im/post/5d81eec56fb9a06add4e63ba

https://zhuanlan.zhihu.com/p/20346379

Reflow & Repaint 
https://medium.com/darrja-%E0%A4%A6%E0%A4%B0%E0%A5%8D%E0%A4%9C%E0%A4%BE/what-the-heck-is-repaint-and-reflow-in-the-browser-b2d0fb980c08

pdd部分面试问题

如何处理页面部分崩溃(ErrorBoundary)
如何处理页面卡顿
web worker的使用
useEffect和useLayoutEffect的区别
https://juejin.im/post/5de38c76e51d455f9b335eff

useReducer的第二个参数
手写一个promise类里面所有静态函数的类型
History是咋么实现的
http://zhenhua-lee.github.io/react/history.html

https://juejin.im/post/5d1afdedf265da1b8333a730



美团部分面试问题(包括了一面和二面)

实现一个深拷贝
说一下事件循环
Https说一下
浏览器的缓存说一下
写几个垂直居中的方式
typeof，instanceof, Object.prototype.toString.call, constructor 一些区别
实现一个replaceAll函数，把原来字符串中的某一个给定子字符串替换成一个给定的新字符串（可以用正则）
求最长的连续不重复的子串
写一个debounce函数, 说出和throttle函数的区别
hot_modules是如何实现的
webpack打包的优化方案
ajax实现原理
如何手动实现一个懒加载
css动画，从一个蓝色的长方形转变成一个红色的圆圈
实现把一个数组进行扁平化
有没有了解过csp和pwa
手写new和instanceof
如何实现继承多个类
有过哪些css的工具，比如css_modules
有没有了解过新的前端技术（当时说了deno）
现在的项目有没有用node.js，app.listen主要是用来干嘛的


跨域问题的解决方案

https://blog.csdn.net/yup1212/article/details/87633272

https://segmentfault.com/a/1190000019227927?utm_source=tag-newest

https://zhuanlan.zhihu.com/p/72146172

第三个链接里面有很多的解决方案
jsonp跨域
动态创建script标签
用nginx反向代理
反向代理的原理就是讲前端的地址和后端的地址用nginx转发到同一个地址下，具体操作见上面的链接



防抖和节流函数的区别以及实现方式

https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/5

防抖函数（debounce）
触发高频事件后n秒内函数只会执行一次，如果n秒内高频事件再次被触发，则重新计算时间

节流函数（throttle）
高频事件触发，但在n秒内只会执行一次，所以节流会稀释函数的执行频率



react的context和redux的区别

https://www.jianshu.com/p/eba2b76b290b

https://www.zhihu.com/question/266895622

https://juejin.im/post/5cf5d24d6fb9a07eb55f4802

简单说就是，当你不想在组件树中通过逐层传递props或者state的方式来传递数据时，可以使用Context来实现跨层级的组件数据传递。
和Redux相比，新旧的Context API都解决了Redux存在的“一些信息的内容需要根据组件的包含关系决定，而Redux难以处理这类包含关系”的问题。
建议看第三个链接，有具体的例子


let, const 和var的区别

https://blog.csdn.net/weixin_43681425/article/details/89484926

总体来说，var和let的区别就是作用域的不同。 const和let是相同作用域，区别就是不可被重新赋值。在一个函数外面，var的作用域是window；在一个函数里面那么作用域就是这个函数本身。而且let和const定义的变量不会被hoisting。


React的keys的作用

https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/1

提升效率，提高diff的速度
react是用key来识别组件的，比如要在一个列表中增加一个元素，这个时候没有key效率就要高很多；相反的，如果要对某一个元素进行挪动，那么有key的时候效率会更高
把一个数组的index作为组件的key，如果重新排序了，而且这个组件本身是一个非受控组件，那么它本身的state会收到影响；同时这么做的话会导致重新渲染的性能变差
通过改变一个组件的key可以让一个组件rerender
对于分页的操作，就可以用默认的index作为每一个组件的key
具体可以参考react keys的文档


用es5实现es6的Map类

主要参考第二个链接的内容

https://blog.csdn.net/weixin_43824566/article/details/85118380

https://www.cnblogs.com/Cathamerst/p/7222878.html



function Map() {

    var items = {};

    this.has = function(key){

        return key in items;

    },

    this.set = function(key,value){

        items[key] = value;

    },

    this.remove = function(key){

        if (this.has(key)) {

            delete items[key];

            return true;

        }

        return false;

    },

    this.get = function(key){

        return this.has(key)?items[key]:undefined;

    },

    this.values = function(){

        let values = [];

        for(const k in items){

            // 这里用hasOwnProperty的作用是忽略所有的继承属性

            if (this.hasOwnProperty(k)) {

                values.push(items[k]);

            }

        }

        return values;

    },

    this.clear = function(){

        items = {};

    },

    this.size = function(){

        return Object.keys(items).length;

    },

    this.getItems = function(){

        return items;

    }

}



ES5/ES6 的继承除了写法以外还有什么区别？

https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/20

在js中，对象都有__proto__属性，一般这个是被称为隐式的原型，该隐式原型指向构造该对象的构造函数的原型。
es5中有最常见的两种继承方式：
1）原型链继承
    // 定义父类

    function Parent(name) {

        this.name = name;

    }

    Parent.prototype.getName = function() {

        return this.name;

    };

    // 定义子类

    function Children() {

        this.age = 24;

    }

    Children.prototype = new Parent(‘陈先生');

    // Children.prototype.constructor ===      Parent.prototype.constructor = Parent



2) 构造函数继承
    // 定义父类

    function Parent(value) {

        this.language = ['javascript', 'react', 'node.js'];

        this.value = value;

    }

    // 定义子类

    function Children() {

    	Parent.apply(this, arguments);

    }



es6的继承
    // 定义父类

    class Father {

        constructor(name, age) {

            this.name = name;

            this.age = age;

        }



        show() {

            console.log(`我叫:${this.name}， 今年${this.age}岁`);

        }

    };

    // 通过extends关键字实现继承

    class Son extends Father {};

    let son = new Son('陈先生', 3000);



this的生成顺序不同，所以需要在constructor中，需要使用super()
子类的继承都是成功的，但是问题出在，子类的_proto_指向不一样。
对于es6的继承，子类可以直接通过 __proto__ 寻址到父类
class Super {}

class Sub extends Super {}

const sub = new Sub();

Sub.__proto__ === Super;

 



function Super() {}

function Sub() {}

Sub.prototype = new Super();

Sub.prototype.constructor = Sub;

var sub = new Sub();

Sub.__proto__ === Function.prototype;



对于ES5 的继承，实质是先创造子类的实例对象this，然后再将父类的方法添加到this上面（Parent.apply(this)）。ES6 的继承机制完全不同，实质是先将父类实例对象的属性和方法（先创建父类的实例对象this，和es5正好相反），加到this上面（所以必须先调用super方法），然后再用子类的构造函数修改this。


setTimeout、Promise、Async/Await 的区别

https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/7

https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/33

宏观任务队列和微观任务队列的区别
三个东西执行的顺序不一样
其中settimeout的回调函数放到宏任务队列里，等到执行栈清空以后执行； promise.then里的回调函数会放到相应宏任务的微任务队列里，等宏任务里面的同步代码执行完再执行；async函数表示函数里面可能会有异步方法，await后面跟一个表达式，async方法执行时，遇到await会立即执行表达式，然后把表达式后面的代码放到微任务队列里，让出执行栈让同步代码先执行


简单讲解一下 http2 的多路复用以及它的原理

https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/14

简单来说， 就是在同一个TCP连接，同一时刻可以传输多个HTTP请求。
之前是同一个连接只能用一次， 如果开启了keep-alive，虽然可以用多次，但是同一时刻只能有一个HTTP请求


React 中 setState 什么时候是同步的，什么时候是异步的？

https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/18

isBatchingUpdates 默认值为 false，当 react 自身的事件处理函数或 react 生命周期触发时，isBatchingUpdates 会被赋值为 true，当更新完成时又会被复原为 false。


介绍下 npm 模块安装机制，为什么输入 npm install 就可以自动安装对应的模块？

https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/22

发出npm install命令
查询node_modules目录之中是否已经存在指定模块。若存在，不再重新安装；若不存在，1) npm 向 registry 查询模块压缩包的网址。2）下载压缩包，存放在根目录下的.npm目录里。 3）解压压缩包到当前项目的node_modules目录


Instanceof是咋么样判断对象

// __proto__: 代表原型对象链

instance.[__proto__...] === instance.constructor.prototype



// return true

instanceof 的内部机制是通过判断对象的原型链中是不是能找到类型的 prototype
能在实例的 原型对象链 中找到该构造函数的prototype属性所指向的 原型对象，就返回true。
但 instanceof 只能用来判断对象类型，原始类型不可以。
并且所有对象类型 instanceof Object 都是 true。
2 instanceof Number === false
true instanceof Boolean === false
‘lalala’ instanceof String === false
[] instanceof Array === true
function(){} instanceof Function === true


Object.prototype.toString.call() 、 instanceof 以及 Array.isArray() constructor

https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/23

https://www.jianshu.com/p/02c51f83d4a7

Object.prototype.toString.call()
Object.prototype.toString.call('An') // "[object String]"

Object.prototype.toString.call(1) // "[object Number]"

Object.prototype.toString.call(Symbol(1)) // "[object Symbol]"

Object.prototype.toString.call(null) // "[object Null]"

Object.prototype.toString.call(undefined) // "[object Undefined]"

Object.prototype.toString.call(function(){}) // "[object Function]"

Object.prototype.toString.call({name: 'An'}) // "[object Object]"

Instanceof
使用 instanceof判断一个对象是否为数组，instanceof 会判断这个对象的原型链上是否会找到对应的 Array 的原型，找到返回 true，否则返回 false。
console.log(2 instanceof Number);                    // false

console.log(true instanceof Boolean);                // false 

console.log('str' instanceof String);                // false  

console.log([] instanceof Array);                    // true

console.log(function(){} instanceof Function);       // true

console.log({} instanceof Object);                   // true    

console.log(undefined instanceof Undefined);// 报错

console.log(null instanceof Null);//报错

Array.isArray()
Constructor
typeof()


介绍redux中间件

https://www.jianshu.com/p/2a1e484061d2

https://www.jianshu.com/p/ae7b5a2f78ae

https://www.jianshu.com/p/ae7b5a2f78ae

上面的第二以及第三个链接比较详细，第三个有一个简单的Middleware的示例
具体业务场景：假如我们有一个列表页面，当用户点击“下一页”的时候，我们需要向后台请求新的数据。解决方案至少有两种：1）在按钮上绑定事件，发起ajax请求，在ajax的回调函数中将新返回的数据作为action的参数，传入reducer。2）编写一个中间件，凡是发起的action都要经过这个中间件，我们假设设置一个action参数promise，凡是检测到action里有这个参数，就生成一个promise对象，在promise的回调中将返回数据传入reducer。
在增加了 middleware 后，我们就可以在这途中对 action 进行截获，并进行改变。
redux saga是处理用来处理redux异步操作的中间件
middlewareAPI主要包含了两个东西，getState和dispatch
一个基本的中间件例子
     const doNothingMiddleware = (dispatch, getState) => next => action => next(action);

compose函数
const compose = (...fns) => {

    if(fns.length === 1) {

        return fns[0];

    }

    // reduce(callbackfn: (previousValue: any, currentValue: any, currentIndex: number, array: any[]) => any): any

    return fns.reduce((a, b) => (...args) => a(b(...args)));

}     

export default function applyMiddleware(...middlewares) {

  return createStore => (...args) => {

    // 利用传入的createStore和reducer和创建一个store

    const store = createStore(...args)

    let dispatch = () => {

      throw new Error(

      )

    }

    const middlewareAPI = {

      getState: store.getState,

      dispatch: (...args) => dispatch(...args)

    }

    // 让每个 middleware 带着 middlewareAPI 这个参数分别执行一遍

    const chain = middlewares.map(middleware => middleware(middlewareAPI))

    // 接着 compose 将 chain 中的所有匿名函数，组装成一个新的函数，即新的 dispatch

    dispatch = compose(...chain)(store.dispatch)

    return {

      ...store,

      dispatch

    }

  }

}





baseline和vertical-align的区别

https://segmentfault.com/a/1190000012803061?utm_source=tuicool&utm_medium=referral

https://developer.mozilla.org/zh-CN/docs/Web/CSS/vertical-align



sourceMap的定位原理

https://juejin.im/post/5d0790996fb9a07f0052dbbb

{

  "version": 3,

  "sources": [      // 所有输入的文件名

    "log.js",

    "main.js"

  ],

  "names": [       // 所有可符号化字符的数组

    "sayHello",

    "name",

    "length",

    "substr",

    "console",

    "log"

  ],

  "mappings": "AAAA,SAASA,SAAUC,MACjB,GAAIA,KAAKC,OAAS,EAAG,CACnBD,KAAOA,KAAKE,OAAO,EAAG,GAAK,MAE7BC,QAAQC,IAAI,QAASJ,MCJvBD,SAAS"

}



不要输出文件中的行号
mappings: “输出文件列位置|输入文件名|输入文件行号|输入文件列号,….."
提取输入文件名
mappings: “输出文件列位置|输入文件名索引|输入文件行号|输入文件列号,….."
可符号化字符的提取 
“输出文件列位置|输入文件名索引|输入文件行号|输入文件列号|字符索引,....."
记录相对位
VLQ编码(mappings)




SSO原理

https://yq.aliyun.com/articles/636281

Todo…


手写一个简单的路由

https://xianyulaodi.github.io/2017/06/18/%E6%89%8B%E5%86%99%E4%B8%80%E4%B8%AArouter/

首先我们需要一个容器来存储我们更新url时的回调函数。
当执行当前url对应的回调函数时，我们需要更新我们的页面
我们需要监听url中hash的改变


高阶组件

https://juejin.im/post/5e169204e51d454112714580



==和===

https://juejin.im/entry/584918612f301e005716add6

[] == false  // true
[]先转变成空的字符串，false转成0
!![] == true  // true
!![]先做如下的运算：!!(ToBoolean([]))
{} == false  // false // 这样写会直接报错
{}先转变成”[object Object]”
https://www.cnblogs.com/lovellll/p/10225524.html

[] == ![] // true
{} == !{} // false




请手写es6和es5的面向对象代码实现

https://www.jianshu.com/p/bfcfec5595c7



    // 面向对象

    (function () {

        // es6的面向对象

        class Person {

            constructor(name, age) {

                this.name = name

                this.age = age

            }

            showName() {

                console.log(this.name)

            }

        }

        // 实例化Person

        let student = new Person('王宏', '36')

        student.showName()

        // 继承

        class Worker extends Person {

            constructor(name, age) {

                super(name, age)

            }

            // 添加Worder自己特有的方法

            showAge() {

                console.log(this.age)

            }

        }

        // 实例化Worker

        let coder = new Worker('廖峰', '40')

        coder.showName()

        coder.showAge()



        // es5的面向对象

        function Animal(name, color) {

            this.name = name

            this.color = color

        }

        Animal.prototype.showName = function () {

            console.log(this.name)

        }

        // 实例化Animal对象

        let dragon = new Animal('龙', '金色')

        dragon.showName()



        // 继承

        function Tiger(name, color) {

            Animal.call(this, name, color)

        }

        Tiger.prototype = new Animal()

        Tiger.prototype.constructor = Tiger



        let smallTiger = new Tiger('小老虎', '灰色')



        smallTiger.showName()

    })();



箭头函数和普通函数的区别

https://blog.csdn.net/qq_25753979/article/details/90237123

https://blog.csdn.net/m0_37686205/article/details/88776259

箭头函数不能作为构造函数，不能new
箭头函数不绑定arguments，但是可以使用…rest参数
arguments的一般使用场景是：允许传入3个参数，中间一个参数是可选。如果只传1个参就是参数1用，传入2个参就是参数1和参数3用
rest默认是[]，多余的传参会加入数组
两种函数的this指向不同，1）箭头函数，this代表上层对象，若无自定义上层，则代表window。2）普通函数，this代表当前对象。 


call函数是用来改变函数内部的this的指向
相比普通函数，箭头函数并没有自己的原型
箭头函数外层没有普通函数，严格模式和非严格模式下它的this都会指向window(全局对象)


上传文件的post请求参数

      const formData = new FormData();

        const { files } = body;



        for (const file of files) {

            formData.append('files', file);

        }



        return ajax.post<IPostCollectionImportResponse>(postCollectionImportUri(userId), formData, {

            headers: {

                'Content-Type': 'multipart/form-data',

            },

        });





js的原型和原型链

https://www.cnblogs.com/ryelqy/p/10997332.html

每一个对象都具有属性_proto_，它会指向该对象的原型
每一个Function除了有_proto_之外，还有prototype属性，它指向了一个对象，这个对象是调用该构造函数而创建的实例的原型


打印以下的console

Object.prototype.a = 'Object';

Function.prototype.a = ‘Function';

function Person(){};

var child = new Person();

console.log(Person.a);   // ‘Function’

console.log(child.a);  // ‘Object’

console.log(child.__proto__);  // constructor，一个对象的原型

console.log(child.__proto__.__proto__);  

console.log(child.__proto__.__proto__.constructor);

console.log(child.__proto__.__proto__.constructor.constructor);

console.log(child.__proto__.__proto__.constructor.constructor.constructor);





ajax的组成，请求过程，如何请求一张图片，如果是post请求，发送的数据类型都有什么

https://blog.csdn.net/h_qingyi/article/details/79935818

组成（支持异步 & 不需要更新整个页面）
Javascript css xml XMLHttpRequest
其中js负责向服务器发请求，xml负责封装数据
步骤
1）创建XMLHttpRequest（ 相当于打开了一个浏览器）
2）连接服务器（ 相当于在地址栏输入访问地址）
3）发送请求（相当于回车或者点击访问发送请求）
4）接受请求（相当于处理网页呈现后的操作）
如何请求一张图片
post请求有对应的headers
headers里面包含的属性如下：Content-Type


webpack打包产物是怎样的，到底是为了什么，优化了什么，为什么要合并文件？

https://www.jianshu.com/p/b8d6ac3041e3

webpack是一个打包模块化javascript的工具，分析你的项目结构，找到JavaScript模块以及其它的一些浏览器不能直接运行的拓展语言（Scss，TypeScript等），并将其打包为合适的格式以供浏览器使用。
webpack打包流程

https://www.bilibili.com/video/av69121363/

https://juejin.im/post/5c62a137f265da2db87b87bb

读取配置文件，按命令 初始化 配置参数，创建 Compiler 对象
调用插件的 apply 方法 挂载插件 监听，然后从入口文件开始执行编译
按文件类型，调用相应的 Loader 对模块进行 编译，并在合适的时机点触发对应的事件，调用 Plugin 执行，最后再根据模块 依赖查找 到所依赖的模块，递归执行第三步
将编译后的所有代码包装成一个个代码块 (Chuck)， 并按依赖和配置确定 输出内容。这个步骤，仍然可以通过 Plugin 进行文件的修改;
最后，根据 Output 把文件内容一一写入到指定的文件夹中，完成整个过程


什么是bundle，什么是chunk，什么是module

bundle是由webpack打包出来的文件，chunk是指webpack在进行模块依赖分析的时候，代码分割出来的代码块，module是开发中的单个模块


什么是loader，什么是plugin

loader是用来告诉webpack如何转化处理某一类型的文件，并且引入到打包出的文件中
plugin是用来自定义webpack打包过程中的方式，一个插件是含有apply方法的一个对象，通过这个方法可以参与到整个webpack打包的各个流程（生命周期）。Webpack 就像工厂中的一条产品流水线，通过事件流机制，让 Plugin 可以插入到整个生产过程中的每个步骤中。


webpack-dev-server和http服务器如nginx有什么不同

webpack-dev-server使用内存来存储webpack开发环境下的打包文件，并且可以使用模块热更新，他比传统的http服务器对开发更加简单高效


loader和plugin的编写，比如说插一行注释

https://segmentfault.com/a/1190000021444966?utm_source=tag-newest

loader的编写
https://segmentfault.com/a/1190000019223302

plugin的编写
https://segmentfault.com/a/1190000019223474

Webpack打包优化

https://www.jianshu.com/p/e4c1a9c40a2e

减少打包时间
1）优化Loader，将babel编译过的文件缓存过来
2）HappyPack，将loader的同步执行转化成并行
3）代码压缩相关，在webpack4中只要启动了mode为production，就会默认使用UglifyJS来压缩代码
减少打包的大小
1）按需加载，首页加载文件越小越好，将每个页面单独打包为一个文件
2）Tree shaking，删除项目中未被引用的代码，而如果在webpack 4中只要开启生产环境就会自动启动这个功能（https://segmentfault.com/a/1190000019220154）




某个页面单独打包

WebPack.optimize.CommonsChunkPlugin



相同引入模块合并打包



react diff的原理

https://www.jianshu.com/p/3ba0822018cf

https://segmentfault.com/a/1190000010686582

React只会对相同颜色方框内的DOM节点进行比较，即同一个父节点下的所有子节点。(把树形结构按照层级分解，只比较同级元素)
给列表结构的每个单元添加唯一的 key 属性，方便比较
React 只会匹配相同 class 的 component（这里面的 class 指的是组件的名字）
选择性子树渲染。开发人员可以重写shouldComponentUpdate 提高 diff 的性能
上面给出的第二个链接讲的太啰嗦，建议只看第一个详细算法


new一个对象的时候发生了什么

https://blog.csdn.net/h15882065951/article/details/69913881

创建一个新的对象
const person = {};
新对象的_proto_指向构造函数的原型对象
person._proto_ = Person.prototype; //引用构造函数的原型对象
将构造函数的作用域赋值给新的对象（this指向了新对象）
Person.call(person); //将构造函数的作用域给person,即：this值指向person
执行构造函数内部的代码，将属性添加给person中的this对象。
返回新对象person。


jS编写一个求和函数sum，使输入sum(2)(3)或输入sum(2,3)，输出结果都为5

function sum(){

    var num = arguments[0];

    if(arguments.length==1){

        return function(sec){

            return num+sec;

        }

    }else{

        var num = 0;

        for(var i = 0;i<arguments.length;i++){

            num = num + arguments[i];

        }

    return num;

    }

}



js 怎么进行性能分析

https://segmentfault.com/a/1190000018651682

Window.performance
性能指标
1）白屏时间（实际拿到页面资源的时间）
2）资源加载（比如js，css）
3）用户可操作时间
4）首屏渲染的时间


package.json中的版本管理

https://blog.csdn.net/shan1991fei/article/details/90207192

'2.1.1'   表示安装指定的版本号，也就是安装2.1.1版本。
'~2.1.1' 表示安装2.1.x的最新版本，安装时不改变大版本号和次要版本号。
'^2.1.1'  表示安装2.x.x的最新版本，安装时不改变大版本号。


什么是闭包

https://zhuanlan.zhihu.com/p/72146172

能够读取其他函数内部变量的函数。
解决的问题
1）可以读取函数内部的变量
2）让这些变量的值始终保持在内存中。不会在函数调用后被清除
可以模拟一个私有变量
缺点：

容易造成内存泄漏
闭包可以使得函数内部的值可以在函数外部进行修改


http请求204和304的区别

https://blog.csdn.net/csdnlijingran/article/details/88397522

等同于请求执行成功，但是没有数据，浏览器不用刷新页面，也不用导向新的页面
不应该认为是一种错误，而是对客户端有缓存情况下面服务端的一种响应




观察者模式和发布订阅模式的区别

前者在react中就像父子组件之间的传值
后者就像组件之间的通信是通过redux的


什么是伪数组

具有length属性
按索引方式存储数据
不具有数组的方法, 比如push(),pop()等


触发BFC的条件

https://zhuanlan.zhihu.com/p/25321647

body 根元素
浮动元素：float 除 none 以外的值
绝对定位元素：position (absolute、fixed)
display 为 inline-block、table-cells、flex
overflow 除了 visible 以外的值 (hidden、auto、scroll)
BFC的特性
同一个 BFC 下外边距会发生折叠
BFC 可以包含浮动的元素（清除浮动）
BFC 可以阻止元素被浮动元素覆盖


opacity: 0、visibility: hidden、display: none区别

display: none (不占空间，不能点击)（场景，显示出原来这里不存在的结构），会发生回流
visibility: hidden（占据空间，不能点击）（场景：显示不会导致页面结构发生变动，不会撑开），会发生重绘的操作
opacity: 0（占据空间，可以点击）（场景：可以跟transition搭配）




实现一个promise.finally

Promise.prototype.finally = function (callback) {

  let P = this.constructor;

  return this.then(

    value  => P.resolve(callback()).then(() => value),

    reason => P.resolve(callback()).then(() => { throw reason })

  );

};



实现一个promise.all

https://zhuanlan.zhihu.com/p/41502945



Promise.prototype.all = function(promises) {

  let results = [];

  let promiseCount = 0;

  let promisesLength = promises.length;

  return new Promise(function(resolve, reject) {

    for (let val of promises) {

      Promise.resolve(val).then(function(res) {

        promiseCount++;

        // results.push(res);

        results[i] = res;

        // 当所有函数都正确执行了，resolve输出所有返回结果。

        if (promiseCount === promisesLength) {

          return resolve(results);

        }

      }, function(err) {

        return reject(err);

      });

    }

  });

};





https怎么通过证书，保证数据的完整性

https://blog.csdn.net/luweicheng24/article/details/80579731

HTTPS要使客户端与服务器端的通信过程得到安全保证，必须使用的对称加密算法，但是协商对称加密算法的过程，需要使用非对称加密算法来保证安全，然而直接使用非对称加密的过程本身也不安全，会有中间人篡改公钥的可能性，所以客户端与服务器不直接使用公钥，而是使用数字证书签发机构颁发的证书来保证非对称加密过程本身的安全。这样通过这些机制协商出一个对称加密算法，就此双方使用该算法进行加密解密。从而解决了客户端与服务器端之间的通信安全问题


tcp和udp的区别

两者的报头和传输协议不同


将图片转化成base64

https://blog.csdn.net/qq_37164847/article/details/86466658

把图片转成base64形式用处主要是减少HTTP请求、实时预览要上传的图片


var img = "imgurl";//imgurl 就是你的图片路径  



function getBase64Image(img) {  

     var canvas = document.createElement("canvas");  

     canvas.width = img.width;  

     canvas.height = img.height;  

     var ctx = canvas.getContext("2d");  

     ctx.drawImage(img, 0, 0, img.width, img.height);  

     var ext = img.src.substring(img.src.lastIndexOf(".")+1).toLowerCase();  

     var dataURL = canvas.toDataURL("image/"+ext);  

     return dataURL;  

}  



var image = new Image();  

image.src = img;  

image.onload = function(){  

  var base64 = getBase64Image(image);  

  console.log(base64);  

} 



cookie和session的区别

https://www.jianshu.com/p/2f7031a69f43



$(document).ready和window. onload的区别

window.onload方法是在网页中所有的元素（包括元素的相关联文件）都加载到浏览器后才能执行，即JavaScript此时才可以访问网页中的任何元素；$(document).ready在DOM完全就绪的时候就可以被调用。
window.onload只能绑定一个函数，而$(document).ready( ) 就可以写很多个


css实现高斯模糊

https://blog.csdn.net/FlyJapan_viba/article/details/82313583



主要采用css的 filter: blur();
react filber算法详解

https://blog.csdn.net/VhWfR2u02Q/article/details/86065194





https://people.toutiaocloud.com/atsx/bridge/video/interviewee/2b80d32e-7796-4346-bec6-6b84861dde36



react的事件机制

https://segmentfault.com/a/1190000015142568

https://juejin.im/post/5c7df2e7f265da2d8a55d49d



事件注册，所有事件注册的逻辑都在 listenTo 中实现的。首先去遍历props中的属性。而registrationNameModules.hasOwnProperty(propKey),registrationNameModules是一个事件名的集合，几乎包含了所有的常见事件，这也就是如果你写一些稀奇古怪的事件,react是不识别的。如果判定props中的属性 如onClick在registrationNameModules中，并且值typeof === function，则会进入到listenTo中。
   listenTo做的事情很简单，就是在组件mount或者update的时候遍历props中的event，然后将事件和事件的依赖事件统统挂载到document上，并且所有的事件的回调函数走的都是dispatchEvent。

   react会把所有的事件都挂载到document上。这也是为什么我们event.stoppropagation()为什么不能阻止原生冒泡。因为所有事件都是绑定在document上的。意味着你的原生事件都执行完了之后，才能执行document的事件。dispatchEvent会做统一的派发。可以说原生事件的执行顺序是早于react事件的。

事件合成
事件合成的过程。首先根据触发事件的target得到inst，然后遍历他的所有父节点(fiber.return属性),存储在局部遍历path中，记住这个path是有顺序关系的（后面可以解释react事件是如何阻止冒泡的）。得到path后进行遍历，假设遍历的组件同样注册了对应事件的listener，那么就挂载到event的_dispatchListeners和_dispatchInstances中去,这两个属性至关重要，后续的事件派发就是根据这两个属性进行的。 注意只有注册了对应事件的listener，才会挂载到event里面去。比如刚刚我们的ABC都绑定了Click，自然都会push到_dispatchListeners中去。



for in和for of的区别

https://blog.csdn.net/aerchi/article/details/80221274



总结下来一句话，前者遍历的是key；后者遍历的是value