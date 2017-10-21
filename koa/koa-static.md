# koa-static

是 koa-send 的 wrapper

```js
const serve = require('koa-static')
app.use(serve(root, options))
```

options

```js
{
  // koa-send options
  root: root
  index: 'index.html'

  // own options
  defer: false // 是否先 `await next()`
}
```
