## 字节部门A

### 一面

- 聊一聊项目，以及项目中遇到的问题
- 常规 `promise` 题, 就不贴了，网上很多
- 编程题
```javascript
  let str = "1+2+3+4-5-6+7";

  /**
  * 实现函数 calc, 使得 calc(str) = 6;
  */

```
- 聊了下 `var`, `let`, `const`, 顺便做了道题
```javascript
  var name = 'World!';
  (function () {
      if (typeof name === 'undefined') {
          var name = 'Jack';
          console.log('Goodbye ' + name);
      } else {
          console.log('Hello ' + name);
      }
  })();
```
- 问了下 CSS 的居中

### 二面

- 聊项目， 问为何选型 `Websocket`, 以及 `Websocket` 如何建立链接，以及状态码 
- 问是否了解 `HLS` 协议
- 问 `Https` 的握手过程，以及证书包含了什么内容
- 问性能监控的指标
- 编程题，实现 `Promisify`
```javascript
  // implements Promisify:
  // turn error first callback style to a promise style
  // error first callback style
  fs.readFile('/path/to/file.txt', 'utf-8', (err, data) => {
    if (err) {
      // handle error
    }
    console.log(data);
  });
  
  const readFileAsync = Promisify(fs.readFile);
  try {
    const data = await readFileAsync('/path/to/file.txt', 'utf-8');
  } catch (err) {
    // handle error
  }
```

## 字节部门B

### 一面

- 聊项目，问性能优化怎么做的
- `Http` 缓存
- 跨域，问的比较细，问了比如 `a.feishu.com` 到 `c.feishu.com` 等域名之间会不会产生跨域之类的问题； 以及跨域如何携带 `cookie`;
- `React` 父组件更新会触发什么，以及 `diff` 算法
- `React` 中的 `key` 有什么作用，以及 `key` 重复了会导致什么
- 编程题， 实现 `LRUCache`
- 编程题，实现 `Promise.all`

### 二面

- 聊如何做模块设计和拆分
- 聊 `PWA` 的缓存策略
- 聊性能优化有哪些手段，以及使用哪些指标，以及如何监控，以及项目有性能问题，可能是哪些原因, 要如何排查
- 问有哪些排序算法，复杂度以及稳定性
- 问 `tcp/udp` 的区别，以及分别有哪些应用
- 编程题，求两个 `dom节点` 的最近公共祖先
- 编程题
```javascript
  /**
  * 实现函数 replace，把字符串中的 'y' 以及连续的 'xz' 移除掉
  * replace('yyyy') = ''
  * replace('xxyz') = 'x'
  * replace('xxxyyyyzzz') = ''
  */
```

## 腾讯部门A

### 一面

一面是全程屏幕共享做题

- 编程题
```javascript
  /**
  * 有 str = '123abz456xyz';
  * 1. 用正则实现， 把 str 中的非数字都替换成空字符串
  * 2. 把 str 中的数字乘以2，英文都加上方括号，最终输出为 '246[a][b][c]81012[x][y][z]'
  */
```

- 编程题
```javascript
  /**
  * 用闭包实现函数 getCount，每次调用 getCount，返回的数都会加 1
  */
```

- 编程题
```javascript
  /**
   * 有数组 [1,2,3,0,4,0,5,0,7,0]
   * 请实现函数, 将数组中为 0 的项移动到数组最后，其他项的相对顺序不变
  */
```

- 编程题
```javascript
  // 有以下代码，请问如何实现 `filterA`, `filterB`, `filterC` 可以保证代码的安全性
  document.write('<a href="' + filterA(a) + '" onclick="' + filterB(b) + '">' + filterC(c) + '</a>');
```

- 给了一段 `nodejs` 代码(实在不记得代码是啥了，太长了)，问代码会产生`孤儿进程`还是`僵尸进程`,以及有什么危害

- 编程题
```javascript
  // 有如下html 和代码，问会产生什么问题，以及如何优化
  //  <ui class="list">
  //    <li class="item1">1</li>
  //    <li class="item2">2</li>
  //    <li class="item3">3</li>
  //    <li class="item4">4</li>
  //    <li class="item5">5</li>
  //  </ui>

  let liEle = document.getElementsByTagName('li');
  for (var i = 0; i < liEle.length; i++) {
    liEle[i].onclick = function() {
      alert(liEle[i].innerHTML);
    }
  }
```
- 编程题, 用 Vue 或者 React 实现一个 `Input` 组件，默认有提示 `请输入内容`, 当输入长度超过 `20` 时, 提示 `输入超长`; 并在结束输入时，提示当前的输入内容

- 给了一个图片，然后实现图片中的布局, 很常见的左侧自适应，右侧顶宽，左侧再分上下，左侧需要实现多行的文字溢出，以及整个部分有个下边框，下边框需考虑多倍屏的问题

### 二面

纯聊天， 只记得聊自动化测试怎么做的

### 三面

纯聊天
- 介绍下项目, 带同学的时候如何分工的
- 项目有什么难点
- 项目有问题如何排查
- 有没有关注什么新技术
- 对未来有什么规划
