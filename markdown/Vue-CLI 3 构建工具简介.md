# Vue-CLI 3构建工具介绍

## 简介

Vue CLI 是一个基于 Vue.js 进行快速开发的完整功能，wapback 针对性2次开发，提供如下功能：

* 通过 `@vue/cli` 搭建交互式的项目脚手架。
* 通过 `@vue/cli` + `@vue/cli-service-global` 快速开始零配置原型开发。
* 一个运行时依赖（`@vue/cli-service`）,该依赖：

  * 可升级；
  * 基于 webpack 构建，并带有合理的默认配置；
  * 可以通过项目内的配置文件进行配置；
  * 可以通过插件进行扩展。
* 一个丰富的官方插件集合，集成了前端生态中最好的工具。
* 一套完全图形化的创建和管理 Vue.js 项目的用户界面。

### CLI

CLI（`@vue/cli`）是一个全局安装的 npm 包，提供了终端里的 vue 命令。

### CLI 服务

CLI 服务（`@vue/cli-service`）是一个开发环境依赖。它是一个 npm 包，局部安装在每个 @vue/cli 创建的项目中，提供了 vue-cli-service 命令。

### CLI 插件

CLI 插件是向你的 Vue 项目提供可选功能的 npm 包。

## 目录分析 （vue-cli 工具生成目录，包含vue-router,vuex）

```bash
hello-world                     # 项目名
├── babel.config.js             # babel 语法编译
├── dist                        # 打包后文件夹
|  ├── css                      # 打包后 css 文件
|  ├── favicon.ico              # 页面图标
|  ├── img                      # 打包后图片文件
|  ├── index.html               # 打包后入口文件
|  └── js                       # 打包后 js 文件
├── package-lock.json           # 记录当前安装的 npm 包确实的版本，类似快照
├── package.json                # 记录了 npm 包，但是记录的是个版本范围，如 ^1.1.1 需兼容的版本
├── postcss.config.js           # PostCSS 配置文件
├── public                      # 打包前入口文件夹
|  ├── favicon.ico              # 打包前页面图标
|  └── index.html               # 打包前入口文件
├── README.md                   # 项目简介说明文件
├── .browserslistrd             # 记录需要适应的浏览器版本与 Node.js 版本 可以记录在 package.json 中
├── .editorconfig               # 统一代码格式的解决方案配置 可以记录在 package.json 中
├── .eslintrc.js                # eslint 配置文件 可以记录在 package.json 中
├── .gitignore                  # 记录提交 git 的时候需要忽略的文件
└── src                         # 项目源码目录
   ├── App.vue                  # 项目入口 Vue 文件
   ├── assets                   # 静态资源，例如图片等
   ├── components               # 项目组件
   ├── main.js                  # 项目入口 js 文件，加载各种组件，与一些全局配置
   ├── router.js                # 项目路由组件
   ├── store.js                 # 项目 Vuex 组件
   └── views                    # 项目视图组件文件夹
      ├── About.vue             # 项目视图组件
      └── Home.vue              # 项目视图组件
```

## 配置文件 package.json

### 文件初始内容

package.json

```json
{
  "name": "hello-world",                    # 项目名
  "version": "0.1.0",                       # 项目版本号
  "private": true,                          # 开源还是私人项目
  "scripts": {                              # 指定运行脚本的 npm 命令行缩写
    "serve": "vue-cli-service serve",       # npm serve = vue-cli-service serve
    "build": "vue-cli-service build",       # 同上   
    "lint": "vue-cli-service lint"          # 同上
  },
  "dependencies": {                         # 当前项目的依赖包及版本要求
    "core-js": "^2.6.5",
    "vue": "^2.6.10",
    "vue-router": "^3.0.3",
    "vuex": "^3.0.1"
  },
  "devDependencies": {                      # 当前开发环境依赖包及版本要求
    "@vue/cli-plugin-babel": "^3.8.0",      
    "@vue/cli-plugin-eslint": "^3.8.0",
    "@vue/cli-service": "^3.8.0",
    "@vue/eslint-config-airbnb": "^4.0.0",
    "babel-eslint": "^10.0.1",
    "eslint": "^5.16.0",
    "eslint-plugin-vue": "^5.0.0",
    "lint-staged": "^8.1.5",
    "vue-template-compiler": "^2.6.10"
  },
  "gitHooks": {                             # git 钩子
    "pre-commit": "lint-staged"             # 在 commit 之前执行的脚本
  },
  "lint-staged": {                          # lint-staged 脚本内容
    "*.{js,vue}": [
      "vue-cli-service lint",               # 运行的命令
      "git add"
    ]
  }
}

```

package-lock.json

