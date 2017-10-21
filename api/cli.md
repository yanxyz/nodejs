# Node.js Command Line Options

## V8

[ECMAScript 2015 (ES6) and beyond](https://nodejs.org/en/docs/es6/) 提到，node.js 搭载的 ECMAScript 功能分为三类：

- shipping 稳定，默认开启。
- staged 不稳定，用 `--harmony` 选项开启。
- in progress 开发中，需要用单独的选项开启。运行 `node --v8-options | grep "in progress"` 查看。

可以去网站 [node.green](http://node.green/) 查看 ECMAScript 兼容列表。

