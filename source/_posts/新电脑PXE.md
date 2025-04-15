---
title:  新电脑 PXE WDS iVentoy 安装 Windows 11
date: 2025-04-13 18:00:00
categories: Diary
---
# 新电脑 ohhhhhh
旧的电脑虽说还能用但是新能已经捉襟见肘, 打游戏偶尔卡卡的不说还管不了机了! 本来想换先电脑好久了就干脆狠了心直接换新.
配置如下:
- CPU: AMD Ryzen 9700x
- GPU: Nvidia RTX 5070ti
- RAM: Asgard 32GBx2
- 硬盘: Predator 9000 1T, Predator G7 4T, Fanxiang 2T x2
- 主板: MSI X670E Gaming Plus Wifi
- 电源: Thermalright 1200w
- 散热: 瓦尔基里 A360

选择 X670E 主板是因为 AM5 系列的 PCIe 通道问题, 见 [AMD 官网](https://www.amd.com/zh-cn/products/processors/desktops/ryzen/9000-series/amd-ryzen-7-9700x.html)



Additional Usable PCIe Lanes from Motherboard:
|Chipset|	PCIe Lanes|
|---|---|
|X870E|	8x Gen4|
X870	|4x Gen4
X670E	|12x Gen4
X670	|12x Gen4
B650E	|8x Gen4
B650	|8x Gen4

我想装很多 SSD 所以只能选择 670 系列的主板了, 虽说已经是2025年4月. 这里吐槽一下新板子的设计(B850 & X870), 把 PCIe 通道全占完了导致没有几个多余的通道. 另外服务器系列的处理器都那么多 PCIe 通道, 为什么家用系列的 CPU 只有 24/28 条!

# PXE
## WDS PXE Win 11 安装
事情起因是身边没有U盘(现在谁还用这个东西?)安装系统, 于是就有了接下来的一串灾难. 尝试使用 Windows Server 部署 WDS 自动通过网络安装系统, 但体验简直灾难. 具体操作如下:
### 预备条件:
1. Windows Server 服务器一台
2. 你可以控制的网络基础设施
3. Windows 10 的 ISO 镜像 `Windows 10.iso` (微软官网下载安装介质后下载 ISO)
4. Windows 11 的 ISO 镜像 `Windows 11.iso` (微软官网下载)
5. 一个没有网络问题的网络
6. 尝试的勇气与解决问题的能力

### 准备工作:
1. 假设你的网络环境非常简单, Windows Server 和要安装的主机通过一根网线或者交换机连接. 
2. 主机主板按 `Del` 进入 BIOS 后更改 Boot 选项为 Network 或者 PXE, 具体参考你的主板说明书操作.
3. 可能需要关闭或开启主板的 **Secure Boot**
4. 配置 Windows Server 所用网口的网卡静态 ipv4 地址为 `192.168.100.1`, 地址配置成什么根据你的具体网络而定. 
5. 打开 `Windows 10.iso` 找到 `sources\boot.wim` 将它复制出来备用.
6. 打开 `Windows 11.iso` 找到 `sources\install.wim` 将它复制出来备用.


### 部署
以下操作在 Windows Server 2022 上完成

#### WDS
1. 启动服务器 WDS 服务, 通过服务器管理中的 Add Roles or Features
2. 配置 WDS **Remote Install** 目录, 我这里就直接放在了 C 盘. WDS 主要配置只需要配置两个文件, 一个 **boot image** 一个 **install image** . 分别选择为准备阶段备用的 `boot.wim` 和 `install.wim` 即可.
3. WDS 客户端配置, 依据你自己的需求配置即可. 可以配置无人值守安装, 具体操作请百度.
4. WDS 会创建一个 TFTP 服务, 设置保持默认即可.
5. 驱动注入. 如果你的电脑需要某些驱动才能启动, 可以向 **boot image** 中提前注入驱动. 在硬件厂商官网下载需要的驱动后将驱动添加到 WDS 的 drivers, 再注入 boot image.

#### DHCP (Windows Server)

1. 启动服务器 DHCP 服务, 通过服务器管理中的 Add Roles or Features(非必需). 假设你的网络中已经有一台 DHCP 服务器, 那么你可能不需要(但是还是大概率要)启动 DHCP 服务. 如果你现有的网络主路由器是一台你可以完全控制的机器如 Openwrt 或者 Linux 那么你大概率不需要启动 DHCP 服务, 但是对于一般家庭而言使用的家用路由器并不能实现我们需要的功能, 所以仍然需要启动服务器的 DHCP 服务. 注意到一个网络中只能有一个 DHCP 服务器所以你最好关掉你的主路由的 DHCP 服务(这可能造成你的新设备没法上网,记得搞完了重新打开). 为了简化我们假设不存在其他的路由器, Windows Server 和你的其他主机之间只通过网线或者傻瓜交换机连接.
2. 配置 Windows Server 上的 DHCP 服务器, 服务段为 `192.168.100.2` ~ `192.168.100.254` .
3. 在 WDS 服务的 DHCP 设置中, 根据提示配置.
4. 检查配置 DHCP 服务器中的 DHCP Option 60, 66, 67. option 66 配置为 Windows Server ip 地址, option 67 配置为启动 efi 文件位置 .

    |option| content(string)|meaning
    |---|---|---|
    60| PXEClient|Vendor Class Identifier
    66|192.168.100.1| TFTP Server Name
    67|boot\x64\wdsmgfw.efi|Bootfile Name

#### DHCP (Openwrt)
假设你的主路由是一台 openwrt , 你希望通过 openwrt 管理网络而非引入 windows server 作为 DHCP 服务器, 可以配置 openwrt 上的 DHCP option. 
1. ssh 进入你的 Openwrt
2. 使用 uci 配置 DHCP Option
    ```bash
    uci set dhcp.lan.dhcp_option='66,192.168.100.1'
    uci add_list dhcp.lan.dhcp_option='67,boot\x64\wdsmgfw.efi'
    uci add_list dhcp.lan.dhcp_option='60,PXEClient'
    uci commit
    /etc/init.d/dnsmasq restart
    ```
    也可以直接在 `/etc/config/dhcp` 中添加这三行:
    ```
    config dhcp 'lan'
        ###

        list dhcp_option '60,PXEClient'
        list dhcp_option '67,boot\x64\wdsmgfw.efi'
        list dhcp_option '66,192.168.100.1'

        ###
    ```
3. 检查是否配置成功:
    ```bash
    uci show dhcp.lan
    ```
4. 重启 openwrt 让配置生效

原理就是 openwrt 使用 DHCP 在分发 ip 的同时告知客户端 WDS 服务器的地址和启动引导位置.

#### 启动 WDS 和 DHCP 服务
理论上所有的配置都完成了并且都能 work, 你会见到正常的Windows 安装引导界面. 如果你的 WDS 客户端配置没有设置无人值守安装那就要输入你的 WDS 所在的 Windows Server 主机密码. 如果你的 Windows Server 名称叫做 **myserver**, 那么你需要输入用户名 `myserver\Administrator` , 密码为你的管理员密码. 

#### 可能存在的错误
- **efi 引导不存在** 
文件: `boot\x64\wdsmgfw.efi` 不存在. WDS 未能正确把这个文件放在 `C:\RemoteInstall\Boot\x64` . 见 [saszhuqing-博客园](https://www.cnblogs.com/saszhuqing/p/9599744.html). 解决办法是可以借用你本机的 `C:\Windows\System32\RemInst\boot\x64\mdsmgfw.efi`, 把它拷贝到 `C:\RemoteInstall\Boot\x64` 就可以了. 
可以用另一台同网络上的计算机使用 tftp 测试一下看文件是否存在:
    ```sh
    tftp 
    connect 192.168.100.1
    get boot\x64\mdsmgfw.efi
    ```
- **家用路由器丢弃 DHCP 数据或者禁止 DHCP Snooping** 
如果你使用了家用路由器的两个 LAN 口当交换机, 即便关闭了家用路由器的 DHCP 功能, 部分固件为了安全考虑仍然可能会处理你的 DHCP 数据, 导致 DHCP 报文中的 option 数据丢失. 有的设备不允许 DHCP snooping, 而在 DHCP 主机不是 PXE 服务器本机时, PXE 服务器需要依赖 DHCP snooping 嗅探网络中的 DHCP 信息. 解决办法就是使用网线或傻瓜交换机直接连接两台机器, 尝试设置路径上设备允许 **DHCP Snooping**.
- **不支持 Windows 11 24H2 (fixed)** 
之前提到只能用 Windows 10 及以前的系统, 这是因为 WDS 已经半死不活了, 对 Windows 11 不支持. 使用 `boot.wim` 无法启动 Windows 11, 但使用 windows 11 镜像时你会遇到 `A media driver your computer needs is missing. This could be a DVD, USB or Hard disk driver. If you have a CD, DVD, or USB flash drive with the driver on it, please insert it now.` 的故障, 详见: [WDS boot.wim support](https://learn.microsoft.com/en-us/windows/deployment/wds-boot-support) 这里并非缺少驱动, 而是官方镜像中的 `boot.wim` 不再能使用, 如果你有其他的 `.wim` 引导, 如 Windows PE 或者其他的 PE 系统的 `.wim` 文件, 可以尝试替换. 本人没试过. 另外解决办法就是抛弃 WDS 改用 Microsoft Configuration Manager 或者 Microsoft Deployment Toolkit, 这二者的臃肿程度更是个$\star$
**update:** 微软的官网可能有点骗人, 使用 Windows 10 的 `boot.wim` 是可以成功安装 Windows 11 的.


## iVentoy PXE
省流: 对于 Windows 11 官方 iso , iVentoy 同样会遇到安装驱动弹窗问题. 可以尝试魔改 ISO.

iVentoy 是一个轻量的 PXE 服务器, [官方网站](https://www.iventoy.com/), [下载地址](https://github.com/ventoy/PXE/releases)
iVentoy 相比 Windows Server WDS 简单太多, 根本不需要 Server 操作系统, 普通的 Windows 安装即可. 配置起来也十分方便, 不到五分钟便能走完 WDS 上面全部的流程. 
iVentoy 的缺点就是没法直接注入启动, 它的驱动注入方式是通过直接拷贝一个文件夹到你的**X**盘根目录让你自己装, 但是对于那些关键的驱动来说没有注入压根就没法正常使用. 如 AMD Raid 驱动.

使用 iVentoy  时遇到了奇怪的 BUG, 使用自己魔改的大容量 iso 时候文件需要修改一些很深的存储参数, 一直失败就没继续尝试了. 因为一直失败就尝试使用 **微PE** 制作一个 PE 镜像, 在 PE 镜像中放入 Windows 的安装文件. 但是最终并不能成功, 我猜测是因为 PE 系统没办法载入 AMD Raid 驱动导致没法正确处理文件系统. 具体尝试记录如下:

因为 iVentoy 不支持配置 install.wim, 所以需要在 ISO 文件中包含 boot 和 install 的文件. 为了偷懒我直接把整个 windows 11 ISO 封装进去了. 

### 魔改 PE ISO (失败)
1. [官网](https://www.wepe.com.cn/)下载工具获取 **微PE** ISO 镜像
2. 挂载镜像, 将镜像中的 `WEPE64.wim` 复制取出, 这相当于 `boot.wim`
3. 使用 dism 命令处理 `WEPE64.wim`
    - 在 `WEPE64.wim` 所在的文件夹启动 powershell
    - 创建一个挂载文件夹, 这里直接放在 C 盘
      ```
      mkdir C:\Mount
      ```
    - 查看 `WEPE64.wim` 的 index 信息
      ```
      dism /get-wiminfo /wimfile:"boot.wim"
      ```
    - 挂载 `WEPE64.wim` 到 `C:\Mount`
      ```
      dism /mount-wim /wimfile:"boot.wim" /index:2 /mountdir:"C:\Mount"
      ```
    - 将你的 windows iso 复制到`Program Files`中
    - 保存提交并退出
       ```
       dism /unmount-wim /mountdir:"C:\Mount" /commit
       ```
       新的 `WEPE64.wim` 会存放在你的当前文件夹中
    这样你就将 Windows 的 ISO 镜像填入了 微PE 的 `WEPE64.wim`  中
4. 更改原来的 PE ISO
    - 下载 Ultra ISO
    - 使用 Ultra ISO 打开原来的 `WEPE.iso`
    - 右键删除镜像中的 `WEPE64.wim`, 再使用左上角的**文件-添加文件** 填入自己制作的 `WEPE64.wim`
    - 左上角保存并退出
    这样就获得了自己定制的镜像
5. 使用 iVentoy 挂载自己的镜像
6. 启动电脑进入 微PE , 使用内置工具安装 Windows. 其中你的 Windows ISO 应该会在`Program Files`中

这并不是一个好主意, 因为某些奇怪的原因 iVentoy 并不能在传输过程中保持文件的完整性, 它只能最多传输 650M, 及原来微PE镜像的设定容量. 导致实际上获取到的是崩坏的文件, 压根没法安装.

于是我使用同样的 ISO 回到 WDS 尝试, WDS 能保持文件在传输过程中的完整性, 但是 微 PE 系统貌似无法安装 Windows 11 24H2, 在写入完成后的首次启动时会报错, 提示无法在本机安装 Windows. emmmmm


### 魔改 Windows ISO (可能可以)
这只是一个可行性分析, 并没有经过实验验证, 但是理论上应该是比较简单且可实现的.
既然魔改 PE ISO 不成, 那我可以尝试魔改 Windows ISO, 用 Windows 10 的 `boot.wim` 替换掉 `Windows 11.iso` 中的 `boot.wim`. 封装后使用 iVentoy 安装. 替换过程可以参考上面魔改 PE ISO 的过程使用 Ultra ISO 或者系统内置的命令行工具 **oscdimg** (需要安装ADK)

## 回到起点 WDS
最后还是回到了 WDS , 因为 iVentoy 在传输上貌似并不可靠, 我也懒得钻研具体原因了. 本来我都想摆烂了直接WDS装 Win 10, 下了个 Windows 10 的 ISO后挂载配置到 WDS 上, 结果发现您猜怎么着 - Windows 10 的 ISO 没有 `install.wim` , 不知道是我下载源的问题还是啥, 我可是从微软官网下载的 Windows 安装介质, 再用那个程序下载的镜像啊! 就死马当活马医了, 直接使用 Windows 10 的 `boot.wim` 和 Windows 11 的 `install.wim`, 结果就成了! 这这这.. 微软官网怎么骗人啊, [WDS boot.wim support](https://learn.microsoft.com/en-us/windows/deployment/wds-boot-support) 这篇文章中的表格中明确写了 Windows 11 无法用 Windows 10 的 `boot.wim` , 但是实验下来发现是可以安装的.

# Windows 安装
## 本地账户创建
在能成功见到安装界面并且一路点"下一步"后发现, 用户名变成了微软账号邮箱的前五位. 例如你的微软账号邮箱是 `genshin@impact.com` , 那么你的Windows用户名会变成 **gensh** , 并且你的个人文件夹的名字也会是这个 `C:\users\gensh` . 这是不能接受的, 要知道多少软件的配置都会用到这个目录, 每次打开 cmd 看到这个目录名字简直跟是受不了. 那些用 qq 邮箱的人的用户名更是成了自己 qq 号的前五位... 于是只能重装系统. 安装过程中在选择计算机给谁用的一步记得选择**给学校或域**用, 然后就能创建本地账户了. 选择自己用就强制你登录微软账号. 源自[keeemf](https://space.bilibili.com/604105730)在[这个视频](https://www.bilibili.com/video/BV1R2Z2YgEg2)下的评论.

## 激活
几种方法:
1. 从微软官方购买对应版本的激活码
2. KMS 激活, 你的网络上有一台 KMS 服务器. 如 Openwrt 的服务中安装 KMS 插件. 配置服务器[密钥](https://learn.microsoft.com/zh-cn/windows-server/get-started/kms-client-activation-keys)即可.
3. 各凭本事