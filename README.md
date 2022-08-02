本质上，是一个用于现代JavaScript应用程序的静态模块打包工具。

1.Webpack中的模块 - Module

webpack 支持如下模块类型：

  ESModule、 CommonJS、 AMD、 Assets.(image, font, video, audio, json)

  1）ESModule

    关键字 export （允许将ESM中的内容暴露给其他模块）；

    关键字 import（允许从其他模块中导入内容）

  2）CommonJS

    关键字module.exports （允许将CommonJS的内容暴露给其他模块）

    关键字require （允许从其他模块中导入内容）

  3）AMD

    关键字define （允许将AMD的内容暴露给其他模块）

    关键字require （允许从其他模块中导入内容）

  4）assets

    关键字 @import （css / sass / less）文件导入




2. Chunk 和 Bundle 的区别

1). chunk是webpack打包过程中 Modules的集合， 是 打包过程 中的概念




webpack的打包是从一个入口模块开始，入口模块引用其他模块，其他模块引用其他模块。。。。。。

webpack通过引用关系逐个打包模块，这些module就形成了一个chunk

那么如果存在多个入口模块，可能会产出多条打包路径，每条路径都会形成一个chunk




2).Bundle

是最终输出的一个或多个打包好的文件




3).Chunk 和 Bundle 的关系是什么

大多数情况下，一个chunk会生成一个bundle；但是如果加了sourcemap, 一个entry，一个chunk对应两个bundle

chunk是过程中的代码快，bundle是打包结果输出的代码块。chunk在构建完成就呈现为bundle。




3.Plugin 和 Loader
1). loader

模块转换器， 将非js模块转换为webpack能识别的js模块

本质上， webpack loader将所有类型的文件，转换为应用程序的 依赖图 可以直接引用的模块




2). Plugin

扩展插件，webpack运行的各个阶段，都会广播出对应的事件，插件去监听对应的事件。




3). Compiler

对象，包含了webpack环境的所有配置信息。包含 options loader plugin

webpack启动的时候实例化，它在全局是唯一的。可以把它理解为webpack的实例




4). Compilation

包含了当前的模块资源，编译生成资源。

webpack 在开发模式下运行的时候，每当检测到一个文件变化，就会创建到一个文件变化，就会创建一次新的compilation




4. webpack的打包过程

1). 初始化参数: shell webpack.config.js

2). 开始编译: 初始化一个Compiler对象，加载所有的配置，开始执行编译

3). 确定入口: 根据entry中的配置，找出所有的入口文件

4). 编译模板: 从入口文件开始，调用所有的loader，再去递归的找依赖

5). 完成模块编译: 得到每个模块被编译后的最终内容以及它们之间的依赖关系

6). 输出资源: 根据得到的依赖关系，组装成一个个包含多个module的chunk

7). 输出完成: 根据配置，确定要输出的文件以及文件路径

5. webpack手写打包原理 以及 自定义一个loader与plugin

地址：https://gitee.com/mao_bingyao/webpack.git
