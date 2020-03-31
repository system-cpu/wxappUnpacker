# wxappUnpacker

![版本 0.3](https://img.shields.io/badge/版本-0.3-red.svg) ![支持的微信版本 >20180111](https://img.shields.io/badge/%E5%BE%AE%E4%BF%A1%E7%89%88%E6%9C%AC-%3E=20180111-brightgreen.svg) ![高级特性支持度 0](https://img.shields.io/badge/%E6%94%AF%E6%8C%81-0%25-yellow.svg)

> Forked from https://github.com/system-cpu/wxappUnpacker
 
> Wechat App(微信小程序, .wxapkg)解包及相关文件(.wxss, .json, .wxs, .wxml)还原工具

### wxapkg 包的获取

Android 手机最近使用过的微信小程序所对应的 wxapkg 包文件都存储在特定文件夹下，可通过以下命令查看：

    adb pull /data/data/com.tencent.mm/MicroMsg/{User}/appbrand/pkg

其中`{User}` 为当前用户的用户名，类似于 `2bc**************b65`。

### 使用

  node wuWxapkg.js  .wxapkg 的文件路径   // 例子  D:/node/wxappUnpacker-master._1123949441_321.wxapkg


### 另注

所有命令上都可以使用`-f`指令来提高一定的并行度，但输出信息会混乱。

如果发现包内文件“缺失”，请先检查解包时是否出现提示`NOTICE: SubPackages exist in this package.`。如存在，请在寻找好分包后，按上文提示操作。（小程序需要访问特定页面；小游戏需要触发特定函数，然后分包才会被下载。）

### 局限（包括但可能不限于以下内容）

- 实现中很多功能基于特定的版本(`wcc-v0.6vv_20180111_fbi`, 且不考虑面向低版本适配)和字符串搜索，所以不能很好的适应各种特殊情况。
- wxml 文件拥有不同于 xml 和 html 文件的字符转义规则，且尚未公开(并非"没有")，因此未能很好的还原相关内容。
- js 文件被压缩后会丢失原始变量名等信息内容无法还原；wxss 文件压缩后的注释也会丢失。
- wxs 文件会将所有的变量如 Math 改为 nv_Math ，这里仅通过字符串替换去除。
- 一些被引用 wxss 文件本身的源文件丢失，因此无法恢复原始目录。
- 有些项目开启了难以复原的`es6转es5`选项，检验本项目结果是否正确时需要关闭项目中的`es6转es5`选项。
- wxml 中一些无法找到相对应 的正向语句的内容无法还原。
- json 中`components`项丢失，仅会标注被其他包引用的自定义组件。

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


## 技术支持  
 Star 一下可以加微信
 微信: li1664771111 //备注：反编译
