# 课程首页

课程会分四个阶段，每个阶段给大家一些视频并且有一个明确的任务期待大家完成。 任务完成过程中遇到困难，可以随时论坛沟通，或者预约答疑。
## 第一阶段

这个阶段瞄准响应式开发。也会一起聊 Google 材料设计。

进入第一阶段
## 第二阶段：

对项目进行重构，突出一个概念：组件化。会用到前端框架 react 和构建工具 webpack 。

进入第二阶段
## 第三阶段：

利用 webpack 和它的 react-hot-loader 来搭建”浏览器内设计“环境。

进入第三阶段
## 第四阶段：

选学内容：React+Meteorjs 搭建 SPA 应用。

## 进入第四阶段



## 第一阶段

这个阶段瞄准响应式开发。会用到 gulp+sass 预处理 css ，media-query 让我们的页面适应多屏。也会一起聊 google 材料设计，git 和 github 技巧，sublime 配置。

这个阶段的任务是：自己制作一个简单的符合 Material Design 视觉规范的响应式网站，学会使用 gulp 处理自动化任务，用 github 来版本控制并进行项目沟通。详细介绍见页顶视频。

视频列表

第一个小任务：用 Github 托管页，进入课程的论坛，熟悉使用 git 配合页面调试。

采用 github pages 方式来展示页面
论坛沟通形式
git 使用技巧：小步快跑
第二个小任务：安装 sass 和 gulp 命令行工具。

安装 Nodejs
使用 gulp 和 sass 来预处理 .scss 文件
第三个小任务：了解移动优先方法论，定制自己的色盘

为何要移动优先？
定制自己的色盘
主色和强调色的用法
其他颜色的用法
第四个小任务：来一起制作手机版页面吧

viewport 设置是每个响应式页面必须的
动手
第五个小任务：适应多种屏幕尺寸

什么是响应式设计
四种常见响应模式
使用媒体查询 media-query
总结第一阶段
即时补充视频

sublime 中自动补齐的 emmet 插件 -- 9月5号更新
photoshop 剪裁图片的技巧 -- 8月31号更新
Clearfix 详解 -- 8月30号更新



第二阶段

对项目进行组件化重构，突出一个概念：组件化。会用到 react 和 webpack 。

这个阶段的任务是：使用 react 重构项目，学会用 webpack 来构建项目。使得代码变得模块化，分层化，便于维护。

视频列表

第一个小任务：用 react 把 html 页面组件化重构

你好 React
组件分离成独立文件
第二个小任务：webpack 基本使用方法

webpack 是什么？
webpack 初相见
第三个小任务：webpack 来构建项目

使用 Webpack 来构建 react 项目
react 组件的嵌套使用
使用 Webpack 来处理 sass
第四个小任务：实践组件化思想

组件分离
组件复用
总结第二阶段


你好 React

应该说用很多其他框架都可以进行项目的组件化开发，但是 React 是我发现最为强大同时也几乎是最好上手的一个框架。

基本使用方法

通常老手使用 React 都是用 npm/webpack 这些工具。但是咱们现在先用一种简单的方式把 React 用起来，后面再慢慢引入各种工具。

在官方的教程页面 可以找到下面三行内容：

<script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.14.0/react.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/react/0.14.0/react-dom.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.23/browser.min.js"></script>
把它们粘贴到咱们页面的 head 标签之内。三者各自的作用，一会儿我们就会看到。

先来抽出一个组件

首先来改写 action 这一部分。之所以所 React 非常容易上手，很大一个原因就是可以把原来页面保持基本不变的前提下，来把页面的某一个局部抽出成一个 React 的组件。

一般 React 组件中的 JSX 代码我们都是自己写的，但是前期如果不熟悉这个语法，可以借助官方给的 html 到 jsx 的转换器 。

引入的三个 js 文件的作用

第一个 react.js 就简单了，提供了 React 这个 class ，所以我们可以使用代码中的这样的接口：

React.createClass
第二个 react-dom.js 提供 ReactDOM.render 接口，让我们可以把定义好的组件，真正渲染到浏览器中去显示。

第三个 babel-core/5.8.23/browser.min.js 是帮助我们把 jsx 代码，转换为 js 代码的。

组件分离成独立文件

组件抽出到单独文件

每个组件文件大概长成下面的样子，Action.js

var Action = React.createClass({
  render: function() {
    return (

      <div className="action clearfix">
        <a href="#" className="action-button button" />
      </div>
    );
  }
});

ReactDOM.render(<Action />, document.getElementById('action'));
然后在 index.html 添加下面的语句：

<script type="text/babel" src="components/Action.js"></script>
浏览器中直接打开 index.html 会报跨域请求（ Cross Origin ）错误。需要启动一个 http 的 server 。后续我们使用 webpack 这样的构建工具，会自带 sever ，不过暂时咱们可以自己在命令行启动文件中（我使用的是 zsh ，所以启动文件是 .zshrc ） 添加下面的内容：

alias server='open http://localhost:8000 && python -m SimpleHTTPServer'
然后执行一下 source .zshrc 就可以了。

webpack 安装和基本用法

本节介绍如何安装 webpack ，以及最基本的使用方法。

安装

首先要进行全局安装：

cnpm i -g webpack
这样的目的是让我们拥有 webpack 这个系统命令。

项目内部也还是要再装一遍的，这样才能在项目代码中 require 到。

cd qd/
cnpm i --save-dev webpack
好，这样安装结束了，webpack 被安装到 qd/node_modules/ 文件夹里面，同时 package.json 文件中会有记录：

Install Webpack

项目中使用

webpack 的心脏就是 webpack.config.js 文件，到 webpack 官方文档 拷贝一份基本的配置内容粘贴到代码中：

copy webpack.config.js

一般输入文件叫 main.js 比较符合习惯，所以把 entry.js 改一下名字。输出文件就是叫 bundle.js 。代码：

try webpack

有了上面的代码，运行

cd qd/
webpack
就可以得到输出文件 bundle.js 了，执行一下可以看到下面的输出

$ node bundle.js
hello.js
main.js
可见 webpack 的打捆功能已经正常工作了。

Loader 的作用

