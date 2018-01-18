##ES6数值方法
1. Number.isFinite()  //检测是否非无穷  
   Number.isNaN()  
   **important**  
   这两个方法只对数值有效，所有非数值一律返回false
   
   ```
   Number.isNaN(NaN);  //true
   Number.isNaN('NaN');  //false
   isNaN(NaN);   //true
   isNaN('NaN');    //true
   ```
2. ES6