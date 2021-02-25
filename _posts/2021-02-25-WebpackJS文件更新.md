---
published: false
---
## A New Post

```
//NodeJs的path模块自带，resolve用来拼接绝对路径的方法
const { resolve } = require("path");
const HtmlWebpackPlugin = require('html-webpack-plugin');
const MiniCssExtractPlugin = require('mini-css-extract-plugin');
// const OptimizeCssAssetsWebpackPlugin = require('optimize-css-assets-webpack-plugin');
// const { use } = require("chai");
module.exports = {
  //入口起点
  entry: ['./src/js/index.js','./src/index.html'],
  //输出
  output: {
    //输出的文件名
    filename: 'js/build.js',
    /*
      resolve用来拼接绝对路径的方法,Node自带需要引入
      __dirname NodeJs的变量，代表当前文件的目录绝对路径
    */
    path: resolve(__dirname, "build"),
    publicPath:'./'
  },
  //loader的配置
  /*
    解析css需要下载style-loader和css-loader 运行 npm i css-loader style-loader -D
    解析less需要下载less和less-loader 运行 npm i less less-loader -D
    sass node-sass sass-loader
    stylus stylus-loader
  */
  module: {
    rules: [
      //处理css
      {
        //test 匹配哪些文件
        test: /\.css$/,
        //use 使用哪些loader进行处理
        use: [
          //use执行顺序 从右到左 or 从下到上 依次执行
          //创建style标签，将js中的css样式资源插入进行，添加到head中生效
          // 'style-loader',

          /*
          MiniCssExtractPlugin.loader 取代style-loader，
          作用：提取js中的css变成单独文件
          需要下载 mini-css-extract-plugin插件 运行 npm i mini-css-extract-plugin -D
          */
          MiniCssExtractPlugin.loader,
          //将css文件变成commonjs模块加载到js中，里面内容是样式字符串
          'css-loader',
          /*
          css做兼容处理：postcss 运行 npm i postcss-loader postcss-preset-env -D
          postcss-preset-env帮助postcss找到package.json中的browserslist里面的配置，通过配置加载指定的css兼容性
          所以对package.json做配置
          "dependencies": {
            ...
           },
           "browserslist": {
             //开发环境
             "development": [
               "last 1 chrome version",//最近版本的谷歌浏览器兼容
               "last 1 firefox version",//最近版本的火狐浏览器兼容
               "last 1 safari version"//最近版本的苹果浏览器兼容
             ],
             "production": [
               ">0.2%",//大于99.8%的浏览器
               "not dead",//不兼容已经下线的浏览器 例如：ie10
               "not op_mini all",//op_mini早已下线，国内没有
             ]
           }
           更多browserslist配置，github搜索
           使用的默认配置
           'postcss-loader'
           修改配置的写法 ↓
           */
          {
            loader: 'postcss-loader',
            options: {
              ident: 'postcss',
              plugins: () => [
                //postcss的插件
                require('postcss-preset-env')()
              ]
            }
          }
        ]
      },
      //处理less
      { 
        test: /\.less$/, 
        use:[
          'style-loader',
      	  'css-loader',
      	  'less-loader' //先安装 npm i less less-lodaer -D
      	]
      },
      /*
        语法检查：eslint-loader eslint
          注意：只检查自己写的源代码，不检查第三方的库
          规则：package.json中的eslintConfig中设置
          "dependencies": {
           ...
          },
          "eslintConfig": {
            "extends": "airbnb-base"
          }
          需要用airbnb 下载运行npm i eslint eslint-config-airbnb-base eslint-plugin-import -D
      */
      {
        test: /\.js$/,
        exclude: /node_modules/,//排除node_modules中的js
        loader: 'eslint-loader',
        options: {
          //自动修复eslint的错误
          fix: true
        }
      },
      /*
        1、基本的兼容处理
          js兼容性处理：babel-loader 
          下载运行 npm i babel-loader @babel/core @babel/preset-env -D
        2.全部的js兼容处理
          体积大，比较暴力，会把所有的语法全部兼容
          下载运行 npm i @babel/polyfill -D
          在入口文件 index.js引入即可 import '@babel/polyfill'
        3.需要做兼容的就做，按需加载
          下载运行 npm i core-js -D
      */
      {
        test: /\.js$/,
        exclude: /node_modules/,//排除node_modules中的js
        loader: 'babel-loader',
        options: {

          /*
            方案一
            预设: 指示babel做什么样的兼容性处理
            presets: ['@babel/preset-env']
          */
         /*
            方案三
            按需加载
          */
         presets: [
           [
             '@babel/preset-env',
             {
               //按需加载
               useBuiltIns: 'usage',
               //制定core-js版本
               corejs: {
                 version: 3
               },
               //制定兼容性做到哪个浏览器版本以上
               targets: {
                chrome: '60',
                firefox: '60',
                ie: '9',
                safari: '10',
                edge: '17'
               }
             }
           ]
         ]
        }
      },
      /*
        处理图片资源
        默认处理不了html里的img
      */
      {
        test: /\.(jpg|png|gif)$/,
        //使用url-loader 下载 url-loader 和 file-loader 运行 npm i url-loader file-loader -D
        loader: 'url-loader',//单个可以简写，不用写use
        //配置
        options: {
          //图片大小小于8kb，就会被base64处理
          limit: 8 * 1024,
          /*
            旧版本问题：url-loader默认使用ES6模块解析，而html-loader引入图片是commonjs
              解析时会出问题：[object Module]
            解决：关闭url-loader的ES6模块化，使用commonjs解析
          */
          esModule: false,
          /*
            给图片重命名
            [hash:10]取图片hash的前10位
            [ext]取原来文件的扩展名
          */
          name: '[hash:10].[ext]',
          //打包后要放置的文件夹
          outputPath: 'images'
        }
      },
      //本处理html里的img的图片资源
      {
        test: /\.html$/,
        //处理html文件的img图片（负责引入img，从而能被url-loader处理）
        //下载 html-loader 运行 npm i html-loader -D
        // loader: 'html-loader',
        loader: 'html-withimg-loader',//html-withimg-loader
      },
      //打包字体资源
      {
        /*
          exclude 排除其他资源 css|js|less
          exclude: /\.(css|js|less)/,
        */
        test:/\.(eot|svg|ttf|woff|otf)/,
        loader: 'file-loader',
      }
    ]
  },
  //plugins的配置
  /*
    打包html文件的插件 
      1.先下载运行 npm i html-webpack-plugin -D
      2.引入 const HtmlWebpackPlugin = require('html-webpack-plugin');
      3.写入到plugins里面 new HtmlWebpackPlugin()
  */ 
  plugins: [
    /*
      new HtmlWebpackPlugin()
      功能：默认创建一个空的html文件，自动引入打包的资源（js&css）
      需求：需要有结构的html文件
    */
    new HtmlWebpackPlugin(
      {
        //复制./src/index.html 文件dom结构
        template: './src/index.html'
      }
    ),
    new MiniCssExtractPlugin({
      //生成的文件名叫build.css，放在build/css下
      filename: 'css/build.css'
    }),
    // optimize-css-assets-webpack-plugin 压缩css的插件 运行 npm i optimize-css-assets-webpack-plugin -D
    //压缩css
    // new OptimizeCssAssetsWebpackPlugin()//2021-02-24 23:02:30 安装不了插件
  ],
  // 模式
  mode: 'development',//开发环境
  // mode: 'production',//生产环境

  /*
    开发服务器 devServer：用来自动化（自动编译，自动打开浏览器，自动刷新）
    特点：只会在内存中编译打包，不会有任何输出
    npx 本地启动
    启动devServer 指令：npx webpack-dev-server or npx webpack serve需要下载 npm i webpack-dev-server -D
  */
  devServer: {
    //要运行项目的目录
    contentBase: resolve(__dirname, 'build'),
    //启动gzip压缩
    compress: true,
    //端口号
    port: 3000,
    //自动打开浏览器
    open: true,
    /*
      开启HMR功能
      HMR：hot module replacement 热模块替换/模块热替换
        作用：一个模块发生变化，只会重新打包这一个模块（而不是打包所有的模块）
        极大提升构建速度

        样式文件：可以使用HMR功能
        JS文件：默认不能使用 ---->修改index.js代码
        Html文件：默认不能使用HMR，同时导致不能热更新了
          解决：更改entry配置，将html文件引入 （之前：'./src/js/index.js'，之后：['./src/js/index.js','./src/index.html'],）
    */
    hot: true
  }
}
```
