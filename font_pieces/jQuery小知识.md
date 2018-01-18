##jQuery
1. 回到顶部按钮

	```
	<a class="top" href="#">Back to top</a>
	
	$(a.top).click(function (e) {
		e.preventDefault();
		$(document.body).animate({scrollTop: 0}, 800);
	});
	```
	将 scrollTop 的值改为你想要 scrollbar 停止的地方。然后你要做的就是，设置在 800 毫秒内回到顶部。  

2. 预加载图片

	```
	$.preloadImages = function () {
		for (let i = 0; i < arguments.length; i++) {
			$('<img>').attr('src', arguments[i]);
		}
	};
	
	$.preloadImages('img/hover-on.png', 'img/hover-off.png');
	```  

3. 检查是否加载完毕  
	检查图片是否完全加载完毕
	
	
	```
	$('img').load(function () {
	  console.log('image load successful');
	});
	```
4. 自动修复损坏的图片

	```
	$('img').on('error', function () {
	  $(this).prop('src', 'img/broken.png');
	});
	```
5. Hover 上的 Class 切换

	```
	$('.btn').hover(function () {
	  $(this).toggleClass('hover');
	});
	```
6. 禁用 input 字段
	有时你也许想让表单的提交按钮或其文本输入框变得不可用，直到用户执行了一个特定行为（例如确认 “我已经阅读该条款” 的复选框）。增加 disabled attribute 到你的 input，就可以实现自己想要的效果：
	
	```
	$('input[type="submit"]').prop('disabled', true);
	```
	当你想把 disabled 的值改为 false 时，仅需在该 input 上再运行一次 prop 方法。
	
	```
	$('input[type="submit"]').prop('disabled', false);
	```
7. 淡入淡出/滑动开关  
	想让该元素在第一次点击时显现，第二次点击时消失
	
	```
	// Fade
	$('.btn').click(function () {
	  $('.element').fadeToggle('slow');
	});
	 
	// Toggle
	$('.btn').click(function () {
	  $('.element').slideToggle('slow');
	});
	```
8. 简单的手风琴效果

	```
	// Close all panels
	$('#accordion').find('.content').hide();
	 
	// Accordion
	$('#accordion').find('.accordion-header').click(function () {
	  var next = $(this).next();
	  next.slideToggle('fast');
	  $('.content').not(next).slideUp('fast');
	  return false;
	});
	```
9. 使两个 Div 高度一样  
	设置了 min-height，意味着它可以比主要 div 更大，但永远不能更小
	
	```
	$('.div').css('min-height', $('.main-div').height());
	```
	遍历一组元素的设置，然后将高度设为元素中的最高值：
	
	```
	var $columns = $('.column');
	var height = 0;
	$columns.each(function () {
	  if ($(this).height() &gt; height) {
	    height = $(this).height();
	  }
	});
	$columns.height(height);
	```
	
	想让所有列都有相同高度：
	
	```
	var $rows = $('.same-height-columns');
	$rows.each(function () {
	  $(this).find('.column').height($(this).height());
	});
	```
10. 在新标签/窗口打开站外链接  
	在一个新标签或者新窗口中打开外置链接，并确保站内链接会在相同的标签或窗口中打开：
	
	```
	$('a[href^="http"]').attr('target', '_blank');
	$('a[href^="//"]').attr('target', '_blank');
	$('a[href^="' + window.location.origin + '"]').attr('target', '_self');
	```
11. 通过文本找到元素  
	通过使用 jQuery 中的 contains() 选择器，你可以找到某个元素中的文本。如果文本不存在，该元素将会隐藏：
	
	```
	var search = $('#search').val();
	$('div:not(:contains("' + search + '"))').hide();
	```
12. 视觉改变触发
	当用户焦点在另外一个标签上，或重新回到标签时，触发 JavaScript：
	
	```
	$(document).on('visibilitychange', function (e) {
	  if (e.target.visibilityState === "visible") {
	    console.log('Tab is now in view!');
	  } else if (e.target.visibilityState === "hidden") {
	    console.log('Tab is now hidden!');
	  }
	});
	```
13. Ajax 调用的错误处理
	当某次 Ajax 调用返回 404 或 500 错误，就会执行错误处理。但如果没有定义该处理，其他 jQuery 代码或许会停止工作。可以通过下面这段代码定义一个全局 Ajax 错误处理：
	
	```
	$(document).ajaxError(function (e, xhr, settings, error) {
	  console.log(error);
	});
	```

14. 插件链式调用

	```
	$('#elem').show();
	$('#elem').html('bla');
	$('#elem').otherStuff();
	```
	
	```
	$('#elem')
	  .show()
	  .html('bla')
	  .otherStuff();
	```


