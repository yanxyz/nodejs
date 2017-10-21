# Guides

本文为 [Guides](https://webpack.js.org/guides/) 笔记。

## Asset Management

```js
{
  test: /\.css$/,
  use: ['style-loader', 'css-loader']
}
```

css-loader 返回 CSS 代码
style-loader 将 CSS 代码插入页面（通过 `<style>`)

file-loader 处理图片，字体。

以模块的思路去管理 assets。

## Output Management

当 bundle 的名字包含 hash 时，每次编译 bundle 的名字都可能不一样，手动修改 HTML 文件不现实。
html-webpack-plugin 自动修改 HTML 文件。
如果 HTML 文件不存在则自动创建一个。

clean-webpack-plugin 在编译之前清空 dist 目录。

## Development

source map

[webpack-dev-server](webpack-dev-server.md)


## Hot Module Replacement

热替换，在应用运行期间替换模块，而不需要重启应用。

想做到热替换，需要几方面条件。 webpack-dev-server 提供了此功能。

## Tree Shaking

Tree shaking 字面意思是摇树，把枯叶抖落下来。这里的意思是把 dead code 从 bundle 中去除。

一个 module 当中未使用的 exports 为 dead code。

在使用 ES module 语法之后，webpack 会在 bundle 中标记未使用的 exports。然后使用支持去除 dead code 的压缩器去除 dead code，比如 uglifyjs-webpack-plugin。

## Production




## Code Splitting

JavaScript libraries 通常不变，把它们和业务代码分开，是一种优化措施。

从 bundle 中剥离出去的文件称为 chunk。

## CommonsChunkPlugin

webpack config

```js
{
  entry: {
    index: './src/index.js',
    vender: ['jquery', 'other-lib']
  },
  output: {
    filename: '[name].bundle.js',
  },
  plugins: [
    new webpack.optimize.CommonsChunkPlugin({
      name: 'vender'
    }),
  ]
}
```

### Dynamic Imports

webpack config

```js
{
  entry: {
    index: './src/index.js'
  },
  output: {
    filename: '[name].bundle.js',
    chunkFilename: '[name].bundle.js'
  }
}
```

client js 使用 `import()`(旧版本使用 require.ensure)

```js
import(/* webpackChunkName: "lodash" */ 'lodash').then(_ => {

}
```

`webpackChunkName` 指定

`import()` 返回 Promise，client 需要支持 Promise

## Lazy Loading

和图片懒加载类似，触发某个条件后才加载 chunk，比如在事件回调当中。

```js
import(/* webpackChunkName: "print" */ './print').then(module => {
  var print = module.default
  print()
})
```

### Caching




