##IE兼容性bug汇总

1. input在IE中为块级元素， chrome和firefox为行内元素
2. 从IE 10开始，type="text" 的 input 在用户输入内容后，会自动产生一个小叉叉（X），方便用户点击清除已经输入的文本
	对于type="password"的 input 则会在右方显示一个小眼睛的图标，占击这个图标可以显示已经输入的内容。
	隐藏IE浏览器自带的文本删除按钮和密码查看按钮
	
	```
	<style>
		::-ms-clear, ::-ms-reveal{display: none;}
	</style>
	```

3. IE10和IE11已经移除了条件注释

	```
	<!--[if IE 11]>
	<p>你在非IE中将看不到我的身影</p>
	<![endif]-->
	```

4. http://www.cnblogs.com/wolo/archive/2013/03/26/2983010.html
5. **input内容改变后，ie11中change事件执行两次的解决办法**
http://cache.baiducontent.com/c?m=9d78d513d99816b8599d977d1a16a63d4516c7252bd7a1442587cf1dc4701c011969b9fd61600705a0d861375ff21c4bea876733615f37b7ec94df0cc0fac87b73de746a374b9b12529542fe9511389777d609b2f158fabcf23194a8d7d4d8&p=893d835d85cc43f508e2947e0e4e91&newp=882a9545d58113b105be9b7c544e81231610db2151d7da1f6b82c825d7331b001c3bbfb423241500d5ce786d04a44a56e8fa30703c0723a3dda5c91d9fb4c57479ca752a2d&user=baidu&fm=sc&query=ie11+input+change&qid=a6dd20a10000bb12&p1=1
	页面文件上传，代码如下：
	
	```
	<form id="noflashUpload" enctype="multipart/form-data" action="ajax/uploadDocument.do" method="post" style="margin-left:-80px;">
   <dl class="form-avatar">
       <dd>
        	<span id="up_span" style="padding: 2px 5px 2px;border: 1px solid #C0C0C0;margin-bottom: 10px;border-radius: 2px;background: #DDDDDD;overflow: hidden;position: relative;cursor: pointer;*position: relative;">添加文件
			<input type="file" id="otherfile" name="file" style="width:60px;opacity: 0;filter:alpha(opacity:0);zoom:1;font-size: 10px;position: absolute;top: 0;right: 0;cursor: pointer;"></span>
			<p>支持PDF,DOC,DOCX,PPT,PPTX格式</p>
       </dd>
   </dl>
   </form>
	```
	为了能实现貌似一次上传多个文件的功能，上图这个input采取ajax提交，并且每次上传后要把input的值设为空，这样才能进行下一次上传
	
	解决方案： 
	**限制当input的val()值为空的时候，不去调用upload方法，如此，当上传结束，把input的value置为空的时候，upload调用接口将不再执行**
	
	```
	import $ from 'jquery';
	import './index.less';
	import uploadTpl from './upload.tpl';
	export default class Uploader {
	    constructor($el, options) {
	        this.ops = {
	            url: '/common/uploads',
	            // 传图片传 image 文件 file, all 所用通用
	            type: 'all',
	            // 动态加水印取法,普通的!thumb320，
	            thumbImg: '!thumb600', // or !thumb320   ?imageView2/2/w/800/h/1424/q/91
	            imgDomain: 'http://mtapplet.meitudata.com/',
	            uploadSuccess() {},
	            uploadFailure() {}
	        };
	        this.ops = $.extend({}, this.ops, options);
	        this.uploadToken = {};
	        this.$el = $el;
	        this.name = this.$el.attr('id') || 'formData' + Math.floor(Math.random() * 1000);
	        this._init();
	    }
	    _init() {
	        this._renderDom();
	        this._bindEve();
	    }
	    _renderDom() {
	        let tpl = uploadTpl({
	            ops: this.ops
	        });
	        this.$el.css('position', 'relative').append($(tpl));
	    }
	    _bindEve() {
	        let that = this;
	        this.$el.off().on('change', 'input',function(e) {
	            // 为解决IE11中，input的value值改变一次，change事件就执行一次的bug。当input的值为空的时候，不去调用upload方法
	            if($(this).val() != '') {
	                that.upload(e.target.files[0]);
	            }            
	        });
	
	    }
	    upload(file) {
	        let that = this;
	        let formData = new FormData();
	        formData.append(this.ops.type || 'all', file);
	        $.ajax({
	            url: this.ops.url,
	            type: 'POST',
	            cache: false,
	            data: formData,
	            processData: false,
	            contentType: false,
	            dataType: 'json'
	        }).done(function (res) {
	            that.ops.uploadSuccess(res, file, that);
	        }).fail(function (res) {
	            that.ops.uploadFailure(res, file, that);
	        });
	        // 为解决upload方法连续上传两个相同的文件，value值不变，导致上传不成功。所以每次上传成功后，将input的value清空
	        this.$el.find('input').val('');
	    }
	}
	
	```
6. IE中不能使用的高级语法，以及兼容性样式问题，可以采用引入polyfill, 进行降级处理
	
	```
	<script src="/{{htmlWebpackPlugin.options.MODULE_NAME}}/page/polyfill.js" charset="utf-8"></script>

	```	
7. IE中，box-sizing: border-box;会带来border-bottom的dash下划线
    ```
    box-sizing: border-box;
    ```
8. IE中，ajax的get请求会默认读取缓存，需设置cached: false; 来禁用默认缓存
9. IE9中， text-overflow: ellipsis;在display：flex元素上无效。