##	web安全

####	cookie

攻击：

通过XSS攻击可获取用户的cookie；

网络截获；

flash代码截获cookie

提高安全性：

设置cookie的HTTPOnly属性可以防止页面脚本获取，但不能完全防范XSS攻击。

使用HTTPS传输；

cookie设置合理的有效期；

写cookie时加密，读cookie时解密。

####	负载均衡

负载均衡（Load Balance，简称LB）是一种服务器或网络设备的集群技术。负载均衡将特定的业务（网络服务、网络流量等）分担给多个服务器或网络设备，从而提高了业务处理能力，保证了业务的高可用性。

目的：
为了解决单个节点压力过大、web服务器相应过慢、服务器负载过重时导致的服务瘫痪，无法正常提供服务的问题。