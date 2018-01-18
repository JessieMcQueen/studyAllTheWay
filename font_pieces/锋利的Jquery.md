1. jquery的节点插入

    ```
    append()  匹配元素内部追加内容
    appendTo() $(A).appendTo(B) A追加到B中
    prepend() 匹配元素内部前置内容
    prependTo() $(A).prependTo(B) A前置到B
    after() 匹配元素之后插入内容
    insertAfter() $(A).insertAfter(B) A插入到B后面
    before() 匹配元素之前插入内容
    insertBefore() $(A).insertBefore(B) A插入到B后面
    ```
2. 节点删除
    
    ```
    remove() 从DOM中删除所选中的元素
    empty() 清空节点，能清空元素中的所有后代节点，以及元素里的内容
    ```
3. 复制节点
    
    ```
    clone() 复制节点， $(A).clone() 复制节点A
    ```
    clone() 方法传一个参数true, 复制元素同时复制元素所绑定的事件
4. 替换节点
    
    ```
    replaceWith() $(A).replaceWith(B)
    ```
    替换后的节点，不再有之前绑定的事件
5. 包裹节点

    ```
    wrap() $('strong').wrap('<b></b>') 把<strong>标签用<b>包裹起来
    wrapAll() 把所有匹配到的元素用同一个标签包裹起来
    wrapInner() 将每一个匹配到的元素的子内容用标签包裹起来
    ```
    
6. 切换样式
    
    ```
    toggle() 用于控制元素的显示隐藏
    toggleClass() $('p').toggleClass('another'); 重复切换类名another
    ```
7. val()和value
    
   val()获取元素的值
8. 遍历节点
    
    ```
    children() 获取元素下的子元素，只考虑子元素而不考虑任何后代元素
    next() 获取紧邻的同辈元素
    siblings() 获取所有的同辈元素
    closest() 获取最近的匹配元素，如未找到，则向上查找父元素
    find()
    filter() 将匹配元素集合缩减为匹配指定选择器的元素。
    nextAll()
    prevAll()
    parent()
    parents()
    ```
  9. height()
    
    ```
    $(A).css('height')
    $(A).height() 获取实际高度
    ```
10. offset()
    
    ```
    offset()
    position()
    scrollLeft()
    scrollTop()
    ```
    