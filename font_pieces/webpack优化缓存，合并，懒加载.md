```
/*生成环境配置文件：不需要一些dev-tools,dev-server和jshint校验等。和开发有关的东西删掉*/
var webpack = require('webpack');
var path = require('path');
var node_modules = path.resolve(__dirname, 'node_modules');
var pathToReact = path.resolve(node_modules, 'react/dist/react.min.js');
var pathToReactDOM = path.resolve(node_modules, 'react-dom/dist/react-dom.min.js');
var ExtractTextPlugin = require('extract-text-webpack-plugin');
var HtmlWebpackPlugin = require('html-webpack-plugin');
//具体作用及缺点见plugins中的描述
//var WebpackMd5Hash = require('webpack-md5-hash');
// 该插件是对“webpack-md5-hash”的改进：在主文件中获取到各异步模块的hash值，然后将这些hash值与主文件的代码内容一同作为计算hash的参数，这样就能保证主文件的hash值会跟随异步模块的修改而修改。
var WebpackSplitHash = require('webpack-split-hash');

var config = {
    entry:{
        app:path.resolve(__dirname, 'src/js/entry.js'),
        mobile: path.resolve(__dirname, 'src/js/mobile.js'),
        //添加要打包在vendors.js里面的库
        vendors:['react','react-dom']
    },
    resolve:{
        alias: {
            'react.js': pathToReact, //alias:别名,
            'react-dom.js': pathToReactDOM
        },
        fallback: path.join(__dirname, "node_modules")
    },
    resolveLoader: { 
        fallback: path.join(__dirname, "node_modules") 
    },
    output:{
        path:path.resolve(__dirname, 'dist'),
        publicPath:'../',//生成的html里的引用路径用 publicPath
        //以文件内容的MD5生成Hash名称的script来防止缓存
        filename: 'js/[name].[chunkhash:8].js',
        //异步加载的模块是要以文件形式加载，生成的文件名是以chunkFilename配置的
        chunkFilename: 'js/[name].[chunkhash:8].js'
    },
    module:{
        loaders:[{
            test: /\.jsx?$/,
            //这里(node_modules文件夹)再也不需通过任何第三方来加载
            exclude:path.resolve(__dirname, 'node_modules'),
            loader: 'babel',
            query:{
                presets:['es2015', 'react']
            }
        },
        {
            test:/\.css$/,
            //loader:'style!css'
            loader: ExtractTextPlugin.extract("style", "css")
        },
        {
            test:/\.scss$/,
            loader:'style!css!sass'
        },
        //url-loader:图片、字体图标加载器，是对file-loader的上层封装,支持base64编码。传入的size（也有的写limit) 参数是告诉它图片如果不大于 25KB 的话要自动在它从属的 css 文件中转成 BASE64 字符串。
        {
            test: /\.(png|jpg|jpeg|gif|svg|woff|woff2|ttf|eot)$/,
            loader: 'url?limit=25000&name=[name].[ext]'
        }]
    },
    plugins:[
        //提取公共代码的插件，用于提取多个入口文件的公共脚本部分，然后生成一个vendors.js。注意HTML代码中要加载这个公共文件
        new webpack.optimize.CommonsChunkPlugin({
            name: 'vendors',
            filename: 'js/vendors.js'
        }),
        //在文件开头插入banner
        new webpack.BannerPlugin("The file is creted by yangmin.--"+ new Date()),
        //压缩js文件
        new webpack.optimize.UglifyJsPlugin({
            compress: {
                warnings: false
            }
        }),
        /*插件：单独使用style标签加载css文件.contenthash代表的是文本文件内容的hash值，也就是只有style文件的hash值*/
        new ExtractTextPlugin("css/[name].[contenthash:8].css"),//设置其路径(路径相对于path)
        /*插件：动态生成html，在webpack完成前端资源打包以后，自动将打包后的资源路径和版本号写入HTML中，达到自动化的效果。*/
        new HtmlWebpackPlugin({
            filename:'view/index.html',    //生成的html存放路径，相对于 path
            template:'src/view/index.html',    //html模板路径
            inject:true,    //允许插件修改哪些内容，true/'head'/'body'/false,
            chunks:['vendors','app'],//加载指定模块中的文件，否则页面会加载所有文件
            hash:false,    //为静态资源生成hash值
            minify:{    //压缩HTML文件
                removeComments:false,    //移除HTML中的注释
                collapseWhitespace:false    //删除空白符与换行符
            }        
        }),
        new HtmlWebpackPlugin({
            filename:'view/mobile.html',    //生成的html存放路径，相对于 path
            template:'src/view/mobile.html',    //html模板路径
            inject:true,    //允许插件修改哪些内容，true/'head'/'body'/false,
            chunks:['vendors','mobile'],//加载指定模块中的文件，否则页面会加载所欲文件
            hash:false,    //为静态资源生成hash值
            minify:{    //压缩HTML文件
                removeComments:false,    //移除HTML中的注释
                collapseWhitespace:false    //删除空白符与换行符
            }
        }),
        /*作用：生成具有独立hash值的css和js文件，即css和js文件hash值解耦.
         *缺点：webpack-md5-hash插件对chunk-hash钩子进行捕获并重新计算chunkhash，它的计算方法是只计算模块本身的当前内容（包括同步模块）。这种计算方式把异步模块的内容忽略掉了，会造成一个问题：异步模块的修改并未影响主文件的hash值。
         */
        //new WebpackMd5Hash()
        new WebpackSplitHash()
    ]
}
  module.exports = config;
```

1. resolve配置用来影响webpack模块解析规则。解析规则也可以称之为检索，索引规则。配置索引规则能够缩短webpack的解析时间，提升打包速度。
    ```
    resolve: {
        root: [],
        alias: {
            src: srcDir,
            css: srcDir + '/css',
            libs: srcDir + '/libs',
            mock: srcDir + '/mock',
            page: srcDir + '/page',
            template: srcDir + 'template',
            images: srcDir + '/images',
            modules: srcDir + '/modules',
            common: srcDir + '/common',
            components: srcDir + '/components'
        }
    },
    ```
    - resolve.root 用来配置搜索路径集合。root配置必须是绝对路径，不能存在./app/modules之类的相对路径。
    - resolve.modulesDirectory 是指需要向上搜索的目录名称（即如果当前目录找不到，找上级目录），一般只会是node_modules之类的。其他自定义的资源一般不需要向上搜索，可以配置alias