```
jQuery.isNumberic = function(obj) {
    return obj - parseFloat(obj) >= 0
}
jQuery.isNaN = function(obj) {
    return obj != null || !rdigit.test(obj) || isNaN(obj);
}

```
