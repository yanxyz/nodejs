# install

```sh
npm install sqlite3
```

sqlite3 是 native module，容易安装失败。

npm 在下载 sqlite3 package 之后，运行 install script

```sh
npm view sqlite3 scripts
# install: 'node-pre-gyp install --fallback-to-build'
```

node-pre-gyp 先尝试下载 pre-compiled binary，若失败则编译安装。
binary 的地址根据 package binary field 生成，例如

```
https://mapbox-node-binary.s3.amazonaws.com/sqlite3/v3.1.13/node-v57-win32-x64.tar.gz
```

上面地址需要代理。
node-pre-gyp 提供一种方案，见 [versioning.js](https://github.com/mapbox/node-pre-gyp/blob/master/lib/util/versioning.js#L303)。
使用淘宝镜像

```sh
npm install sqlite3 --node_sqlite3_binary_host_mirror=http://npm.taobao.org/mirrors

// or
npm config set node_sqlite3_binary_host_mirror=http://npm.taobao.org/mirrors/
npm install sqlite3
```

每次安装都要下载 binary，可以将下载的 tar.gz 文件放在本机的本机的服务器上

```sh
npm install sqlite3 --node_sqlite3_binary_host_mirror=http://localhost/mirrors
```

当 node 升级 major 时，需要等待 sqlite3 升级。 功夫好的，可以编译安装。

## 编译安装

参考 sqlite3 readme

```sh
npm view sqlite3 dist-tags
npm docs sqlite3
```

### Windows

[Compiling native Addon modules](https://github.com/Microsoft/nodejs-guidelines/blob/master/windows-environment.md#compiling-native-addon-modules)
