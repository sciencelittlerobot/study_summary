# Can't find Python executable "python", you can set the PYTHON env variable.

## 一、遇到的问题
执行 npm install 命令时报错，在看最后的错误时，误以为又是node-sass安装版本的问题，后面就仔细从开始报错的地方开始解决，发现 【failed Error: not found: python2】、【Error: not found: python】等错误提示。
<pre>
gyp verb cli   'rebuild',
gyp verb cli   '--verbose',
gyp verb cli   '--libsass_ext=',
gyp verb cli   '--libsass_cflags=',
gyp verb cli   '--libsass_ldflags=',
gyp verb cli   '--libsass_library=' ]
gyp info using node-gyp@3.8.0
gyp info using node@8.17.0 | win32 | x64
gyp verb command rebuild []
gyp verb command clean []
gyp verb clean removing "build" directory
gyp verb command configure []
gyp verb check python checking for Python executable "python2" in the PATH
gyp verb `which` failed Error: not found: python2
gyp verb `which` failed     at getNotFoundError 
......
gyp verb `which` failed     at FSReqWrap.oncomplete (fs.js:152:21)
gyp verb `which` failed  python2 { Error: not found: python2
gyp verb `which` failed     at getNotFoundError 
......
gyp verb `which` failed     at FSReqWrap.oncomplete (fs.js:152:21)
gyp verb `which` failed   stack: 'Error: not found: python2\n    at getNotFoundError 
......
gyp verb `which` failed   code: 'ENOENT' }
gyp verb check python checking for Python executable "python" in the PATH
gyp verb `which` failed Error: not found: python
gyp verb `which` failed     at getNotFoundError 
......
gyp verb `which` failed     at FSReqWrap.oncomplete (fs.js:152:21)
gyp verb `which` failed  python { Error: not found: python
gyp verb `which` failed     at getNotFoundError 
......
gyp verb `which` failed     at FSReqWrap.oncomplete (fs.js:152:21)
gyp verb `which` failed   stack: 'Error: not found: python\n    at getNotFoundError 
......
gyp verb `which` failed   code: 'ENOENT' }
gyp verb could not find "python". checking python launcher
gyp verb could not find "python". guessing location
gyp verb ensuring that file exists: C:\Python27\python.exe
gyp ERR! configure error
gyp ERR! stack Error: Can't find Python executable "python", you can set the PYTHON env variable.
gyp ERR! stack     at PythonFinder.failNoPython 
......
gyp ERR! stack     at FSReqWrap.oncomplete (fs.js:152:21)
gyp ERR! System Windows_NT 10.0.16299
gyp ERR! command "C:\\Program Files\\nodejs\\node.exe" 
......
gyp ERR! node -v v8.17.0
gyp ERR! node-gyp -v v3.8.0
gyp ERR! not ok
Build failed with error code: 1
......

npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! node-sass@4.12.0 postinstall: `node scripts/build.js`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the node-sass@4.12.0 postinstall script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.
</pre>

## 二、解决方法
通过上网查找资料，找到了解决方法,运行下面命令就解决了。
<pre>
npm install --python=python2.7
</pre>

## 三、参考资料
* 参考一：[https://blog.csdn.net/lamp_yang_3533/article/details/80294675](https://blog.csdn.net/lamp_yang_3533/article/details/80294675)
* 参考二：[https://cloud.tencent.com/developer/ask/28951](https://cloud.tencent.com/developer/ask/28951)