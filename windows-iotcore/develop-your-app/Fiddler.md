---
title: 捕获 Fiddler 跟踪
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Fiddler 在 Windows IoT Core 上捕获 Fiddler 跟踪。
keywords: windows iot，Fiddler，跟踪，PuTTY，Fiddler 跟踪
ms.openlocfilehash: fcebce188b40ed6d97d663af30d1ac223cf5a5e9
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782949"
---
# <a name="capturing-fiddler-traces-on-windows-iot-core"></a>捕获 Windows IoT Core 上的 Fiddler 跟踪

Fiddler 是一种用于调试 web 流量的工具。 此方法特别有用，因为你可以使用扩展和加载项对其进行自定义，并且该工具提供了特定于 web 流量的大量有用信息。

## <a name="assumptions"></a>假设 

* 你的开发人员机箱或 SSH 的替代方法[PuTTY](http://www.putty.org/)
* 以下说明对 IoT 核心 VM 进行了假设，但可在 *任何* IoT 核心设备上使用

## <a name="initial-setup"></a>初始设置

1. 下载并安装最新版本的 [Fiddler](http://www.telerik.com/fiddler/) （如果尚未安装）
2. 启动 Fiddler，然后在 " _工具-> Telerik Fiddler 选项-> HTTPS_ " 选项卡下执行以下设置更新
    * 选中 "_捕获 HTTPS 连接_"
    * 检查 _解密 HTTPS 流量-从所有进程 >_
    * 单击 "生成的证书" 链接，然后选择 " _MakeCert engine_ " (建议： Restart Fiddler，使此更改生效) 
    * 接下来，通过操作导出 FiddlerRoot 文件 _-> 将根证书导出到桌面_
3. 在 " _工具-> Telerik Fiddler 选项-> 连接_ " 选项卡下执行以下设置更新：
    * 通过选中 "_允许远程计算机连接_"，将 Fiddler 设置为系统代理
    * _Fiddler 侦听端口_ 应设置为 _8888_
  
注意：应在此之后重新启动 Fiddler 并接受任何 UAC 提示。

## <a name="transfer-and-import-fiddler-root-certificate"></a>传输和导入 Fiddler 根证书
需要将 Fiddler 根证书导入到 IoT 映像或设备，以便通过电脑调试 https 流量路由。  要执行此操作：

1. 安装 VHD 文件 (右键单击 VHD，然后选择 " _装载_) " 或 "通过 PuTTY (或备用 SSH 客户端连接到 IoT 设备") 
2. 浏览到 mainOS 分区，并通过 SSH 在根 (创建 _测试_ 文件夹，使用 _md c:\test_) 
3. 复制上面生成的 FiddlerRoot (应默认位于桌面上) 到测试文件夹位置
4. 如果使用 VHD，请通过弹出任何已装载的驱动器将其卸载，然后通过 Hyper-v 启动 IoT 核心 VM
5. 启动 [SSH 会话](../connect-your-device/ssh.md) 并以管理员身份登录 
6. 导航到 SSH 会话中的 c:\test 目录
7. 通过命令导入 Fiddler 根证书：
    * `certmgr -add FiddlerRoot.cer -r localmachine -s root`
8. 关闭 SSH 会话


## <a name="setup-proxy-on-vm-or-iot-core-device"></a>在 VM 或 IoT 核心设备上设置代理
以下步骤将允许 IoT VM 或设备通过电脑路由流量，使 Fiddler 可以捕获用于分析的网络流量：

1. 通过_ipconfig_使用 CMD 控制台确定开发计算机的 IP
2. 启动新的 SSH 会话，然后以 defaultUser 的身份登录 (Username： _DefaultAccount_  Pwd： _[空白]_ ) 
3. 通过以下命令设置代理：
    * `reg add "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyEnable /t REG_DWORD /d 1`
    * `reg add "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyServer /t REG_SZ /d [PC IP address]:8888`

如果尚未运行，请在你的电脑上启动 Fiddler，重新启动 VM 或 IoT 核心设备，流量现在应通过 Fiddler 路由。 

注意：如果你在 Fiddler 中看到 https 连接，但没有数据，则可能是证书安装不正确。 请确保未错过上述 _传输和导入 Fiddler 根证书_ 的步骤。

此外，如果想要重新打开代理，请注意，上面的注册表项会缓存在另一个键的二进制 blob 中。 因此，除了删除刚刚在上面的步骤3中添加的密钥，还需要执行以下操作：

    reg delete "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections"
    
    
