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

### 字节跳动 Tiktok
#### 一面
- 请介绍下http缓存机制？
- cookie，localStorage，sessionStorage之间的区别？
- cookie都有哪些字段，http-only的作用，secure是什么作用？
- cookie中为什么要设置domain？有什么好处？
- 浏览器script标签的async和defer有什么区别？
- ssr中的renderToString怎么解决阻塞问题，renderToString和
- ssr中的hydrate是干嘛的，和render的区别是什么?
- ssr中数据同构的处理流程
- 编程题：es6写个发布订阅模式
```
// 1. Support subscribing to events. 
emitter = new Emitter (); 
sub = emitter.subscribe('event_name', callback); // subscribe returns a subscription object
sub2 = emitter.subscribe('event_name', callback2);  // support multiple subscribing

// 2. Support emitting events. 
// This particular example should lead to the `callback` above being invoked with `foo` and `bar` as parameters. 
emitter.emit('event_name', foo, bar); 

// 3. Support unsubscribing existing subscriptions by releasing them. 
sub.release(); // `sub` is the reference returned by `subscribe` above 
```
#### 二面
- 编程题： 压缩字符串
```
// "aaaaaaabbbbbbccccceee" => a7b6c5e3
// "aaaabbaaa" => a4b2a3

function transformStr1(str) {
    if (!str) return "";
    var list = [];
    var last = 0;
    var len = str.length;
    for (var i = 0; i <= len; i++) {
        if (i > 0 && str[i] !== str[i - 1]) {
            list.push(str[i - 1]);
            list.push(i - (last));
            last = i;
        }
    }
    return list.join("");
}

var res = transformStr1("aaaaaabbbbbcccceee");
console.log(res);

var strStr = function (haystack, needle) {
    var obj = haystack.split("").reduce((res, val, index) => {
        if (!res[val]) {
            res[val] = index;
        }
        return res;
    }, {});
    return obj[needle[0]] || 0;
};

const res = strStr("hello", "ll");
console.log("res", res);
```
- 编程题：格式化日期「YYYY-MM-DD hh:mm:ss」
```
// format(new Date)
// 2021-06-23 22:01:11
function format(date, str) {
    const year = date.getFullYear();
    const month = date.getMonth();
    const day = date.getDay();
    const hour = date.getHours();
    const minite = date.getMinutes();
    const second = date.getSeconds();

    const formatMap = {
        "YYYY": year,
        "MM": addFixNumber(month),
        "DD": addFixNumber(day),
        "HH": addFixNumber(hour),
        "mm": addFixNumber(minite),
        "ss": addFixNumber(second)
    };

    const keys = Object.keys(formatMap);
    const len = str.length;
    for (var i = 0; i < keys.length; i++) {
        const idx = str.indexOf(keys[i]);
        console.log("str keys[i] idx", str, keys[i], idx);
        if (idx > -1) {
            const strLen = keys[i].length;
            if (idx == 0) {
                str = formatMap[keys[i]] + str.slice(i + strLen, len);
            } else {
                str = str.slice(0, idx) + formatMap[keys[i]] + str.slice(idx + strLen, len);
            }
            console.log("format after str", str);
        }
    }

    return str;
}

const res = format(new Date(), "YYYY-MM-DD HH:mm:ss");
console.log("res", res);
```
#### 三面
- 怎么样优化长列表的性能，如果有一个10w条数据的长列表，怎么让列表滑动不卡顿?
- 编程题： 给定一个字符串，请找出其中不含有重复字符的 "最长子串" 的长度。
```
// 样例
// - 输入: "abcabcbb"，输出: 3
//   - 解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
// - 输入: "bbbbb"，输出: 1
//   - 解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
// - 输入: "pwwkew"，输出: 3
//   - 解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
// - 输入: "dvdf"，输出: 3
//   - 解释: 因为无重复字符的最长子串是 "vdf"，所以其长度为 3。
// - 输入: "asjrgapa"，输出: 6
//   - 解释: 因为无重复字符的最长子串是 "sjrgap"，所以其长度为 6。
// - 输入: "aabaab!bb"，输出: 3
//   - 解释: 因为无重复字符的最长子串是 "ab!"，所以其长度为 3。
// - 输入: "abcb"，输出: 3
//   - 解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
// - 输入: "asljlj"，输出: 4
//   - 解释: 因为无重复字符的最长子串是 "aslj"，所以其长度为 4。
// - 输入: "qwnfenpglqdq"，输出: 8
//   - 解释: 因为无重复字符的最长子串是 "fenpglqd"，所以其长度为 8。

// 代码实现，仅供参考
function findMaxSubStrLen(str) {
    var start = 0;
    var end = 1;
    var maxLen = 0;

    while (end <= str.length) {
        var idx = str.slice(start, end).indexOf(str[end]);
        if (idx > -1) {
            start += idx + 1;
        }
        end++;
        maxLen = Math.max(end - start, maxLen);
    }
    return maxLen;
}
```
- 编程题：找出给定数字组合里下一个比它大的数
```
// 比如给定一个数 1234， 输出 1243；
// 输入1342，输出1423
// 输入12543，输出13245

// 代码实现，仅供参考
function findNextNumber(str) {
    if (str.length <= 1) return str;
    var pointer = str.length - 1;
    if (pointer > 0) {
        var subStr = str.slice(-pointer);
        var max = Math.max(subStr.slice(1).split(""));
        if (max <= subStr[0]) {
            p--;
        } else {
            var idx = subStr.slice(1).split("").reduce((res, val) => {
                if
            }, 0);
        }
    }
}

const res = findNextNumber(12543);
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
#### 二面
- 编程题：求孤岛的数量
```
Description
Given a 2D array of integer describing an area of an ocean: 0 means water and 1 means land. Lands are connected if they’re 4-connected (connected via up / down / left / right) Count the number of islands in the area.

