### 阿里钉钉文档  

参考： https://my.oschina.net/u/4592353/blog/4434447  

1. 如何获取一个浏览器的唯一标识
   https://cloud.tencent.com/developer/article/1665746

2. react如何使用render prop component请求数据

   https://www.robinwieruch.de/react-fetching-data#how-to-fetch-data-in-render-props

3. cookie共享

   https://www.ruanyifeng.com/blog/2016/04/same-origin-policy.html 

   https://segmentfault.com/a/1190000010419598

   cookie区分域名，而不区分端口，也就是说，同一个ip下的多个端口下的cookie是共享的！

   cookie可以通过domain属性区分，为了保障安全性，cookie只能设置当前域名或者其父域的domain

4. React实现一个message组件  

   单例模式和策略模式

   全局配置和实例配置

   https://cloud.tencent.com/developer/article/1590907

   ```
   message[type](config)
   meesage.open(config, type)
   message.remove(key)
   message.close(key)
   ```

   功能以及接口定义： 

   - 类型type 

   - 时间

   - 自定义关闭图标

   - 自定义提示图标

   - 自定义提示信息

   - 能够手动销毁

   - 关闭时提供回调函数

   - 自定义容器

   - 自定义位置（top, bottom, left, right）

     ```
     export interface IConfig<T> {
         content: React.ReactNode;
         key?: <T>;
         duration?: number;
         icon?: React.ReactNode;
         onClose?: () => void;
     }
     
     export interface IMessage<T extends string | number> {
         open: (config: IConfig<T>, type: any) => void; // 基本方法
         close: (key: T) => void;
         destroy: () => void;
         config: () => void; // 全局的config
         // success/error等方法
     }
     
     const message: IMessage<string | number> = {
         open: (config) => {},
     };
     
     const TYEPS = ["error", "success", "info", "warning"]
     
     TYEPS.forEach(item => {
         message[item] = (config: IConfig) => {
             message.open(config, item);
         }
     })
     ```

     - 单例模式

     作为容器列表组件，使用单例模式不仅节约了内存空间，而且单利延迟执行的特性也保证了在没有通知的情况下不会生成notification组件，提升了页面性能

     ```
     function getNotificationInstance(prefixCls: string, placement: NotificationPlacement, callback: (n: any) => void) {
       const cacheKey = `${prefixCls}-${placement}`;
       if (notificationInstance[cacheKey]) {
         callback(notificationInstance[cacheKey]);
         return;
       }
     
       //---实例化Notification组件
       (Notification as any).newInstance({
         prefixCls,
         className: `${prefixCls}-${placement}`,
         style: getPlacementStyle(placement),
         getContainer: defaultGetContainer,
       }, (notification: any) => {
         notificationInstance[cacheKey] = notification;
         callback(notification);
       });
     }
     ```

5. 如何通过url传递一个数组 

   https://stackoverflow.com/questions/1763508/passing-arrays-as-url-parameter/1764199#1764199

   理论上是转化成字符串，后端解析字符串，然后转化成数组

6. 为什么使用react，react给我们带来了什么

7. css的解析过程：http://jartto.wang/2017/11/13/Exploring-the-principle-of-CSS-parsing/

   

#### 酷家乐

1. 继承/异步/eventLoop/es6/react的diff算法

2. canvas计算图片中的个数和面积： https://juejin.cn/post/6844903680945192974#heading-10 

   ```
   
   ```

3. 判断自身是否是质数: https://juejin.cn/post/6844903895194402824  

   ```
   // 硬方法，使用while循环，从2开始，计算是否可以整除
   const isPrime = target => {
   	if (num === 1) {
       return '1 不是质数，请输入大于1的数字'
     }else if (num === 2) {
       return true
     }else {
       for (let i = 2; i < num; i++) {
        if (num%i === 0) {
          return false
        }
       }
       return true
     }
   }
   // 缩小范围，2-根号n
   const isPrime = target => {
   	if (target < 3) {
   		return num > 1;
   	}
   	let sq = Math.sprt(target);
   	for (let i = 2; i <= sq; i++) {
   		if (target % i === 0) {
   			return false;
   		}
   	}
   	
   	return true;
   }
   ```

