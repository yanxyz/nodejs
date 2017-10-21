# npm cli

```bash
npm install -h  # 简短帮助
npm help install # 详细帮助，Windows 下是在浏览器中打开帮助页面。
```

查看帮助。

```sh
npm init
```

通过问答创建 package.json，如果已存在则是修改。
author, license 等默认值可以由 [config](config.md) 命令修改。


```sh
npm docs express
```

打开 package 的主页，通常是 Github 页面。


## view

view 查看 package 信息

```sh
npm view express # 查看完整信息，会很长

npm view express version # 查看最新版本
npm view express version # 查看最新版本

npm view express dependencies
```

```bash
# 查找模块
npm search express

# 安装模块，并将它保存到 package.json
npm install --save express
```
