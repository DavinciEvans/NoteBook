# webpack 食用方法

## 基本使用

使用 webpack 对 js 进行打包

`webpack ./src/main.js ./dist/bundle.js`

修改 webpack 的配置文件 `webpack.config.js`

```Javascript
const path = require("path")

module.exports = {
    entry: "./src/main.js",
    output: {
        path: path.resolve(__dirname, "dist"),
        filename: "bundle.js"
    }
}
```

这样就可以直接使用 `webpack` 命令进行打包而不用输入后面的参数。

这里导入 path 模块，是因为 output 需要使用绝对路径，通过 path 来定位。

使用 `npm init` 初始化 `package.json`

```Javascript
{
  "name": "webpack-first-try",
  "version": "1.0.0",
  "description": "",
  "main": "src/main.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "build": "webpack"
  },
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "webpack": "^3.9.1"
  }
}
```

在这里，添加了一个 `build` 命令指向 `webpack`。可以通过 `npm run build` 来执行，同时优先从局部安装的 webpack 使用。

局部安装 webpack：

`npm install --save-dev webpack@3.9`

## 引入 CSS

官方文档有详解

[https://webpack.docschina.org/loaders/style-loader/](https://webpack.docschina.org/loaders/style-loader/)

分别安装 css-loader 和 style-loader

并根据官方的配置把配置导入 webpack.config.js

## 图片资源

使用 url-loader 和 file-loader

在 url-loader 的 option 下有一个 limit，小于 limit 的图片文件会以 base64 打包，大于的需要使用 file-loader，单独放入 dist 当中。