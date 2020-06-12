# webpack-demo

Webpack [Getting Started](https://webpack.js.org/guides/getting-started/)

使用 webpack 來管理這些腳本

「源」代碼(/src) 書寫和編輯的代碼  
「分發」代碼(/dist) 構建過程產生的代碼最小化和優化後的「輸出」目錄

`npx webpack src/index.js --output dist/bundle.js`  
The `npx` command, which ships with `Node 8.2` or higher

`npm run build`

# sample

Webpack 範例

體驗一下 Webpack  
教學：https://www.webpackjs.com/concepts/

1. 安裝 webpack 相關套件
2. 設置 webpack.config.js
3. 建立 index.html 及 src 內的相關檔案
4. 使用 [css loader](https://github.com/webpack-contrib/css-loader)
5. [Sass loader](https://github.com/webpack-contrib/sass-loader)

6. [web server](https://github.com/webpack/webpack-dev-server)

[DevServer](https://webpack.js.org/configuration/dev-server/)

## webpack-dev-server

The [webpack-dev-server](https://webpack.js.org/guides/development/#using-webpack-dev-server) provides you with a simple web server and the ability to use live reloading.

`npm install --save-dev webpack-dev-server`

webpack.config.js

```js
  module.exports = {
    mode: 'development',
    entry: {
      app: './src/index.js',
      print: './src/print.js',
    },
    devtool: 'inline-source-map',
+   devServer: {
+     contentBase: './dist',
+   },
    plugins: [
      new CleanWebpackPlugin({ cleanStaleWebpackAssets: false }),
      new HtmlWebpackPlugin({
        title: 'Development',
      }),
    ],
    output: {
      filename: '[name].bundle.js',
      path: path.resolve(__dirname, 'dist'),
    },
  };
```

This tells `webpack-dev-server` to serve the files from the dist directory on localhost:8080.

package.json

```js
"scripts": {
    "start": "webpack-dev-server --open",
},
```

npm start

[devServer.contentBase](https://webpack.js.org/configuration/dev-server/#devservercontentbase)

Usage via the CLI

```js
webpack-dev-server --content-base /dir

"start": "webpack-dev-server --content-base src --open --hot",
```
