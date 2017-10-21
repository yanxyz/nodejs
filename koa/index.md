# Koa

Koa.js 是一款 web framework

- [docs](https://github.com/koajs/koa/tree/master/docs)
- [changelogs](https://github.com/koajs/koa/blob/master/History.md)

## 中间件

[挑选](https://github.com/koajs/koa/wiki)

### 理解

看 koa 的源码来理解 middleware。

application.js

```js
use(fn) {
  this.middleware.push(fn);
// middleware 是一个函数，fn(ctx, next)
// app.use(fn) 将中间件 fn 推入一个数组 app.middleware。
// 中间件的参数 next 用于调用 fn 在这个数组当中的下一个中间件。

callback()
const fn = compose(this.middleware);
// fn 是一个 promise
return fn(ctx).then(handleResponse).catch(onerror);
// handleResponse 会调用 res.end()
```

现在把 koa 放一边，想一想下面例子

```js


```

## 项目


## 资料

- [chenshenhai/koa2-note: 《Koa2进阶学习笔记》](https://github.com/chenshenhai/koa2-note)
