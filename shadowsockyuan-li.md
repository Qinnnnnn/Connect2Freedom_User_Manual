# Shadowsocks工作原理

目前来说虽然Shadowsocks有被检测到的可能性，但是目前来说还算是比较有效的上网方式。所以介绍一下Shadowsocks工作原理，在工作原理上有什么理解有误的地方请多多包涵。

### 原理

### ![](/assets/import.png)在我们和目标地址之间有一个代理服务器（我们的服务器）

1. 我们首先通过SS Local和SS Server进行通信，通过Socks5协议进行通信。
2. SS Local连接到VPS，并对Socks5中传输的数据进行对称加密传输，传输的数据格式是Shadowsocks的协议。
3. SS Server收到请求后，对数据解密，按照SS协议来解析数据。
4. SS Server根据协议内容转发请求。
5. SS Server获取请求结果后回传给SS Local
6. SS Local获取结果回传给应用程序

所以这个VPS一定是要能访问到，并且可以访问目标网站的，所以一般VPS选择国外的。如果这个VPS IP被封就没有办法翻墙了。



