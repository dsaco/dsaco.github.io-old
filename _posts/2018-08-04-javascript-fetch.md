---
layout: post
title:  "fetch"
date:   2018-08-04 17:36:00 +0800
tags: javascript api fetch
---

Fetch Api 提供了一个javscript接口，用于访问和操纵HTTP管道的部分，例如请求和响应。
fetch规范与jQuery.ajax()主要有两种方式的不同：
- 当接收到一个代表错误的HTTP状态码时，从fetch()返回的Promise不会被标记为reject，即使该HTTP响应的状态码是404或500。相反，它会将Promise状态标记为resolve（但是会将resolve的返回值的ok属性设置为false），仅当网络故障时或请求被阻止时才会标记为reject。
- 默认情况下，fetch不会从服务端发送或接收任何cookies（需手动设置credentials）。

#### 语法
> Promise<Response> fetch(input[, init]);

##### input
定义要获取的资源。
- 一个USVString字符串，包含要获取资源的URL
- 一个Request对象

##### init 可选
- method: 请求使用的方法，如GET、POST等等，默认为GET
- headers: 请求的头信息，形式为 Headers 的对象或包含 ByteString 值的对象字面量。
  - Content-Type
    - application/json 指出实体的类型是 JSON
    - application/x-www-form-urlencoded  key1=value1&key2=value2
    - text/plain 纯文本
    - text/xml xml
- body: 请求的 body 信息：可能是一个 Blob、BufferSource、FormData、URLSearchParams 或者 USVString 对象。注意 GET 或 HEAD 方法的请求不能包含 body 信息。JSON格式需要转为字符串。
- mode: 请求的模式，如 cors、 no-cors 或者 same-origin。
  - same-origin：如果使用此模式向另外一个源发送请求，显而易见，结果会是一个错误。你可以设置该模式以确保请求总是向当前的源发起的。
  - no-cors：保证其对应的方法只有HEAD，GET或POST方法 。即使ServiceWorkers 拦截了这个请求,除了simple header之外不会添加或覆盖任意其他header, 另外JavaScript不会读取Response的任何属性 . 这样将会确保ServiceWorkers不会影响Web语义(semantics of the Web), 同时保证了在跨域时不会发生安全和隐私泄露的问题
  - cors（默认）：允许跨域请求，例如访问第三方供应商提供的各种API
  - navigate：支持导航的一个模式
- credentials: 请求的 credentials，如 omit、same-origin 或者 include。用于表示用户代理是否应该在跨域请求的情况下从其他域发送cookies。
  - omit：从不发送cookies
  - same-origin（默认）：只有当URL与响应脚本同源才发送 cookies、 HTTP Basic authentication 等验证信息.(浏览器默认值,在旧版本浏览器，例如safari 11依旧是omit，safari 12已更改)
  - include: 不论是不是跨域的请求,总是发送请求资源域在本地的 cookies、 HTTP Basic authentication 等验证信息
- cache:  请求的 cache 模式: default 、 no-store 、 reload 、 no-cache 、 force-cache 或者 only-if-cached 。
- redirect: 可用的 redirect 模式: follow (自动重定向), error (如果产生重定向将自动终止并且抛出一个错误), 或者 manual (手动处理重定向). 在Chrome中，Chrome 47之前的默认值是 follow，从 Chrome 47开始是 manual。
- referrer: 一个 USVString 可以是 no-referrer、client或一个 URL。默认是 client。
- referrerPolicy: Specifies the value of the referer HTTP header. May be one of no-referrer、 no-referrer-when-downgrade、 origin、 origin-when-cross-origin、 unsafe-url 。
- integrity: 包括请求的  subresource integrity 值 （ 例如： sha256-BpfBw7ivV8q2jLiT13fxDYAe2tJllusRSZ273h2nFSE=）。

##### Response
###### 属性
- status (number) - HTTP response code in the 100–599 range
- statusText (String) - Status text as reported by the server, e.g. "Unauthorized"
- ok (boolean) - True if status is HTTP 2xx

###### 方法
- text() - yields the response text as String
- json() - yields the result of JSON.parse(responseText)
- blob() - yields a Blob
- arrayBuffer() - yields an ArrayBuffer
- formData() - yields FormData that can be forwarded to another request








---------
