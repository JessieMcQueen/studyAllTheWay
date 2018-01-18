##Javascript

1. 最好不要在块内声明函数

```
let a = true;
if (a) {
	function foo() {
		console.log(111);
	}
} else {
	finction foo() {		
		console.log(111);
	}
}
```