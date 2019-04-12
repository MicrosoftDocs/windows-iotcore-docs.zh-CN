---
title: 远程显示
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何查看和远程控制您的 Windows 10 IoT Core UWP 应用程序。
keywords: windows iot，UWP，远程显示远程，UWP 应用程序
ms.openlocfilehash: 6f46ddbc5738f377ce3ebd15a49785e27c6a40bf
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510886"
---
# <a name="remote-display"></a>远程显示
查看和控制 Windows 10 IoT Core UWP 应用程序远程，从 Windows 10 桌面 PC、 平板电脑或手机

> [!WARNING]
> Windows IoT 远程客户端是开发人员的唯一功能。 它不打算使用或生产设备的受支持。

> [!IMPORTANT]
> Windows IoT 远程客户端并不适用于 Raspberry Pi。 使用如 Minnowboard 最大或 Dragonboard 加速图形使用看板或附加的本地显示的监视器。

## <a name="overview"></a>概述
___
远程显示体验是用来远程控制的 Windows 10 IoT Core 设备上运行的 UWP 应用程序的开发人员工具。   

## <a name="setup"></a>安装
___
若要开始，你将需要设置具有最新版本的 Windows 10 的 Windows 10 IoT Core 设备-请访问[开始](https://developer.microsoft.com/en-us/windows/iot/getstarted)页后，可以设置你的板。

安装程序的过程快速而简单-请按照下面使用的远程显示技术的三个步骤。

1. 请确保 IoT Core 设备和开发计算机上相同的网络和 n 安全的环境。

    一种方法是将设备连接直接到便携式计算机使用支持自动交叉的 USB 以太网适配器。

1. 启用 Windows 10 IoT Core 设备上的远程显示功能。
  
    将设备连接到 Internet 并连接到 Windows Device Portal。
  
    从左侧的选项选择页"Remote"并标记该复选框，标记为"启用窗口 IoT 远程服务器"。  你的设备现已为远程显示体验。
    ![启用远程显示体验](../media/RemoteDisplay/enable-remote.png)

1. 在随附 Windows 10 设备上安装 Windows IoT 远程客户端。
  
    若要使 Windows 10 设备能够连接到 Windows 10 IoT Core 设备，需要安装应用商店应用程序。  Windows IoT 远程客户端应用程序当前可通过仅链接，可在[此处](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz)。
    
    ![安装客户端应用程序](../media/RemoteDisplay/store-app.png)


1. 连接到 Windows 10 IoT Core 设备通过已安装的应用程序。
  
    在 Windows 10 配套设备上运行 Windows IoT 远程客户端应用程序。  在连接屏幕中，输入你的设备的 IP 地址。 两台设备应连接远程处理到伴侣设备的 Windows 10 IoT Core 设备的 UI 体验。
    
    你现在已连接 ！ 从此时转发、 触摸和单击配套设备可用于控制 Windows 10 IoT Core UWP 应用程序的 Windows 10 上的输入。  
    ![设备连接](../media/RemoteDisplay/connect-device.png)
      

## <a name="compatibility-and-scope"></a>兼容性和作用域
___
若要使用 IoT 远程客户端，您必须在最新版本的 Windows 10 IoT Core 上运行目标设备和最新的客户端应用程序从应用商店。 
    
  
## <a name="troubleshooting"></a>疑难解答
___
使用远程显示技术的过程快速而简单，但仍有一些用户可能会遇到的问题。  请务必遵循上述说明密切-如果问题仍然存在，请查看以下安装程序。

### <a name="when-i-try-to-connect-the-client-app-goes-to-a-white-screen"></a>当我尝试进行连接时，客户端应用程序将进入白色屏幕。
失败的连接可能会导致通过一系列问题，但我们已经遇到了一些较为常见的问题：

1. 请确保运行最新内部版本的 Windows 10 IoT 核心版和 IoT 远程客户端应用程序。
1. 首先，请确保你的 IoT 设备与伴侣设备位于同一网络上。
    检查可以启用 Windows IoT 远程服务器运行 Windows 10 IoT Core 的最新的预览体验内部版本。
1. 如果这不是问题，请尝试更改为我们肯定将会支持你设备的分辨率请执行上述步骤 1 中的设置部分的说明进行操作以导航到你的设备的 web 服务器。  在"主页"页上保持而不是从左侧菜单中选择"远程"，并向下滚动以查找解决方法。  请尝试 800 x 600。
1. 如果这样仍不能解决你遇到的问题，您可能永远不会将你的设备连接到外部显示器的根源的问题。
    这将导致设备本身将视为纯无外设。  若要解决此问题：
    * 弹出 MicroSD 卡，并将其置于您的计算机
    * 编辑 `<MicroSD card drive>:\config.txt`
    * 添加以下行：
 
```
  hdmi_force_hotplug=1
  hdmi_group=2
  hdmi_mode=9
```
