## Webpack

- 有哪些可以配置的参数
- loader 和 plugin 的区别
- loader 执行顺序

## ts

- 枚举有哪些特点、编译之后区别
- ts 实现继承的方式
- class 的 public 和 protected、private 区别
- interface 和 type 有什么区别
- 泛型是什么？使用场景？
- 如果某个依赖没有用 ts，如何补充该 api 的类型
- 如何将某个属性挂到全局变量上

## js

- es5 实现类的继承
- es5 实现 promise 和 promise.all
- 原型链、实现继承有哪些方式
- 事件循环题
- 实现 instanced
- this 指向：

```javascript
function Foo() {
  Foo.a = function () {
    console.log(1);
  };
  this.a = function () {
    console.log(2);
  };
}
Foo.prototype.a = function () {
  console.log(3);
};
Foo.a = function () {
  console.log(4);
};
Foo.a();
let obj = new Foo();
obj.a();
Foo.a();
```

## react

- Hooks 引入的意义？
- usecallback 用法
- useRef 和 useState 有什么区别
- Filber 做了什么优化更新
- 16 之后的 dom 结构和之前 15 的有什么区别
- diff 算法
- Context 的用法，优缺点
- 技术选型-redux 和 context 如何选择？
- Redux 的特性
- 共用组件的方式
- React.memo 的优点

## 设计

- 函数式编程是什么，有什么特点，比起其他的面向对象编程有什么优势
- 异步的引入解决了什么问题
- 用过哪些设计模式，哪个用的比较多？相比其他有什么好处？

## 编程和思路

```
给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串 s ，判断字符串是否有效。
有效字符串需满足：
● 左括号必须用相同类型的右括号闭合。
● 左括号必须以正确的顺序闭合。
示例：checkBrackets('[(])') => false; checkBrackets('[()]') => true;
```

## http

- 状态码，301、302、304
- http2
- 强制缓存和协商缓存
- 跨域
