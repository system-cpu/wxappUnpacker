
# wxappUnpacker

![版本 0.3](https://img.shields.io/badge/版本-0.3-red.svg) ![支持的微信版本 >20180111](https://img.shields.io/badge/%E5%BE%AE%E4%BF%A1%E7%89%88%E6%9C%AC-%3E=20180111-brightgreen.svg) ![高级特性支持度 0](https://img.shields.io/badge/%E6%94%AF%E6%8C%81-0%25-yellow.svg)

> Forked from https://github.com/system-cpu/wxappUnpacker
 
> Wechat App(微信小程序, .wxapkg)解包及相关文件(.wxss, .json, .wxs, .wxml)还原工具

### wxapkg 包的获取

    Android 手机最近使用过的微信小程序所对应的 wxapkg 包文件都存储在特定文件夹下，可通过以下命令查看：

    adb pull /data/data/com.tencent.mm/MicroMsg/{User}/appbrand/pkg
 
    其中`{User}` 为当前用户的用户名，类似于 `2bc**************b65`。

# 安装
```
npm install
```

## 依赖

这些 node.js 程序除了自带的 API 外还依赖于以下包:
[cssbeautify](https://github.com/senchalabs/cssbeautify)、[CSSTree](https://github.com/csstree/csstree)、[VM2](https://github.com/patriksimek/vm2)、[Esprima](https://github.com/jquery/esprima)、[UglifyES](https://github.com/mishoo/UglifyJS2/tree/harmony)、[js-beautify](https://github.com/beautify-web/js-beautify)

您需要安装这些包才能正确执行这些程序，为了做到这一点，您可以执行`npm install`；另外如需全局安装这些包可执行以下命令:

    npm install esprima -g
    npm install css-tree -g
    npm install cssbeautify -g
    npm install vm2 -g
    npm install uglify-es -g
    npm install js-beautify -g
    npm install escodegen -g

此外，这些 node.js 程序之间也有一定的依赖关系，比如他们都依赖于 wuLib.js 。

### 使用

  node wuWxapkg.js  .wxapkg 的文件路径   // 例子  D:/node/wxappUnpacker-master._1123949441_321.wxapkg

# 分包功能

当检测到 wxapkg 为子包时, 添加-s 参数指定主包源码路径即可自动将子包的 wxss,wxml,js 解析到主包的对应位置下. 完整流程大致如下: 
1. 获取主包和若干子包
2. 解包主包 `./bingo.sh testpkg/master-xxx.wxapkg`
3. 解包子包 `./bingo.sh testpkg/sub-1-xxx.wxapkg -s=../master-xxx`

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
# 本人代搭建流量主小程序
 ```
   技术微信 : li1664771111
 ```

# 支持
 ```
   Star 一个吧
```