4. 深度和广度优先遍历（递归和迭代【栈和队列】）

5. 零钱兑换：https://leetcode-cn.com/problems/coin-change/

   ```
   // 动态规划
   // 深度优先遍历（递归）回溯法
   ```
   
6. node.js的事件循环和浏览器的事件循环，以及区别

   Node.js的事件循环： https://zhuanlan.zhihu.com/p/37427130。

##### 快手商业化

###### 一面

1. 性能优化

   

2. react相关（react中classComponent和FunctionComponent的区别/声明周期/hook）

   1. classComponent和functionComponent的区别
      - functionComponent没有state
      - classComponent对象有实例属性this,functionComponent是function,没有this属性,使用ref可以代替
      - functionComponent的props和hook state是捕获的，classComponent的props和state利用this.props和this.state是实时的，classComponent的render函数利用闭包是可以实现functionComponent
      -  functionComponent没有生命周期的概念
   2. 为什么会有hook?
      - functionComponent无法完全取代替classComponent,需要hook
      - 带有状态的逻辑很难复用
      - 复杂组件难以理解，大量的业务逻辑需要放在componentDidMount和componentDidUpdate等生命周期函数中，useEffect可以粒度更加细分

3. es6

4. Http1/http2/http3

   1. Http2

   - 二进制格式传输，更加高效，更加紧凑
   - 多路复用技术（链接共享），一个网络链接实现并行请求
   - header压缩，降低开销
   - 服务端推送（与SPDY一样，支持server push），减少请求延时
   - 默认使用加密

   2. Http3（定制和测试阶段）
      - 运行在 QUIC 之上的 HTTP 协议被称为 HTTP/3(HTTP-over-QUIC)
      - QUIC 协议(Quick UDP Internet Connection)基于 UDP，正是看中了 UDP 的速度与效率。同时 QUIC 也整合了 TCP、TLS 和 HTTP/2 的优 点，并加以优化

5. 数组flatten的实现（包括去重复）

   ```
   var flatten = (arr) => {
     const set = new Set(); // 去重
     const self = (list) => {
       for (const item of list) {
         if (Array.isArray(item)) {
           self(item);
         } else {
           set.add(item);
         }
       }
     }
     self(arr);
     return Array.from(set);
    }
   ```

   

