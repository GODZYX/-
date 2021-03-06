(最后修改时间: 2019.05.24)
# 强缓存
  * 浏览器本地存储静态资源，并根据字段 `Expires/Cache-Control` 进行强缓存过期控制。
  * `Expires` 为 HTTP/1.0 使用，`Cache-Control` 为 HTTP/1.1 使用。
  * `Expires` 根据 “服务端时间” 生成 “过期时间”。（判断是否过期需要依赖客户端时间）
  * `Cache-Control` 根据 “服务端时间” 返回 “Date” + “max-age” 确定过期时间。（判断是否过期需要依赖客户端时间）
  * 强缓存过期前，请求资源不会再发生HTTP请求。
# 协商缓存
  * 浏览器本地存储静态资源，当强缓存过期时，根据字段 `Last-Modified/ETag` 进行协商缓存过期控制。
  * `Last-Modified` 和 `ETag` 为 HTTP/1.1 使用。
  * `Last-Modified` 表示服务器资源最后修改时间。强缓存过期后，发送 “If-Modified-Since”。如果未修改，继续使用客户端缓存数据，**返回304，同时更新强缓存时间**。
  * `ETag` 表示资源的内容标识。（不唯一，通常为文件的md5或者一段hash值，只要保证写入和验证时的方法一致即可）。强缓存过期后，发送 “If-None-Match”。如果未修改，继续使用客户端缓存数据，**返回304，同时更新强缓存时间**。
  * 如果 “服务器资源修改” 或者 “内容变化”，则重新请求资源，**返回200，并更新强缓存、协商缓存状态**

# 分布式系统下，强缓存和协商缓存
  * 尽量关闭Etag，因为每台机器生成的Etag都不一样。
  * 多台机器间文件的Last-Modified必须一致，以免负载均衡不同导致对比失败。
  * **更多 ...**