##ES6扩展正则
1. RegExp构造函数

	```
	let reg = new RegExp(/xyz/i);
	// 等价于
	let reg = /xyz/i;
	```
2. 字符串的4个方法可以使用正则表达式 
 
	```
	match()
	replace()
	search()  // search() 方法用于检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串。
	split()
	eg:
	let str="Visit W3School!";
	str.search(/W#School);
	```
3. u修饰符，含义为Unicode模式
4. y修饰符 ？？ sticky属性
5. flags属性
	```
	source 返回正则表达式的正文
	flags 返回正则表达式的修饰符
	eg:
	/abc/ig.source   "abc"
	/abc/ig.flags    "gi"
	```
