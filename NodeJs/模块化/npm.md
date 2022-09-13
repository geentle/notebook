# npm

---

### npm安装模块

```shell
$ npm install <Module Name>
$ npm install <Module Name>@version
```

### 使用Node.js模块
```javascript
var express = require('express');
```

### 全局安装和本地安装
```shell
$ npm install express          # 本地安装
$ npm install express -g   # 全局安装
```

如果出现以下错误：
```
npm err! Error: connect ECONNREFUSED 127.0.0.1:8087
```

解决办法为：

```shell
$ npm config set proxy null
```

#### 本地安装
1. 将安装包放在 ./node_modules 下（运行 npm 命令时所在的目录），如果没有 node_modules 目录，会在当前执行 npm 命令的目录下生成 node_modules 目录。
2. 可以通过 require() 来引入本地安装的包

#### 全局安装
1. 将安装包放在 /usr/local 下或者你 node 的安装目录。
2. 可以直接在命令行里使用。

### 查看安装信息

查看所有全局安装模块
```shell
$ npm list -g
```
查看某个模块版本号
```shell
$ npm list grunt
```

### 使用 package.json

package.json 位于模块的目录下，用于定义包的属性。记录项目都用了哪些包。

* name - 包名。

* version - 包的版本号。

* description - 包的描述。

* homepage - 包的官网 url 。

* author - 包的作者姓名。

* contributors - 包的其他贡献者姓名。

* dependencies - 依赖包列表。如果依赖包没有安装，npm 会自动将依赖包安装在 node_module 目录下。

* repository - 包代码存放的地方的类型，可以是 git 或 svn，git 可在 Github 上。

* main - main 字段指定了程序的主入口文件，require('moduleName') 就会加载这个文件。这个字段的默认值是模块根目录下面的 index.js。

* keywords - 关键字

#### 快速创建package.json
```shell
$ npm init -y
```
> 注意：运行 `npm install` 命令安装包的时候，npm管理工具会自动把包的名称和版本号记录到`package.json`中。
> 使用 `npm install` 命令会去安装`package.json`的`dependencies`节点配置的所有包

### 卸载和更新模块
```shell
# 卸载
$ npm uninstall express

# 更新
$ npm update express
```

### 包的语义化版本规范

eg: 2.22.1

第一个数字：大版本
第二个数字：功能版本
第三个数字：bug修复版本