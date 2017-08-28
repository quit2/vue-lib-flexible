# vue-lib-flexible
vue中使用手淘的 lib-flexible 

- 安装npm i lib-flexible --save
- main.js中引入 lib-flexible

  import LibFlexible from 'lib-flexible';

- 将 px 转换成 rem 我们将使用 px2rem 这个工具，它有 webpack 的 loader：px2rem-loader

   npm i px2rem-loade --save-dev
   
- 在 vue-cli 生成的 webpack 配置中，vue-loader 的 options 和其他样式文件 loader 最终是都是由 build/utils.js 里的一个方法生成的。

// build/utils.js

    var cssLoader = {
      loader: 'css-loader',
      options: {
        minimize: process.env.NODE_ENV === 'production',
        sourceMap: options.sourceMap
      }
    }
    var px2remLoader = {
      loader: 'px2rem-loader',
      options: {
        remUnit: 75
      }
    }

并放进 loaders 数组中

// build/utils.js

    function generateLoaders (loader, loaderOptions) {
        var loaders = [cssLoader, px2remLoader]
        if (loader) {
          loaders.push({
           ....
          })
        }
        .....
    }
    
- 修改配置后需要重启，然后我们在组件中写单位直接写px，设计稿量多少就可以写多少了。
