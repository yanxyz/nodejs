# npm install

```sh
npm install -h
npm help install
```

npm@5 `npm install` 默认保存到 package.json，并生成 `package-lock.json`。

options：

```sh
--no-save  # npm 5.0+，不保存到 package.json dependencies
--save     # npm < 5.0，保存到 package.json dependencies
--save-dev

--save-optional
--no-optional

--save-prod
--save-exact
```

examples:

```sh
# 全局安装
npm i -g webpack

# 限制版本
npm i koa@next
npm view koa dist-tags

npm i sax@">=0.1.0 <0.2.0"

# 强制重新安装
npm i sax --force

# 私有模块
npm i @types/

# 从 github 安装某个分支
npm i gulpjs/gulp#4.0

npm shrinkwrap  # 生成 npm-shrinkwrap.json
npm i --no-shrinkwrap
```

## install native modules

native modules 如 sqlite3、node-sass 等，它们可能已经提供了编译好的 binary，不过被墙无法正常下载。

### 本地编译

需要准备：

- [编译环境](https://github.com/Microsoft/nodejs-guidelines/blob/master/windows-environment.md#prerequisites)
- Node.js 头文件，[下载办法](https://github.com/mafintosh/node-gyp-install)

```sh
set "PYTHON_MIRROR=http://npm.taobao.org/mirrors/python"
npm install --global --production windows-build-tools
```

### 使用国内镜像

<https://npm.taobao.org/mirrors> 为常用的模块提供镜像。

```shell
# 将 sqlite3 添加到 npm 配置中
npm config set SQLITE3_BINARY_SITE=http://npm.taobao.org/mirrors/sqlite3
```
