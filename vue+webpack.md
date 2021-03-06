## 官方vue-cli手脚架vue2.0 + webpack2.0 项目构建
1. 采用vue-cli
2. 按需加载
3. 组件化开发
4. 路由配置
## vue-cli命令行工具
1. 全局安装vue-cli
    *$ npm install --global vue-cli
2. 创建一个基于 webpack 模板的新项目
    *$ vue init webpack my-project
3. 安装依赖
    *$ cd my-project
    *$ npm install
4. 开启服务器
    *$ npm run dev
## 按需加载
* [vue-router](https://router.vuejs.org/zh-cn/advanced/lazy-loading.html)
***
      const Foo = resolve => {
        // require.ensure 是 Webpack 的特殊语法，用来设置 code-split point
        // （代码分块）
        require.ensure(['./Foo.vue'], () => {
          resolve(require('./Foo.vue'))
        })
      }
***
## 组件化开发
1. component目录下创建.vue组件
2. 组件格式: 
    *每个组件用template包含且template内层仅有一个dom元素包含
    *js文件写在template下方的script里面(分离出来的话要在script标签内引入)
    *css文件分离出来
[自定义组件](https://cn.vuejs.org/v2/guide/single-file-components.html)
## 路由配置
1. 配置路径在src->router->index.js
2. 路由的三个状态 
***
     beforeRouteEnter (to, from, next) {
        // 在渲染该组件的对应路由被 confirm 前调用
        // 不！能！获取组件实例 `this`
        // 因为当钩子执行前，组件实例还没被创建
      },
***
      beforeRouteUpdate (to, from, next) {
        // 在当前路由改变，但是该组件被复用时调用
        // 举例来说，对于一个带有动态参数的路径 /foo/:id，在 /foo/1 和 /foo/2 之间跳转的时候，
        // 由于会渲染同样的 Foo 组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用。
        // 可以访问组件实例 `this`
      },
 ***
      beforeRouteLeave (to, from, next) {
        // 导航离开该组件的对应路由时调用
        // 可以访问组件实例 `this`
      }
 ***
3. 路由状态中必须添加next方法，否则会阻断路由跳转

* [路由钩子](https://router.vuejs.org/zh-cn/advanced/navigation-guards.html)


4.nginx方向代理服务器或者用vue-cli中的proxyTable解决
* [proxyTable](http://www.jianshu.com/p/95b2caf7e0da)
* 目录在config文件夹的index.js文件中

## vue常用状态钩子
* [vue生命周期钩子](https://cn.vuejs.org/v2/api/#选项-生命周期钩子)
