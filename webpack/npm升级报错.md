# 关于升级npm 出现 “Refusing to delete C:\Users\lt\AppData\Roaming\npm\npx.cmd:”

## 一、遇到的问题
由于node环境的版本与npm最新版本不兼容，所以将npm版本降级到6.0.1，降级完发现还是无效，继续要降级到5.6.0的时候，发现报错了
```
2788 verbose stack Error: Refusing to delete C:\Users\Administrator\AppData\Roaming\npm\npm.cmd: is outside C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm and not a link
2788 verbose stack     at clobberFail (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\gentle-fs\lib\rm.js:121:12)
2788 verbose stack     at isSafeToRm (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\gentle-fs\lib\rm.js:114:15)
2788 verbose stack     at C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\gentle-fs\lib\rm.js:54:5
2788 verbose stack     at LOOP (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\slide\lib\chain.js:7:26)
2788 verbose stack     at C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\slide\lib\chain.js:18:7
2788 verbose stack     at C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\gentle-fs\lib\rm.js:180:7
2788 verbose stack     at C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\gentle-fs\node_modules\iferr\index.js:13:50
2788 verbose stack     at _readAllLinks (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\gentle-fs\lib\rm.js:215:28)
2788 verbose stack     at C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\gentle-fs\node_modules\iferr\index.js:13:50
2788 verbose stack     at resolveSymlink (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\gentle-fs\lib\rm.js:226:22)
2788 verbose stack     at _readAllLinks (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\gentle-fs\lib\rm.js:217:5)
2788 verbose stack     at readAllLinks (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\gentle-fs\lib\rm.js:212:3)
2788 verbose stack     at C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\gentle-fs\lib\rm.js:179:5
2788 verbose stack     at C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\gentle-fs\node_modules\iferr\index.js:13:50
2788 verbose stack     at cb (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\slide\lib\async-map.js:47:24)
2788 verbose stack     at C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\gentle-fs\lib\rm.js:153:16
2789 verbose cwd F:\XXXX\XXXX\XXXX
2790 verbose Windows_NT 10.0.16299
2791 verbose argv "C:\\Program Files\\nodejs\\node.exe" "C:\\Users\\Administrator\\AppData\\Roaming\\npm\\node_modules\\npm\\bin\\npm-cli.js" "uninstall" "npm" "-g"
2792 verbose node v10.15.0
2793 verbose npm  v6.0.1
2794 error path C:\Users\Administrator\AppData\Roaming\npm\npm.cmd
2795 error code EEXIST
2796 error Refusing to delete C:\Users\Administrator\AppData\Roaming\npm\npm.cmd: is outside C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm and not a link
2797 error File exists: C:\Users\Administrator\AppData\Roaming\npm\npm.cmd
2798 error Move it away, and try again.
2799 verbose exit [ 1, true ]
```

## 二、解决方法
下载cnpm，使用cnpm命令来升级npm，可能是npm有问题不能只用npm自己来升级自己，需要使用其它的工具升级。

## 三、参考资料
* 参考一：[https://www.cnblogs.com/sugarwxx/p/12581514.html](https://www.cnblogs.com/sugarwxx/p/12581514.html)