前面的 webpack.config.js 中的 loader 部分咱们还没用用到，因为暂时 require 的 hello.js 是纯粹的 js 语法内容，所以用不着 loader 。但是后面，如果我们 require 的是 react 的组件文件，或者是 css 文件，就需要安装使用 loader 了，这个后面会有实例演示。

用 webpack 来构建 react 项目

本节介绍用 webpack 来构建 react 项目。

输出就是一个文件

使用了 webpack ，所有的 js 文件就都可以打捆成一个 bundle.js 文件了，所以首先可以把代码改成下面这样：

only bundle.js

那么后续所有的努力就是来生成这个 bundle.js 文件了。

使用 loader

这次咱们就真的是需要 loader 了，因为要 require 进来的基本都是 react 的 jsx 格式的文件，不是纯 js 。我们需要

cnpm i -D babel-loader
安装好这个 loader 之后，就可以修改 webpack.config.js 文件，这样 webpack 就有能力把 jsx 翻译成纯 js 文件了，所以 index.html 中的 babel 那行 script 标签也可以删除了：

babel loader

npm 安装 react

index.html 中还有 react.js 和 reactdom.js 也一样可以通过 npm 进行安装

npm i -D react react-dom
删除 index.html 中的相关 script 标签，然后每个组件中都添加

var React = require('react');
var ReactDOM = require('react-dom');
就可以继续使用这两个家伙了。同时也因为有了 babel loader 的设置，main.js 文件中就可以直接 require 各个组件了。总之，有了下面的代码：

npm react

这样运行

$ webpack
就可以得到 bundle.js 了，此时再来运行

$ server
就可以在浏览器中看到，页面已经可以正常显示了。

结语

好，这样我们就用 npm+webpack 对咱们的项目进行了重构。

react 组件的嵌套使用

本节的任务是把前面的三个 react 组件都包裹在一个父组件之内。也就是实现所谓的组件嵌套使用。

一个顶级组件

现在 index.html 中有

<div id="action"></div>
<div id="haoduo"></div>
<div id="books"></div>
可以变为一行

<div id="app"></div>
这样我们只要构建一个组件，叫 App ，让它同时包含 Action Haoduo Books 三个组件就可以了。假设我们有个这个组件，放到 components/App.js 中，那么 main.js 中只要这样写就行了

var React = require('react');
var ReactDOM = require('react-dom');
var App = require("./components/App.js");


ReactDOM.render(<App />, document.getElementById('app'));
注意最后的 ReactDOM.render 语句，有了它，现在 Action.js Haoduo.js Books.js 中的 render 语句就都不需要了，删掉。

实现 App 组件

来创建 components/App.js 文件，里面这样写

var React = require('react');
var ReactDOM = require('react-dom');
var Action = require("./Action.js");
var Books = require("./Books.js");
var Haoduo = require("./Haoduo.js");

var App = React.createClass({
  render: function() {
    return (
      <div>
        <Action />
        <Haoduo />
        <Books />
      </div>
    );
  }
});
改动的内容是简单的，就是 require 了三个子组件，然后都在 App 组件中调用。

模块（ module ）

但是，App 组件以及它的三个子组件，如果只是写成现在这样，require 它们是不会成功的。需要分别添加 module.exports 语句：

App.js 中

module.exports = App;
其他三个也类似，只是最后的 App 要改成各自的 class 名。（详见，下面的最终代码 commit ）。

但为何要这样做呢？

跟前面使用 script 标签引进 js 文件的形式不同，webpack 在进行 require 文件操作的时候，会把每一个文件都当做一个 Nodejs 的模块。模块的特点是里面的变量的的作用范围默认被限制在本文件内。这样做的好处是明显的，就是防止变量冲突。所以，如果我们这里直接 require 组件文件进来，并且试图使用组件，就会出现“未定义”的错误。

那么，如何把本模块内的变量导出呢？就是用 module.exports 就好了。比较详细的解释，参考这篇文章 。

实现代码

最终的代码如下：

react nest

运行 webpack 命令，就可以得到新的 bundle.js 文件了。浏览器中打开 index.html 文件，可以看到项目依旧运行良好。但是现在代码的层级结构已经变得更加清晰。

使用 Webpack 来处理 sass

前面咱们用 gulp 来处理 sass 文件，这里来切换到 webpack 下实现相同的功能。

安装 loader

$ cnpm i -D style-loader css-loader autoprefixer-loader sass-loader
注意：-D 和 --save-dev 是等价的。

小插曲，安装时候报错了

也许您那边不会出现下面的问题的，万一出现，解决方法如下：

是这样，上面的装包命令执行报错了：

npm ERR! peerinvalid The package node-sass does not satisfy its siblings' peerDependencies requirements!
npm ERR! peerinvalid Peer sass-loader@3.1.0 wants node-sass@^3.3.3
问题显然是我这里的 node-sass 这个包版本太低了，所以需要升级一下：

$ npm install -D node-sass
...
> node-sass@3.4.0 install /Users/peter/Desktop/modern-web-dev-stuff/qd/node_modules/node-sass
...
输出信息中看到安装的是 3.4.0 版本，满足了前面报错信息中要求的 ^3.3.3 （高于 3.3.3，对 package.json 各种格式的意义感兴趣？参照这里） 。所以在此安装各个 loader ，就能成功了。

修改配置

然后到 webpack.config.js 来添加 loader 的配置

    module: {
        loaders: [
          { test: /\.scss$/, loader: 'style!css!autoprefixer!sass' },
        ]
    }
导入 sass 文件。

到 main.js 中把 main.scss 导入一下就可以了

require('./styles/main.scss');
结语

有了 webpack 来帮我们编译 sass 代码，那么 gulpfile.js 就没有存在的必要了，删除。

最终代码： webpack sass

组件分离

复杂的代码分离成独立组件，每个组件都不超过50行代码，项目就会变得非常好维护了。

添加一个按钮组件

前面介绍过了 react 组件的嵌套使用。比如 Action 这个组件就是 App 的子组件。但是当 Action 本身的代码越写越多，那么它自己也可以繁衍下一代了。

比如 Action 这一部分我们想要实现一个比较复杂的按钮，那么明智的做法就是把按钮单独抽出成一个组件，代码如下：

add SearchButton

CSS 组件化

