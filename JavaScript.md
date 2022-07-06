
### day6:
题目：[1071. 字符串的最大公因子](https://leetcode.cn/problems/greatest-common-divisor-of-strings/)

对于字符串 s 和 t，只有在 s = t + ... + t（t 自身连接 1 次或多次）时，我们才认定 “t 能除尽 s”。

给定两个字符串 str1 和 str2 。返回 最长字符串 x，要求满足 x 能除尽 str1 且 X 能除尽 str2 。
```
示例 1：
输入：str1 = "ABCABC", str2 = "ABC"
输出："ABC"
```
```js
/**
 * @param {string} str1
 * @param {string} str2
 * @return {string}
 */
var gcdOfStrings = function(str1, str2) {
    if (str1 + str2 !== str2 + str1) {
        return ''
    }
    let len = gcd(str1.length, str2.length)
    return str1.substring(0, len)
};

let gcd = (a, b) => (b === 0 ? a : gcd(b, a % b))
```

解析：如果str1、str2有最大公因子str，那str1就是n个str的拼接，str2就是m个str的拼接，那str1 + str2 === str2 + str1,反之则无解。
在确定有解的情况下，那就是str1.length 和str2.length的最大公约数就是str.length.


### day5:

题目：有n个函数，执行顺序为后面函数依赖上次函数的返回值，用同步和异步模拟执行对应的函数

例如：初始值为1，先加20，后减4，接着\*5，随后\/ 2,求最终的结果(42.5)

同步函数为：

 ```js
 const add = x => x + 20;
 const subtraction = x => x - 4;
 const multiply = x => x * 5;
 const division = x => x / 2;
 const pipeFn = (...args) => {
   return args.reduce((preFn, curFn) => {
      return (...arg) => {
         const result = preFn(...arg);
         return curFn(result);
      } 
   });
  };
  const reduceFn = pipeFn(add, subtraction, multiply, division);
  reduceFn(1)
 ```
 
 异步函数
 
 ```js
 const asyncFn = async (x) => {
  return new Promise(resolve => { // 用promise模拟异步
     setTimeout(() => {
       resolve(x);
     }, Math.random() * 1000); // 使用setTimeout及随机数时间模式后端随机时间后返回数据
  })
 }
 const add = async x => await asyncFn(x + 20);
 const subtraction = async x => await asyncFn(x - 4);
 const multiply = async x => await asyncFn(x * 5);
 const division = async x => await asyncFn(x / 2);
 const pipeFn = (...args) => {
   return args.reduce((preFn, curFn) => {
      return async (...arg) => {
         const result = await preFn(...arg);
         return curFn(result);
      } 
   });
  };
  const reduceFn = pipeFn(add, subtraction, multiply, division);
  await reduceFn(1)
 ```
 
 ### day4:

 ```js
 let arr = [12,23];
 arr[20] = [45];
 let a = arr.filter(item => item === undefined);
 let b = arr.filter(item => item == undefined);
 ```
 a  // []
 b // []
 
 解析：ECMAScript版本不同对应方法行为不同的问题，ES6之前的遍历方法都会跳过数组未赋值过的空位，但是ES6的for of 方法不会跳过;
 
 ### day3:

 ```js
 let a = b = 'out';
 (function(){let a = b = 'in';})()
 ```
 a  // 'out'
 b // 'in'
 
 解析：连等赋值从右往左执行，先 b = 'in' ;再let a = b;b没有声明，会被一层一层覆盖掉，最终全局变量为'in';
 
 ### day2:

 ```js
 var a = {a: 1};
 var b = a;
 a.n = a = {n: 2};
 ```
 a = {n: 2}
 
 b = {a: 1,n: {n: 2}}
 
 赋值为地址赋值；先给a赋值为对象{a:1},接着将地址给b,a.n = a;a访问的是b的地址；
 从左到右依次赋值，也可以直接b = a;a.n = {n: 2};a = {n: 2};

### day1:

 ```js
 var length = 10;
 
 function fn() {
   console.log(this.length);
 }
 var obj = {
   length: 5,
   method: function (fn) {
     fn();
     arguments[0]();
   }
 }
 obj.method(fn, 1);
 ```
 >
 [day1_issure](https://github.com/nanajs/Question/issues/2)
