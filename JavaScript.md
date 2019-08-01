### day2:

 ```js
 var a = {a: 1};
 var b = a;
 a.n = a = {n: 2};
 ```
 a = {n: 2}
 
 b = {a: 1,n: {n: 2}}
 
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
