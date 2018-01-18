## word-beak:break-all和 word-wrap:break-word
1. 了解word-break属性  

	```
	/* 关键字值 */
	word-break: normal; 
	word-break: break-all; 
	word-break: keep-all;  
	/* 全局值 */
	word-break: inherit;
	word-break: initial;
	word-break: unset;
	```
2. 了解word-wrap属性  

	``` 
	/* 关键字值 */
	word-wrap: normal;
	word-wrap: break-word;  
	/* 全局值 */
	word-wrap: inherit;
	word-wrap: initial;
	word-wrap: unset;
	```
3. 区别  
	word-break:break-all正如其名字，所有的都换行。毫不留情，一	点空隙都不放过。而word-wrap:break-word则带有怜悯之心，如果	这一行文字有可以换行的点，如空格
4. word-spacing和white-space  
	word-spacing是单词之间间距的，white-space是字符是否换行显示的。  
	规定段落中的文本不进行换行：  
	white-space: nowrap
