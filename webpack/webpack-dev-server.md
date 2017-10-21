# webpack-dev-server

webpack 的配置 options.devServer 是用于配置 webpack-dev-server。

- [usage](https://webpack.js.org/configuration/dev-server/)
- [changelog](https://github.com/webpack/webpack-dev-server/releases)
- [Examples](https://github.com/webpack/webpack-dev-server/tree/master/examples)

v2.8 scripts 包含 ES6 keywords const and let，一些运行环境将受到影响，比如 UglifyJS, IE

- uglifyjs-webpack-plugin 新版本支持 ES6，独立安装它，不使用 webpack 内置版本。
- IE 应使用 v2.7.1

webpack-dev-server 依赖于 webpack(peerDependencies)

```sh
yarn info webpack-dev-server peerDependencies
yarn add --dev webpack webpack-dev-server uglifyjs-webpack-plugin
./node_modules/.bin/webpack-dev-server -h
```

遇到问题，打开 `/webpack-dev-server` 查看。

## Hot Module Replacement

在使用 webpack-dev-server 时会遇到一个概念 Hot Module Replacement (HMR)，说的是在应用运行过程中添加删除模块，而不用重启应用。

https://webpack.js.org/guides/hot-module-replacement/

这是如何实现的呢？