React 社区其实提倡一种比较彻底的方法，就是不要 CSS 文件了，直接把所有的代码都 inline 的写到组件文件之中。但是我们这里稍微传统一点，还是单独使用 SCSS 文件来控制样式。

把 SearchButton 组件的样式单独抽出到一个文件中，同时让 CSS 代码也有一定的层级结构，代码如下：

css component

结语

这样，新添加的代码就在逻辑上互相隔离了，可以方便的进行复用，下一节来介绍。

组件复用

React 组件其实就像一个函数，我们传递给它参数值，它的返回结果是一个好看的组件。Web 组件化来了，Peter 感觉 Web 开发要进入一个崭新的时代。

传人参数

如果要想复用 SearchButton 先要把它的名字改得通用一些，就叫 Button 吧。

可以用这样的语法来传人变量值：

<Button text={'Search'}/>
那么 Button 组件内容，要取用这个值只需要这样：

<a href="#" className="button" >{this.props.text}</a>
把 SearchButton 改为可以复用的 Button 组件的代码如下：

Button.js

改变 Button 的颜色

有了上面的代码，Button 中就可以通过传人 text 属性来任意改变按钮文字了。但是有时候我们还想让按钮颜色也是可以变化的：

isGreen

有了上面的代码，按钮颜色就可以通过传人不同的值来改变了。代码中通过传人 isGreen={true} 让按钮显示成了绿色。如果在页面上另外一个地方想使用一个粉色的按钮，只需要写下面的代码就可以了：

<Button isPink={true} text={'Search'}/>
很方便吧？

注意，代码运行需要安装 classnames

npm i -D classnames
结语

有了如此方面的组件复用，相信未来基于 react 的各种现成的组件库就会很多了。

第三阶段

利用 webpack 和它的 react-hot-loader 来搭建”浏览器内设计“环境。

视频列表

第一个小任务：安装使用 react-hot-boilerplate

react-hot-boilerplate
第二个小任务：把 React Hot Loader 用到自己项目中

集成 React Hot Loader
集成 React Hot Loader

基本的配置就是参考：react-hot-boilerplate 。

需要安装两个包：

$ cnpm i -D react-hot-loader webpack-dev-server
其中 webpack-dev-server 是 webpack 在开发模式下的 server 。

项目需要修改内容

代码如下

use hot loader

下面来解释一下几处比较重要的修改的意义：

    devtool: 'eval',
根据官方文档 上的说明，上面一句的作用是可以提高编译的速度。

    entry: [
        'webpack-dev-server/client?http://localhost:3000',
        'webpack/hot/only-dev-server',
        './src/main.js'
    ],
上面这几行的作用可见 react-hot-loader 网站

 publicPath: '/static/'
为何要加上面这句呢？因为在开发模式下，并不真正需要真的编译出 bundle.js 文件并把它保存到硬盘上。只需要把 bundle.js 的保存到内存中就可以了，但是总要有一个位置去指定它的，所以就有了上面这句，文件系统上我们是看不到这个文件夹的。对应的 index.html 中要写 <script src="/static/bundle.js"></script> 来引用这个虚拟文件。

    path: path.join(__dirname, 'dist'),
这个正好是与 publicPath 相对的。这个是 bundle.js 的编译输出位置，保存成一个实际硬盘上的文件，用来部署项目。

{ test: /\.js$/, loaders: ['react-hot', 'babel'], include: path.join(__dirname, 'src') }
上面的 include 选项指定了 react-hot-loader 要跟踪哪些文件。上面我们把这个位置设置为 src 文件夹，所以需要把一些文件移动进去，具体是哪些文件，参考上面 git commit 的代码。

关于 http server

有了 webpack-dev-server 原来咱们那个 python 的 server 就不需要了。直接拷贝 react-hot-boilerplate 中的 server.js 过来就可以了。

启动开发模式

node server.js
结语

这样源码中我们做任何更改，页面上都立刻会更新了。而且由于有 react-hot-loader 的支持，页面不会刷新，我们所谓的“浏览器内设计”的环境也就达成了。

第四阶段

本阶段的任务是让 React 配合上 Meteorjs 全栈框架和 Material-UI 组件库，来制作成一个单页面应用（ SPA ） 。

第一个小任务：理解 SPA 的概念

好多视频#170
第二个小任务：安装 Meteor ，学会使用 React 和 Material-ui 。

当 meteor 遇见 React
Material UI
第三个小任务：通过 react-router 来添加路由控制

添加路由
第四个小任务：学习 Material UI 组件的使用

使用 MUI tabs 组件
第五个小任务：添加博客功能

添加博客页面
从服务器读取数据
渲染博客页面
博客页面的 Hero
第六个小任务：添加评论功能

保存评论到 MongoDB
显示评论
第七个小任务：收尾

完成剩余功能

SPA 是 Single Page App 的缩写。意思是“单页面应用”。指的不是本地应用，而是网站。传统的网站都是多页面的，每次点击一个链接就会打开一个新的页面。但是 SPA 是“单页面”的，意思是一旦我打开这个网站，这个“页面”就会一次性的下载到本地。SPA 页面给用户最直观的一个感受是，每次点击一个链接，页面是不会刷新的。所以用户体验更接近于本地应用，舒适感提高很多。需要注意的是，这里所谓的“单页面”指的是技术底层网站只有一个页面，但是从显示内容角度而言，一个 SPA 仍然可以展示多页内容的。一个例子 http://differential.com/ ，点击这里的导航栏链接，会发现会有新的页面内容加载进来，但是整个应用是不刷新的。

为啥要写 SPA ？

原来的网站架构不是挺好吗？为何 SPA 这个概念最近几年这么火？

简单答案是，为了追求更高一层楼的用户体验。SPA 应用的特点是一次性的把页面显示逻辑都加载到了本地浏览器中，以后每次请求，服务器那边都是提供新的数据，而不再向以往一样传送 HTML 。所以，每次点一个链接，页面上能看到的是显示加载数据的转来转去小圈圈，而不是页面整个刷新，闪我们一下。这个逻辑其实跟用 C++ 写的桌面应用，Swift 和 Java 写的 ios 和安卓 APP 一样了。

