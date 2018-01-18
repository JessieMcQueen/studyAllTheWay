##jquery深拷贝

    jQuery.extend( [deep ], target, object1 [, objectN ] )
    
    jQuery.extend = jQuery.fn.extend = function () {
        let options, name, src, copy, copyIsArray, clone, 
            target = argument[0] || {},
            i = 1,
            length = argument.length,
            deep = false; // 默认不是深拷贝
        if (typeof target === 'boolean') {
            deep = target;
            target argument[1] || {};
            i = 2;
        }    
    
        if (typeof target !== 'object' && !jQuery.isFunction(target)) {
            //jQuery.isFunction() 用于判断指定参数是否为函数
            target = {};
        }
        if (length === i) {
            target = this;
            --i;
        }
        for (; i < length; i++) {
            if ((options = arguments[i])) {
                // options为源对象
                for (name in options) {
                    // 遍历源对象的属性名
                    src = target[name];
                    copy = options[name];
                    if (target === copy) {
                        continue;
                    }
    
                }
            }
            if (deep && copy && (jQuery.isPlainObject(copy) || (copyIsArray = jQuery.isArray(copy))) {
                // jQuery.isPlainObject()，该对象是通过"{}"或"new Object"创建的。
                // jQuery.isArray(), 判断指定参数是否是一个数组。
                if (copyIsArray) {
                    copyIsArray = false;
                    clone = src && jQuery.isArray(src) ? src : [];
                } else {
                    clone = src && jQuery.isPlainObject(src) ? src : {};
                }
                // 遍历拷贝
                target[name] = jQuery.extend(deep, clone, copy);
            } else if (copy !== 'undefined') {
                target[name] = copy;
            }
        }
        return target;
    }