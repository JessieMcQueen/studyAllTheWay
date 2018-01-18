#ajax 
1. serialize()
	通过序列化表单值，创建 URL 编码文本字符串
	
	```
	$('form').serialize();
	
	<form action="">
	First name: <input type="text" name="FirstName" value="Bill" /><br />
	Last name: <input type="text" name="LastName" value="Gates" /><br />
	</form>
	```
	结果：  
	FirstName=Bill&LastName=Gates
2. serializeArray()
	返回 JSON 数据结构数据  
	！！！important
	此方法返回的是 JSON 对象而非 JSON 字符串。需要使用插件或者第三方库进行字符串化操作。返回的 JSON 对象是由一个对象数组组成的，其中每个对象包含一个或两个名值对 —— name 参数和 value 参数（如果 value 不为空的话）。
3. param()
	序列化一个 key/value 对象, 数组
	
	```
	var myObject = {
	  a: {
	    one: 1, 
	    two: 2, 
	    three: 3
	  }, 
	  b: [1,2,3]
	};
	$.param(myObject);  //a%5Bone%5D=1&a%5Btwo%5D=2&a%5Bthree%5D=3&b%5B%5D=1&b%5B%5D=2&b%5B%5D=3
	decodeURIComponent($.param(myObject)); //a[one]=1&a[two]=2&a[three]=3&b[]=1&b[]=2&b[]=3
	```