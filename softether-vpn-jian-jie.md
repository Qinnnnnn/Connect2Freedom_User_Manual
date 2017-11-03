# SoftEther VPN 简介

SoftEther VPN是世界上功能最强大，最简单的VPN软件之一。它是开源软件并托管于GitHub，作为[日本筑波大学](http://www.tsukuba.ac.jp/english/)的学术研究项目开发。

### 指导

![](http://www.softether.org/@api/deki/files/5/=selogo.jpg "selogo.jpg")

阅读指导，快速掌握SoftEther的主要特点和优势

* [极其强大的VPN连接](http://www.softether.org/1-features/1._Ultimate_Powerful_VPN_Connectivity)
* [二层以太网VPN](http://www.softether.org/1-features/2._Layer-2_Ethernet-based_VPN)
* [安全可靠](http://www.softether.org/1-features/3._Security_and_Reliability)
* [快速吞吐量高，能力高](http://www.softether.org/1-features/4._Fast_Throughput_and_High_Ability)
* [易于安装和管理](http://www.softether.org/1-features/5._Easy_Installation_and_Management)

### 特征

![](/assets/import1.png)

* 免费和[开源](http://www.softether.org/5-download/src)软件
* 轻松建立[远程访问](http://www.softether.org/4-docs/1-manual/A._Examples_of_Building_VPN_Networks/10.4_Build_a_PC-to-LAN_Remote_Access_VPN)和[站点到站点](http://www.softether.org/4-docs/1-manual/A._Examples_of_Building_VPN_Networks/10.5_Build_a_LAN-to-LAN_VPN_%28Using_L2_Bridge%29)VPN
* SSL-VPN通过HTTPS隧道[通过NAT和防火墙](http://www.softether.org/1-features/1._Ultimate_Powerful_VPN_Connectivity)
* 革命性的[VPN over ICMP和VPN over DNS](http://www.softether.org/1-features/1._Ultimate_Powerful_VPN_Connectivity#1.6._VPN_over_ICMP.2C_and_VPN_over_DNS_%28Awesome!%29)功能
* 抵抗高度限制的防火墙
* [以太网桥接（L2）](http://www.softether.org/1-features/2._Layer-2_Ethernet-based_VPN)和[IP路由（L3）](http://www.softether.org/4-docs/1-manual/A._Examples_of_Building_VPN_Networks/10.6_Build_a_LAN-to-LAN_VPN_%28Using_L3_IP_Routing%29)通过VPN
* 嵌入式[动态DNS](http://www.softether.org/1-features/1._Ultimate_Powerful_VPN_Connectivity#1.4._Built-in_Dynamic_DNS_%28*.softether.net%29)和[NAT遍历，](http://www.softether.org/1-features/1._Ultimate_Powerful_VPN_Connectivity#1.5._NAT_Traversal)因此不需要静态或固定的IP地址
* [AES 256位和RSA 4096位](http://www.softether.org/1-features/3._Security_and_Reliability)加密
* 足够的安全功能，如[日志记录](http://www.softether.org/4-docs/1-manual/3._SoftEther_VPN_Server_Manual/3.5_Virtual_Hub_Security_Features)和[防火墙](http://www.softether.org/4-docs/1-manual/3._SoftEther_VPN_Server_Manual/3.5_Virtual_Hub_Security_Features)内部VPN隧道
* [1Gbps级的高速吞吐量性能，](http://www.softether.org/4-docs/9-research/Design_and_Implementation_of_SoftEther_VPN)具有低内存和CPU使用率。
* **支持Windows，Linux，Mac，Android，iPhone，iPad和Windows Mobile**
* VPN隧道底层协议都支持SSL-VPN（HTTPS）和6个主要VPN协议（[OpenVPN](http://www.softether.org/1-features/1._Ultimate_Powerful_VPN_Connectivity#Support_OpenVPN_Protocol)，[IPsec](http://www.softether.org/4-docs/2-howto/9.L2TPIPsec_Setup_Guide_for_SoftEther_VPN_Server)，[L2TP](http://www.softether.org/4-docs/2-howto/9.L2TPIPsec_Setup_Guide_for_SoftEther_VPN_Server)，[MS-SSTP](http://www.softether.org/1-features/1._Ultimate_Powerful_VPN_Connectivity#Support_Microsoft_SSTP_VPN_Protocol)，[L2TPv3](http://www.softether.org/4-docs/2-howto/9.L2TPIPsec_Setup_Guide_for_SoftEther_VPN_Server/6.Cisco_IOS_L2TPv3%2F%2F%2F%2FIPsec_Edge-VPN_Router_Setup)和[EtherIP](http://www.softether.org/3-spec)）
* 该[OpenVPN的克隆功能](http://www.softether.org/1-features/1._Ultimate_Powerful_VPN_Connectivity#Support_OpenVPN_Protocol)支持传统的OpenVPN的客户
* IPv4 /[IPv6](http://www.softether.org/1-features/4._Fast_Throughput_and_High_Ability#4.8._Full_IPv6_Supports)双栈
* 在[VPN服务器](http://www.softether.org/4-docs/1-manual/3._SoftEther_VPN_Server_Manual)上运行[的Windows，Linux，FreeBSD的，Solaris和Mac OS X的](http://www.softether.org/3-spec)
* 在[GUI](http://www.softether.org/1-features/5._Easy_Installation_and_Management)上配置所有设置
* [多种语言](http://www.softether.org/1-features/5._Easy_Installation_and_Management#5.8._Multi-language.2C_Single_Binary_Package_and_Unicode_Support)（英文，日文和简体中文）
* 没有内存泄漏。高质量稳定的代码，用于长期运行。我们总是验证在释放构建之前没有内存或资源泄漏
* RADIUS / NT域用户认证功能
* RSA证书认证功能
* 深度检查数据包记录功能
* 源IP地址控制列表功能
* syslog传递函数
* [详细规格](http://www.softether.org/3-spec)

### SoftEther VPN架构

![](/assets/import2.png)

以太网设备的虚拟化是SoftEther VPN架构的关键。SoftEther VPN虚拟化以太网设备，以实现[远程访问VPN](http://www.softether.org/4-docs/2-howto/1.VPN_for_On-premise/2.Remote_Access_VPN_to_LAN) 和 [站点到站点VPN](http://www.softether.org/4-docs/2-howto/1.VPN_for_On-premise/3.LAN_to_LAN_Bridge_VPN)的灵活的虚拟专用网络 。SoftEther VPN实现虚拟网络适配器程序作为软件仿真的传统以太网网络适配器。SoftEther VPN将虚拟以太网交换机（Virtual Ethernet Switch， [虚拟中枢](http://www.softether.org/4-docs/1-manual/3._SoftEther_VPN_Server_Manual/3.4_Virtual_Hub_Functions)）作为软件仿真的传统以太网交换机实现。SoftEther VPN通过网络适配器和交换机之间的软件仿真以太网电缆实现VPN会话。

您可以 在服务器计算机上使用SoftEther VPN创建一个或多个 [虚拟集线器](http://www.softether.org/4-docs/1-manual/3._SoftEther_VPN_Server_Manual/3.4_Virtual_Hub_Functions)。该服务器计算机将成为 [VPN服务器](http://www.softether.org/4-docs/1-manual/3._SoftEther_VPN_Server_Manual)，它接受来自[VPN客户端](http://www.softether.org/4-docs/1-manual/4._SoftEther_VPN_Client_Manual) 计算机的VPN连接请求 。

您可以 在客户端计算机上使用SoftEther VPN创建一个或多个 [虚拟网络适配器](http://www.softether.org/4-docs/1-manual/4._SoftEther_VPN_Client_Manual/4.3_Virtual_Network_Adapter)。该客户端计算机将成为一个VPN客户端，它与VPN服务器上的Virtual Hub建立VPN连接。

您可以在VPN客户端和VPN服务器之间建立VPN会话，称为“VPN隧道”。VPN会话是虚拟化网络电缆。通过TCP / IP连接实现VPN会话。通过VPN会话的信号由SSL加密。因此，您可以安全地建立超出Internet的VPN会话。VPN会话由SoftEther VPN的 [“VPN over HTTPS”技术建立](http://www.softether.org/1-features/1._Ultimate_Powerful_VPN_Connectivity)。这意味着SoftEther VPN可以创建超过[任何类型的防火墙和NAT](http://www.softether.org/4-docs/2-howto/7.Replacements_of_Legacy_VPNs/1.Penetrates_Firewall_by_SSL-VPN)的VPN连接 。

![](/assets/import3.png)

虚拟Hub将所有连接的VPN会话的所有以太网数据包交换到其他连接的会话。这种行为与传统的以太网交换机相同。虚拟集线器具有FDB（转发数据库），以优化以太网帧的传输。

您可以定义 [本地网桥](http://www.softether.org/4-docs/1-manual/3._SoftEther_VPN_Server_Manual/3.6_Local_Bridges) 使用本地网桥功能的虚拟集线器与现有的物理以太网段之间。本地桥接器在物理以太网适配器和虚拟集线器之间交换数据包。您可以 通过使用本地桥接功能实现从家庭或移动到公司网络的 [远程访问VPN](http://www.softether.org/4-docs/2-howto/1.VPN_for_On-premise/2.Remote_Access_VPN_to_LAN)。

您可以 在两个或多个远程Virtual Hub之间定义 [级联连接](http://www.softether.org/4-docs/1-manual/A._Examples_of_Building_VPN_Networks/10.5_Build_a_LAN-to-LAN_VPN_%28Using_L2_Bridge%29)。通过级联，您可以将两个或多个远程以太网段集成到单个以太网段。例如，在站点A，B和C之间建立级联连接后，站点A中的任何计算机将能够与站点B和站点C中的计算机进行通信。这是 [站点到站点VPN](http://www.softether.org/4-docs/2-howto/1.VPN_for_On-premise/3.LAN_to_LAN_Bridge_VPN)。

SoftEther VPN还可以通过UDP建立VPN会话。SoftEther VPN的UDP模式支持 [NAT穿越](http://www.softether.org/4-docs/2-howto/6.VPN_Server_Behind_NAT_or_Firewall/1.Dynamic_DNS_and_NAT_Traversal)。NAT穿越功能允许现有NAT或防火墙后面的VPN服务器接受传入的VPN会话。在防火墙或NAT之后的公司网络上设置VPN服务器之前，您不需要网络管理员的特殊许可。此外，SoftEther VPN Server可以放置在动态IP地址环境中，因为SoftEther VPN具有内置的 [动态DNS（DDNS）](http://www.softether.org/4-docs/2-howto/6.VPN_Server_Behind_NAT_or_Firewall/1.Dynamic_DNS_and_NAT_Traversal) 功能。

SoftEther VPN Server支持额外的VPN协议，包括 [L2TP / IPsec](http://www.softether.org/4-docs/2-howto/9.L2TPIPsec_Setup_Guide_for_SoftEther_VPN_Server)， [OpenVPN](http://www.softether.org/4-docs/2-howto/7.Replacements_of_Legacy_VPNs/2.Replacements_of_OpenVPN)， [Microsoft SSTP](http://www.softether.org/1-features/1._Ultimate_Powerful_VPN_Connectivity)， [L2TPv3](http://www.softether.org/1-features/1._Ultimate_Powerful_VPN_Connectivity) 和 [EtherIP](http://www.softether.org/1-features/1._Ultimate_Powerful_VPN_Connectivity)。这些实现了与[iPhone，iPad，Android，Windows和Mac OS X](http://www.softether.org/4-docs/2-howto/9.L2TPIPsec_Setup_Guide_for_SoftEther_VPN_Server)以及 [Cisco VPN路由器](http://www.softether.org/4-docs/2-howto/9.L2TPIPsec_Setup_Guide_for_SoftEther_VPN_Server/6.Cisco_IOS_L2TPv3%2F%2F%2F%2FIPsec_Edge-VPN_Router_Setup) 和其他厂商VPN产品的[内置L2TP / IPsec VPN客户端](http://www.softether.org/4-docs/2-howto/9.L2TPIPsec_Setup_Guide_for_SoftEther_VPN_Server)的互操作性 。

> 以上链接来自SoftEther VPN官方网站



