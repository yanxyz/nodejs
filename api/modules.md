# Modules

因为目前 modules 还没有普遍实现，Node.js 使用的是 CommonJS modules，

## CommonJS Modules

对于 modules，top-level scope 不是 global scope。

modules 文件将包裹在一个函数（module wrapper）内，因此 modules top-level scope 不是 global scope。

## ECMAScript Modules

目前处于试验阶段。

模块扩展名为 `.mjs`

```js
// foo.mjs
export default { name: 'foo' }

// app.mjs
import foo from './foo.mjs' // 不能省略扩展名，不然找不到这个模块
console.log(foo.name)
```

```js
node --experimental-modules app.mjs
```
