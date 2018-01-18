##异步加载图片

```
function loadImageAsync(url) {
	return new Promise(resolve, reject) {
		let image = new Image();
		image.onload() = function() {
			resolve(image);
		}
		image.onerror() = function() {
			reject(new Error('could not load image at' + url));
		}
		image.src = url;
	}
}
```
##Promise实现Ajax操作

```
let getJSON = function(url) {
	let promise = new Promise(resolve, reject) {
		let client = new XMLHttpRequest();
		client.open("GET", url);
		client.onreadystatechange = handler;
		client.responseType = "json";
		client.sendRequestHeader("Accept", "application/json");
		client.send();
		
		function handler() {
			if (this.readyState!== 4) {
				return;
			}
			if (this.state == 200) {
				resolve(this.response);
			} else {
				reject(new Error(this.statusText));
			}
		}
	}
	return promise;
};

getJSON("/posts.json").then(function(json) {
	console.log('Contents' + json);
}, function(error) {
	console.error('出错了' + error);
});
```

##Javescript实现Ajax

```
let xhr = createXHR()；
xhr.onreadystatechange = function() {
	if (xhr.readyState == 4) {
		if (xhr.state == 200) {
			alert(xhr.responseText);
		} else {
			alert("Response is not success:" + xhr.status);
		}
	}
};
xhr.open("get", url, true);
xhr.send();
```
其中，XHR对象的readyState属性表示请求/响应过程的当前活动阶段，这个属性的值如下  
0-未初始化，尚未调用open()方法；  
1-启动，调用了open()方法，未调用send()方法；  
2-发送，已经调用了send()方法，未接收到响应；  
3-接收，已经接收到部分响应数据；  
4-完成，已经接收到全部响应数据；  
