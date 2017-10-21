# webpack

## 全局安装

```sh
npm install -g webpack
webpack -h
```

这种方式适用于简单项目，毕竟 webpack 体积较大。

[cli](https://webpack.js.org/api/cli/)

## 本地安装

如果对 webpack 版本有要求，使用本地安装

```sh
npm install --save-dev webpack
node_modules/.bin/webpack -h
```

这样运行 webpack 不方便，可以通过 npm scripts 运行。修改 package.json

```json
  "scripts": {
    "build": "webpack"
  },
```

npm 将 `node_modules/.bin` 放在 PATH 前面，上面 "webpack" 即 `node_modules/.bin/webpack`。

运行 webpack

```sh
npm run build
```

### 安装特定版本

```sh
npm view webpack dist-tags
npm install --save-dev webpack@beta
```