6. typescript相关

   1.  type和interface的区别
      相同点：
        - 都可以描述一个对象或者一个函数
        ```
          interface User {
            name: string;
            age: number
          }
          interface SetUse {
            (name: string, age: number): void;
          }
          type User = {
            name: string;
            age: number;
          }
          type SetUser = (name: string, age: number): void
        ```
        - 拓展和交叉类型: interface可以extends,但type是不允许extends和implement的，但是type可以通过交叉类型实现interface的extends行为
        ```
          interface Name {
            name: string;
          }
          interface User extends Name {
            age: number;
          }
          type Name = {
            name: string;
          }
          type User = Name & {age: number}
        ```
   不同点：
     - type可以声明基本类型别名。联合类型，元组等类型
     ```
   ​    // 基本类型别名
   ​    type Name = string

   ​    // 联合类型, 结合类型守卫
   ​    interface Dog {

   ​    }
   ​    interface Cat {

   ​    }
   ​    type Pet = Cat | Cat

   ​    // 元组
   ​    type PetList = [Dog, pet]
     ```
     - type语句中还可以使用typeof获取实例的类型进行赋值
     ```
   ​    let div = document.createElement('div');
   ​    type B = typeof div
     ```
     - interface能够声明合并
     ```
   ​    interface User {
   ​      name: string;
   ​      age: number;
   ​    }

   ​    interface User {
   ​      sex: string;
   ​    }
     ```

   2. interface和abstract的区别
      抽象类: abstract修饰，里面可以有抽象方法。但是抽象方法必须在抽象类里面(通常控制实现)
      ```
      abstract class Thing {
        height: number;
        setAttribute: (value: any) => void;
        abstract setValue: (value: any) => void;
      }
      ```
      接口（多态）: 父类定义方法和属性，让继承它的子类去实现，每一个子类由不同的表现
      ```
      interface Electrician {
        layWires(): void
      }
      interface Plumber {
        layPipes(): void
      }
      function restoreHouse(e: Electrician, p: Plumber) {
        e.layWires()
        p.layPipes()
      }
      ```

   [https://github.com/SunshowerC/blog/issues/7#type-%E5%8F%AF%E4%BB%A5%E8%80%8C-interface-%E4%B8%8D%E8%A1%8C](https://github.com/SunshowerC/blog/issues/7#type-可以而-interface-不行)

   3. 工具函数的实现
      https://zhuanlan.zhihu.com/p/40311981
      ```
      type Partial<T> = {[P in keyof T]?: T[P]}
      type Pick<T, K extends keyof T> = {[P in K]: T[P]};
      type Exclude<T, U> = T extends U ? nerver : T;
      type Omit<T, K> = Pick<T, Exclude<keyof T, K>>
      type ReturnType<T> = T extends (...args: any[]) => infer R ? R : any;
      ```

7. css问题（如何实现宽高等比例缩放）

   1.  如何实现一个宽度和高度等比缩放

      - 使用隐藏的图片（宽高比列相同）： 原理是额外的子元素撑满父元素
      - 增加wrap,使用padding-top或者padding-bottom实现
      -  使用vw视口单位实现  

      ```
      .box {
        width: 100%;
          height: 50vw;
        }
      }
      ```

      

8. curry函数的实现fn(1, 2, 3),curry = makeCurry(fn), fn(1, 2, 3) = curry(1)(2)(3)

   ```
   var makeCurry = (fn) => {
     const len = fn.length; // Function.length获取函数形参个数
     const args = [];
     const self = (...arg) => {
       args.push(...arg);
       if (args.length >= len) {
         return fn(...args);
       } 
       return self;
     }
     return self;
    }
   ```

###### 二面

1. React.suspense/lazy的原理（以及执行时机）

   React.suspense的作用

   - split Code

   React.lazy将组件包裹成LazyComponent

   ```
   function lazy(ctor) {
     var lazyType = {
       $$typeof: REACT_LAZY_TYPE,
       _ctor: ctor,
       // React uses these fields to store the result.
       _status: -1,
       _result: null
     };
   
     return lazyType;
   }
   ```

   React.suspense利用componentDidCatch捕获promise，promise执行resolve之后再渲染子元素，之前渲染fallback

   ```
   export function readLazyComponentType<T>(lazyComponent: LazyComponent<T>): T {
     const status = lazyComponent._status
     const result = lazyComponent._result
     switch (status) {
       case Resolved: {
         const Component: T = result
         return Component
       }
       case Rejected: {
         const error: mixed = result
         throw error
       }
       case Pending: {
         const thenable: Thenable<T, mixed> = result
         throw thenable
       }
       default: {
         lazyComponent._status = Pending
         const ctor = lazyComponent._ctor
         const thenable = ctor()
         thenable.then(
           moduleObject => {
             if (lazyComponent._status === Pending) {
               const defaultExport = moduleObject.default
               lazyComponent._status = Resolved
               lazyComponent._result = defaultExport
             }
           },
           error => {
             if (lazyComponent._status === Pending) {
               lazyComponent._status = Rejected
               lazyComponent._result = error
             }
           },
         )
         lazyComponent._result = thenable
         throw thenable
       }
     }
   }
   ```

   - Data Fetching

     https://reactjs.org/blog/2018/11/27/react-16-roadmap.html#react-16x-mid-2019-the-one-with-suspense-for-data-fetching

   Concurrent mode的理解： https://developer.51cto.com/art/202011/631109.htm

2. 图形编辑器矩阵

3. 矩阵的顺时针遍历

   ```
   /**
    * @param {number[][]} matrix
    * @return {number[]}
    */
   var spiralOrder = function(matrix) {
       const res = [];
       const row = matrix.length;
       if (row < 1) {
           return res;
       }
       const column = matrix[0].length;
       let i = 0, j = 0;
       let boundU = 0;
       let boundL = 0;
       let boundD = row - 1;
       let boundR = column - 1;
       let turn = column === 1 ? 'd' : 'r';
       for (let c = 0; c < row * column; c++) {
           res.push(matrix[i][j]);
           if (turn === 'r') {
               j++;
               if (j === boundR) {
                   boundU++;
                   turn = 'd';
               }
           } else if (turn === 'd') {
               i++;
               if (i === boundD) {
                   boundR--;
                   turn = 'l';
               }
           } else if (turn === 'l') {
               j--;
               if (j === boundL) {
                   boundD--;
                   turn = 'u'
               }
           } else if (turn === 'u') {
               i--;
               if (i === boundU) {
                   boundL++;
                   turn = 'r'
               }
           }
       }
       return res;
   };
   ```

##### 三面

1. renderProps的复杂用法：https://zh-hans.reactjs.org/docs/render-props.html

   ```
   
   ```

   

2. 实现一个请求缓存

   ```
   // 利用axios事项promise缓存
   const map = new Map();
   const requestCache = (url, method, data, config) => {
   		const key = `${url}_${method}_${JSON.stringfy(data)}`;
   		if (map.has(key)) {
   			return map.get(key);
   		}
   		const promise = axios(url, data, config)
   		map.set(key, promise);
   		return promise;
   }
   ```

   

#### 淘宝拍卖

##### 一面

1. 项目（宏观态势和模版技战法）

2. 重排与重绘

   https://zhuanlan.zhihu.com/p/161468550 

##### 二面

聊项目

##### 三面

项目

##### 四面

交叉面试



#### PDD

##### 一面

1. 定位
2. 盒子模型
3. Hook/HOC/renderProps
4. Var/let/const
5. React-router的原理
6. tree数据结构的封装（遍历，增删改查）
7. 性能优化。

##### 二面

1. renderProps和HOC的区别: https://medium.com/simply/comparison-hocs-vs-render-props-vs-hooks-55f9ffcd5dc6

   ```
   // 手写HOC
   // class写法
   const withFetch = (WrapComponet, url) => {
   	class HOC extends React.pureComponent {
   		state: { visible: false };
   		handleOpen = () => { setState({ visible: true })}
   		handleClose = () => { setState({ visible: false })}
   		
   		render () {
   			return <WrapComponent 
   							onOpen={hanldeOpen}
   							onClose={handleClose}
   							visible={visible}
   							{...this.props}
   							/>
   		}					
   	} 
   	return HOC;
   }
   
   // FunctionComponent也可以使用HOC
   const withNothing = Component => ({ ...props }) => {
   	const data = useFetch(url);
   	<Component data={data} {...props} />
   };
   ```

2. http缓存

3. typescript

    - 枚举编译成es5，enum和const的区别

      

    - nerver: 一个永远不会发生的类型

      一个从来不会有返回值的函数： while(true) {}

      一个总是会抛出错误的函数 function foo () { throw new Error('test')}. 

##### 三面

1. 性能优化
2. 埋点
3. MultiInput的实现

##### 四面

1. 虚拟列表
2. 前端埋点



#### 美团（点评）

##### 一面

1. Http2/3

2. 优点和技术点

3. 项目的难点

4. 组件抽象的理解

5. 什么是pwa

   真的不知道

6. 项目工程化的理解

   CI/CD

7. 1或2的楼层问题（动态规划）

   ```
   const test = n => {
   	if (n <= 1) {
   		return n;
   	}
   	const dp = [1];
   	for (let i = 1; i < n; i++) {
   		dp[i] = dp[i - 1] + (dp[i - 2] || 1);
   	}
   	return dp[n - 1];
   }
   ```

8. 正则表达式实现中划线改变成驼峰的写法

   // ab-ter => abTer

   ```
   // 考察捕获的知识和replace的API
   const convertStr = (str) => {
   	if (!str) {
   		return;
   	}
   	return replace(/\-([a-z]{1})/, $1 => $1[1] ? '' : $1[1].toUpperCase());
   }
   ```

##### 二面

项目

埋点

性能分析和性能评估

##### 三面

项目(项目架构)

难点

关注技术



#### 头条（教育）

##### 一面

1. 性能分析

2. 项目中的点

3. flat（原数组）

   ```
   const flat = arr => {
       const self = list => {
           for (let i = 0; i < list.length; ) {
               if (Array.isArray(list[i])) {
                   const subList = self(list[i]);
                   list.splice(i, 1, ...subList);
                   i += subList.length;
               } else {
                   i++;
               }
           }
           return list;
       }
       return self(arr);
   }
   ```

   

4. 实现控制并发量的工厂函数createFetchFactory

  ```
   const proxyFetch = createFetchFactory(2)

   proxyFetch('/v1/test/name') 

   proxyFetch('/v1/test/age') 

   proxyFetch('/v1/test/sexy') 
   ```

   ```
   var fetch = url => new Promise((resolve, reject) => {
       setTimeout(() => { 
           resolve(url);
       }, 2000);
   })
   var createFetchFactory = count => {
       let urls = [];
       let current = 0;
       const self = url => {
           return new Promise((resolve, reject) => {
               if (current >= count) {
                   urls.unshift({
                       url,
                       resolve,
                   })
               } else {
                   current++;
                   fetch(url).then(res => {
                       resolve(res);
                       current--;
                       const pop = urls.pop();
                       if (!pop) return;
                       self(pop.url).then(res => pop.resolve(res))
                   })
               }
           })
       }
       
       return self;
   }
   
   var proxyFetch = createFetchFactory(2);
   
   proxyFetch('/v1/test/name').then(res => console.log('one: ', `${res}-${performance.now()}`))
   proxyFetch('/v1/test/age').then(res => console.log('two: ', `${res}-${performance.now()}`))
   proxyFetch('/v1/test/sexy').then(res => console.log('three: ', `${res}-${performance.now()}`))
   proxyFetch('/v1/test/body').then(res => console.log('four: ', `${res}-${performance.now()}`))
   proxyFetch('/v1/test/bra').then(res => console.log('five: ', `${res}-${performance.now()}`))
   ```

5. react实现一个editable组件

   

#### 二面

1. 性能优化

2. 项目

3. webpack的tree-shaking

   https://juejin.cn/post/6844903544756109319

4. react的虚拟dom

5. react的setState: https://github.com/Advanced-Frontend/Daily-Interview-Question/issues/17

   - 如果是在react事件触发的setState，不会同步更新this.state

   - 除此之外（通过addEventListener或着setTimeout/setInterval）会同步执行this.state

     原理：在React的setState函数实现中，会根据一个变量isBatchingUpdates判断是直接更新this.state还是放到队列中回头再说，而isBatchingUpdates默认是false，也就表示setState会同步更新this.state，但是，**有一个函数batchedUpdates，这个函数会把isBatchingUpdates修改为true，而当React在调用事件处理函数之前就会调用这个batchedUpdates，造成的后果，就是由React控制的事件处理过程setState不会同步更新this.state**（不是真正的同步异步）

     可以通过setState的callback参数同步获取this.state的值

6. 请求并发而且可以取消

7. 最大公共子串

   ```
   var commonStr = (str1, str2) => {
       const m = str1.length;
       const n = str2.length;
       const dp = Array.from({length: m + 1}).map(() => new Array(n + 1).fill(0));
       let res = 0;
   
       for (let i = 1; i <= m; i++) {
           for (let j = 1; j <= n; j++) {
               if (str1[i - 1] === str2[j - 1]) {
                   dp[i][j] = dp[i - 1][j - 1] + 1;
                   res = Math.max(res, dp[i][j])
               } else {
                   dp[i][j] = 0;
               }
           }
       }
   
       return res;
   }
   
   console.log(commonStr('hundan', 'haodanuuh'))
   ```

#### 三面

1. 项目难点

2. 项目贡献

3. 项目优化

4. 性能检测指标

5. 重绘与回流

6. 感兴趣的方向

7. 发展目标

8. ssr/nsr/csr

9. 微前端

10. 第二大的数

    ```
    var getSecondNum = arr => {
        if (!arr || arr.length <= 1) {
            return arr;
        }
        let max = -Infinity;
        let second = -Infinity;
        for(const item of arr) {
            if (item <= second) {
                continue;
            }
            if (item > max) {
                second = max;
                max = item;
                continue;
            }
            second = item;
        }
        return second;
    }
    
    console.log(getSecondNum([1, 2, 3, 4]));
    ```

#### 四面

1. 项目难点
2. 项目优化
3. 擅长的技术点
4. 职业规划
5. babel插件的解法
6. 团队的贡献
7. 埋点


