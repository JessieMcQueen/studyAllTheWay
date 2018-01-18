##window.open

1. 在当前窗口打开百度,并且使URL地址出现在搜索栏中.
	window.open("http://www.baidu.com/", "_search");
	window.open("http://www.baidu.com/", "_self");
2. 在一个新的窗口打开百度
	window.open("http://www.baidu.com/", "_blank");
3. 打开一个新的窗口,并命名为"hello"
	window.open("", "hello");  
	_top : 如果页面上有framesets,则url会取代framesets的最顶层, 即, 如果没有framesets, 则效果等同于_self.  
	_parent: url所指向的页面加载到当前frame的父亲, 如果没有则效果等同于_self.  
	_media : url所指向的页面加载到Media Bar所包含的HTML代码区域中.如果没有Media Bar则加到本身.   
	如果还要添加其它的东西在新的窗口上, 则需要第三个参数:    
	channelmode : yes|no|1|0  (窗口显示为剧场模式[全屏幕显示当前网页, 包括工具栏等],或频道模式[一般显示]).  
	directories :  yes|no|1|0 (是否添加目录按钮, 比如在IE下可能会有一个"链接"这样的按钮在最上面出现)  
	fullscreen : yes|no|1|0 (使浏览器处理全屏幕模式, 并隐藏标题栏和菜单等)  
	menubar : yes|no|1|0 (是否显示浏览器默认的菜单栏)  
	resizeable : yes|no|1|0 (窗口是否可调整大小)  
	scrollbars : yes|no|1|0 (是否允许水平或垂直滑动条)  
	titlebar : yes|no|1|0 (是否添加一个标题栏)  
	toolbar : yes|no|1|0 (是否添加浏览器默认的工具栏)  
	status : yes|no|1|0 (是否显示状态栏)  
	location : yes|no|1|0  (是否显示搜索栏)  
	copyhistory :  yes|no|1|0 (似乎已经废弃, 如果只要工具栏显示, 历史按钮就会显示出来)  
	height : 窗口的高度, 最小值为100像素  
	width :  窗口的宽度, 最小值为w100像素  
	left : 窗口的最左边相对于屏幕的距离  
	 
	 
	关于open函数还有最后一个参数,是关于历史记录的,即是把当前要打开的窗口与现在的窗口的历史URL相同还是另外记忆.	  	