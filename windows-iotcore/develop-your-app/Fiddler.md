---
title: 捕获 Fiddler 跟踪
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Fiddler 捕获 Fiddler 跟踪在 Windows IoT Core 上。
keywords: windows iot，Fiddler，跟踪，PuTTY，Fiddler 跟踪
ms.openlocfilehash: b8bf4fa6390aad9640ad9139a8a164a9c83fcff5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510865"
---
# <a name="capturing-fiddler-traces-on-windows-iot-core"></a>捕获 Windows IoT Core 上的 Fiddler 跟踪

Fiddler 是一个用于调试的 web 流量工具。 该功能特别有用，因为你可以为特定需要，使用扩展和外接程序，自定义它，并且该工具提供了大量有用的信息特定于 web 流量。

## <a name="assumptions"></a>假设 

* 你有[PuTTY](http://www.putty.org/)上在开发人员工具箱或 SSH 的替代方法
* 下面的说明假设 IoT Core VM 但上将起作用*任何*IoT Core 设备

## <a name="initial-setup"></a>初始设置

1. 下载并安装最新版[Fiddler](http://www.telerik.com/fiddler/)如果尚未在开发人员工具箱上
2. 启动 Fiddler，进行以下设置更新下的_工具-> Telerik Fiddler 选项-> HTTPS_选项卡
    * 检查_捕获 HTTPS 连接_
    * 检查_解密 HTTPS 通信-> 与所有进程_
    * 单击证书生成的链接，然后选择_MakeCert 引擎_(建议：重启 Fiddler，此更改才会生效）
    * 接下来，导出 FiddlerRoot.cer 文件通过_操作-> 将根证书导出到桌面_
3. 进行以下设置更新下的_工具-> Telerik Fiddler 选项-> 连接_选项卡：
    * 安装 Fiddler 来充当系统代理通过检查_允许远程计算机连接到连接_
    * _Fiddler 侦听端口_应设置为_8888_
  
注意：应在此之后重启 Fiddler，并接受任何 UAC 提示。

## <a name="transfer-and-import-fiddler-root-certificate"></a>传输并导入 Fiddler 根证书
你将需要导入到你的 IoT 映像或设备以调试 https 流量路由通过您的 PC Fiddler 根证书。  要实现此目的，请执行以下操作：

1. 装载 VHD 文件 (在 VHD 上右键单击并选择_装载_) 或连接到 IoT 设备通过 PuTTY （或替代 SSH 客户端）
2. 浏览到 mainOS 分区和创建_测试_位于根文件夹 (通过 ssh 连接，使用_md c:\test_)
3. 复制上述生成的 FiddlerRoot.cer （应为默认情况下在桌面上） 到测试文件夹位置
4. 如果使用的 VHD，通过弹出任何已装载的驱动器来卸载它，然后启动 IoT Core VM 通过 HyperV
5. 启动[SSH 会话](../connect-your-device/ssh.md)并以管理员身份登录 
6. 在 SSH 会话中导航到 c:\test 目录
7. 通过命令导入 Fiddler 根证书：
    * `certmgr -add FiddlerRoot.cer -r localmachine -s root`
8. 关闭 SSH 会话


## <a name="setup-proxy-on-vm-or-iot-core-device"></a>在 VM 或 IoT Core 设备上安装代理
执行以下步骤将允许你的 IoT VM 或将流量路由到您的 PC 的设备，因此该 Fiddler 可以捕获网络流量以进行分析：

1. 确定使用 CMD 控制台中的，通过在开发计算机的 IP _ipconfig_
2. 开始一个新的 SSH 会话，这一次，defaultUser 作为登录名 (用户名：_DefaultAccount_ Pwd: _[空白]_ )
3. 设置代理通过以下命令：
    * `reg add "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyEnable /t REG_DWORD /d 1`
    * `reg add "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings" /v ProxyServer /t REG_SZ /d [PC IP address]:8888`

如果尚未运行，在您的 PC 上启动 Fiddler、 重启 VM 或 IoT Core 设备和现在应该通过 Fiddler 路由流量。 

注意：如果您看到的 https 连接中 Fiddler 但没有数据，该证书时可能未正确安装。 请确保未遗漏_传输和导入 Fiddler 的根证书_上述步骤。

此外，如果你想要启用退避注意上面的注册表密钥获取缓存在另一个密钥中的二进制 blob 中的代理。 因此，除了删除刚在上面的步骤 3 中添加的键还需要执行操作：

    reg delete "hkcu\Software\Microsoft\Windows\CurrentVersion\Internet Settings\Connections"
    
    
