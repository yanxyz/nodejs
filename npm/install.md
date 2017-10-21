# 安装 npm

npm 随 Node.js 安装。如果不想使用 Node.js 自带的 npm，见下文。

## 升级

[Windows 升级 npm](https://github.com/npm/npm/wiki/Troubleshooting#upgrading-on-windows)。

Ubuntu 升级 npm:

```shell
# 最新的稳定版本
sudo apt-get install -g npm
# 最新的 LTS 版本
sudo apt-get install -g npm@lts
```

## 配置

[使用淘宝镜像](https://npm.taobao.org/)

### 改变 npm 的目录

在 Linux 下安装全局包时默认需要权限，一个解决办法是 [改变 npm 的默认目录](https://docs.npmjs.com/getting-started/fixing-npm-permissions#option-2-change-npms-default-directory-to-another-directory)。

Windows 下 npm 的默认目录在系统盘上，将它调整到非系统盘上比较好。在命令行中运行 `npm -h`，在末尾可以看到配置文件位置。我的配置：

```ini
cache = F:\Nodejs\npm-cache
prefix = F:\Nodejs\npm-g
python = F:\Python\Python27\python.exe
```

- cache 模块下载保存位置。
- prefix 模块全局安装的位置，需要将它添加到环境变量 PATH 中。
- python 安装原生模块时的工具。
