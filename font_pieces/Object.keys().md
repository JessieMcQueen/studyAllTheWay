1. Object.keys()
    返回一个由给定对象的自身可枚举属性组成的数组，数组中属性名的排列顺序和使用for...in循环遍历该对象时返回的顺序一致  
    区别是for...
    pollyfill中兼容Object.keys()  
    ```
    if (!Object.keys) {
        Object.keys = (fucntion(){
            let hasOwnProperty = Object.prototype.hasOwnProperty,
                hasDontEnumBug = !({toString: null}).propertyISEnumerable('toString'),
                dontEnums = [
                    'toString',
                    'toLocalString',
                    'valueOf',
                    'hasOwnProperty',
                    'isPrototypeOf',
                    'propertyIsEnumberale',
                    'constructor'
                ],
                dontEumsLength = dontEnums.length;
        
            return function(obj) {
                if (type obj !== 'object' && typeof obj != 'function' || obj == null) throw TypeError('Object.keys called on non-object');
                let result = [];
                for (let prop in obj) {
                    if (hasOwnProperty.call(obj, prop)) result.push(prop);
                }
                if (hasDontEnumBug) {
                    for (var i=0; i < dontEnumsLength; i++) {
                        if (hasOwnProperty.call(obj, dontEnums[i]))result.push(dontEnums[i]);
                    }
                }
                return result;
            }
        })();
    }
    ```