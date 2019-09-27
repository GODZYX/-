# 跨域
  * 广义：跨域是指一个域下的文档或脚本，试图去请求另一个域下的资源。
    - 资源跳转：A链接、重定向、表单提交
    - 资源嵌入：`<link>、<script>、<img>、<frame>` 等dom标签，还有样式中`background:url()、@font-face()`等文件外链
    - 脚本请求：js发起的ajax请求、dom和js对象的跨域操作等
  * 狭义：是由浏览器同源策略限制的一类请求场景。
# 同源策略
  * 同源策略/SOP（Same origin policy）是一种约定，它是浏览器最核心也最基本的安全功能，如果缺少了同源策略，浏览器很容易受到XSS、CSFR等攻击。所谓同源是指**协议+域名+端口**三者相同，即便两个不同的域名指向同一个ip地址，也非同源。
  * 同源策略限制以下几种行为：
    - Cookie、LocalStorage 和 IndexDB 无法读取
    - DOM 和 Js 对象无法获得
    - AJAX 请求不能发送
# 跨域解决方案
  * 原生 form表单提交 跨域
  * 通过 jsonp 跨域
  * iframe 跨域（document.domain + location.hash + window.name）
  * postMessage 跨域
  * 跨域资源共享（CORS）
  * nginx代理跨域
  * nodejs中间件代理跨域
  * WebSocket协议跨域

## 后续还有，每种跨域的具体解决方案

form表单提交没有跨域问题，提交form表单到另外一个域名，原来页面是无法获取新页面的内容，或者说form提交后不需要返回，但是ajax是需要返回的。


[跨域请求大全](https://segmentfault.com/a/1190000011145364)