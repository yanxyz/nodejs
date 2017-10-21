# child_process

其它方法都是建立在 spawn() 基础上。

- `spawn(command, args)`
- `exec(command, options)` 派生 shell，由它运行 command
- `execFile(executable, args)` 直接派生 executable
- `fork(modulePath)` 派生 Node.js，由它运行 module


`exec(command, options)`, 返回 ioptions.encoding 默认是 'utf8'

`execSync(command, options)` 返回 stdout，encoding 默认是 'buffer'。


## 资料

- [opn](https://github.com/sindresorhus/opn/)
- [execa](https://github.com/sindresorhus/execa/)

