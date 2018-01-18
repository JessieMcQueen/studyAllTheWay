#ES6 类
1. Object.assign
2. ES6类内部定义的方法，是不可枚举的枚举方法 
	Object.keys()
	Object.getOwnPropertyNames()
3. hasOwnProperty
 
	```
	class Point {
		constructor (x, y) {
			this.x = x;
			this.y = y;
		}
		toString() {
			return '(' + this.x + ',' + this.y + ')';
		}
	}
	```
	
	```
	var point = new Point(2, 3);
	point.toString();
	point,hasOwnProperty('x');   // true
	point,hasOwnProperty('y');   // true
	point,hasOwnProperty('toString');   // false
	```
4. 从子类上获取父类

	```
	Object.getPrototypeOf(子类) === 父类；
	```
5. ES6中，可计算属性名，可以在文字形式中使用[]包裹一个表达式来当做属性名
	
	```
	let Object = {
		[a + "b"]: "hello"
	};
	``` 