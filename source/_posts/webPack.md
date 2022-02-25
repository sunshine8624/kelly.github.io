---
title: webPackBase
---
[TOC]

[webpack基础知识点](https://www.bilibili.com/video/BV1ub4y1Z7Mx?from=search&seid=4918705768939279631&spm_id_from=333.337.0.0)

[解锁 Webpack 重点](http://mp.weixin.qq.com/s?__biz=MzI5MTUyMjk0Mw==&mid=2247484844&idx=1&sn=cc63698437613a2d4872a738e3e1cf30&chksm=ec0e15bcdb799caa596532a64b9b440aca9c13bfaee4deef6b029fbfa516580cbf4ee6c40948&scene=21#wechat_redirect)

#### webPack 相应知识点的(相应的配置都在 解锁 Webpack 重点中 )

- 将JS转义成低版本的 

  > ```bash
  >  // JS代码向低版本转换，我们需要使用 babel-loader 首先安装一下 babel-loader
  > npm install babel-loader -D
  > // 相应的文件配置 在上面的 解锁WebPack中
  > ```

- 图片/字体文件处理

  > ```bash
  > // 我们可以使用 url-loader 或者 file-loader 来处理本地的资源文件。url-loader 和 file-loader 的功能类似，但是 url-loader 可以指定在文件大小小于指定的限制时，返回 DataURL，因此，个人会优先选择使用 url-loader
  > npm install url-loader -D
  > ```

- 如何处理样式文件

  > ```bash
  > // webpack 不能直接处理 css，需要借助 loader。如果是 .css，我们需要的 loader
  > npm install style-loader less-loader css-loader postcss-loader autoprefixer less -D
  > 
  > // 简单说一下的配置：
  > style-loader 动态创建 style 标签，将 css 插入到 head 中.
  > 
  > css-loader 负责处理 @import 等语句。导入css模块，对css代码进行编译和处理
  > 
  > postcss-loader 和 autoprefixer，自动生成浏览器兼容性前缀了，应该没人去自己徒手去写浏览器前缀了吧
  > 
  > less-loader 负责处理编译 .less 文件,将其转为 css
  > ```

- 处理 html 中的本地图片

  > ```bash
  > // 安装 html-withimg-loader 来解决咯。
  > 
  > npm install html-withimg-loader -D
  > ```

- 抽离公共代码

  > ```js
  > // 抽离公共代码是对于多页应用来说的，如果多个页面引入了一些公共模块，那么可以把这些公共的模块抽离出来，单独打包。公共代码只需要下载一次就缓存起来了，避免了重复下载 optimization.splitChunks
  > 
  > ```

- #### happypack

  > 由于有大量文件需要解析和处理，构建是文件读写和计算密集型的操作，特别是当文件数量变多后，Webpack 构建慢的问题会显得严重。文件读写和计算操作是无法避免的，那能不能让 Webpack 同一时刻处理多个任务，发挥多核 CPU 电脑的威力
  >
  > ```bash
  > // HappyPack 就能让 Webpack 做到这点，它把任务分解给多个子进程去并发的执行，子进程处理完后再把结果发送给主进程
  > npm install happypack -D
  > ```

#### webPack中laoder对css的处理

###### Loader 的作用: 模块转换器，将非JS模块转化为webPack能识别的JS模块

 本质上，webPack loader将所有类型的文件，转换成应用程序的依赖图 可以直接引用的模块

###### Piugin 

扩展插件，webPack运行的各个阶段，都会广播出对应的事件，插件去监听对应的事件

> webPack中操作css需要两个关键的loader: css-loader和style- loader
>
> - css-loader：导入css模块、对css代码进行编译处理
> - style- loader：创建style标签，把css写入标签