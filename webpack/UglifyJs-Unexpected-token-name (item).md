# UglifyJs Unexpected token: name (item)

## 一、遇到的问题
在使用jerkins进行npm run build打包时，一直提示：
<pre>
ERROR in js/client.bd862eb6.js from UglifyJs
Unexpected token: name (item) [js/client.bd862eb6.js:1321,8]
</pre>

查找了很久，一直没有找到办法，尝试通过babel-preset-es2015去修改ES6转ES5的设置，但是都没有起效，后面通过biying搜索下，找到了解决方法。

代码情况：<br>
使用的webpack是3.12.0版本的，默认加载的是uglifyjs-webpack-plugin@0.4.6版本的，后面将版本升级为1.2.4的，重新打包就可以了。

原因：uglifyjs-webpack-plugin的版本太低，不支持ES6语法。

<pre>npm install uglifyjs-webpack-plugin@1.2.4 --save-dev</pre>


## 二、关于uglifyjs-webpack-plugin插件
uglifyjs-webpack-plugin插件是用来缩小（压缩优化）js文件。

npm包的地址：[https://www.npmjs.com/package/uglifyjs-webpack-plugin](https://www.npmjs.com/package/uglifyjs-webpack-plugin)

配置参数中文版的可以参考：[https://blog.csdn.net/u013884068/article/details/83511343](https://blog.csdn.net/u013884068/article/details/83511343)

通过查看uglifyjs-webpack-plugin插件在github上的CHANGELOG.md可以看到至2.0.0 (2018-09-14)版本，uglifyjs-webpack-plugin将不再支持ES6，如果需要对ES6进行压缩的话可以使用terser-webpack-plugin插件。先前的支持ES6的压缩是由于uglify-es，但是从uglifyjs-webpack-plugin 2.0.0版本开始已舍弃uglify-es。具体可以查看：
[https://github.com/webpack-contrib/uglifyjs-webpack-plugin/blob/master/CHANGELOG.md#200-2018-09-14](https://github.com/webpack-contrib/uglifyjs-webpack-plugin/blob/master/CHANGELOG.md#200-2018-09-14)

## 三、参考资料
* 参考一：[https://www.jianshu.com/p/0911db6c7555](https://www.jianshu.com/p/0911db6c7555)
* 参考二：[https://codereviewvideos.com/blog/how-i-fixed-uglifyjs-unexpected-token-name-dropin/](https://codereviewvideos.com/blog/how-i-fixed-uglifyjs-unexpected-token-name-dropin/)
* 参考三：[https://www.cnblogs.com/qiqi715/p/11804632.html](https://www.cnblogs.com/qiqi715/p/11804632.html)