Sample Input
0000000000
0110001100
0010001000
0000000100
0000000000
Sample Output
3

[]

const data = [
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
    [0, 1, 1, 0, 0, 0, 1, 1, 0, 0],
    [0, 0, 1, 0, 0, 0, 1, 0, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 1, 0, 0],
    [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
];

function getIslandCount(arr) {

    const direction = [
        [0, -1], // left
        [0, 1],  // right
        [-1, 0], // up
        [1, 0],  // down
    ];

    // 是否已经访问过
    let unVisitedArr = [];

    if (arr.length === 0) return 0;

    for (var i = 0; i < arr.length - 1; i++) {
        unVisitedArr[i] = [];
        for (var j = 0; j < arr[i].length; j++) {
            unVisitedArr[i][j] = true;
        }
    }

    let count = 0;
    for (var i = 0; i < arr.length; i++) {
        for (var j = 0; j < arr[i].length; j++) {
            if (arr[i][j] === 1 && unVisitedArr[i][j]) {
                count++;
                unVisitedArr[i][j] = false;
                const current = [i, j];
                markLand(arr, direction, current, unVisitedArr);
            }
        }
    }

    return count;
}

function markLand(arr, direction, current, unVisitedArr) {
    console.log("current", current);
    const [i, j] = current;
    unVisitedArr[i][j] = false;
    for (var m = 0; m < direction.length; m++) {
        const [row, col] = direction[m];
        if (arr[i + row][j + col] === 1 && unVisitedArr[i + row][j + col]) {
            markLand(arr, direction, [i + row, j + col], unVisitedArr);
        }
    }
}

console.log(getIslandCount(data)); // 3
```

### 拼多多
#### 一面
- 埋点上报怎么手机代码中异步处理的报错？
- 简单介绍下flex弹性布局，flex的三个属性分别表示什么？
- 浏览器的js事件循环机制？
```
// 代码块
```
- 函数的防抖和节流的原理是什么？
- onload和contentloaded的区别是什么？
- 怎么监听页面上的js执行报错？
- 大屏自适应怎么处理？
- react-intl国际化的原理是什么？
- 实现一个数组拍平的函数？
- async和await的区别是什么？分别使用在什么场景？
```
// 实现一个 flat 函数，函数的作用是可以拍平一个数组，如 flat([1, [2, [3,4], [5]]]) = [1,2,3,4,5]
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
#### 二面
- 编程题： 实现一个链表的反转？
```
// 1 -> 2 -> 3 -> 4 -> 5
// 反转: 5 -> 4 -> 3 -> 2 -> 1
function reverseNodeList(node) {
        let prev = null;
        let cur = node;

        while (cur !== null) {
            const next = cur.next;
            cur.next = prev === null ? null : prev;
            prev = cur;
            cur = next;
        }

        return prev;
    }
```
- 编程题： 实现一个递归回文子串的判断？
```
// "abcba"  true
// "asfssfde"  false
function isTraceStr1(str) {
    var start = 0;
    var end = str.split('').length - 1;

    if (str.split("").length <= 2 && str[start] === str[end]) {
        return 1;
    }

    if (str[start] === str[end]) {
        return isTraceStr1(str.slice(1, end));
    }

    return 0;
}
```
- 项目细节

### 阿里淘特
#### 一面
- 编程题：实现一对querystring的转换函数parse和stringify
```
/**
 * 简单实现一个QueryString，具有parse和stringify的能力。
 * 
 * parse，用于把一个URL查询字符串解析成一个键值对的集合。
 * 输入：查询字符串 'foo=bar&abc=xyz&abc=123'
 * 输出：一个键值对的对象
 * {
 *   foo: 'bar',
 *   abc: ['xyz', '123'],
 * }
 * 
 * stringify，相反的，用于序列化给定对象的自身属性，生成URL查询字符串。
 * 输入：一个键值对的对象
 * {
 *   foo: 'bar',
 *   abc: ['xyz', '123'],
 * }
 * 输出：查询字符串 'foo=bar&abc=xyz&abc=123'
 *
 * 测试代码
 * QueryString.parse('foo=bar&abc=xyz&abc=123');
 * QueryString.stringify({ foo: 'bar', abc: ['xyz', '123'], });
 */

// 代码实现, 仅供参考
 const QueryString = {
    parse(str) {
        var pairs = str.split('&');
        var obj = {};
        pairs.forEach(pair => {
            const [key, value] = pair.split("=");
            if (obj[key]) {
                if (typeof obj[key] === "string") {
                    obj[key] = [obj[key], value];
                } else {
                    obj[key].push(value);
                }
            } else {
                obj[key] = value;
            }
        });
        return obj;
    },
    stringify(obj) {
        var strList = [];
        Object.keys(obj).forEach(key => {
            if (typeof obj[key] === "string") {
                strList.push(`${key}=${obj[key]}`);
            } else {
                obj[key].forEach(val => {
                    strList.push(`${key}=${val}`);
                });
            }
        });
        return strList.join("&");
    }
}
```
- 编程题：实现一个版本比较函数
```
/**
 * 说明：实现一个方法，用于比较两个版本号（version1、version2），
 * 如果version1 > version2，返回1；如果version1 < version2，返回-1，其他情况返回0。
 * 版本号规则`x.y.z`，xyz均为大于等于0的整数，至少有x位。
 *
 * 示例：
 * compareVersion('0.1', '1.1.1'); // 返回-1
 * compareVersion('13.37', '1.2 '); // 返回1
 * compareVersion('1.1', '1.1.0'); // 返回0
 */

// 代码实现, 仅供参考
function compareVersion(v1, v2) {
    var v1s = v1.split(".");
    var v2s = v2.split(".");
    for (var i = 0; i < v1s.length; i++) {
        if (v1s[i] > v2s[i]) {
            return 1;
        } else if (v1s[i] == v2s[i]) {
            continue;
        } else {
            return -1;
        }
    }
    return 0;
}
```
- 编程题： 打家劫舍 - 求抢到的最大财宝值
```
/**
 * 假设你是一个专业的劫匪，你计划去打劫一条街上的家舍，每家有一定数量的钱财，
 * 但相邻两家有一个彼此连接的安全系统，一旦相邻两家在同一晚被打劫，那么这个安全系统就会自动报警。
 * 
 * 给你一个由非负整数组成的数组，用来代表每家的钱财，在不让安全系统自动报警的前提下，
 * 求你能打劫到的钱财的最大数量。
 [1,0,2,3,0,5,0,2,1]
 * 
 * 比如 [2, 0, 0, 4, 5]，能打劫到的最大钱财是7
 */
// 对于 [2, 0, 0, 4, 5]，能打劫到的最大钱财是7

// 代码实现, 仅供参考
var statusList = arr.forEach(item => true);

function getMaxValue(arr, statusList) {
  	// 找到最大值位置
  	var maxIdx = 0;
  	if(!statusList[0]) {
    	arr.forEach((item, index) => {
        	if(statusList[index]) {
              maxIdx = index;
              break;
            }
        });
    }
  	arr.forEach((item, index) => {
    	if(item > arr[maxIdx] && statusList[index]) {
        	maxIdx = index;
        }
    });
  
  	// 标记不可计算数据
  	statusList[maxIdx] = false;
  	if(maxIdx > 0) {
    	statusList[maxIdx-1] = false;
    }
  	if(maxIdx < arr.length-1) {
    	statusList[maxIdx+1] = false;
    }
  
  	// 剩下数据找最大值
  	return [maxIdx, ...getMaxValue(arr, statusList)];
}
```
#### 二面
- 项目经历
- 基础问题

### 滴滴国际化
#### 一面
- 有用过哪些数据可视化的框架？原理是什么？
- 怎么考虑一个项目的选型是否需要node层？
- reduxe的原理是什么，有什么缺点？
- webpack的代码处理流程是怎样的？
- webpack5有哪些新特性？
- react diff的更新机制是什么？
- react fiber的工作原理？解决了什么问题？
- 怎么在纯js代码中使用redux?
- typescript中的接口和泛型怎么理解？
- 项目中有用过websocket的么？如果连接中断了要怎么处理？

-------------- 持续更新中 ---------------------
### 快手电商
#### 一面

#### 二面

### 微软bing
#### 一面

### shopee seller
#### 一面

#### 二面

### 商汤教育
#### 一面
#### 二面

