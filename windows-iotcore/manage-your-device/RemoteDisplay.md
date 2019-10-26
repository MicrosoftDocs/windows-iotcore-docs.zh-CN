---
title: 远程显示
ms.date: 08/28/2017
ms.topic: article
description: 了解如何远程查看和控制 Windows 10 IoT Core UWP 应用程序。
keywords: windows iot，UWP，远程显示，远程，UWP 应用程序
ms.openlocfilehash: c0e082284e5bceb6f1a7a87723e883ad6e552c4e
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917397"
---
# <a name="remote-display"></a>远程显示
从 Windows 10 台式计算机、平板电脑或手机远程查看并控制 Windows 10 IoT Core UWP 应用程序

> [!WARNING]
> Windows IoT 远程客户端是一项仅开发人员功能。 它不适合生产设备，也不受支持。

> [!IMPORTANT]
> Windows IoT 远程客户端不适用于 Raspberry Pi。 使用带加速图形的板（例如 Minnowboard Max 或 Dragonboard），或者连接一个用于本地显示的监视器。

## <a name="overview"></a>概述
___
远程显示体验是一种开发人员工具，用于远程控制 Windows 10 IoT Core 设备上运行的 UWP 应用程序。   

## <a name="setup"></a>“安装程序”
___
若要开始，需要使用最新版本的 Windows 10 设置 Windows 10 IoT Core 设备-请访问[入门](https://developer.microsoft.com/en-us/windows/iot/getstarted)页面以设置板。

安装程序可以快速轻松地执行以下三个步骤，以使用远程显示技术。

1. 确保 IoT Core 设备和开发计算机位于同一网络中，并确保安全环境为 n。

    一种方法是使用支持自动交叉的 USB 以太网适配器将设备直接连接到便携式计算机。

1. 启用 Windows 10 IoT Core 设备上的远程显示功能。
  
    将设备连接到 Internet 并连接到 Windows 设备门户。
  
    从左侧的选项中选择 "远程" 页，并将标记为 "启用 Windows IoT 远程服务器" 的复选框标记为 "启用"。  你的设备现在已启用远程显示体验。
    ![启用远程显示体验](../media/RemoteDisplay/enable-remote.png)

1. 在随附的 Windows 10 设备上安装 Windows IoT 远程客户端。
  
    若要使 Windows 10 设备能够连接到 Windows 10 IoT Core 设备，需要安装我们的应用商店应用程序。  Windows IoT 远程客户端应用当前仅通过链接提供，可在[此处](https://www.microsoft.com/en-us/store/apps/iot-remote-client/9nblggh5mnxz)找到。
    
    ![安装客户端应用](../media/RemoteDisplay/store-app.png)


1. 通过已安装的应用程序连接到 Windows 10 IoT Core 设备。
  
    在 Windows 10 配套设备上运行 Windows IoT 远程客户端应用程序。  在 "连接" 屏幕上，输入设备的 IP 地址。 这两个设备应该连接，将 Windows 10 IoT Core 设备的 UI 体验远程处理到配套设备上。
    
    你现在已经连接了！ 从此开始，可使用触控并单击配套 Windows 10 设备上的输入来控制 Windows 10 IoT 核心 UWP 应用程序。  
    ![连接设备](../media/RemoteDisplay/connect-device.png)
      

## <a name="compatibility-and-scope"></a>兼容性和范围
___
若要使用 IoT 远程客户端，必须在目标设备上运行 Windows 10 IoT Core 的最新版本，并在应用商店中运行最新的客户端应用程序。 
    
  
## <a name="troubleshooting"></a>“疑难解答”
___
使用远程显示技术非常简单，但仍有一些用户可能会遇到的问题。  请确保按照上面的设置说明进行操作，如果问题仍然存在，请检查以下各项。

### <a name="when-i-try-to-connect-the-client-app-goes-to-a-white-screen"></a>当我尝试连接时，客户端应用程序会进入一个白屏。
失败的连接可能是由许多问题引起的，但我们遇到了一些更常见的问题：

1. 确保运行最新版本的 Windows 10 IoT Core 和 IoT 远程客户端应用程序。
1. 首先，请确保 IoT 设备与配套设备位于同一网络中。
    检查是否正在运行 windows 10 IoT Core 的最新内部版本，并启用了 Windows IoT 远程服务器。
1. 如果这不是问题，请尝试将设备的分辨率更改为我们保证支持的内容，按照上述 "设置" 部分的步骤1中的说明导航到设备的 web 服务器。  请在 "主页" 页上停留，并向下滚动以查找分辨率，而不是从左侧菜单中选择 "远程"。  试试800x600。
1. 如果这仍不能解决问题，则可能是由于从不将设备连接到外部显示器而产生的问题。
    这将导致设备将自身视为纯粹无外设。  若要解决此问题：
    * 弹出 MicroSD 卡，并将其放入计算机
    * 编辑 `<MicroSD card drive>:\config.txt`
    * 添加以下行：
 
```
  hdmi_force_hotplug=1
  hdmi_group=2
  hdmi_mode=9
```
