# yarn

yarn 是 npm 的替代品。

- [安装](https://yarnpkg.com/en/docs/install)
- [changelog](https://github.com/yarnpkg/yarn/releases)

```sh
yarn --version
yarn --help
```

## Config

查看配置

```sh
yarn config list
```

yarn 会使用 [npm 的配置选项](https://docs.npmjs.com/misc/config)，比如 "init-license"。

设置缓存位置

```sh
yarn config set cache-folder <path>
```

使用 taobao 镜像

```sh
yarn config set registry https://registry.npm.taobao.org
```

配置文件为 `~/.yarnrc`。

yarn 1.3.0 可以在 npmrc 使用 `${HOME}`。

## Usage

[yarn 与 npm 命令对照表](https://yarnpkg.com/docs/migrating-from-npm)

```sh
yarn # 同 yarn install
npm  # 同 npm -h
```

yarn 没有缩写命令，比如 list 不能缩写为 ls。
也没有命令别名，比如 remove 没有别名 rm, info 没有别名 show。

`yarn install` 安装 `package.json` 指定的模块，并创建 `yarn.lock`。模块默认安装目录为 `./node_modules`，注意是当前目录下的 `node_modules`，即使当前目录下不存在 `package.json`。

`yarn add` 添加模块（保存到 `package.json`）。如果当前目录下不存在 `package.json` 则创建一个。

`yarn clean`，清除已安装的模块中不必要的文件，在当前目录生成一个配置文件 `.yarnclean`。

### `yarn global`

`yarn global` 管理全局安装的模块。

`yarn global -h` 查看子命令。

`yarn global add`，将全局安装的模块添加为 global package 的 dependencies。

`yarn global dir` 查看 global package 所在目录，即 `$dir/global`。
[不能修改全局安装的位置](https://github.com/yarnpkg/yarn/issues/630)

`yarn global bin` 查看 global bin 目录的位置, 即 `$prefix/bin`。
这个目录应当添加到 PATH 中。
如果 yarn 没有设置 $prefix 则使用 npm 的 $prefix。查看 $prefix

```sh
yarn config get prefix
yarn config list
```

$prefix 必须和 dir 在同一个磁盘，不然 Windows 下生成的 `.cmd` 文件存在问题，无法启动。例如

```
@"%~dp0\C:\Users\yan\AppData\Local\Yarn\config\global\node_modules\.bin\mocha.cmd"   %*
```

### `yarn link`

在 `$dir/link` 目录下生成 module 的链接。
Windows 下 module bin 存在问题。
