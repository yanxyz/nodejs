# opn

打开程序，文件，网址等。

`opn(target, [options])`

options

```js
{
  wait: true,
}
```

## Windows

Windows 是通过 [start 命令](/note/cmd/utils/start/) 启动程序。

```js
opn(target, {
  wait: true,
  app: [ program, ...programArgs ]
})

// cmd /c 'start' '""' '/b' '/wait' program programArgs target
```

'/wait'，对于 GUI 程序，需要程序提供支持，浏览器一般没有。
cmd 在启动浏览器后，不会等待浏览器关闭便返回，随即结束运行。

## Linux

使用 opn 自带的 xdg-open 启动程序。
