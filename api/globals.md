# Global Objects

一些模块的 API 已经在 global scope 中，不需要 require 它们：

- process
- console
- timers，setTimeout 等函数
- buffer

module wrapper 传递的参数，不是 global objects, 不过所有的模块都可以使用

- module
- exports
- require
- `__dirname`
- `__filename`

模块的顶层域不是 global scope，在模块的顶层域声明的变量不是 global objects。
