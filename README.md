# README

## 运行

```shell
# 安装nodejs：
choco install nodejs

# 安装yarn
npm install -g yarn

# 修改yarn源地址
yarn config set registry https://registry.npm.taobao.org/

# 安装vue-cli
yarn global add @vue/cli

# 克隆项目
git clone https://github.com/SsrCoder/money-note.git
cd money-note

# 获取依赖
yarn

# 运行项目
yarn run electron:serve
```

## 项目搭建记录

### 基本框架搭建

```shell
# 安装nodejs：
choco install nodejs

# 安装yarn
npm install -g yarn

# 修改yarn源地址
yarn config set registry https://registry.npm.taobao.org/

# 安装vue-cli
yarn global add @vue/cli
# 安装vue-cli-init
yarn global add @vue/cli-init
# 安装npm-check-updates用于更新依赖
yarn global add npm-check-updates

# 初始化vue项目(根据个人喜好选择，我这里除了testing以外全开启了)
vue create money-note

# 进入项目目录
cd money-note

# 添加electron插件
vue add electron-builder

# 更新项目依赖
ncu -u

# 获取依赖
yarn

# 运行
yarn run electron:serve

# git提交
git add .
git commit -m "init"
```

### 配置eslint

```js
module.exports = {
    root: true,
    env: {
        node: true
    },
    'extends': [
        'plugin:vue/essential',
        'eslint:recommended',
        '@vue/typescript/recommended'
    ],
    parserOptions: {
        ecmaVersion: 2020
    },
    rules: {
        'no-console': process.env.NODE_ENV === 'production' ? 'warn' : 'off',
        'no-debugger': process.env.NODE_ENV === 'production' ? 'warn' : 'off',
        // 不检测语句末尾的分号
        'semi': ['off', 'always'],
        // 强制缩进为2个空格
        'indent': ['error', 2]
    }
}
```

### 配置vue

```js
const path = require('path');

function resolve (dir) {
  return path.join(__dirname, dir);
}

module.exports = {
  publicPath: './',
  devServer: {
    // can be overwritten by process.env.HOST
    host: '0.0.0.0',  
    port: 8080
  },
  chainWebpack: config => {
    config.resolve.alias
      .set('@', resolve('src'))
      .set('src', resolve('src'))
      .set('common', resolve('src/common'))
      .set('components', resolve('src/components'))
  }
}
```

### 安装Vuetify

```shell
vue add vuetify
```

在 tsconfig.json 中 compilerOptions -> types 数组中添加 "vuetify"

```json
{
  "compilerOptions": {
    "target": "esnext",
    "module": "esnext",
    "strict": true,
    "jsx": "preserve",
    "importHelpers": true,
    "moduleResolution": "node",
    "experimentalDecorators": true,
    "esModuleInterop": true,
    "allowSyntheticDefaultImports": true,
    "sourceMap": true,
    "baseUrl": ".",
    "types": [
      "webpack-env",
      "vuetify"
    ],
    "paths": {
      "@/*": [
        "src/*"
      ]
    },
    "lib": [
      "esnext",
      "dom",
      "dom.iterable",
      "scripthost"
    ]
  },
  "include": [
    "src/**/*.ts",
    "src/**/*.tsx",
    "src/**/*.vue",
    "tests/**/*.ts",
    "tests/**/*.tsx"
  ],
  "exclude": [
    "node_modules"
  ]
}
```

### 引入 Material Design 图标

```shell
yarn add material-design-icons-iconfont
```

在main.ts 中添加

```ts
import 'material-design-icons-iconfont/dist/material-design-icons.css'
```

### 修改窗口样式

```ts
  win = new BrowserWindow({
    width: 800,
    height: 600,
    frame: false, // 取消边框
    transparent: true, // 背景透明
    webPreferences: {
      nodeIntegration: true
    }
  })
```
