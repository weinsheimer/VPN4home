鉴于墙内在当前的环境下无法正常讨论这方面的内容，所以就借宝地GitHub发表此分享
### 用WireGuard 建立个人/家庭使用的VPN以实现远程控制、翻墙等功能
在此先强调一下，这完全在现有设备基础上的方案，达到成本最小化

下图的小房子可以是在国内或世界上任何一个有网络的地方

<img src = https://cdnjson.com/images/2023/12/31/pc_net3.png>

https://cdnjson.com/images/2023/12/31/pc_net3.png 不知为何此图在预览中只显示一半
上图中最关键的地方是有颜色的Tunnel，用WireGuard建立的隧道/Tunnel就是一个高性能点对点VPN(虚拟专用网络)，而且操作简单；
小屋内的设备为“被对方”，右边的设备为“主动方”。
特别强调一下：这里是一个完全针对于个人/家庭低成本的VPN方案，不需要如Teamviewer，qq，ToDesk，花生壳，向日葵等第三方服务商(对临时性遥控第三方免安装方案更快捷)，不受他们政策干扰(一会要求注册、免费/付费等等)，不担心他们截取信息。
有了这个VPN就可以远程启动、远程使用、远程关闭上图左边小屋内的PC和Laptop，可以有下面的使用场景：
1. 在外面用一台很轻薄弱小的笔记本操纵一台强大的台式机，把重要的资料存入台式机，比如视频剪辑；
2. 远程办公，不用把电脑带来带去，或者跨境办公；
3. 通过VPN实现科学上网，轻松跨境（需要在路由器里相应设置）；
4. 从海外到国内看境内网上电影；
5. 把服务器端程序放在公网上，同时把数据库及重要数据放在房内以减少被黑的机会；
6. 在一个相对安全的地方建立大容量资料库，同时保证可用性。

实施的前提+步骤提示(此处讨论Windows电脑)：
1. 对被动方路由器有一定要求，目前查到的信息 260元左右的 [TP-Link AX3000](https://www.zhihu.com/question/592181060/answer/3016874278) 就支持WireGuard；还有华硕/Asus，斐讯，腾达，荣耀：荣耀，水星，蒲公英，Netgear，领势/Linksys，GL.iNet，小米等都有支持WireGuard的型号；
2. 操刀者要有一定的理解力和动手能力，因为有太多种组合，在此只能给出思路，如果具体到某个型号的设备意义不大；操作上有很多细节问题，也许需要根据具体情况在网上找解决的办法，通常很简单；
3. 需要有这个软件 wireguard-amd64-0.5.3.msi 2.7 MB，可以在网上比较难找，安装在主动方的电脑上；
4. 被动方路由器要做相应设置，各个品牌开通WireGuard是异曲同工，但界面会有所不同，需要开通和导出配置文件，并提供给主动方电脑，然后主动方电脑安装wireguard并导入设置文件
5. 接通wireguard以后打开win RDP远程控制；这里也可以使用[WOL2](http://oette.info)，这个程序用起来很方便；
6. 想用网络唤醒功能，在上图的房子中的PC和笔记本必须用网线跟路由器连接，不然无法唤醒；

关键步骤：
1. 在支持WireGuard路由器开通WireGuard功能+导出设置文件；
2. 在主动电脑(需要进入VPN的设备上)上安装Wireguard+导入设置文件，（安装成功就可以在WireGuard界面图中看到链接成功）；
3. 根据参考资料里的“Windows的RDP远程控制”教程在被动电脑上打开允许Win RDP接入的开关，从主动设备启动RDP，如连接成功就已经完成了最主要的遥控功能了；
4. 如果想要完美的“远程启动、远程使用、远程关闭”功能可以安装[WOL2](http://oette.info)，通过WOL2控制RDP会更方便，整个用户体验好爽。

参考资料：
如何打开win远程控制 C:\Windows\system32\mstsc.exe 或 DOS窗户 + mstsc
下图为WireGuard界面
<img src=https://cdnjson.com/images/2024/01/02/wireguard_setup.jpg>

[WireGuard-UI 安装和配置](https://songxwn.com/WireGuard-UI-install/)
[WireGuard 教程：WireGuard 的工作原理 2020.7](https://icloudnative.io/posts/wireguard-docs-theory/)

[华硕路由器使用ipv6+ddns开启wireguard vpn实现内网穿透](https://zhuanlan.zhihu.com/p/659604306)

[记录: Redmi AX5 安装wireguard实现内网访问](https://zhuanlan.zhihu.com/p/446120839)

[WOL网络唤醒远程开机的关键步骤，魔术唤醒一步都不能少！](https://blog.csdn.net/lsw_Cs/article/details/119885621)
WOL(Wake on lan)远程唤醒-> WOL2.exe 非常好用 http://oette.info

<img src=https://cdnjson.com/images/2024/01/02/WOL2_setup3.jpg>

[Windows的RDP远程控制](https://blog.csdn.net/qq_41439534/article/details/130675236)

[自动关闭和启动 Debian Linux Dell Thinkpad 笔记本电脑](Debian_wol.html)