这种类原生应用的体验无疑是更好的用户体验，所以像 Facebook Twitter 这样的大公司多年来都通过各种复杂的技术来达成类似这样的效果。那么，用户用了这些网站，他们对其他应用的用户体验的要求也就会水涨船高。未来如果你的网站，不能做出这样“无刷新”的效果，用户就会觉得你很 Low 了。

各种为 SPA 而生的框架



最早大公司达成 SPA 效果，都是手工打造，用很复杂的手段来实现。随着 SPA 的流行，诞生了一些框架，让开发 SPA 变得简单。

这一类的框架比较知名的有 AngularJS, Ember.js, ExtJS 还有 facebook 的 React ，国人尤小右开发的 vue.js 。 上面这些都是前端框架，还有一个奇葩就是 meteorjs 。这个是个全栈框架，但是也是用来写 SPA 应用的。

AngularJS 和 Ember.js 都比较复杂，学习曲线陡峭。 Vue.js 其实和 React 非常像（其实 vue.js 实现很多想法要比 react 还要早，目前 react 大火，所以 vue 的作者很多方面也都在向 react 看齐）。Vue 的好处是简单高效，但是毕竟 react 社区最为火爆，资源最多，同时又比 Angular 和 Ember 容易上手，所以 Peter 的最爱是 React 。

但是 React 本身只是 View 层（界面），要完成一个完整的应用需要其他应用架构的支持，例如 Flux 。但是更容易上手，而且功能也非常强大的一种组合式 React + Meteor 来构建单页面应用。目前这种方式是 Peter 的最爱。

自己选择框架

http://todomvc.com/ 给出了同一个应用的各种版本的实现，每个人的技术背景和思维方式都不同，所以对比一下才能找到自己的最爱。

当 Meteor 遇见 React

Meteor 是目前 Nodejs 社区最为流行的全栈框架。Meteor 官方支持三种前端框架来写 UI，分别是 Blaze ，React 和 Angular 。本节来把 Meteor 安装上，然后看看 React 如何与 Meteor 协同工作。

安装 meteor

安装参考 这里 ，说到底就是下面一条命令：

curl https://install.meteor.com/ | sh
这样 meteor 就装好了。

创建一个新项目

来新建一个项目

meteor create meteor-react
这样一个简单的 meteor 项目就有了，来启动一下

cd meteor-react
meteor
这样，就可以浏览器中访问 http://localhost:3000/ 看到运行效果。自动生成的代码，我做了一个 commit

meteor create meteor-react

不用 blaze 用 react

默认 meteor 项目的 UI 库是 Blaze ，所以生成的这几个文件中的语法也是 Blaze 的语法，咱们就不详细介绍了。因为咱们要用一个更为强大的，也就是 react 。

既然这样，那么项目中可以看到的这三个文件就可以删除了

rm -rf *
这里做一个 commit:

rm blaze

但是项目现在可不是空的，里面有一个重要的隐藏文件夹 .meteor

ls  .meteor
local/     packages  platforms release   versions
其中 local/ 文件夹是很大的，因为里面装了很多包，但是做版本控制的时候也不用担心，因为和它同级的位置有一个 .gitignore 里面已经注明了忽略这个文件夹。其他的几个文件是需要跟源码一起进行版本控制的，里面分别存放了包的版本信息。

用 meteor 装包

meteor 作为一个快速开发框架，当然需要有自己的一个很大的包仓库了，比如我们运行

meteor add react
就可以把 meteor 官方提供的 react 这个包（注意跟 npm 中提供的 react 包要区分开）安装上。那么安装位置就是前面提到的 .meteor/local 里面，并且包自身的版本信息也在 .meteor/versions 文件中记录了。

命令执行完毕，可以看到安装了下面这几个包

coffeescript        added, version 1.0.11
cosmos:browserify   added, version 0.8.3
jsx                 added, version 0.2.3
react               added, version 0.14.1_1
react-meteor-data   added, version 0.2.3
react-runtime       added, version 0.14.1_1
react-runtime-dev   added, version 0.14.1
react-runtime-prod  added, version 0.14.1
其中最主要的是来自 facebook 的 react 包，还有 meteor 团队添加的 react-meteor-data 这个包，用来沟通 meteor 和 react 之间的数据的。其他的包咱们用到的时候再提。

装包结束后，咱们来做一个 commit ，看看源码中记录了那些信息：

meteor add react

跑一个 react 的 Hello World

首先到项目中新建一个 client/ 文件夹

mkdir client
注：根据 Meteor 的规范，凡是要在浏览器中执行的代码一律放在 client 文件夹下。官方文档在 这里 。

在里面添加一个 react 的组件来显示 Hello World ，具体代码如下

需要一个启动文件 startup.jsx

Meteor.startup(function () {
  ReactDOM.render(<Hello />, document.getElementById("container"));
});
组件文件 Hello.jsx

Hello = React.createClass({
  render(){
    return (
      <div>Hello World!</div>
    );
  }
});
最后一个是 index.html

<head>
  <title>Peter</title>
</head>
<body>
  <div id='container'></div>
</body>
react hello world

注意： react 代码的文件后缀一定要是 jsx ，这样 meteor 系统才能够正确识别并进行编译。参考这里 。

End

这样在 http://localhost:3000/ 就可以看到组件的显示效果了。另外，meteor 还自带了自动页面刷新功能，一旦 client/ 中的代码有变动，页面就会自动刷新，非常方便开发。

使用 material-ui

至此，一个 meteor+react 的基本项目就跑起来了，我们可以定义自己的 react 组件来添加到项目中来。但幸运的是，网上有现成的 react 组件仓库可以用的，这就是 Material-ui 。 Material-ui 是实现了 Google Material Design 风格的 React 组件套装。本节来看看如何在 Meteor + React 的环境下使用它。

下面所有操作的代码，都在这个 commit 中(需要自己动手写的代码，下面的讨论中都会提到，其他的代码都是自动生成的)：

material-ui

npm 装包

有趣而且强大无比的一点是，meteor 项目中不但能使用 meteor 包（例如前面 meteor add react 中的 react 包），也可以使用原生的 npm 包。参考这里的说明。比如我们这儿要用 materil-ui ，就采用 npm 的形式来装包。

