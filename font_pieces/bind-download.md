##bind 

```
// 下载文件
this.$el.delegate('.js-download-schedule', 'click', this. downloadFile.bind(this));

方法1：
window.open(url);
方法2：
downloadFile() {
    let url = `/order/orderdatedown?orderId=${this.orderInfo.orderId}`;
    try {
        let elemIF = document.createElement('iframe');
        elemIF.src = url;
        elemIF.style.display = 'none';
        document.body.appendChild(elemIF);
    } catch (e) {
	
    }
}
```