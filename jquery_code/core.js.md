参考 http://www.cnblogs.com/aaronjs/p/3278578.html

1. 空格正则

    ```
    rtrim = /^[\s\uFEFF\xA0]+|[\s\uFEFF\xA0]+$/g
    ```
    匹配不换行的空格代码，即nbsp
2. jQuery
    ```
    jQuery = function(selector, context) {
        return new jQuery.fn.init(selector, context);
    }
    ```
    ![image](http://note.youdao.com/noteshare?id=cdd4c8b6f13ad6082e322931d3fa04c4)
    访问jQuery类原型上的属性和方法
    ```
    jQuery.fn.init.prototype = jQuery.fn;
    ```
3. 链式调用
    
    ```
    aQuery().init().name()
    // 分解
    a = aQuery();
    a.init()
    a.name()
    
    // 本质
    aQuery.prototype = {
        init: function() {
            return this;
        },
        name: function() {
            return this
        }
    }
    ```
    需要链式的方法访问this就可以了，因为返回当前实例的this,从而又可以访问自己的原型了
4. 插件接口
    ```
    jQuery.extend = jQuery.fn.extend = function() {}
    ```
    jQuery.extend 调用的时候，this是指向jQuery对象的(jQuery是函数，也是对象！)，所以这里扩展在jQuery上。  
    而jQuery.fn.extend 调用的时候，this指向fn对象，jQuery.fn 和jQuery.prototype指向同一对象，扩展fn就是扩展jQuery.prototype原型对象。  
    这里增加的是原型方法，也就是对象方法了。所以jQuery的api中提供了以上2中扩展函数。