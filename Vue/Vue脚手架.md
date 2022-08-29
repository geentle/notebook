# Vue CLI脚手架

---

> Vue CLI: Vue **C**ommand **L**ine **I**nterface

### 安装

* 下载慢可配置npm淘宝镜像 `npm config set registry http://registry.npm.taobao.org`
* 全局安装 @vue/cli 命令 `npm install -g @vue/cli`
* 创建新项目 `vue create project-name`
* 启动项目 `npm run serve`
* 打包项目 `npm run build`

> Vue脚手架隐藏了所有`webpack`相关配置，若想查看具体的`webpack`配置，执行 `vue inspect > output.js` 命令

### 脚手架文件结构
```
.文件目录
├── node_modules 
├── public
│   ├── favicon.ico: 页签图标
│   └── index.html: 主页面
├── src
│   ├── assets: 存放静态资源
│   │   └── logo.png
│   │── component: 存放组件
│   │   └── HelloWorld.vue
│   │── App.vue: 汇总所有组件
│   └── main.js: 入口文件
├── .gitignore: git版本管制忽略的配置
├── babel.config.js: babel的配置文件
├── package.json: 应用包配置文件 
├── README.md: 应用描述文件
└── package-lock.json: 包版本控制文件
```

### 关于不同版本的Vue

脚手架创建的`Vue`项目中，默认引入的`Vue`版本是`vue.runtime.esm.js`
* `vue.js`与`vue.runtime.esm.js`的区别
  * `vue.js`是完整版的`Vue`，包含核心功能+模板解析器
  * `vue.runtime.esm.js`是运行版的`Vue`，只包含核心功能。`esm`指ES6 module。
  * 其他版本的`Vue`类似，是完整版的删减版本。

### vue.config.js配置文件

使用vue.config.js可以修改脚手架的默认配置。详见[配置参考](https://cli.vuejs.org/zh/config/#vue-config-js)