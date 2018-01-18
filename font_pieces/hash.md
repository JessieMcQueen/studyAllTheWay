1. hash处理冲突的方法
    ###开发定址法  
    其基本思想是：当关键字key的哈希地址p=H（key）出现冲突时，以p为基础，产生另一个哈希地址p1，如果p1仍然冲突，再以p为基础，产生另一个哈希地址p2，…，直到找出一个不冲突的哈希地址pi ，将相应元素存入其中。    
    Hi=（H（key）+di）% m   i=1，2，…，n  
    其中H（key）为哈希函数，m 为表长，di称为增量序列。
    - 线性探测再散列
    dii=1，2，3，…，m-1
    这种方法的特点是：冲突发生时，顺序查看表中下一单元，直到找出一个空单元或查遍全表。
    - 二次探测再散列
    di=12，-12，22，-22，…，k2，-k2    ( k<=m/2 )
    这种方法的特点是：冲突发生时，在表的左右进行跳跃式探测，比较灵活。
    - 伪随机探测再散列
    di=伪随机数序列。
2. webpack中hash的用法
    ```
     new htmlWebpackPlugin({   
        // webpack 指定目录(package内设置)生成静态HTML文件
        title: "自动生成网页标题",
        filename: "test.html",
        template: "temIndex.html",
        hash: true,      
        // true | false。如果是true，会给所有包含的script和css添加一个唯一的webpack编译hash值。这对于缓存清除非常有用。
        inject: true,    
        // | 'head' | 'body' | false  ,注入所有的资源到特定的 template 或者 templateContent 中，如果设置为 true 或者 body，所有的 javascript 资源将被放置到 body 元素的底部，'head' 将放置到 head 元素中。
        chunks: ["app"]   // 使用chunks 需要指定entry 入口文件中的哪一个模块
        })
    ```
    hash: true。如果是true，会给所有包含的script和css添加一个唯一的webpack编译hash值。这对于缓存清除非常有用。
    <link href="/static/page/apply/index.css?e7df8fd7bd161440ccb4" rel="stylesheet">
    如此，当js,css文件发生变动时，根据文件内容生成的hashcode不同，会重新读取变动的文件。