使用时，先引入其他的库，然后引入jQuery, 调用$.noConflict()进行改名
```
var window = this,
    undefined,
    _jQuery = window,jQuery,
    _$ = window.$,
    jQuery = window.jQuery = window.$ = function (selector, context) {
        return new jQuery.fn.init(selector, context);
    }
jQuery.extend({
    noConflict: function(deep) {
        window.$ = _$;
        if (deep) {
            window.jQuery = _jQuery;
        }
        return jQuery;
    }
});
```