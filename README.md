
# 安装
```
npm install
```

# 安装依赖
```
npm install esprima
    
npm install css-tree
    
npm install cssbeautify
    
npm install vm2
    
npm install uglify-es
    
npm install js-beautify


```
# 使用

Android 手机最近使用过的微信小程序所对应的 wxapkg 包文件都存储在特定文件夹下，可通过以下命令查看：

adb pull /data/data/com.tencent.mm/MicroMsg/{User}/appbrand/pkg


--
node wuWxapkg.js  .wxapkg

其中`{User}` 为当前用户的用户名，类似于 `2bc**************b65`。





# 分包功能

当检测到 wxapkg 为子包时, 添加-s 参数指定主包源码路径即可自动将子包的 wxss,wxml,js 解析到主包的对应位置下. 完整流程大致如下: 
1. 获取主包和若干子包
2. 解包主包  
    - windows系统使用: `./bingo.bat testpkg/master-xxx.wxapkg`
    - Linux系统使用: `./bingo.sh testpkg/master-xxx.wxapkg`
3. 解包子包  
    - windows系统使用: `./bingo.bat testpkg/sub-1-xxx.wxapkg -s=../master-xxx`
    - Linux系统使用:  `./bingo.sh testpkg/sub-1-xxx.wxapkg -s=../master-xxx`


TIP
> -s 参数可为相对路径或绝对路径, 推荐使用绝对路径, 因为相对路径的起点不是当前目录 而是子包解包后的目录

```
├── testpkg
│   ├── sub-1-xxx.wxapkg #被解析子包
│   └── sub-1-xxx               #相对路径的起点
│       ├── app-service.js
│   ├── master-xxx.wxapkg
│   └── master-xxx             # ../master-xxx 就是这个目录
│       ├── app.json
```