后续操作按照 http://react-in-meteor.readthedocs.org/en/latest/client-npm/ 。

要在 Meteor 项目中使用原生的 npm 包，下面两个包是首先要装的（需要翻墙）：

meteor add meteorhacks:npm cosmos:browserify
第一个 meteor 包 npm ，负责把原生的 npm 包添加到咱们的 meteor 应用中运行，后续的 packages.json 文件就是由这个包生成的。

第二个 browserify 在客户端代码中提供了 require 的功能，这个后面是会到处都用到的，相关功能是后面的 app.browserify.js 文件。

安装完成，运行一下

$ meteor
就可以生成一个 packages.json 文件（对，是有 s 的 )。

我们需要在里面填写要安装的原生 npm 包（由 https://www.npmjs.com 提供）：

{
  "material-ui": "0.13.1",
  "externalify": "0.1.0"
}
上面的版本号，都是我在 https://www.npmjs.com 上查到的当前最新版本号。写好之后，不着急安装，先把后续的配置做好。

配置 browserify

目前，Meteor 不支持使用 require 语法加载模块，所以需要通过添加 cosmos:browserify 软件包支持的一个特殊文件，来实现这个功能。 在项目中创建一个目录 client/lib，进入到新建目录，创建一个文件名为 app.browserify.js。

在这个新建的文件里面，你可以 require 任意已安装的 NPM 模块，这样可以把它导出成一个在本项目范围内全局使用的变量（意味着项目中的每一个 JavaScript 文件都能访问这个变量）。 例如，要使用 material-ui 模块，在 app.browserify.js 文件添加下面这几行代码：

var injectTapEventPlugin = require("react-tap-event-plugin");
injectTapEventPlugin();
mui = require('material-ui');
其实最主要的就是最后一句啦。但是，为何要有 injectTapEventPlugin 相关的这两行代码呢？这个是临时的，加上就是了，不必深究，material-ui 官方的文档 有说明。

配置 externalify

我们的意图是让 material-ui 使用 meteor 的 react 包，而不是 npm 提供的 react 包，但是这个行为不是默认的，需要我们手动配置一个 Browserify 的 transforms 。步骤很简单，创建 client/lib/app.browserify.options.json 里面添加

{
  "transforms": {
    "externalify": {
      "global": true,
      "external": {
        "react": "React.require"
      }
    }
  }
}
执行装包

上面的各个配置都写好之后，运行

$ meteor
来安装 material-ui 和 externalify 这两个包并加载相关设置。

特别警告：上面两个包如前所述那样一起写到 packages.json 中，然后把相关的配置文件都写好之后然后再运行 meteor 一块儿把这两个包装好。如果操作顺序不对，最后的浏览器终端中就会报错：Uncaught Error: Invariant Violation: addComponentAsRefTo(...) 。

使用 material-ui

把 Hello.jsx 改成下面这样

const { RaisedButton } = mui;
Hello = React.createClass({
  render(){
    return (
      <div>
      <RaisedButton label="Hello World" />
      </div>
    );
  }
});
结语

这样，在 http://localhost:3000/ 就可以看到来自 material-ui 的一个按钮了，鼠标点一下可以看到漂亮的波纹效果。


添加路由

SPA 应用开发的一个挑战就是，怎么样给让单页面上看起来是有“多个页面”的。这个涉及到的就是“路由控制”（ route ）的问题。本节咱们来通过 react-router 来实现路由功能。

安装 react-router

更改 packages.json 文件，添加一行代码：

"react-router": "1.0.0"
上面的最新版本号，可以到 https://www.npmjs.com/package/react-router 来查询。 回到命令行，运行 meteor 命令，安装 react-router ，可以看到下面这样的输出：

npm-container: updating npm dependencies -- externalify, material-ui, react-router...
注意 react-router 包含了 history，所以不需要单独安装 history 了，这个干啥用，后面会看到。

使用 react-router

更改 client/lib/app.browserify.js 文件

ReactRouter = require("react-router");
把 client/startup.jsx 文件，改为下面这样：

const {
  Router,
  Route
} = ReactRouter;

const Routes = (
  <Route path="/" component={App}/>
);

Meteor.startup(function() {
  ReactDOM.render((
    <Router>
      {Routes}
    </Router>
  ), document.getElementById("container"));
});
创建一个新文件 client/App.jsx 文件：

App = React.createClass({
  render() {
    return (
      <div>
        This is App.jsx
      </div>
    );
  }
});
浏览器中访问 http://localhost:3000/ 就可以看到一个傻乎乎的页面了，显示 This is App.jsx 这些文字内容。 到这里，我们验证了 react-router 已经成功运行了。代码如下

try react-router

其实最关键的就是这一句：

 <Route path="/" component={App}/>
实现的效果应该是比较易懂的，当我访问 / 的时候，显示 App （ App.jsx ）这个组件。

添加更多路由进来

可以通过给路由组件添加 children 的形式来添加更多页面进来。 先给出这一部分的实现代码：

more routes

然后来介绍一下主要的接口功能。

startup.jsx 中

  <Route path="/" component={App}>
    <Route path="about" component={About}/>
    <Route path="blog" component={Blog}/>
    <Route path="home" component={Home}/>
    <IndexRoute component={Home}/>
  </Route>
上面的代码实现了路由的一级嵌套，每个子路由里面也可以继续进行多级嵌套的。路由的嵌套同时也对应着组件的嵌套。这句话不太好理解，看看实际代码运行效果就一目了然了。

例如 about 这一行发挥的作用是当我们访问 /about 的时候（需要完成下面的《美化 URL》那一小部分才能实现），浏览器中会显示 App 组件里面嵌套 About 组件。到 App.jsx 文件中，可以看到 {this.props.children} ，此时，这里的 children 就对应 About 组件。但是有一个小问题就是，顶级 <Route/> 中包含多个子 <Route/> ，那么默认使用哪一个子路由呢？答案是，可以通过 <IndexRoute /> 来指定默认项。

所以到这里，我们达成的效果是：访问 / ，页面中显示的内容是 App 套 Home ；访问 /blog 会显示 'App' 套 'Blog' 。

再来看一下，如何添加路由连接。 App.jsx 中添加了

