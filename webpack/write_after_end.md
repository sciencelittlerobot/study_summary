# npm install 报错 "stack Error: write after end"

## 一、遇到的问题
由于node环境的版本与npm最新版本不兼容，所以将npm版本降级到6.0.1，降级完发现还是无效，继续要降级到5.6.0的时候，发现报错了
```
521 verbose stack Error: write after end
521 verbose stack     at writeAfterEnd (_stream_writable.js:236:12)
521 verbose stack     at PassThrough.Writable.write (_stream_writable.js:287:5)
521 verbose stack     at PassThrough.Writable.end (_stream_writable.js:562:10)
521 verbose stack     at ReadEntry.entry.on (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\pacote\lib\extract-stream.js:19:41)
521 verbose stack     at emitOne (events.js:121:20)
521 verbose stack     at ReadEntry.emit (events.js:211:7)
521 verbose stack     at ReadEntry.emit (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\tar\node_modules\minipass\index.js:296:25)
521 verbose stack     at ReadEntry.[maybeEmitEnd] (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\tar\node_modules\minipass\index.js:249:12)
521 verbose stack     at ReadEntry.end (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\tar\node_modules\minipass\index.js:162:27)
521 verbose stack     at Unpack.[consumeBody] (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\tar\lib\parse.js:210:13)
521 verbose stack     at Unpack.[consumeChunkSub] (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\tar\lib\parse.js:391:40)
521 verbose stack     at Unpack.[consumeChunk] (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\tar\lib\parse.js:362:30)
521 verbose stack     at Unzip.(anonymous function).on.chunk (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\tar\lib\parse.js:291:59)
521 verbose stack     at emitOne (events.js:116:13)
521 verbose stack     at Unzip.emit (events.js:211:7)
521 verbose stack     at Unzip.emit (C:\Users\Administrator\AppData\Roaming\npm\node_modules\npm\node_modules\tar\node_modules\minipass\index.js:296:25)
522 verbose cwd F:\XXXX\XXXX\XXXX
523 verbose Windows_NT 10.0.16299
524 verbose argv "C:\\Program Files\\nodejs\\node.exe" "C:\\Users\\Administrator\\AppData\\Roaming\\npm\\node_modules\\npm\\bin\\npm-cli.js" "install"
525 verbose node v8.17.0
526 verbose npm  v6.0.1
527 error write after end
528 verbose exit [ 1, true ]
```

## 二、解决方法
降低npm版本号
```
npm install -g npm@5.6.0
```

## 三、参考资料
* 参考一：[https://www.imooc.com/wenda/detail/402655](https://www.imooc.com/wenda/detail/402655)
* 参考二：[https://blog.csdn.net/you23hai45/article/details/86590528](https://blog.csdn.net/you23hai45/article/details/86590528)