## 腾讯医疗

### 一面

- 先做笔试题目，大约一小时，和吉吉的完全一样。题目是会给一个腾讯文档的链接，只能看，自己在本地写（需要录屏),写完后提交到腾讯会议的文档中。
- 笔试完聊项目以及遇到的问题。
> 开发公共包都会做哪些文档上的事情

> 脚手架升级是怎么做的，如何避免对项目的影响

> hooks的概念

## 字节抖音部门-前端安全方向

### 一面

- 自我介绍
- react fiber介绍
- react 如何做批处理更新的。如果要强制更新应该怎么做
- 给你一个项目，会从哪些方面去考虑前端工程优化
- ssr，data是怎么在服务端和浏览器之间传输的
- mongo，树结果，覆盖索引
- java，几种同步的方式，反射原理
- 算法题，类似于模拟试下match的正则匹配，给定一个字符串s和字符规律p，只包含小写字母和 '.' '*',  '.'代表一个字符， '*'代表零个或多个前一个字母 [leetcode原题](https://leetcode-cn.com/problems/regular-expression-matching/)
```js
console.log(match('aa', 'a')); // => false
console.log(match('', 'a*')); // => true
console.log(match('abc', '.*')); // => true
console.log(match('aaa', 'a*')); // => true
console.log(match('ab', 'a*b*ab')); // => true
console.log(match('mississippi', 'mis*is*p*i')); // => false
```

