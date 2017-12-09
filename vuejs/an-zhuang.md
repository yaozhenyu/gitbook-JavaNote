## &lt;直接 `<script>` 引入 {#直接-lt-script-gt-引入}

推荐：[https://cdn.jsdelivr.net/npm/vue](https://cdn.jsdelivr.net/npm/vue)，会保持和 npm 发布的最新的版本一致。可以在[https://cdn.jsdelivr.net/npm/vue/](https://cdn.jsdelivr.net/npm/vue/)

浏览 npm 包资源。

```
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```

## NPM {#NPM}

在用 Vue.js 构建大型应用时推荐使用 NPM 安装，NPM 能很好地和诸如 `Webpack` 或 `Browserify `模块打包器配合使用。Vue.js 也提供配套工具来开发**单文件组件**。

```
# 最新稳定版 
$ npm install vue
```

## 命令行工具 \(CLI\) {#命令行工具-CLI}

```
# 全局安装 vue-cli
$ npm install --global vue-cli
# 创建一个基于 webpack 模板的新项目
$ vue init webpack my-project
# 安装依赖，走你
$ cd my-project
$ npm install
$ npm run dev
```