```json
{
  "name": "hello-world",                        # 项目名
  "version": "0.1.0",                           # 项目版本
  "lockfileVersion": 1,                         # 该 lock 文件版本
  "requires": true,
  "dependencies": {                             # 安装的项目依赖包信息
    "@babel/code-frame": {                      # 安装的依赖包名称
      "version": "7.0.0",                       # 安装的依赖包版本
      "resolved": "http://registry.npm.taobao.org/@babel/code-frame/download/@babel/code-frame-7.0.0.tgz",
      # 安装依赖依赖包的下载地址
      "integrity": "sha1-BuKrGb21NThVWaq7W6WXKUgoAPg=", # 依赖包的 Subresource Integrity 验证
      "dev": true,                              # 是否是开发依赖
      "requires": {                             # 该 npm 包的依赖
        "@babel/highlight": "^7.0.0"            # 依赖的版本要求
      }
    },
    "@babel/core": {                            # 同上
      "version": "7.4.5",
      "resolved": "https://registry.npm.taobao.org/@babel/core/download/@babel/core-7.4.5.tgz",
      "integrity": "sha1-CB+X6P/KZam0sP3H4nTnA/AAwGo=",
      "dev": true,
      "requires": {
        "@babel/code-frame": "^7.0.0",
        "@babel/generator": "^7.4.4",
        "@babel/helpers": "^7.4.4",
        "@babel/parser": "^7.4.5",
        "@babel/template": "^7.4.4",
        "@babel/traverse": "^7.4.5",
        "@babel/types": "^7.4.4",
        "convert-source-map": "^1.1.0",
        "debug": "^4.1.0",
        "json5": "^2.1.0",
        "lodash": "^4.17.11",
        "resolve": "^1.3.2",
        "semver": "^5.4.1",
        "source-map": "^0.5.0"
      }
    },
    ......
    ......
    ......
  }
}
```

### 修改配置文件内容

> 配置文件修改[官方参考文件](https://cli.vuejs.org/zh/config/#runtimecompiler)
>> 日后有时间完善下列内容

* 浏览器兼容性
* HTML 和静态资源
* CSS 相关
* webpack 相关
* 环境变量和模式
* 构建目标
* 部署

## 附录

### 常用 npm 指令

```bash
# 生成 package.json 文件（需要手动选择配置）
npm init

# 生成 package.json 文件（使用默认配置）
npm init -y

# 一键安装 package.json 下的依赖包
npm i

# 在项目中安装包名为 xxx 的依赖包（配置在 dependencies 下）
npm i xxx

# 在项目中安装包名为 xxx 的依赖包（配置在 dependencies 下）
npm i xxx --save

# 在项目中安装包名为 xxx 的依赖包（配置在 devDependencies 下）
npm i xxx --save-dev

# 全局安装包名为 xxx 的依赖包
npm i -g xxx

# 运行 package.json 中 scripts 下的命令
npm run xxx
```

### 常用 vue-cli 命令

```bash

vue serve

Usage: serve [options] [entry]

在开发环境模式下零配置为 .js 或 .vue 文件启动一个服务器


Options:

  -o, --open  打开浏览器
  -c, --copy  将本地 URL 复制到剪切板
  -h, --help  输出用法信息
```

```bash
vue build

Usage: build [options] [entry]

在生产环境模式下零配置构建一个 .js 或 .vue 文件


Options:

  -t, --target <target>  构建目标 (app | lib | wc | wc-async, 默认值：app)
  -n, --name <name>      库的名字或 Web Components 组件的名字 (默认值：入口文件名)
  -d, --dest <dir>       输出目录 (默认值：dist)
  -h, --help             输出用法信息
```

```bash
vue create

用法：create [options] <app-name>

创建一个由 `vue-cli-service` 提供支持的新项目


选项：

  -p, --preset <presetName>       忽略提示符并使用已保存的或远程的预设选项
  -d, --default                   忽略提示符并使用默认预设选项
  -i, --inlinePreset <json>       忽略提示符并使用内联的 JSON 字符串预设选项
  -m, --packageManager <command>  在安装依赖时使用指定的 npm 客户端
  -r, --registry <url>            在安装依赖时使用指定的 npm registry
  -g, --git [message]             强制 / 跳过 git 初始化，并可选的指定初始化提交信息
  -n, --no-git                    跳过 git 初始化
  -f, --force                     覆写目标目录可能存在的配置
  -c, --clone                     使用 git clone 获取远程预设选项
  -x, --proxy                     使用指定的代理创建项目
  -b, --bare                      创建项目时省略默认组件中的新手指导信息
  -h, --help                      输出使用帮助信息
```

```bash
vue ui            #图形化界面创建和管理项目
```

```bash
vue-cli-service serve

用法：vue-cli-service serve [options] [entry]

选项：

  --open    在服务器启动时打开浏览器
  --copy    在服务器启动时将 URL 复制到剪切版
  --mode    指定环境模式 (默认值：development)
  --host    指定 host (默认值：0.0.0.0)
  --port    指定 port (默认值：8080)
  --https   使用 https (默认值：false)
```

```bash
vue-cli-service build

用法：vue-cli-service build [options] [entry|pattern]

选项：

  --mode        指定环境模式 (默认值：production)
  --dest        指定输出目录 (默认值：dist)
  --modern      面向现代浏览器带自动回退地构建应用
  --target      app | lib | wc | wc-async (默认值：app)
  --name        库或 Web Components 模式下的名字 (默认值：package.json 中的 "name" 字段或入口文件名)
  --no-clean    在构建项目之前不清除目标目录
  --report      生成 report.html 以帮助分析包内容
  --report-json 生成 report.json 以帮助分析包内容
  --watch       监听文件变化
```

```bash
vue-cli-service inspect

用法：vue-cli-service inspect [options] [...paths]

选项：

  --mode    指定环境模式 (默认值：development)
```

```bash
vue add
vue add @vue/eslint
#vue add 的设计意图是为了安装和调用 Vue CLI 插件。对于普通的 npm 包而言，这不意味有一个替代（命令）。对于这些普通的 npm 包，你仍然需要（根据所选的 npm 包）使用包管理器。以 @vue/cli-plugin- 开头
```
