# Shadowsocks/ShadowsocksR用户手册

> 翻越防火长城，你可以到达世界上的每一个角落
>
> Across the Great Firewall, you can reach every corner in the world.

### Shadowsocks主要特点

* Shadowsocks使用自行设计的协议进行加密通信。加密算法有[AES](https://zh.wikipedia.org/wiki/高级加密标准)、[Blowfish](https://zh.wikipedia.org/wiki/Blowfish_%28密码学%29)、[IDEA](https://zh.wikipedia.org/wiki/IDEA算法)、[RC4](https://zh.wikipedia.org/wiki/RC4)等，除建立[TCP](https://zh.wikipedia.org/wiki/TCP)连接外无需[握手](https://zh.wikipedia.org/wiki/握手_%28技术%29)，每次请求只转发一个连接，因此使用起来网速较快，在移动设备上也比较省电
* 所有的流量都经过算法加密，允许自行选择算法，所以比较安全
* Shadowsocks通过[异步I/O](https://zh.wikipedia.org/w/index.php?title=异步I/O&action=edit&redlink=1)和事件驱动程序运行，响应速度快
* 客户端覆盖多个主流操作系统和平台，包括Windows、OS X、Android和iOS系统和路由器（OpenWrt）等
* 专为移动设备和无线网络优化

### Shadowsocks安全性

* 然而Shadowsocks自行设计的加密协议对双方的身份验证仅限于[预共享密钥](https://zh.wikipedia.org/w/index.php?title=%E9%A2%84%E5%85%B1%E4%BA%AB%E5%AF%86%E9%92%A5&action=edit&redlink=1)，亦无[完全前向保密](https://zh.wikipedia.org/wiki/%E5%AE%8C%E5%85%A8%E5%89%8D%E5%90%91%E4%BF%9D%E5%AF%86)，也未曾有安全专家公开分析或评估协议及其实现
* Shadowsocks不能替代[TLS](https://zh.wikipedia.org/wiki/TLS)或者[VPN](https://zh.wikipedia.org/wiki/VPN)，本质上只是设置了密码的[网络代理](https://zh.wikipedia.org/wiki/%E4%BB%A3%E7%90%86%E6%9C%8D%E5%8A%A1%E5%99%A8)协议，不能用作[匿名](https://zh.wikipedia.org/wiki/%E5%8C%BF%E5%90%8D)通信方案，该协议的目标不在于提供完整的通信安全机制，主要是为了协助上网用户在[严苛的网络环境中](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E5%AE%A1%E6%9F%A5)突破封锁。專案貢獻者中不少建議有企業級用途需求的使用者使用VPN
* 在某些[极端的环境下](https://zh.wikipedia.org/wiki/%E9%98%B2%E7%81%AB%E9%95%BF%E5%9F%8E)，通过[深度包检测](https://zh.wikipedia.org/wiki/%E6%B7%B1%E5%BA%A6%E5%8C%85%E6%A3%80%E6%B5%8B)（DPI）也有可能识别出协议特征。为了确保安全，用户应做好额外的加密和验证措施，以免泄露信息，无论使用的服务器来源是否可靠



