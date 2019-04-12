---
title: 使用 Windows 10 IoT 核心版项目罗马
author: saraclay
ms.author: saclayt
ms.date: 11/14/2017
ms.topic: article
description: 了解并了解要执行 Windows IoT 设备推向市场的步骤。
keywords: windows 10 IoT Core，项目罗马，远程设备
ms.openlocfilehash: cc016abad05dd54c7b948bcae8120b6da1724ee0
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59511018"
---
# <a name="using-project-rome-with-windows-10-iot-core"></a>使用 Windows 10 IoT 核心版项目罗马 
 
[项目罗马](https://developer.microsoft.com/en-us/windows/project-rome)，可远程使用运行 Windows 10 IoT 核心版 RemoteSystems 和 AppServiceProvider Api 使用的设备。 
 
在本文中，我们将逐一介绍如何发现，控件，并连接到与项目罗马运行 Windows 10 IoT 核心版的设备。  
 
## <a name="discovering-iot-core-devices-with-the-remotesystem-apis"></a>发现与 RemoteSystem Api IoT Core 设备 
 
_安装：_
* 在桌面上到你的 Microsoft 帐户登录时运行 RemoteSystems 示例。  
* 与任何 IoT Core 上运行的应用，登录到你的 Microsoft 帐户上通过转到 Cortana 到登录名。 
 
_步骤：_
1. 在您的桌面上运行 RemoteSystems 示例 
2. "1） 发现，"下单击"搜索系统" 

![搜索系统](../media/ProjectRome/SearchForSystems.gif)
 
## <a name="control-iot-core-devices-with-remotesystemslaunchuri"></a>控制与 RemoteSystems.LaunchUri IoT Core 设备 
 
_安装：_
* 运行[RemoteSystems 示例](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems)上桌面 while[登录到你的 Microsoft 帐户](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)。
* 与任何 IoT Core 上运行的应用，登录到你的 Microsoft 帐户上通过转到 Cortana 到登录名。 
 
_步骤：_
1. 打开 Cortana 并登录到你的 Microsoft 帐户从 Cortana IoT 核心版虚拟机。 
2. 在桌面上运行 RemoteSystems 示例。 
3. 在"1） 发现"，单击"搜索系统"。 
4. 在"2） 启动 URI"，选择正在运行 Cortana 的 IoT Core 设备。 
5. 输入此 URI 并启动。 

![启动 URI](../media/ProjectRome/LaunchURI.gif)

## <a name="connecting-to-the-remote-app-service-running-on-iot-core"></a>连接到 IoT Core 上运行的远程应用程序服务 
_安装：_
* 运行[RemoteSystems 示例](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems)上桌面 while[登录到你的 Microsoft 帐户](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)。 
* 请确保有[AppServiceProvider 应用](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices)部署且至少一个 IoT Core 设备上正在运行。 
 
_步骤：_
1. 打开 IoT Core 虚拟机上与 Cortana，并登录到 Microsoft 帐户从 Cortana。 AppServiceProvider 应用部署，运行一次，然后将其关闭。 
2. 在桌面上运行 RemoteSystems 示例。 
3. 在"1） 发现"，单击"搜索系统"。 
4. 在"3） 启动应用服务、"选择 IoT core 设备具有部署的 AppServiceProvider 应用并且已运行。 
5. 生成一个随机数。  

![启动应用服务](../media/ProjectRome/LaunchAppServices.gif)
 
## <a name="controlling-other-devices-and-app-services-from-an-iot-core-device"></a>控制其他设备和应用程序服务从 IoT Core 设备 

_安装：_
* 运行[RemoteSystems 示例](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems)同时 IoT Core 设备上部署[登录到你的 Microsoft 帐户](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)从 Cortana 应用。 
* 桌面计算机有[AppServiceProvider 应用](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices)部署并且具有运行至少一次。 
 
_步骤：_
1. 运行 RemoteSystems 示例。 
2. 在"1） 发现"，单击"搜索系统"。 
3. 在"2） 启动 URI"，选择桌面计算机并启动。 
4. 在"3） 启动应用服务"下选择的桌面机。  
 
> [!NOTE] 
> 第一次尝试，这可能需要很长时间。 这再试一次更快响应。 
 
### <a name="helpful-links"></a>有用的链接： 
* [MSDN 上的项目罗马文档](https://developer.microsoft.com/en-us/windows/project-rome )
* [使用适用于 UWP 项目罗马](https://docs.microsoft.com/windows/uwp/launch-resume/connected-apps-and-devices )
 
