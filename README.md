# Vue.js音乐播放器
Vue全家桶打造的一款音乐播放器

## 预览

在线预览地址：[Vue音乐播放器](http://lenshen.com:8000)

演示：
![](https://github.com/lensh/vue-music/blob/master/preview/my.gif)

## 技术栈
**Vue2**：采用最新Vue2的语法

**Vuex**：实现不同组件之间的状态共享

**vue-router**：单页应用路由管理必备

**axios**：发起http请求

**SASS(SCSS)**：css预处理语言

**Express**(上线版本是**Koa2**)：因为vue-cli是用的Express做服务器，所以开源的开发版本是Express，自己生产环境用的是Koa2。 😜 

**Webpack**：自动化构建工具，大部分配置vue-cli脚手架已经弄好了，很方便。

**ES6**：采用ES6语法，这是趋势。

**localStorage(HTML5)**：本地存储，保存用户个性化设置。

**CSS3**：CSS3动画及样式。

## 使用 Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8000
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

## 遇到的问题
1. 异步编程：JS是单线程，异步编程尤为重要。当我们向后端请求数据，是异步的，如果没有处理好相关的异步操作，是会有各种问题的。JS可以利用`setTimeout`、`回调`、`Generator`、`Promise`、`Async`。
定时这种方式太麻烦，还是不推荐；回调层次多了，有回调地狱，代码维护性很差；Generator需要手动去执行，当然可以使用类似`co`的模块。相比之下`Promise`和`Async`是比较理想的。
2. 本项目中使用了QQ音乐和One的接口，后端API编写也是难点，包含了各种异步请求。对返回数据的解析也是难点，有的时候你还需要对数据进行解码。
3. 各组件结构的设计：一开始大纲没设计好，后面想修改涉及面会很广。
4. 过渡动画让交互更有趣，但是有的还是耗性能的，有设备差异，没用好会造成卡顿。