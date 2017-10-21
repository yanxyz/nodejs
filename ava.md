# AVA

AVA 是测试框架

- [docs](https://github.com/avajs/ava#readme)
- [changelog](https://github.com/avajs/ava/releases)

```sh
npm install --global ava
ava --init
npm test # run tests
```

## 用法

```sh
ava --help
```

忽略目录

- fixtures
- helpers
- node_modules

忽略名字以 _ 开始的文件，方便为测试提供配套。

ava -- --verbose
不指定测试文件时，要

ava --match='*foo'
Match titles ending with foo
不区分大小写
.only 无效

## 配置

"babel": "inherit"
意思是使用项目的 babel 配置
