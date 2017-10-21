# path

path 处理路径。Linux 和 Windows 两个平台的路径规则迥异，所以 path 分为 path.posix 和 path.win32

```js
const path = require('path')
path.posix.basename('C:\\Users') // 'C:\\Users'
path.win32.basename('C:\\Users') // 'Users'
path.basename('C:\\Users')       // 根据当前平台使用 path.posix 或 path.win32
```

在 Linux 下处理 Windows 路径，需要明确使用 path.win32 才能正确处理路径。

Linux

- root path 为 '/'
- path separator(path.sep) 为 '/'
- path delimiter(path.delimiter, PATH 环境变量当中路径定界符) 为 ':'

Windows

- root path，例如 `C:\\` 为 C 盘根目录，`\\` 为当前盘的根目录
- path separator 为 '\\'
- path delimiter 为 ';'

Windows 路径不区分大小写，在判断是否为同一位置时要小心。

path 的方法，若无特别说明，它们有以下共同点：

- 参数必须是 strings，其它类型不会隐式转换，会抛出错误。

其它相关方法

- `process.cwd()` 盘符大小写不定。
- `process.chdir(directory)` 改变当前目录
- `os.homedir()`
- `os.tmpdir()`

### `path.join([...paths])`

参数可选，不传入参数时返回 '.'。

先用 path.sep 拼接参数（不管是不是 root path），然后 normalize（见 path.normalize）。

```js
path.posix.join('/foo', '/bar/') // "/foo/bar/"
```

### `path.normalize(path)`

一个必选参数。

处理路径当中的 `..`, `.`, 连续的 path.sep 等。

末尾的 path.sep 保留。

```js
path.posix.normalize('/foo///.//../../../bar/') // "/bar/"
```

### `path.relative(from, to)`

两个必选参数。

先对两个参数调用 path.resolve，将它们转为绝对路径（这意味着 "" 转为当前目录），然后返回它们的相对值。若它们指向相同位置，则返回 ""。

### `path.resolve([...paths])`

参数可选。

参数列表，从后向前逐步构造路径，若构造出绝对路径，则不再进行下去，返回这个绝对路径；若到最后是一个相对路径，则相对于当前目录返回一个绝对路径。因此，不传入参数时返回当前目录（`process.cwd()`）。

返回的路径会 normalize，跟 path.normalize 不一样的是，不保留末尾 path.sep。

Windows 有一种特殊的相对路径（per-drive working directory），比如

- "C:tmp.txt" 表示 C 盘当前目录下的 tmp.txt

假定当前目录为 "F:\\tests"

```js
path.win32.resolve('C:\\tmp.txt')   // "C:\\tmp.txt"
path.win32.resolve('C:tmp.txt')     // "C:tmp.txt"
path.win32.resolve('F:tmp.txt')     // "F:\\tests\\tmp.txt"
path.win32.isAbsolute('C:tmp.txt')  // false
```
