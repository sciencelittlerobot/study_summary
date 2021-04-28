# integrity checksum failed when using sha512

## 一、遇到的问题
在本地使用npm install下载依赖包时报错，误以为是node环境的问题，第一次报错的node环境的版本是14.16.0，更换了低版本的node环境8.17.0，问题扔存在，第二次将node环境版本更换为10.15.0，问题仍然存在。
```
13848 verbose node v10.15.0
13849 verbose npm  v6.4.1
13850 error code EINTEGRITY
13851 error sha512-BVINzXBInuM/8ggJpDwt+KnLg0te0+3leVpcjCyrKI9LqsjtTF4VO95oD1hn0WuCAZpAs4PbcHFhDfI1+VmUyw== integrity checksum failed when using sha512: wanted sha512-BVINzXBInuM/8ggJpDwt+KnLg0te0+3leVpcjCyrKI9LqsjtTF4VO95oD1hn0WuCAZpAs4PbcHFhDfI1+VmUyw== but got sha512-ONhaKPIufzzrlNbqtWFFd+jlnemX6lJAgq9ZeiZtS7I1PIf/la7CW4m83rTXRnVnsMbW2k56pGYu7AUFJD9Pow==. (15110 bytes)
13852 verbose exit [ 1, true ]
```

## 二、解决办法
* 1、删除已存在的node_modules文件夹
* 2、清楚npm缓存
  ```
  npm cache clean --force
  ```
* 3、下载最新版本的npm安装包
  ```
  npm install -g npm
  ```

## 三、参考资料
* 参考一：[https://blog.csdn.net/wy_51131/article/details/108465259](https://blog.csdn.net/wy_51131/article/details/108465259)