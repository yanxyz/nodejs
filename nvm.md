# nvm

[nvm](https://github.com/creationix/nvm#readme)，node 多版本管理工具，只用于 Linux 和 macOS。

`~/.bashrc`：
​
```bash
# 使用淘宝的镜像
export NVM_NODEJS_ORG_MIRROR=http://npm.taobao.org/mirrors/node
# 随 bash 启动
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"
# 默认启动 Node.js 6.x
nvm use 6
```
​
安装最新的 Node.js 并安装当前使用的 Node.js 的全局包, 不然新的版本没有全局包
​
```bash
nvm install node --reinstall-packages-from=node
```
