### day2:

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