const { Link } = ReactRouter;
...
        <Link to="/"> HOME </Link>
        <Link to="/blog"> BLOG</Link>
        <Link to="/about"> ABOUT </Link>
...
这样就添加了几个路由链接进来，形成了一个导航栏。

美化 URL

但是，此时点击导航栏的路由连接条目，可以看到访问每一个页面的链接是这样的

http://localhost:3000/#/about?_k=t47s0c
先来解释一下上面的链接。首先 # 会出现是正常的，毕竟我们这里只是单页面应用，显示的 about 其实也就是页面上的一个局部。后面 _k=t47s0c 是会话信息，暂时不必关心。

但是这样的链接毕竟很不美观，如何解决这个问题呢？就需要用到前面提过的 history 这个 NPM 包提供的功能了。补充一点，在传统 Web 应用中，路由是在 server 端实现的。但是 SPA 的特点是，“显示逻辑在客户端，服务器端只提供数据”，所以路由这部分自然也是在客户端（ client ）运行的。这就要用到 history.pushState() 接口。这也就是咱们用的这个包之所以叫 history 的原因了，这里了解一下就行，不必深究。

首先，需要导入 history 模块，修改 client/lib/app.browserify.js 文件

History = require("history");
修改 startup.jsx 文件，添加一行代码

const { createHistory } = History;
再修改 startup.jsx 文件中与 Router 相关的代码：

<Router history={createHistory()}>
  {Routes}
</Router>
注：这里的 createHistory 方法就是 createBrowserHistory 方法，可以参考下面的说明：

http://rackt.org/history/stable/GettingStarted.html
https://github.com/rackt/react-router/blob/master/docs/guides/basics/Histories.md
但是现在就可以访问 /about 来打开 about 页面了，url 美化工作完毕。代码如下：

pretty url

结语

这样就让单页面应用中看起来有了多个页面。

使用 MUI tabs 组件

本节来使用一个 Material UI （简称 MUI ）的组件，来制作咱们项目的导航栏。看看如何给组件传递参数，如何进行样式自定制，也会涉及到 React 的一点基础知识。Peter 发现通过使用 MUI 来学习 React 和 Material Design 的基础知识是个好方法，生动不枯燥。

加载 Tabs 组件

参考文档在这里 http://material-ui.com/#/components/tabs 。

代码如下：

basic tabs

基本上代码是一目了然的。代码中的 value 值是用来选定这个 tab 所用的标号，后面马上就会用到，详细的说明上面给出的参考文档里都有。

设置路由

现在一个漂亮的导航栏就有了，但是目前最大的问题是路由不工作了。

实现的代码如下：

add route

来解释几个不好理解的点。

this.props.history.isActive('/home') ? '1' :
上面这句用到的 history 接口来自 react-router 。文档在这里，具体 isActive 接口的详细解释也有的。简单来讲，这句就是去读 url ，如果 url 中包含 /home 字样，那么 isActive 的返回值就为 true ，同时 value 值设为 1 ，这里的 value 值传递给 <Tabs> 组件，就会让相应 value 值的那个 tab 变为活跃状态。

  _handleTabsChange(value, e, tab) {
    this.props.history.pushState(null, tab.props.route);
    this.setState({tabIndex: this._getSelectedIndex()});
  }
上面这个函数也不太好明白。先说它在什么时候被触发吧，代码中有：

 onChange={this._handleTabsChange}
意味着有人点 Tab 的时候会复发这个函数（ onChange 的参考文档在这里的 "Tabs Events" 标题下面）。再来看参数和里面的语句对参数的使用，tab.props.route 会把被点击的那个 tab 中的 route 对应的值取出（e.g /home ，/blog）。history.pushState 接口得到这个值，用来改变链接指向了。

接下来一行中的 setState 用来改变 Tabs 组件的 tabIndex 这个 state （ react 状态），tabIndex 变了，带来得结果就是活跃的 tab 项的改变。

  componentWillMount() {
    this.setState({
      tabIndex: this._getSelectedIndex()
    });
  };
上面的 componentWillMount 是 react 的 Lifecycle Methods，当页面被渲染到页面显示之前会被执行到。比如我们现在的链接是 /home 那么此时如果刷新一下页面，这个函数中的语句就会被执行，从而把对应的那个 tab 置于活跃状态。

修改样式

上面的代码已经实现了最重要的功能，下面的这些代码都仅仅是为了自定制一下样式：

change inline style

对于 MUI 组件，虽然也能添加 calssName，但是优先级要低于 inline styles，若修改 MUI 组件的样式，使用 inline styles。

另外，上面的代码中添加了一个小组件 Paper ，作用就是给导航栏加上好看的阴影而已。Paper 组件参考这里。

总结

上面介绍使用一个 Material UI 的一个较为复杂的组件，并且演示了如何进行简单的自定制样式。但是样式自定制，其实还包括主题自定制的技巧 ，这个暂时我们还没有用到。

添加博客页面

本节添加博客相关的功能。所涉及到的代码中依然会生动的引入一些 React 和 Meteor 的基础知识点进来。

添加博客列表

在 /blog 对应的页面上，来添加一个博客列表，代码如下：

blog index

博客数据后续会从 server 端取得的，但是暂时为了演示就在 getInitialState 中来随便填写一些博客数据了。然后把这些数据作为一个 prop 传递给 BlogList.jsx 。在这个文件中 _.map 接口来自于 meteor 默认就会为我们安装的 underscore.js （参考 .meteor/versions 文件中的已安装的包列表）。

注意 BlogList.jsx 中每个博客标题的链接是

       <Link to={`/blog/${post.post_name}`}>
暂时打不开，后面我们需要来来添加对应的 route 项目。

博客展示页面

如果点击一个博客条目，访问 /blog/1-beauty 链接，我们应该能够看到博客展示页面，这部分中我们就来添加。代码如下：

blog show

首先添加了对应的路由，然后是对应的博客展示页面组件 Post.jsx ，里面数据同样也是暂时伪造一下。

取消活跃状态

现在有一个小问题，就是当打开博客展示页面之后，我们希望取消导航栏上的 Blog 一项的活跃状态。可以通过添加下面的代码来达成：

set state

  componentWillReceiveProps(nextProps, nextContext) {
    this.setState({
      tabIndex: this._getSelectedIndex()
    });
  },
