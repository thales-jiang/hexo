---
title: 模块开发
date: 2019-09-03 15:12:45
tags: npm vue module publish
---
# 目的
把一些常用的公共组件单独拿出来做成npm组件包，可以直接下载使用


# 好处
1. 一套组件，多个项目用，减少重复开发
2. 组件开发和项目开发可以同步进行
3. 组件可以多个版本轻松升降级


# 结构
文件 | 描述 
---------| ---------
vue.config.js | vue-cli配置
.npmignore | 发包过滤文件
package.json | npm包文件，发布公共组件来说，这里非常重要
packages | 模块源文件
┣ popup | 弹窗组件
┃ ┣ src | 源文件
┃ ┃ ┗ popup.vue | 实际文件
┃ ┗ index | 引导文件
┣ module | *其他的模块都按照popup的方式添加*
┗ index.js | 主文件，配置加载内容，以及需要依赖
lib | 模块(编译后，用来publish)
┣ dayu.umd.js | 糅合模式组件
┣ dayu.umd.min.js | 糅合模式组件(最小化)
┗ dayu.common.js | commonjs模式组件
examples | 模块示例，可以理解成以前的src
┣ router | 路由
┣ views | 页面
┃ ┣ popup.vue | 弹窗展示页面
┃ ┗ page | *其他页面文件按照都按照popup的方式添加*
┣ app.vue | 
┗ main.js | 入口文件
public | 公共模板，给examples用的

## 组件
以前做项目基本就是一个src为源文件，一个dist为生成文件  
但是做组件，肯定要有packages为组件源文件，lib为组件的生成文件。可以理解为src和dist，生成组件就是build   
```shell
vue-cli-service build --target lib --name dayu --dest lib packages/index.js
```
我们创造一个lib，名称为dayu，从packages/index.js文件创造  
vue-cli-service的各种命令，可以去官网 https://cli.vuejs.org/zh/guide/cli-service.html#使用命令
## 示例
examples是示例页面，就是专门做一个页面去调试一下packages的组件  
以前dev和build都是编译src的内容，现在build是生成lib组件，dev是新打开一个示例页面去测试lib的组件
```js
// examples/main.js
import Vue from 'vue';
import router from './router';
import app from './app';
import dayu from '../packages'; // 载入组件源码

Vue.use(dayu); // 应用组件

Vue.config.productionTip = false;

new Vue({
  router,
  render: h => h(app)
}).$mount('#app');
```
因为把src改成了examples，需要修改webpack的配置，我们使用的vue-cli，有专门的vue配置
```js
// vue.config.js
const path = require('path');
module.exports = {
  pages: { // 将 examples 目录添加为新的页面
    index: {
      entry: 'examples/main.js', // page 的入口
      template: 'public/index.html', // 模板来源
      filename: 'index.html' // 输出文件名
    }
  },
  css: { extract: false }, // css文件不分离
  configureWebpack: {
    resolve: {
      alias: {
        '@': path.join(__dirname, 'examples') // @的根目录位置从之前的src改成了examples
      }
    }
  }
};
```
vue.config的各种配置可以看 https://cli.vuejs.org/zh/config/#pages

