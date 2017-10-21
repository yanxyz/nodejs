# ESLint

ESLint 用于检查 code style。

- [docs](https://eslint.org/)
- [changelog](https://github.com/eslint/eslint/releases)

## Usage

第一种方式，全局安装

```shell
npm install -g eslint
eslint --init # 要求当前目录或上级目录有 package.json
```

以问答的方式选择使用哪种 style：google, standard, airbnb，然后生成 `.eslintrc` 配置文件。

第二种方式，本地安装，这样不受全局安装的影响。在 `package.json` 中添加

```json
"scripts": {
  "lint": "eslint"
}
```

```sh
npm run lint
```

### Environments

[Specifying Environments](http://eslint.org/docs/user-guide/configuring#specifying-environments)

```js
/* eslint-env node, mocha */
```

### Globals

[Specifying Globals](http://eslint.org/docs/user-guide/configuring#specifying-globals)

```js
/* global var1:false, var2:false */
```

### Rules

[Configuring Rule](http://eslint.org/docs/user-guide/configuring)

[Rules](http://eslint.org/docs/rules/)
rule 默认关闭。在这个页面上有对号的是 `eslint:recommended` 开启的 rule。


### 实例

- <https://github.com/eslint/eslint/blob/master/.eslintrc.yml>


## Configure

为了最大的便利，ESLint 的配置方式非常灵活（复杂）。

配置来源有下面几种，配置最终会合并，优先级从高到低：

1. inline comment
1. command line arguments
1. `.eslintrc` 文件

### `.eslintrc`

`.eslintrc` 文件细分为下面格式，优先级从高到低：

1. `.eslintrc.js`,
1. `.eslintrc.yaml`,
1. `.eslintrc.yml`,
1. `.eslintrc.json`,
1. `.eslintrc` 废弃
1. `package.json`（`eslintConfig` 属性）

从当前文件所在目录开始向上查找 `.eslintrc` 文件，每个目录只取一种格式，然后把找到的所有文件合并起来，离文件最近的优先级最高。

如果没有找到 `.eslintrc` 文件，命令行也没有指定 `.eslintrc` 文件（`--config` 选项），则使用 `$HOME` 目录下的 `.eslintrc` 文件。

如果没看明白，建议看[源码](https://github.com/eslint/eslint/blob/master/lib/config.js#L242)。

### inline comments

在代码文件内以注释的方式指定配置，优先级最高，比较适合临时配置。

配置从配置所在的地方开始生效。

注意：适用于单行的配置用单行注释，适用于多行的配置用多行注释。


## 忽略文件

[Ignoring Files and Directories](https://eslint.org/docs/user-guide/configuring#ignoring-files-and-directories)

配置

- .eslintignore
- package.json `"eslintIgnore": []`

跟 .eslintrc 不同，只在当前工作目录下查找 .eslintignore。

默认规则为

```
/node_modules/*
/bower_components/*
```

我在 VSCode 下遇到一个问题，node_modules 在子目录下，ESLint 没有忽略它。默认规则匹配项目根目录下的 node_modules，因此创建 .eslintignore，添加规则

```
# 任意目录下的 node_modules
**/node_modules/*
```

文档上说 .eslintignore 和 .gitignore 规则一样，但是下面规则在 .gitignore 中有效，而在 .eslintignore 中无效

```
node_modules/
node_modules
```

似乎 .eslintignore 必须明确指定。


### async/await

添加下面配置：

```yaml
parserOptions:
    ecmaVersion: 2017
```

## code style

通用 code style：

- 2 个空格缩进
    html/js/css 文件的常常几百上千行，2 个空格缩进

- string 使用单引号
    html attribute 用双引号，js 使用单引号，处理 html 方便。

- 关键字后面要有一个空格，比如 if, while, function

- 操作符左右要有一个空格


### JavaScript Standard Style

[JavaScript Standard Style](http://standardjs.com/)

- 不使用分号
- 函数名字后面有一个空格
    原因是将函数定义和函数调用分开。
    <https://github.com/feross/standard/issues/217>
    我觉得这个理由并不是特别强，函数定义通常有 function 关键字。

`eslint --init` 选择 standard，会生成 `.eslintrc` 配置文件，并在本地安装 eslint 以及 standard 插件。

如果想全局使用，比如单个 JavaScript 文件（不创建项目），全局安装 eslint 以及 standard 插件，并在 `$HOME` 目录放一个 `.eslintrc` 文件。

### Airbnb

[Airbnb JavaScript Style](https://github.com/airbnb/javascript#readme)

- 使用分号
- 函数名字后面没有空格

## Plugins

"eslint-plugin-html" 检查 HTML 中的 JavaScript，HTML 文件格式除了 html 外，还支持 ejs, vue 等模板文件。

## Editors

ESLint 有一定的自动修复能力（`--fix` 选项），比如添加或删除分号。

编辑器安装 ESLint 插件后，可以比较方便的修复当前文件。

- [VSCode](../software/vscode/index.md)

