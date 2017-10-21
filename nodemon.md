# nodemon

[nodemon](https://github.com/remy/nodemon) Monitor for any changes in your node.js application and automatically restart the server - perfect for development

安装

```sh
npm install -g nodemon
nodemon -h
```

## 启动应用

用 nodemon 代替 node

```sh
nodemon app.js
nodemon app.js -- [appArgs]
rs # 手动重启
```

## 配置

```
nodemon --help config
```

- [Sample nodemon.json](https://github.com/remy/nodemon/blob/master/doc/sample-nodemon.md)
- [default options for config.options](https://github.com/remy/nodemon/blob/master/lib/config/defaults.js)

```js
{
  "restartable": "rs" // 若为 false，不监听 rs
  "execMap": {
    "js": "node --harmony",
    "py": "python", // 支持非 js 脚本
  },
  "env": {
    "NODE_ENV": "development"
  },
  // 默认值 https://github.com/remy/nodemon/blob/master/lib/config/exec.js#L76
  "ext": "js json",
  "delay": "2500", // ms，延迟监听，给应用初始化时间
}
```

注： nodemon.json 不能有注释，上面只是注解。

### ignore

- [Overriding the underlying default ignore rules](https://github.com/remy/nodemon/blob/master/faq.md#overriding-the-underlying-default-ignore-rules)

## 资料

- [nodemon 基本配置与使用 - JuFoFu - 博客园](http://www.cnblogs.com/JuFoFu/p/5140302.html)
