### 字节跳动 - 飞书
#### 字节一面
- 编程题
- 给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。lengthOfLongestSubstring('babcaacbd') = 4
```
function findSubString(str) {
    var start = 0;
    var subStrLen = 1;
    for (let i = 1; i < str.length + 1; i++) {
        var subStr = str.slice(start, i);
        var index = subStr.indexOf(str[i]);
        if (index > -1) {
            start = start + index + 1;
        }
        subStrLen = Math.max(subStrLen, i - start);
    }
    return subStrLen;
}

var res = findSubString("babcaacbd");
console.log("findSubString subStrLen", res);
```
- 实现一个 flat 函数，函数的作用是可以拍平一个数组，如 flat([1, [2, [3,4], [5]]]) = [1,2,3,4,5]
```
function flat(arr) {
    var list = [];
    for (let i = 0; i < arr.length; i++) {
        if (typeof arr[i] === 'number') {
            list.push(arr[i]);
        } else {
            list = list.concat(flat(arr[i]));
        }
    }
    return list;
}
```

- 定时器打印函数
```
repeatFunc("hellworld"); // 会输出 4次 helloworld, 每次间隔3秒
const repeatFunc = repeat(console.log, 4, 3000);

// 我的代码
function repeat(func, times, wait) {
    var timer = null;
    var count = 0;

    return function () {
        const context = this;
        const args = arguments;

        const func1 = function () {
            if (count === times) {
                clearTimeout(timer);
                return;
            }
            count++;
            timer = setTimeout(() => {
                func.apply(context, args);
                func1();
            }, wait)
        }
        func1();

        // for (let i = 0; i < times; i++) {
        //     setTimeout(() => {
        //         func.apply(context, args);
        //     }, wait * i);
        // }

        // timer = setInterval(() => {
        //     if (times === count) {
        //         clearInterval(timer);
        //     }
        //     func.apply(context, args);
        //     count++;
        // }, wait);
    }
}
```

- 项目中做过的基础架构工作有哪些?

- 做过哪些性能优化相关的？

- React组件中需要引入react但是没用到是为什么？

- react组件列表渲染要加key是为什么？


#### 字节二面
- 浏览器都有哪些限制？
```
同源策略跨域限制，6个并发请求限制
```
- 浏览器同时加载100个资源请求，怎么优化页面首屏的加载时间？

- http和https有什么区别？https做了什么事情？

- https怎么实现数据加密传输的？中间人有办法窃取吗？https绝对安全吗？

- 简单介绍下tcp协议？三次握手具体怎么建立连接的？

- React中`setState`更新后的流程是怎样的？

- 为什么`setTimeout`中的setState是同步执行的，不回批量更新？

- 两个人同时修改一份数据？最终结果是怎样的？A和B同时提交修改，最终结果是什么？
```
Server: Hello world
A: Hello
B: Hello world and you.
```
- 编程题，实现从二叉树中找到连续的子节点，找到了返回true, 没有的话返回false?
```
// 二叉树找连续数组
//     1
//   2  3
// 4 5 6 7
// [2, 4] true
// [2, 6] false

// 我的代码
function isContain(origin, arr) {
    const originStr = origin.toString();
    const arrStr = arr.toString();
    const res = originStr.indexOf(arrStr) > -1;
    return res;
}

function findArray(tree, arr, origin) {
    if (isContain(origin, arr)) {
        return true;
    }
    if (tree.left && tree.right) {
        return findArray(tree.left, arr, origin.concat([tree.left.val])) ||
            findArray(tree.right, arr, origin.concat([tree.right.val])) ||
            false;
    }
    return false;
}

const tree = {
    val: 1,
    left: {
        val: 2,
        left: { val: 4 },
        right: { val: 5 }
    },
    right: {
        val: 3,
        left: { val: 6 },
        right: { val: 7 }
    }
}

var res = findArray(tree, [1, 2], [tree.val]);
console.log("res", res);
```

### 携程旅游 
#### 一面
- 浏览器从输url到页面加载完成经历了什么？
- React的`Component`和`FunctionComponent`有什么区别？
- 介绍下React的生命周期函数有哪些，`getDerivedStateFronProps`都会在什么时候触发？
- 写`Component`都要注意什么，怎么做到性能优化？
- `FunctionComponent`怎么模拟`componentDidUpdate`减少组件的从新渲染呢？
- js加载解析为什么会阻塞页面的渲染？
- css动画为什么比js动画要好，为什么可以提供性能？
- React中的ref在`FunctionComponent`和`Component`分别指向什么？怎么在`FunctionComponent`使用父组件的`ref`?
- 实现一个简单的浅比较函数`isEqual(obj1, obj2)`？
```
function isEqual(obj1, obj2) {
    // 代码块
}
```
#### 二面
- 网络请求
- 项目经历
- 性能优化


### 美团一面
- `_proto_`和`prototype`分别是什么？有什么区别？

- node.js怎么解决循环引用的问题？

- 下面的等式成立吗？
```
0.1 + 0.2 === 0.3
```

- es6中新增的数据类型有哪些？ `Symbol`类型一般在什么情况下用的？

- es6的模块化和`commonJS`有什么区别和联系？

- `useState`的源码有看过吗？怎么实现的？

- webpack的热更新原理是什么？怎么实现修改保存后页面自动刷新？

- webpack打包编译时间优化怎么做的？

- 简单讲下js的事件循环？

- 进程和线程有什么区别？

- 状态码`401`和`403`分别什么意思？有什么区别？
```
https://www.cnblogs.com/adroitwolf/p/14309570.html
```
- 手写promise.all
```
Promise.all = function(promises) {
    return new Promise((resolve, reject) => {
        const results = [];
        promises.forEach((promise, index) => {
            promise.then(res => {
                results[index] = res;
                if(results.length === promises.length) {
                    resolve(results);
                }
            }, error => {
                reject(error);
            })
        });
    });
}
```

### 得物App 一二三四面
- 编程题 实现一个时间的格式化函数
```
function formatCurrentTime(format) {
    // 代码块
}
formatTime("%y-%M-%d %h:%m:%s"); // 2021-05-12 12:43:21
```
现场面的，回忆中...

### pony.ai 一面
- 编程题
```
Description
给一个长度为2<=n<=10^5的deque，每次操作取出队首两个元素，将较大的放到队尾，较小的放到队首，求第1<=m<=10^18次操作时取出的元素。

4,3,5,1,2  4,3
3,5,1,2,4  3,5
3,1,2,4,5  3,1
1,2,4,5,3  1,2
1,4,5,3,2  1,4
1,5,3,2,4  1,5
1,3,2,4,5  1,3
1,2,4,5,3  1,2

*/

// 我的代码，只表示思路还没调通过
function findMElement(list, m) {
 const resMap = {};
  let findLoopTime = false;
  const times = 0;
  let period = 0;
  
  // 找到循环位置
  while(!findLoopTime) {
   const headEl = list.slice(0, 2);
    list.push(headEl[0] > headEl[1] ? headEl[1] : headEl[0]);
    list.unshift(headEl[0] > headEl[1] ? headEl[0] : headEl[1]);
    if(resMap[headEl.toString()]) {
      period = times - resMap[headEl.toString()]
      findLoopTime = true;
      break;
    }
    resMap[headEl.toString()] = times;
    times++;
  }
  
  // 求余找到对应的位置
  let target = [];
  const rest = ((m - (times - period)) % (period));
  Object.keys(resMap).forEach((key) => {
   if(rest + times - period === resMap[key]) {
     target = resMap[key].split(",").map(item => Number(item));
    }
  });
  return target;
}
```