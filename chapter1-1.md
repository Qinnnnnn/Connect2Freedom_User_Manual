# Shadowsocks 简介

### Shadowsocks 主要特点

* Shadowsocks使用自行设计的协议进行加密通信。加密算法有[AES](https://zh.wikipedia.org/wiki/高级加密标准)、[Blowfish](https://zh.wikipedia.org/wiki/Blowfish_%28密码学%29)、[IDEA](https://zh.wikipedia.org/wiki/IDEA算法)、[RC4](https://zh.wikipedia.org/wiki/RC4)等，除建立[TCP](https://zh.wikipedia.org/wiki/TCP)连接外无需[握手](https://zh.wikipedia.org/wiki/握手_%28技术%29)，每次请求只转发一个连接，因此使用起来网速较快，在移动设备上也比较省电
* 所有的流量都经过算法加密，允许自行选择算法，所以比较安全
* Shadowsocks通过[异步I/O](https://zh.wikipedia.org/w/index.php?title=异步I/O&action=edit&redlink=1)和事件驱动程序运行，响应速度快
* 客户端覆盖多个主流操作系统和平台，包括Windows、OS X、Android和iOS系统和路由器（OpenWrt）等
* 专为移动设备和无线网络优化

### Shadowsocks 安全性

* 然而Shadowsocks自行设计的加密协议对双方的身份验证仅限于[预共享密钥](https://zh.wikipedia.org/w/index.php?title=预共享密钥&action=edit&redlink=1)，亦无[完全前向保密](https://zh.wikipedia.org/wiki/完全前向保密)，也未曾有安全专家公开分析或评估协议及其实现
* Shadowsocks不能替代[TLS](https://zh.wikipedia.org/wiki/TLS)或者[VPN](https://zh.wikipedia.org/wiki/VPN)，本质上只是设置了密码的[网络代理](https://zh.wikipedia.org/wiki/代理服务器)协议，不能用作[匿名](https://zh.wikipedia.org/wiki/匿名)通信方案，该协议的目标不在于提供完整的通信安全机制，主要是为了协助上网用户在[严苛的网络环境中](https://zh.wikipedia.org/wiki/互联网审查)突破封锁。专案贡献者中不少建议有企业及用途需求的使用者使用VPN
* 在某些[极端的环境下](https://zh.wikipedia.org/wiki/防火长城)，通过[深度包检测](https://zh.wikipedia.org/wiki/深度包检测)（DPI）也有可能识别出协议特征。为了确保安全，用户应做好额外的加密和验证措施，以免泄露信息，无论使用的服务器来源是否可靠

### Shadowsocks 工作原理

目前来说虽然Shadowsocks有被检测到的可能性，但是目前来说还算是比较有效的上网方式。所以介绍一下Shadowsocks工作原理，在工作原理上有什么理解有误的地方请多多包涵。

![](/assets/import.png)在我们和目标地址之间有一个代理服务器搭建Shadowsocks协议作为SS Server

1. 我们首先通过Socks5协议在SS Local和SS Server之间进行通信。
2. 建立通信后SS Local连接到SS Server，并对Socks5中传输的数据进行对称加密传输，传输的数据格式是Shadowsocks的协议。
3. SS Server收到请求后，对数据解密，按照SS协议来解析数据。
4. SS Server根据协议内容转发请求。
5. SS Server获取请求结果后回传给SS Local
6. SS Local获取结果回传给应用程序

所以这个SS Server一定是要能访问到，并且可以访问目标网站的，所以一般SS Server选择国外的。如果这个SS Server IP被ban就没有办法翻墙了。

### Shadowsocks 协议

#### Protocol

> The shadowsocks protocol is very similar to [SOCKS5](https://www.ietf.org/rfc/rfc1928.txt) but encrypted and simpler.
>
> Below is the structure of a shadowsocks request \(sent from client-side\), which is identical for both TCP and UDP connections before encrypted \(or after decrypted\).
>
> ```
> +--------------+---------------------+------------------+----------+
> | Address Type | Destination Address | Destination Port |   Data   |
> +--------------+---------------------+------------------+----------+
> |      1       |       Variable      |         2        | Variable |
> +--------------+---------------------+------------------+----------+
> ```
>
> Possible values of address type are 1 \(IPv4\), 4 \(IPv6\), 3 \(hostname\). For IPv4 address, it’s packed as a[32-bit \(4-byte\)](https://tools.ietf.org/html/rfc791#section-2.3)big-endian integer. For IPv6 address,[a compact representation](https://tools.ietf.org/html/rfc1924)\(16-byte array\) is used. For hostname, the first byte of destination address indicates the length, which limits the length of hostname to 255. The destination port is also a big-endian integer.
>
> The request is encrypted using the specified cipher with a random IV and the pre-shared key, it then becomes so-called_payload_.

Shadowsocks基于Socks5，支持TCP和UDP，而且支持远端DNS解析，所以对于Client来说，不需要设置DNS，这样使用Shadowsocks也能避免DNS污染和劫持。 发送的TCP或UDP数据的格式如上，指定了要访问的地址、端口和数据。整个结构非常简单。

#### TCP

> The first packet of a shadowsocks TCP connection sent either from server-side or client-side must contains the randomly generated IV that used for the encryption.
>
> ```
> +-------+----------+
> |  IV   | Payload  |
> +-------+----------+
> | Fixed | Variable |
> +-------+----------+
> ```
>
> Once this packet is received, payload is decrypted using the specified cipher with the IV in the packet and the pre-shared key. For the server-side, the data is then forwarded to the destination. For client-side, the data is forwarded to the application. And this shadowsocks TCP relay goes into\_stream\_stage, in which the data is being encrypted with the same IV and transmitted directly without IV prepended.
>
> ```
> +----------+
> | Payload  |
> +----------+
> | Variable |
> +----------+
> ```

Client和Server第一次建立连接后发送的第一条数据前面带上了IV信息，这个IV是Client加密使用的IV，但是Secret Key 是保存在Client和Server的。所以Server会保存这个IV，用来解密Client的数据。然后从Payload中获取数据进行转发。而后续的请求，就不需要带上IV信息了。

服务端会根据Payload中的`AddressType的值来判断请求是否合法，如果不满足要求的3个数字，就会断开连接。`

**漏洞**

因为目前客户端大量使用AES加密方式，所以IV长度是固定的，那么很容易确定Payload中的`AddressType的位置，而AES密文和明文的位置有对应关系。所以可以模拟客户端请求，模拟密文数据，并修Address Type的值来枚举256种情况，发送给服务器。如果有3种情况没有断开连接，那么这个服务很可能是Shadowsocks服务。`

#### UDP

> When the client-side receives a UDP request from other applications, RSV and FRAG are dropped and a shadowsocks UDP request is made out from it. A random IV is always generated and used for the encryption of shadowsocks UDP request and response. Therefore, all UDP requests and responses have the same structure, no matter whether it’s the first packet or not.
>
> ```
> +-------+----------+
> |  IV   | Payload  |
> +-------+----------+
> | Fixed | Variable |
> +-------+----------+
> ```

UDP和TCP区别在于，每次都要带上IV信息。

> 以上链接来自Wikipedia



