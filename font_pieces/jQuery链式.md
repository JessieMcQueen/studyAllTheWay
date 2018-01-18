##jQuery链式操作
给当前点击元素添加mt-button-rose类， 然后移除兄弟元素的mt-button-rose类。

```
$(document).delegate('.js-day-type', 'click', function () {
    that.dayType = $(this).data('type');
    $(this).addClass('mt-button-rose').siblings().removeClass('mt-button-rose');
});
```

```
// 资源去重
resources = resources.filter(res => {
    return !that.scheduleInfo.resList[res.resId];
});
```
