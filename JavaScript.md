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
