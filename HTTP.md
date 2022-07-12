### 介绍

超文本传输协议（`HyperText Transfer Protocol`）

HTTP是一个在计算机世界里专门在两点之间传输文字、图片、音频、视频等超文本数据的约定和规范。

#### 相关概念

CDN：全称是“Content Delivery Network”，内容分发网络

TCP/IP：全称是“Transmission Control Protocol / Internet Protocol ” ，传输控制协议与网际协议

DNS：全称是 “Domain Name System”，域名系统

URI：全称是 “Uniform Resource Identifier”， 统一资源标识符

URL：全称是 “Uniform Resource Locator”，统一资源定位符

HTTPS：全称是 “HTTP over SSL/TLS ”

SSL / TLS：全称是 “Secure Socket Layer / Transport Layer Security”

#### 版本比较

- HTTP / 0.9
  1. 只允许GET请求
  2. 响应后立即关闭链接
- HTTP / 1.0
  1. 增加了 `Head`、`POST`、等新方法
  2. 增加了响应状态码
  3. 引入了协议版本号
  4. 引入了 `HTTP Header` 的概念
  5. 传输数据的格式不仅限于文本
- HTTP / 1.1
  1. 增加了`Put`、`Delete` 等新方法
  2. 增加了缓存管理和控制
  3. 明确了连接管理，允许持久化连接
  4. 允许响应数据分块
  5. 强制要求 `Host` 头
- HTTP / 2.0
  1. 支持二进制协议，不再是纯文本
  2. 可发起多个请求，废弃了之前的管道
  3. 头部压缩，减少数据传输
  4. 允许服务器主动推送
  5. 增强了安全性

#### 请求方法

- GET：获取资源
- HEAD：获取资源的元信息
- POST：向资源提交数据
- PUT：类似POST
- DELETE：删除资源
- CONNECT：建立特殊的连接隧道
- OPTIONS：列出可对资源使用的方法
- TRACE：追踪请求-响应的传输路径

#### 状态码

- 1xx：提示信息，表示目前为协议处理的中间状态，还需要后续的操作
  - 101：Switching Proto
- 2xx：成功，报文被正确处理
  - 200：OK 成功状态码
  - 204：No Content 响应后没有body数据
  - 206：Partial Content `HTTP` 分块下载与断点续传的基础，在当客户端发起 “范围请求”，要获取资源的部分数据时出现，body里的数据为一部分，通常还伴随着 “Content-Range”
- 3xx：重定向，资源位置发生变动，需要客户端重新发送请求
  - 301：Move Permanently 永久重定向
  - 302：Move Temporary 临时重定向
  - 304：Not Modified 资源未更改，在缓存控制时出现
- 4xx：客户端错误，请求报文有误，服务器无法处理
  - 400：Bad Request 通用错误码，表示请求报文有错误，可能是数据格式错误，请求头错误等
  - 403：Forbidden 服务器禁止访问资源
  - 404：Not Found 服务器未找到资源
  - 405：Method Not Allowed 请求方法不允许
  - 406：Not Acceptable 资源无法满足客户端请求的条件
- 5xx：服务器错误，服务器在处理请求内部发生了错误
  - 500：Internal Server Error 通用错误码
  - 501：Not Implemented 客户端请求的功能还不支持
  - 502：Bad Gateway 通常是服务器作为网关或者代理时返回的错误
  - 503：Service Unavailable 服务器当前很忙，暂时无法响应服务

### HTTP报文

请求报文和响应报文的结构基本相同，由三大部分组成：

1. 起始行（start line）：描述请求或响应的基本信息
2. 头部字段集合（header）：使用 `key-value` 的形式更详细地说明报文
3. 消息正文（entity）：实际传输的数据，不一定是纯文本，也可以是图片、视频等二进制数据。

#### 请求行

包括三部分：

1. 请求方法：是一个动词，如 `GET / POST`，表示对资源的操作
2. 请求目标：通常是一个 `URI`，标记了请求方法要操作的资源
3. 版本号：表示报文使用的 `HTTP` 协议版本

![](/Users/xiaoyaozi/Library/Mobile Documents/com~apple~CloudDocs/notes/HTTP/http-request-header-line.webp)

#### 状态行（响应行）

包含三部分：

1. 版本号：表示报文使用的 `HTTP` 协议版本
2. 状态码：一个三位数，用代码的形式表示处理的结果
3. 原因：作为数字状态码的补充，是更详细的解释文字

![](/Users/xiaoyaozi/Library/Mobile Documents/com~apple~CloudDocs/notes/HTTP/http-response-header-line.webp)



#### 头部字段

`HTTP` 协议包括了非常多的头部字段，基本分为四类：

- 通用字段：在请求头和响应头里都可以出现
- 请求字段：仅出现在请求头里，进一步说明请求信息或额外的附加条件
- 响应字段：仅出现在响应头里，补充说明响应报文信息
- 实体字段：实际上属于通用字段，但专门描述 `body` 的额外信息

基本的头字段有：

- Host；指定服务器端的哪个主机来处理
- User-Agent：用一个字符串描述发起请求的客户端
- Date：报文的创建时间
- Server：正在提供Web服务的软件名称与版本号
- Content-Length：表示报文里body的长度

### TCP / IP

##### 网络分层模型

![](/Users/xiaoyaozi/Library/Mobile Documents/com~apple~CloudDocs/notes/HTTP/tcp-ip-model.webp)

1. 第一层是“**链接层**，负责在以太网、WiFI这样的底层网络上发送原始数据包
2. 第二层是“**网际层**”或者"**网络互联层**"，`IP`协议就处在这一层，在链接层的基础上，用`IP`地址取代`MAC`地址，把局域网、广域网连接起来。
3. 第三层是“传输层”，这个层协议的职责是保护数据在IP地址标记的两点之间可靠地传输，是`TCP`协议工作的层次，此外还有`UDP`
4. 第四层协议是“应用层”，这一层有很多面向具体应用的协议，例如 “Telnet”、“SSH”、“FTP”、“SMTP”等

>
>
>Mac层的传输单位是帧（frame）、IP层的传输单位是包（packet），TCP层的传输单位是段（segment）、HTTP的传输单位是消息或报文（message）。统一可称为数据包。



### 域名

域名是一个有层次的结构，是一串用“.” 分隔的多个单词，最右边的被称为“顶级域名”，然后是“二级域名”，层级关系向左依次降低。最左边的是主机名。

#### 域名的解析

DNS的核心系统是一个三层的树状、分布式服务、基本对应域名的结构：

1. 根域名服务器：管理顶级域名服务器，返回 “com”，“net”，“cn”等顶级域名服务器的IP地址。
2. 顶级域名服务器：管理各自域名下的权威域名服务器，比如 `com` 顶级域名服务器可以返回 `apple.com` 域名服务器的IP地址。
3. 权威域名服务器：管理自己域名下主机的IP地址，比如 `apple.com`权威域名服务器可以返回 `www.apple.com`的IP地址。

### HTTPS



