## 目录说明
| 目录/文件 | 说明 |
|-------|-------|
| node_modules | npm 加载的项目依赖模块 |
| src | 这里是我们要开发的目录，基本上要做的事情都在这个目录里 |
| assets | 放置一些图片，如logo等。 |
| components | vue组件文件的存放目录,也是主要的工作目录 |
| App.vue | 项目入口文件，我们也可以直接将组件写这里，而不使用 components 目录。 |
| main.js | 项目的核心文件。 |
| index.html | 首页入口文件，你可以添加一些 meta 信息或统计代码啥的。 |
| package.json | 项目配置文件。 |
| README.md | 项目的说明文档，markdown 格式 |
## index.html
> 启动页面 <div id="app">为后续的vue文件提供可替换的壳标签
```
<!DOCTYPE html>
<html lang="">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <link rel="icon" href="<%= BASE_URL %>favicon.ico">
    <title><%= htmlWebpackPlugin.options.title %></title>
  </head>
  <body>
    <noscript>
      <strong>We're sorry but <%= htmlWebpackPlugin.options.title %> doesn't work properly without JavaScript enabled. Please enable it to continue.</strong>
    </noscript>
    <div id="app"></div>
    <!-- built files will be auto injected -->
  </body>
</html>
 
```
## main.js
入口文件，功能有两个：
> 1、导入vue框架；
> 2、将App.vue的内容挂载(替换)到index.html的div id="app"标签

```
import { createApp } from 'vue'
import App from './App.vue'
 
createApp(App).mount('#app')
 
```
## App.vue：第一个vue文件
```
<!-- 
  一、Vue的文件结构为三段式
    1.template负责页面元素搭建
    2.script负责js代码
    3.style负责css样式
  二、使用其他的vue组件分两步
    1.导入：
      1.1在js方法中import组件
      1.2在export default中使用components注册组件
    2.使用：
      在template中使用组件标签
-->
<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>  <!-- 在template中使用组件标签 -->
</template>
 
<script>
import HelloWorld from './components/HelloWorld.vue' // 在js方法中import组件
 
export default {
  name: 'App',
  components: {
    HelloWorld        // 在export default中使用components注册组件
  }
}
</script>
 
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
 
```
## HelloWorld.vue
展示页面
```
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      <a href="https://cli.vuejs.org" target="_blank" rel="noopener">vue-cli documentation</a>.
    </p>
  </div>
</template>
 
<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>
 
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
```