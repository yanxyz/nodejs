# 安装 Node.js

## Windows

下载安装程序

- [官网](https://nodejs.org/)
- [淘宝镜像](https://npm.taobao.org/mirrors/node/)

安装完成之后，在命令行中运行下面命令，看看是否正常:
​
```bat
node -v
npm -v
```
​
可以用 [nvmw](https://github.com/hakobera/nvmw) 安装不同版本的 node.js，同时会安装 npm，但是它下载的是 npm 的源码包，而包内的文档需要编译后才能使用。
​
## Linux
​
[Installing Node.js via package manager](https://nodejs.org/en/download/package-manager/)

Ubuntu:
​
```bash
sudo apt-get install nodejs
node -v
```
​
Debian 的 node.js 版本比较旧，可以使用 [NodeSource 的源](https://github.com/nodesource/distributions#readme)。

多版本可以用 [nvm](nvm.md)。
​
