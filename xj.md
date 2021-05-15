只记得手写的题目。。。
 酷家乐智力题(二面的题目面官设的场景题，忘了)
  * 有4瓶药，其中只有一瓶是毒药，我们有2只老鼠，能被毒药很快毒死。请问最少几次能把毒药试出来？ ab,bc 两次
  * 有8瓶药，其中只有一瓶是毒药，我们有三只老鼠，能被毒药很快毒死。请问最少几次能把毒药试出来？ 不会
   
pdd 
 * 写一个闭包实现的方法，选择了写防抖
 * 将两个数组排序，选择了写归并排序
 * 深拷贝
 * 智力题：闹钟的三点半，夹角多少度？ 75


* 反转单链表
* 面官是大叔感觉很关注股票，[买卖股票的最佳时机](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock/)
   
* [将有序数组转换为二叉搜索树](https://leetcode-cn.com/problems/convert-sorted-array-to-binary-search-tree/)
* [二叉树展开为链表](https://leetcode-cn.com/problems/flatten-binary-tree-to-linked-list/)  说了下思路，没让我手写，就让我走了（开心），

字节  
* 一个自定义hook，点击Increase button 加一，decrease button减一
      
* canvas，简单的实现自我介绍项目里面一个音量播放的动画 （个人项目，可能普适性不大）
* vue 观察者模式我说不会，面官说那写双向绑定

  字节的公共题库？和彭老板两题撞题
 * 最大公共子串

        ```js
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
        ```

  * 实现控制并发量的工厂函数createFetchFactory
  ```js
   const proxyFetch = createFetchFactory(2)

   proxyFetch('/v1/test/name') 

   proxyFetch('/v1/test/age') 

   proxyFetch('/v1/test/sexy') 

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
