## 一、理解css标签的加载方式
* CSS 不会阻塞 DOM 的解析，但是会阻塞页面渲染。
## 二、理解script标签的加载方式
* 在加载普通的 script 标签时，如下：
>
    <script src="a.js"></script>
* 浏览器会做如下处理：
    * 停止解析 document，但浏览器会”偷看”DOM，预先下载相关资源（但会等到脚本执行完成后，才会标识最新状态）
    * 请求 a.js 脚本文件
    * 执行 a.js 中的脚本
    * 继续解析 document

* 加defer属性的 script标签，如下：
>
    <script src="d.js" defer></script>
    <script src="e.js" defer></script>
* 浏览器会做如下处理：
    * 不阻止解析 document，并行下载 d.js, e.js
    * 即使下载完 d.js, e.js 仍继续解析 document
    * 按照页面中出现的顺序，在其他同步脚本执行后，DOMContentLoaded 事件前 依次执行 d.js, e.js
    * 当全部执行完，并再 DOMContentLoaded 事件前 再渲染 document (这里，可以再探讨)

* 加async属性的 script标签，如下：
>
    <script src="b.js" async></script>
    <script src="c.js" async></script>
* 浏览器会做如下处理：
    * 不阻止解析 document，并行下载 d.js, e.js
    * 当脚本下载完后立即执行（两者执行顺序不确定，执行阶段不确定，可能在 DOMContentLoaded 事件前或者后 ）
    * 可能渲染 document完成后，再执行。

## 三、理解 DOM 解析渲染方式
* 浏览器 解析DOM生成DOM Tree，解析CSS生成CSS Tree，最终组成render tree，再渲染页面。

## 四、参考文档，链接如下：
* 参考文档：
    * [彻底搞懂 async & defer](https://github.com/xiaoyu2er/blog/issues/8 "Markdown")
    * [原来 CSS 与 JS 是这样阻塞 DOM 解析和渲染的](https://ljf0113.github.io/2017/09/24/how-css-and-js-block-dom/ "Markdown")
* defer 和 async 浏览器支持性
    * [查询网址](http://caniuse.com/ "Markdown") 
