## 基本框架搭建
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

```











# money-note

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Lints and fixes files
```
yarn lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
