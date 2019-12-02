## history路由模式下可能遇到的问题

### 1、确认vue.config.js中的路径配置
<pre>
publicPath: "./", // 构建好的文件输出到哪里
outputDir: "dist", // where to put static assets (js/css/img/font/...) // 是否在保存时使用‘eslint-loader’进行检查 // 有效值: true | false | 'error' // 当设置为‘error’时，检查出的错误会触发编译失败
assetsDir: 'static',  // 放置生成的静态资源 (js、css、img、fonts) 的 (相对于 outputDir 的) 目录
</pre>
* publicPath的默认值是'/'，也可以被设置为空字符串 ('') 或是相对路径 ('./')，这样所有的资源都会被链接为相对路径，这样打出来的包可以被部署在任意路。具体的内容可以查阅vue-cli的官网[https://cli.vuejs.org/zh/config/#publicpath](https://cli.vuejs.org/zh/config/#publicpath)。

ps：需要注意的地方<br>
* ./ 是指用户所在的当前目录（相对路径）；<br>
* / 是指根目录（绝对路径，项目根目录），也就是项目根目录。<br>

### 2、确认router中的base属性配置，需要与vue.vonfig.js中的publicPath保持一致，若不一致会导致有多个页面时，不能进行访问，只能访问首页；当前都是配置为'./'，也可以配置为'/',但是一定要确保publicPath和base一致
<pre>
export default new Router({
  mode: 'history',
  base: './',
  routes: [
    {
      path: '/',
      name: 'home',
      component: Home
    },
    {
      path: '/about',
      name: 'about',
      component: () => import(/* webpackChunkName: "about" */ './views/About.vue')
    }
  ]
});
</pre>
* base的默认值是process.env.BASE_URL，对应的值是'/'。

ps：需要注意的地方
* 如果希望首页访问的地址是http://XXXXX/home，直接在routes中的path设置为'/home'，但是这样会导致直接访问http://XXXXX/时页面为空。

### 3、history模式的发布还需要nginx或者appache等的配合，当前主要是已nginx为例
<pre>
location / {
  try_files $uri $uri/ /index.html;
}
</pre>

### 参考
* 1、路径配置参考 [https://www.cnblogs.com/xyyt/p/7718867.html](https://www.cnblogs.com/xyyt/p/7718867.html)
* 2、nginx配置的原理参考 [https://www.jb51.net/article/162268.htm](https://www.jb51.net/article/162268.htm)

