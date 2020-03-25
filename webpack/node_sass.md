# Error: node-sass@4.5.3 postinstall: `node scripts/build.js`

## 一、遇到的问题
在进行npm install时，出现了报错，具体报错内容如下：
<pre>
3125 verbose stack Exit status 1
......
3126 verbose pkgid node-sass@4.5.3
......
3128 verbose Windows_NT 10.0.16299
......
3130 verbose node v10.15.0
3131 verbose npm  v6.4.1
3132 error code ELIFECYCLE
3133 error errno 1
3134 error node-sass@4.5.3 postinstall: `node scripts/build.js`
3134 error Exit status 1
3135 error Failed at the node-sass@4.5.3 postinstall script.
3135 error This is probably not a problem with npm. There is likely additional logging output above.
3136 verbose exit [ 1, true ]
</pre>

二、解决方法
通过上网查找【npm node-sass报错】资料，多次下载了卸载了node-sass的不同版本，发现最新版本的4.11.0可以正常安装；后面通过查看github上面node-sass关于各个版本的支持和说明，发现是本地的nodejs的版本太高，4.5.3版本的无法兼容。为了保持node-sass版本为4.5.3，所以对照版本，把本地的nodejs版本重新安装为8.17.0。

三、参考资料：
* 参考一：[https://github.com/sass/node-sass/releases](https://github.com/sass/node-sass/releases)