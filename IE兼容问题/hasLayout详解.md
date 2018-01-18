## hasLayout详解
###定义
　　haslayout是IE7-浏览器的特有属性。hasLayout是一种只读属性，有两种状态：true或false。当其为true时，代表该元素有自己的布局，否则代表该元素的布局继承于父元素。
　　[注意]通过element.currentStyle.hasLayout可以得出当前元素的hasLayout情况
###触发条件
CSS属性
　　可以触发hasLayout的有如下CSS属性：
　　【1】display:inline-block
　　【2】height/width:除了auto
　　【3】float:left/right
　　【4】position:absolute
　　【5】writing-mode(IE专有属性，设置文本的垂直显示):tb-rl
　　【6】zoom(IE专有属性，设置或检索对象的缩放比例):除了normal

 【IE7专有的触发hasLayout的CSS属性】
　　【1】min-height/max-height/min-width/max-width:除none
　　【2】overflow\overflow-x\overflow-y:除visible
　　【3】position:fixed
### 用途
    来源 https://www.cnblogs.com/xiaohuochai/p/4845314.html

## zoom:1
Zoom属性是IE浏览器的专有属性，它可以设置或检索对象的缩放比例
此属性对于 currentStyle 对象而言是只读的，对于其他对象而言是可读写的。

当设置了zoom的值之后，所设置的元素就会就会扩大或者缩小，高度宽度就会重新计算了，这里一旦改变zoom值时其实也会发生重新渲染，运用这个原理，也就解决了ie下子元素浮动时候父元素不随着自动扩大的问题。    