有了上面这个函数，每当我们点击一个 Blog 条目，也就是打开一篇博客的展示页面的时候，此时链接为类似这样的格式 /blog/1-beauty ，这样 _getSelectedIndex 函数运算结果为 0 ，导航栏 Blog 一项下面的蓝色下划线就会消失了。

前面咱们使用过 componentWillMount 这里用的是 componentWillReceiveProps 它们二者都属于 React 的 Lifecycle Methods 。二者的区别是：componentWillMount 只是在组建最初加载的时候执行一次，所以后面如果页面不刷新，一般是不会触发这个方法的。而 componentWillReceiveProps 故名思议，就是每次组建接受到了新的属性值就会触发一次。在这里，每次打开一个新的链接 App 组件的 this.props.children 都会变一下，所以会触发 componentWillReceiveProps。

使用 Sass

到这里，基本功能就都有了，下面来添加一些样式进来。除了可以用 inline style 来设置样式，也可以用 Sass 给 React 组件设置样式的。

meteor 中使用 sass 很简单，添加一个包：

meteor add fourseven:scss
然后就可以用 sass 了，代码如下

use sass

结语

这样，基本的博客展示功能就有了。

从服务器读数据

前面显示的博客数据是用假数据填充的，本节来实现用 Meteor 的接口从后台读数据。主要涉及到 Meteor 自身的一些使用技巧啦，很简单也很实用。

服务器上的数据存储格式

一种常见的做法是把数据存储在 MongoDB 中，但是我这里是以文本文件的形式来存储的。在项目根目录下创建一个文件夹，名字叫 private ，这个位置是 Meteor 要求的（参考这里的文档，搜 private ）。凡是放到这个文件夹中的数据，都可以很方便的用 Meteor 的 Assets API 读出。

实际中，我会把 private 添加到 .gitignore 文件中忽略，目的是把项目代码和博客文章内容分离（可以把博客内容放到单独一个 git 仓库中进行版本控制和存储）。具体的数据存放格式参考下面的代码 commit 。主要就是一个 posts.json 文件，相当于博客的目录，另外就是 1-blog-name.md 这样来命名的一篇篇的博客文件了。

blog data format

注意：上面的 commit 代码运行的时候，要把 blog-data 文件夹放到项目顶级目录下，并且重命名为 private 。后续操作基于项目中有 private 文件夹来做。

从服务器端请求博客内容

放在 private 中的数据，如果我们在客户端代码中不主动请求，数据是不会自动跑到客户端的。

read blog data

