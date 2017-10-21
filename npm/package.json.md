# npm package.json

```sh
npm help package.json
```

package.json 是 node.js package meta file。必须指定 name 和 version。

### name

name

- 不能有大写字母

### scripts

将 npm 当作构建工具


### license

license 的值有下面几种

第一种：为 [SPDX license id](https://spdx.org/licenses/)

```jsson
"license": "MIT"
"license": "(MIT OR Apache-2.0)"
```

如果不是有效的 SPDX ID，会报错：

> Sorry, license should be a valid SPDX license expression

第二种：指定一个 license 文件，该文件应该在 package 根目录下

```json
"license" : "SEE LICENSE IN <filename>"
```

第三种：为私有，此时最好同时设置 `private: true`

```json
{ "license": "UNLICENSED" }
```

### engines

engines 不是强制性的，只给出 warning。

