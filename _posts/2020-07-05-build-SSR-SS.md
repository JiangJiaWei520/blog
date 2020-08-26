---
layout: post
title: 搭建SSR-SS服务器教程
categories: [SSR,SS,技术分享]
description: some word here
keywords: SSR, SS
---

![img](http://jiangjiawei.epizy.com/wp-content/uploads/2020/07/images.png)

![img](https://ae01.alicdn.com/kf/Hf62b13c4369e431d8cb44fa2f239760da.png)

### 自己搭建ss/ssr教程很简单，整个教程分三步：

- 第一步：购买VPS服务器
- 第二步：一键部署VPS服务器
- 第三步：一键加速VPS服务器

### 第一步购买VPS服务器

PS服务器需要选择国外的，推荐国际知名的vultr，速度不错、稳定且性价比高，按小时计费，能够随时开通和删除服务器，新服务器即是新ip。关键就算出错了，随便怎么折腾怎么戳都没事，所以比较适合新手

**注册地址：**https://www.vultr.com/

虽然是英文界面，但是现在的浏览器都有网页翻译功能，鼠标点击右键，选择网页翻译即可翻译成中文。

注册并邮件激活账号，充值后即可购买服务器。充值方式是支付宝或paypal，使用paypal有银行卡

计费从你开通服务器开始算的，不管你有没有使用，即使服务器处于关机状态仍然会计费，如果你没有开通服务器就不算。比如你今天早上开通了服务器，但你有事情，晚上才部署，那么这段时间是会计费的。同理，如果你早上删掉服务器，第二天才开通新的服务器，那么这段时间是不会计费的。在账号的Billing选项里可以看到账户余额。

**账号充值截图**

![img](https://ae01.alicdn.com/kf/H15fabfde06714542b4ef1faf3deb0606J.png)

![img](https://ae01.alicdn.com/kf/Ha590c8b4a88141d08b4dd5141b454939Y.png)

**开通服务器步骤如图**

![img](https://ae01.alicdn.com/kf/H094cd2baf6a748568b2c6094e1e283e5A.png)

![img](https://ae01.alicdn.com/kf/H708612c8f6c842ac848efcc42d1f28c0I.png)

![img](https://ae01.alicdn.com/kf/He516bf83bed5404ca93e55428cb18f78l.png)

- 点击图中的CentOS几个字，会弹出centos6，然后选中centos6！ （不要选默认的centos8，脚本不支持centos8！）

开通服务器时，当出现了ip，不要立马去ping或者用xshell去连接，再等5分钟之后，有个缓冲时间。完成购买后，找到系统的密码记下来，部署服务器时需要用到。vps系统（推荐centos6）的密码获取方法如下图：

![img](https://ae01.alicdn.com/kf/H792ae68ad887450eb2f6e7b9990361baK.png)

![img](https://ae01.alicdn.com/kf/Hd376f32c42664d23a76dee14d00de35a3.png)

**删除服务器如下图**

![img](https://ae01.alicdn.com/kf/H65d400a94c7843e88562f912d56c6c9fj.png)

![img](https://ae01.alicdn.com/kf/H08d0091a31e0466e8ae1f377dd3776cb8.png)

一个被墙ip的vps被删掉后，其ip并不会消失，会随机分配给下一个在这个服务器位置新建服务器的人，这就是为什么开新服务器会有一定几率开到被墙的ip。被墙是指在国内地区无法ping通服务器，但在国外是可以ping通的，vultr是面向全球服务，如果这个被墙ip被国外的人开到了，它是可以被正常使用的，半年或1年后这个被墙的ip可能会被国内防火墙解封，那么这就是一个良性循环。

------

### 第二步部署vps服务器

购买服务器后，需要部署一下。因为你买的是虚拟东西，而且又远在国外，我们需要一个叫Xshell的软件来远程部署。Xshell windows版下载地址：

[点击下载Xshell windows](http://xturludmhbvcwu2numac2amelz1awaz5tygcuuyzqn1exatafnq1uvjabnlywddsbcqogbgwkpg）/)

> 如果你是MAC操作系统，更简单，无需下载xshell，系统可以直接连接VPS。打开终端（Terminal），输入ssh root@ip 其中“ip”替换成你VPS的ip, 按回车键，然后复制粘贴密码，按回车键即可登录。粘贴密码时有可能不显示密码，但不影响， 参考设置方法 如果不能用MAC自带的终端连接的话，直接网上搜“MAC连接SSH的软件”，有很多，然后通过软件来连接vps服务器就行，具体操作方式参考windows xshell。

**部署教程**

下载windows xshell软件并安装后，打开软件

![img](https://ae01.alicdn.com/kf/H4e0ca2d5cc6f4d2a8f5c0605c23dd4d0h.png)

选择文件，新建

![img](https://ae01.alicdn.com/kf/H3e9814eee886419ab23c93b015bcdbb5R.png)

随便取个名字，然后把你的服务器ip填上

![img](https://ae01.alicdn.com/kf/H59e733487fef47f183292e1b0986ca61j.png)

连接国外ip即服务器时，软件会先后提醒你输入用户名和密码，用户名默认都是root，密码是你购买的服务器系统的密码。

> 如果xshell连不上服务器，没有弹出让你输入用户名和密码的输入框，表明你开到的ip是一个被墙的ip，遇到这种情况，重新开新的服务器，直到能用xshell连上为止，耐心点哦！如果同一个地区开了多台服务器还是不行的话，可以换其它地区。

![img](https://ae01.alicdn.com/kf/Hb2f6415a94554f44a1d783eb121145eby.png)

![img](https://ae01.alicdn.com/kf/H77a6444195974c1589d5f79c01fdc3f5J.png)

连接成功后，会出现如上图所示，之后就可以复制粘贴代码部署了。
CentOS 6和7/Debian6+/Ubuntu14+ ShadowsocksR一键部署管理脚本（2018.11.21更新）：

------

```
yum -y install wget
wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssr.sh && chmod +x ssr.sh && bash ssr.sh
```

备用脚本二（2018.11.21更新）
如果上面的脚本暂时用不了，可以用下面的备用脚本，备用脚本没有单独做图文教程，自己摸索下就会了。备用脚本卸载命令：./shadowsocksR.sh uninstall

```
yum -y install wget
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh
chmod +x shadowsocksR.sh
./shadowsocksR.sh 2>&1 | tee shadowsocksR.log
```

*如果提示 wget: command not found 的错误，这是你的系统精简的太干净了，wget都没有安装，所以需要安装wget。CentOS系统安装wget命令: yum install -y wget Debian/Ubuntu系统安装wget命令:apt-get install -y wget*

复制上面的脚本一代码到VPS服务器里，复制代码用鼠标右键的复制（整个代码一起复制，而不是分段哦！），然后在vps里面右键粘贴进去，因为ctrl+c和ctrl+v无效。接着按回车键，脚本会自动安装，以后只需要运行这个快捷命令就可以出现下图的界面进行设置，快捷管理命令为：bash ssr.sh

![img](https://ae01.alicdn.com/kf/H68ea896a85714b94ad8703d6328b40c5E.png)

如上图出现管理界面后，输入数字1来安装SSR服务端。如果输入1后不能进入下一步，那么请退出xshell，重新连接vps服务器，然后输入快捷管理命令bash ssr.sh 再尝试。

![img](https://ae01.alicdn.com/kf/H9e8ded9474854b5290605e9f7638e47eA.png)

根据上图提示，依次输入自己想设置的端口和密码 (密码建议用复杂点的字母组合，端口号为40-65535之间的数字)，回车键用于确认

注：关于端口的设置，总的网络总端口有6万多个，理论上可以任意设置，但不要以0开头！但是有的地区需要设置特殊的端口才有效，一些特殊的端口比如80、143、443、1433、3306、3389、8080。

![img](https://ae01.alicdn.com/kf/H1dd6fb70a34a46fe95244b07b637046aJ.png)

如上图，选择想设置的加密方式，比如10，按回车键确认

接下来是选择协议插件，如下图：

![img](https://ae01.alicdn.com/kf/Ha2a3ad95271c4a18a9bcc648c4ec132ez.png)

![img](https://ae01.alicdn.com/kf/H1e651754b4064c4da86cc20204babf4b7.png)

选择并确认后，会出现上图的界面，提示你是否选择兼容原版，这里的原版指的是SS客户端（SS客户端没有协议和混淆的选项），可以根据需求进行选择，演示选择y

之后进行混淆插件的设置。

**注意：如果协议是origin，那么混淆也必须是plain；如果协议不是origin，那么混淆可以是任意的。有的地区需要把混淆设置成plain才好用。因为混淆不总是有效果，要看各地区的策略，有时候不混淆（plain）或者（origin和plain一起使用），让其看起来像随机数据更好。（特别注意：tls 1.2_ticket_auth容易受到干扰！请选择除tls开头以外的其它混淆！！！）**

![img](https://ae01.alicdn.com/kf/H43b1d55cc60a4ae694543990164a91eeq.png)

进行混淆插件的设置后，会依次提示你对设备数、单线程限速和端口总限速进行设置，默认值是不进行限制，个人使用的话，选择默认即可，即直接敲回车键。

注意：关于限制设备数，这个协议必须是非原版且不兼容原版才有效，也就是必须使用SSR协议的情况下，才有效！

![img](https://ae01.alicdn.com/kf/H98bb2a0b19534802a8b3bca12fb3a4abH.png)

之后代码就正式自动部署了，到下图所示的位置，提示你下载文件，输入：y

![img](https://ae01.alicdn.com/kf/H3c277aeb206e43c1a3977d47cb453cccY.png)

耐心等待一会，出现下面的界面即部署完成：

![img](https://ae01.alicdn.com/kf/H2cb4a67eabc9473599e7bc6670125e4cc.png)

![img](https://ae01.alicdn.com/kf/H99be20de459847b1986617b8a55555f1A.png)

根据上图就可以看到自己设置的SSR账号信息，包括IP、端口、密码、加密方式、协议插件、混淆插件，这些信息需要填入你的SSR客户端。提醒一下：二维码链接地址由于域名失效不可用，所以部署好的账号需要自己在客户端里面手动填写信息。

如果之后想修改账号信息，直接输入快捷管理命令：bash ssr.sh 进入管理界面，选择相应的数字来进行一键修改。例如：

![img](https://ae01.alicdn.com/kf/Hef59f4ebe202440492a27e752e6d30e3a.png)

![img](https://ae01.alicdn.com/kf/H48a9424da7d940f89c3b39b8be7412416.png)

**脚本演示结束。**

此脚本是开机自动启动，部署一次即可。最后可以重启服务器确保部署生效（一般情况不重启也可以）。重启需要在命令栏里输入reboot ，输入命令后稍微等待一会服务器就会自动重启，一般重启过程需要2～5分钟，重启过程中Xshell会自动断开连接，等VPS重启好后才可以用Xshell软件进行连接。如果部署过程中卡在某个位置超过10分钟，可以用xshell软件断开，然后重新连接你的ip，再复制代码进行部署。

### 第三步：一键加速VPS服务器

总共有2种加速方法，锐速加速和bbr加速，选择1种。

**加速教程1：破解版锐速加速教程**

此加速教程为破解版锐速加速,Vultr的服务器centos6系统官方进行了更新，导致目前不支持BBR的部署，但锐速应该是可以部署的，故增加了此部署脚本，加速后对速度的提升很明显，所以推荐部署加速脚本。该加速方法是开机自动启动，部署一次就可以了。

第一步，先更换服务器内核（脚本只支持centos系统，其它系统可以直接尝试第二步）

```
yum -y install wget
wget --no-check-certificate https://blog.asuhu.com/sh/ruisu.sh && bash ruisu.sh
```

![img](https://ae01.alicdn.com/kf/H24b358b860934823b061acd3f2e7710dt.png)

不动的时候敲回车键，在上图时需要多等一会儿。

![img](https://ae01.alicdn.com/kf/He2005f96d45844cf8775c4f2d00a9c51K.png)

出现上图时表示已成功替换内核并服务器自动重启。

完成后会重启，2分钟后重新连接服务器，连上后开始第二步的操作。

第二步，一键安装锐速

```
wget -N --no-check-certificate https://raw.githubusercontent.com/91yun/serverspeeder/master/serverspeeder-all.sh && bash serverspeeder-all.sh
```

卸载加速代码命令为：

```
chattr -i /serverspeeder/etc/apx* && /serverspeeder/bin/serverSpeeder.sh uninstall -f
```

但有些内核是不适合的，部署过程中需要手动选择推荐的，当部署时出现以下字样：

![img](https://ae01.alicdn.com/kf/Hd306e02a1e57403bbcc6bcf2cfb08e80e.png)

提示没有完全匹配的内核,随便选一个内核就行,按照提示来输入数字,按回车键即可

锐速安装成功标志如下：

![img](https://ae01.alicdn.com/kf/H7954f91dc6cf45db8b57b378827b0a06C.png)

出现running字样即可!

------

**加速教程2：谷歌BBR加速教程**

vultr服务器的centos6不支持bbr加速，但centos7系统支持bbr加速，所以如果你想用bbr加速教程，vps操作系统需要选择centos7或其它系统。

```
yum -y install wget
wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh
chmod +x bbr.sh
./bbr.sh
```

把上面整个代码复制后粘贴进去，不动的时候按回车，然后耐心等待，最后重启vps服务器即可。

演示开始，如图：

复制并粘贴代码后，按回车键确认

![img](https://ae01.alicdn.com/kf/Hfe25a488656f4c9e8e95937898fde73bk.png)

如下图提示，按任意键继续部署

![img](https://ae01.alicdn.com/kf/H9f0e463983fa48a1ae39c8a048a43fc7l.png)

![img](https://ae01.alicdn.com/kf/Hf83968e35cd8410ea3340f39895f6a51f.png)

部署到上图这个位置的时候，等待3～6分钟

![img](https://ae01.alicdn.com/kf/H2f5da9892b4944dbbaa222e0476c68d8J.png)

最后输入y重启服务器，如果输入y提示command not found ，接着输入reboot来重启服务器，确保加速生效，bbr加速脚本是开机自动启动，装一次就可以了。

服务器重启成功并重新连接服务器后，输入命令lsmod | grep bbr 如果出现tcp_bbr字样表示bbr已安装并启动成功。如图：

![img](https://ae01.alicdn.com/kf/H52bc9a778e274caa91123d6479ac9cabT.png)

**注意1：**根据反馈，少部分人安装bbr脚本并重启后，几分钟过去了，发现xshell无法连接服务器且服务器ip无法ping通。解决方法是：开新服务器或者重装系统，然后先安装bbr脚本再安装ssr脚本，或者改用锐速加速脚本。

重装系统方法，点击vultr服务器设置界面——“Server Reinstall”，如下图：

![img](https://ae01.alicdn.com/kf/H886bf597bb9c44109fc384f66f1e0a47L.png)

重装过程一般需要5～10分钟。

注意2：如果创建的是centos7的服务器，安装bbr加速后需要使用命令关闭防火墙，否则无法使用代理。CentOS 7.0默认使用的是firewall作为防火墙。

查看防火墙状态命令：

```
firewall-cmd --state
```

停止

```
firewall命令：systemctl stop firewalld.service
```

禁止firewall开机启动命令：

```
systemctl disable firewalld.service
```

来源: 跨界思享
文章作者: 李龙耀
文章链接: [https://www.kuajie.me/2019/12/01/%E6%90%AD%E5%BB%BASSR-SS%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%95%99%E7%A8%8B%E3%80%8A%E9%80%82%E5%90%88%E6%96%B0%E6%89%8B%E3%80%8B/](https://www.kuajie.me/2019/12/01/搭建SSR-SS服务器教程《适合新手》/)
本文章著作权归作者所有，任何形式的转载都请注明出处。