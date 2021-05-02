# Error: node-sass@4.5.3 postinstall: `node scripts/build.js`

## 一、问题1
* 1、场景
在进行npm install时，出现了报错，具体报错内容如下：
```
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
```

* 2、解决办法
通过上网查找【npm node-sass报错】资料，多次下载了卸载了node-sass的不同版本，发现最新版本的4.11.0可以正常安装；后面通过查看github上面node-sass关于各个版本的支持和说明，发现是本地的nodejs的版本太高，4.5.3版本的无法兼容。为了保持node-sass版本为4.5.3，所以对照版本，把本地的nodejs版本重新安装为8.17.0。

## 二、问题2
* 1、场景
在进行npm run dev时，出现了报错，具体报错内容如下：
```
Node Sass could not find a binding for your current environment: Windows 64-bit with Node.js 12.x

Found bindings for the following environments:
  - Windows 64-bit with Node.js 10.x

This usually happens because your environment has changed since running `npm install`.
Run `npm rebuild node-sass` to download the binding for your current environment.
```

* 2、解决办法
执行npm rebuild node-sass后重新npm run dev即可。
```
npm rebuild node-sass
```

三、参考资料：
* 参考一：[https://github.com/sass/node-sass/releases](https://github.com/sass/node-sass/releases)
* 参考一：[https://www.cnblogs.com/milo-wjh/p/9175138.html](https://www.cnblogs.com/milo-wjh/p/9175138.html)