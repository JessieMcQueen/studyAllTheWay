## 上下边距叠压问题
    例如一上一下两个div，上div设置margin-bottom:10px，
    下div设置margin-top:10px，结果只会让两个margin叠压在一起，
    而不会相加为20px
## margin传递问题
    IE6,7下父子级包含的时候子级的margin-top会传递给父级；
    子级的margin-top会消失
    在IE6下父级有边框的时候，子元素的margin值消失
    解决办法:触发父级的haslayout (zoom:1)
## IE6下最后一个子元素margin消失问题
    当一行子元素占有的宽度之和和父级的宽度相差超过3px,
    或者有不满行状态的时候,最后一个子元素的下margin在IE6下就会失效    
## IE6下的双边距BUG
    在IE6下，块元素有浮动和横向margin的时候，横向的margin值会被放大成两倍
    解决办法: display:inline;  
## IE6下内容撑开设置宽高
    在IE6下，内容会撑开设置好的宽高   
    例如，给固定宽度的wrap_div下放left_div、right_div两个div并浮动，
    wrap_div的宽度正好放下两个内部div(两个内部div也设置了宽度)。
    在IE6下，如果left_div或right_div内部内容宽度大于div本身宽度，
    内容就会撑开宽度让wrap_div容不下，就会发生折行。
    解决办法: 给内容计算好宽高，不要溢出
## IE6下子元素浮动问题
    在IE6下，父级下的两个子元素(块元素、未设置宽高)都浮动，
    如果两个子元素内部有块元素时，两个子元素不会内容撑开宽高，而会
    占满整行。
    解决办法:在IE6下父级下子元素浮动，如果子元素宽度需要内容撑开，
    就给子元素里面的块元素都加浮动          
## IE6，7下3像素BUG
    父级下两个div，左div设置左浮动width:100px，右div设置margin-left:100px
    标准浏览器下左div和右div会相连。IE6,7下两者之间会有3px的间距。
    解决办法:在IE6，7下元素要通过浮动并在同一行，就给这行元素都加浮动
## IE6下绝对定位元素消失———————————————————
    当浮动元素和绝对定位元素是并列关系的时候，在IE6下绝对定位元素会消失
    解决办法:
    给定位元素外面包个div
## 在IE6，7下父级的overflow包不住相对定位子元素———————————-
    在IE6，7下，子元素有相对定位的话，父级的overflow包不住子元素
    解决办法: 给父级也加相对定位
## IE6,7 下不支持fixed————————————————————
    position:fixed在IE6下失效
    解决办法:
    1. _position:absolute;
       _top:expression(eval(document.documentElement.scrollTop+100));
    2.用JS代替这个效果
