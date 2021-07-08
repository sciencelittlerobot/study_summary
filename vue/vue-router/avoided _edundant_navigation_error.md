# Error: Avoided redundant navigation to current location:

## 一、遇到的问题
在360浏览器中，当用户点击backspace进行返回时，会返回至登录页面，需要监听返回键并设置路由还是当前页面，但是会提示路由重复渲染的提示:
```
Error: Avoided redundant navigation to current location:
```

## 二、解决办法
在/src/router/index.js中添加以下代码
```
// 隐藏重复路由跳转的报错
const originalPush = Router.prototype.push;

Router.prototype.push = function push(location) {
  return originalPush.call(this, location).catch(err => err);
}

Vue.use(Router);
```

## 三、参考资料
* 参考一：[https://www.cnblogs.com/yequxue/p/13255945.html](https://www.cnblogs.com/yequxue/p/13255945.html)
* 参考二：[https://blog.csdn.net/delise9787/article/details/107324777](https://blog.csdn.net/delise9787/article/details/107324777)