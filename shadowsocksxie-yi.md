# Shadowsocks协议

### Protocol

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

### TCP

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

#### **漏洞**

因为目前客户端大量使用AES加密方式，所以IV长度是固定的，那么很容易确定Payload中的`AddressType的位置，而AES密文和明文的位置有对应关系。所以可以模拟客户端请求，模拟密文数据，并修Address Type的值来枚举256种情况，发送给服务器。如果有3种情况没有断开连接，那么这个服务很可能是Shadowsocks服务。`

### UDP

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

