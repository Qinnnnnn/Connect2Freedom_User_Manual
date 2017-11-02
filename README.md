# Shadowsocks/ShadowsocksR用户手册

> 翻越防火长城，你可以到达世界上的每一个角落
>
> Across the Great Firewall, you can reach every corner in the world.

### Shadowsocks主要特点

Shadowsocks使用自行设计的协议进行加密通信。

* 加密算法有[AES](https://zh.wikipedia.org/wiki/%E9%AB%98%E7%BA%A7%E5%8A%A0%E5%AF%86%E6%A0%87%E5%87%86)、[Blowfish](https://zh.wikipedia.org/wiki/Blowfish_%28%E5%AF%86%E7%A0%81%E5%AD%A6%29)、[IDEA](https://zh.wikipedia.org/wiki/IDEA%E7%AE%97%E6%B3%95)、[RC4](https://zh.wikipedia.org/wiki/RC4)等，除建立[TCP](https://zh.wikipedia.org/wiki/TCP)连接外无需[握手](https://zh.wikipedia.org/wiki/%E6%8F%A1%E6%89%8B_%28%E6%8A%80%E6%9C%AF%29)，每次请求只转发一个连接，因此使用起来网速较快，在移动设备上也比较省电
* 所有的流量都经过算法加密，允许自行选择算法，所以比较安全
* Shadowsocks通过[异步I/O](https://zh.wikipedia.org/w/index.php?title=%E5%BC%82%E6%AD%A5I/O&action=edit&redlink=1)和事件驱动程序运行，响应速度快
* 客户端覆盖多个主流操作系统和平台，包括Windows、OS X、Android和iOS系统和路由器（OpenWrt）等
* 专为移动设备和无线网络优化



