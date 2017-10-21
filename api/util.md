# util

常用工具。

## `util.debuglog(section)`

这个方法返回一个函数，若环境变量 NODE_DEBUG 的值包含指定的 section，它向 `stderr` 写入调试信息。

hello.js

```js
const debug = require('util').debuglog('foo') // section 为 foo
debug('hello') // debug message
```

运行

```sh
NODE_DEBUG=foo node hello.js
```

相关模块

- debug

## `util.deprecate(function, string)`




## `util.promisify(original)`