上面的代码所做的事情主要就是把 Blog.jsx 和 Post.jsx 中的那些假数据清空，然后用 componentWillMount() 接口中的 Meteor.call('/blog/getPost', 来从服务器端读取真正的博客数据。 Meteor.call 的文档在这里 。被 Meteor.call 调用的这个 Method （ /blog/getPost ）是要执行在 server 端的，所以定义这个方法的文件也就必须放到 server 文件夹中。

结语

到这里，我们学会了从后台的数据文件中读取数据，用来在前端显示。后面博客也会添加评论功能，到时候可以看到 Meteor 下如何操作 MongoDB 。

渲染博客内容

我们的 private 文件夹中的博客会用 markdown 格式来写，要让它能在页面上美观的展示出来，有两个任务：第一，把 markdown 转换成 html ；第二，给代码添加高亮。怎么弄？本节揭晓。

Markdown 转 html

现在面临的最大任务是把博客转化为 html 格式。这个过程我们需要借助著名的 marked 这个 npm 包的帮助。 packages.json 中添加一下包名和版本，运行 meteor 命令把它装上，然后到 app.browserify.js 中添加 require 语句，这样就可以使用包里面提供的接口了。

代码如下：

marked

参照代码可以看到，marked 接口会把 markdown 格式的 post 内容转化成 html 格式的字符串。但是 html 字符串直接插入页面中会有被 XSS 攻击的风险。{sanitize: true} 和 dangerouslySetInnerHTML 配合使用是为了防范 XSS 攻击。 详情可以参考 dangerouslySetInnerHTML 的说明文档 ，建议不必深究。

添加代码高亮

markdown 的语法格式参考 Github 的 Markdown 语法 。对应代码高亮部分的语法，写成下面这样，把代码用三个导引号包裹起来。

```
code
```
如何让代码显示的适合带高亮呢？这个需要使用 highlight.js 这个 npm 包（ 注意 highlight.js 可以自动识别代码的语言类型，所以上面不必注明代码的语言类型）。依旧是到 packages.json 中添加一下包名和版本，运行 meteor 命令把它装上，然后到 app.browserify.js 中添加

hljs = require("highlight.js");
如何使用这个包呢？需要配置一下 marked 的选项，让 marked 来调用它。参考文档在这里 ，参考官方给的代码，添加下面的设置：

marked.setOptions({
  highlight: function (code) {
    return hljs.highlightAuto(code).value;
  }
});
经过上面的 highlight 配置之后，marked 导出的 html 中，代码中包含的关键字就会被合适的高亮标签所包裹的。然后配合添加 client/stylesheets/vendor/highlight.css 这个文件（从官方的 github 仓库下载的，原始链接），页面上的代码高亮就显示出来了。

最终实现代码：

highlight.js

结语

博客中也可以使用图片，推荐可以用一个第三方的 CDN 服务来做图床，然后 markdown 文件中这样写

![](http://cdn.example.com/hello.jpg)
就可以成功使用图片了。

添加博客页面的 Hero

从 posts.json 文件中读取博客标题和发布日期，显示在博客展示页面上。

实现代码

通过下面这些代码就可以实现了：

blog meta

步骤解释

第一步，修改 methods.js 文件中的 /blog/getPost 方法，让每一篇博客的展示页面中也可以获得这篇博客的标题和日期信息：

var metaData = JSON.parse(posts)[postId - 1];
第二步，到 Post.jsx 中拿到这些元数据（ metaData ），传递给 <PostHero /> 组件

 <PostHero metaData={this.state.metaData}/>
第三步，创建 PostHero.jsx 文件，其中定义 <PostHero / 组件。

结语

一些普通的 js 的代码逻辑而已，没有太多新技巧要掌握。

保存评论到 MongoDB

从这一节开始我们给项目添加评论功能。本节先做一部分，达成的效果是，表单可以提交成功，同时数据库中可以把数据保存。

全部的实现代码：

save comments

下面来解释一下。

数据添加操作

代码中我觉得最值得一聊的一点是，/comments/add 这个方法的定义是在 lib/comments.js 文件中。根据 meteor 文件结构规范 ，定义在 lib 文件夹（也就是既不在 client/ 也不在 server/ 中）中的内容会同时在 client 和 sever 端都执行一次，这个是为什么呢？

有意思的是，Meteor 不同于传统框架的一个特点是它在客户端和服务器端都有 MongoDB 数据库。执行数据库相关的操作，最好的做法是让代码同时在客户端和服务器上都执行一下。 详细原理可以参考官方教程的 "Optimistic UI" 这一部分。

评论和博文的从属关系

一句话，评论从属于某一篇博文的体现是这条评论的存储记录中包含博文的 id 。

client/blog/Post.jsx 中新添加的这些语句

getPostId() {
  return this.props.params.postName.split('-')[0];
},
...
let postId = parseInt(this.getPostId());
...
 <CommentBox postId={postId} />
都是为了把当前博文的 id 值从链接中取出，然后传递给表单，最后在 client/comment/CommentForm.jsx 文件中，博文的 id （也就是下面的 postId）会被和其他信息一起提交并存储到 Mongodb 中。

let postId = this.props.postId;
Mongodb 中查看数据

可以服务器端（也就是命令行）中运行下面的命令

meteor mongo
use meteor
show collections
db.comments.find()
来查看数据是否已经存储。从命令行输出，可以看到评论信息已经存储到 server 端了。

不是说了前后端都有 mongodb 吗？那前端 chrome 开发者 console 中能看吗？可以的，运行

Comments.find().fetch()
就可以看到数据在前端也存储了。

结语

Database Everywhere 是 meteor 的一个伟大发明（其他地方我还真没见过这种前后端都有数据库的，你呢？），这种机制可以让应用看起来实时性更强，这一点后面需要通过例子慢慢体会。

显示评论

前面已经把评论数据存储到服务器了，这一节看如何在浏览器页面上显示出这些数据。会涉及到 websocket 长连接条件下，数据的发布和订阅技巧。

代码如下：

show comments

禁用客户端读写服务器数据的权限

默认情况下，meteor 会安装两个包 autopublish 和 insecure ，这两个包的作用是保证开发者在开发的时候在浏览其中直接操作 server 端的 mongodb 中的数据。但是在产品环境下，这样肯定不安全，所以要去掉这两个包：

meteor remove autopublish insecure
参考文档在这里 。

websocket 下的数据传输

Meteor 是一个实时性框架，这个就是它最好玩的地方，获取数据的时候不是用普通 http 请求，也不是 ajax 请求，而是通过 DDP 协议 。DDP 本质上就是客户端和服务器之间建立了基于 websocket 的长连接。而且，每次客户端或者服务器端任何一方数据有了变化，数据就会自动同步，注意是自动同步哦。

所以，既然是自动，那么没有必要专门为数据发请求了，我们只是需要搭建起这条数据的管道。如何来做呢？简单一句话：server 端做一下数据发布，client 端来订阅一下就好了。

发布数据，在 server/publish.js 中完成：

Meteor.publish('comments', function(postId) {
  return Comments.find({postId: postId});
});
订阅数据，在 client/blog/Post.jsx 中

Meteor.subscribe("comments", postId);
通道打通之后，react 组件就可以随时用下面这条语句

comments: Comments.find({}, {sort: {createdAt: 1}}).fetch(),
来获取 comments 数据了。最终得到的数据通过

<CommentBox comments={this.data.comments} postId={postId} />
来传递给组件来显示，这个数据传递过程涉及到 ReactMeteorData 这个 mixin 使用。

注意，上面得到的不是单纯的一组数据，而是一个随时可能更新的数据流。于是，Meteor 加上 React 真的是制作实时性应用的最轻便的解决方案。Meteor 的特性是，一旦服务器端数据有变化（例如我的朋友发了一条评论），那么我自己的浏览器这边也就自动的会收到数据（数据从我朋友的浏览器，经过 server 直接同步到了我的浏览器中），而同时 react 的特点是一旦组件的 state 数据有变化，那么组件会自动重新 render 的（类似于刷新）。所以，这样等于形成了一个“一根筋”的链条了。那么这个道理明白了，就可以理解，为啥在 meteor + react 条件下，实现一个评论功能，却自动就有了实时聊天的效果。

显示头像

Gravatar.com 是一个头像托管服务，比如我在上面留下了我的头像和 email 地址。那么后续，在支持 gravatar 的评论页面，只要我留下我的 email ，头像就可以自动取出来。咱们的代码中就实现了这个功能，下面来看看到底怎么实现。

首先要装包

meteor add jparker:gravatar
client/comment/Comment.jsx 中再来添加对应的代码

getGravatar() {
  let md5Hash = Gravatar.hash(this.props.email);
  return url = `http://gravatar.com/avatar/${md5Hash}.png?s=512&d=monsterid`
},
上面的方法还有个妙处，如果您没有 gravatar 账号，但是也留下了 email ，这样 gravatar 会生成一个头像给您。

结语

虽然只是一个评论显示功能，但是却给我们打开了一种做实时性应用的全新可能。原来在传统 web 框架下难死人的实时功能，现在简单了。

完成剩余功能

这是 meteor+react+materialUi 这个项目的最后一节了，来扫一下尾，把最后几个小功能添加上。

搜索功能

实现搜博客列表的功能，纯前端方式，用 React 方式实现：

add search feature

抽屉式侧边栏

由汉堡按钮触发的可隐藏的侧边导航栏：

left navbar

填充 about 和 home 页面

这些都是为了好看一些：

decorate home, about and footer components

防止页面抖动的一些小技巧

好，基本功能都有了，加上个数据加载的旋转标签，用户体验稍微好一点。另一个好处是，后续在导航栏上各个项目来回切换的时候，页面就不会看起来抖动了。

imporve UE

总结

咱们课程 demo 的制作，到此结束。


