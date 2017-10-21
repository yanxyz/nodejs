# File System

fs API 是 POSIX functions 的包装，所以名字和行为跟 Shell commands 类似。

与 dir 相关的方法的格式 xxxdir, 如 readdir;
与 file 相关的方法的格式 xxxFile, 如 readFile。

Node v7.0+，省略 callback 会收到 warning。

## 目录操作

### readdir

- 只读取一层，不递归读取
- callback(err, files), files 只是 basename, 不是 fullname

遍历目录

### mkdir

- 不能创建多级目录
- 目录已存在则报错
- callback(err)

相关目录

- make-dir 创建多级目录

### rmdir

删除空目录。

用在文件上报错，error.code 在 Windows 下为 `ENOENT`，在 POSIX 下为 `ENOTDIR`。

### mkdtemp

创建一个临时目录，名字为 prefix + six random characters

```js
fs.mkdtemp(path.join(os.tmpdir(), 'foo-'), (err, folder) => {
  // folder 为 full path
}
```

## 文件操作

### readFile

options.encoding 默认值为 null，返回 buffer。若想返回 string, 指定 encoding. Node.js 支持的 encoding 见 buffer。

```js
fs.readFile(path, 'utf8', callback)
```

### writeFile

跟 readFile 不同，options.encoding 默认为 'utf8'。

```js
fs.writeFile(path, callback)
```

### appendFile




### copyFile

复制文件。若 dest 存在则覆盖，不想覆盖则指定 flags 参数：

```js
fs.copyFile(src, dest, fs.constants.COPYFILE_EXCL, callback)
```

若复制过程中出错则删掉 dest。


### rename

重命名（移动）文件。

newPath，需要保证目录都存在，不然报错。

### existsSync

判断文件是否存在。

异步方法 exists 废弃。异步方法 existsSync 没有废弃。

## 链接操作

### readlink

### symlink

### unlink


## 通用操作

通用，即对文件和目录均适用。

### fchmod

change a files mode bits，即文件权限。

### fchown

change file ownership。

###

### realpath


### stat


若 path 是 symbolic link，lstat 若

### watch

watchFile, 用 unwatchFile 取消监视。


## 第三方模块


- fs-extra 常见功能集合
