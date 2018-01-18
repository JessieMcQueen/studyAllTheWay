##eval
eval接收一个参数，相当于这个参数本来就书写在此，而不是通过传参到此

```
function foo(str, a) {
	eval(str);
	console.log(a, b);  // 1 3
}
var b = 2;
foo("var b = 3;", 1);
```

等价于

```
function foo(a) {
	var b = 3;
	console.log(a, b);  // 1 3
}
var b = 2;
foo(1);
```