1. git ls-files -stage  查看暂存文件  
2. git cat-file -p 版本id 查看文件
3. git reset --hard
4. 删除分支  
	git branch -D XXX  
	git push origin :XXX 
5. git cherry-pick  
	http://blog.csdn.net/wh_19910525/article/details/7554430  
	情景： 假设我们有个稳定版本的分支，叫v2.0，另外还有个开发版本的分支v3.0，我们不能直接把两个分支合并，这样会导致稳定版本混乱，但是又想增加一个v3.0中的功能到v2.0中，这里就可以使用cherry-pick了。	