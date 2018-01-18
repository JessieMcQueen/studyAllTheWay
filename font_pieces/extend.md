##less extend
1. 通过使用:extend 选择器在一个选择器中扩展其他选择器样式

	```
	.style:extend(.container, .img)
	{
	  background: #BF70A5;
	}
	.container {
	  font-style: italic;
	}
	.img{
	   font-size: 30px;
	 }
	```
	编译后
	
	```
	.style {
	  background: #BF70A5;
	}
	.container,
	.style {
	  font-style: italic;
	}
	.img,
	.style {
	  font-size: 30px;
	}
	```
2. jQuery $.extend(), 将两个或更多对象的内容合并到第一个对象。

	```
	var object = $.extend({}, object1, object2);
	```
	
	在默认情况下，通过$.extend()合并操作不是递归的;如果第一个对象的属性本身是一个对象或数组，那么它将完全用第二个对象相同的key重写一个属性。这些值不会被合并。可以通过检查下面例子中 banana 的值，就可以了解这一点。然而，如果将 true 作为该函数的第一个参数，那么会在对象上进行递归的合并。