## sessionStorage

主要用于客户端的持久化数据存储，分为三种类型：GlobalStorage、LocalStorage 和 SessionStorage

```
globalStorage['developer.mozilla.org'].username = "John"; 
localStorage.username = "John"; 
sessionStorage.username = "John"; 
sessionStorage.setItem("username", "John");
```
globalStorage: 可以跨域存取数据。
localStorage: 主要针对同一个域下面数据的存取。
sessionStorage: 其生命周期为一个 session，刷新标签页时数据保留，但是当标签页关闭时，sessionStorage 内存储的数据会消失。