# json

对 json 的读写是由 jsonfile 模块实现

### `readJson()`

调用 `jsonfile.readFile(filename, [options], callback)`

options

```
{
  // fs.readFile options
  encoding: undefined, // jsonfile 会将 buffer 转为 utf8 string。

  // own options
  throws = true, // JSON parse 出错时，true 抛错；false 不抛错并返回 null
}
```

### `writeJson()`

调用 `jsonfile.writeFile(filename, obj, [options], callback)`

```
{
  // fs.writeFile options
  encoding: 'utf8',

  // own options
  replacer: undefined,
  spaces: undefined,
  EOL: '/n',
}
```

### `outputJson()`

先判断文件所在目录是否存在，若不存在则创建。
然后调用 jsonfile.writeFile 创建文件。
