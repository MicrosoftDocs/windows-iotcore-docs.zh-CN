---
title: 使用 Windows 10 IoT 核心版 Project 罗马
ms.date: 11/14/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解并了解将 Windows IoT 设备投放市场的步骤。
keywords: windows 10 IoT Core，Project 罗马，远程设备
ms.openlocfilehash: 96bb797ea857aea3c876959a006f2dd4a325aca5
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113228673"
---
# <a name="using-project-rome-with-windows-10-iot-core"></a>使用 Windows 10 IoT 核心版 Project 罗马 
 
[Project 罗马](https://developer.microsoft.com/en-us/windows/project-rome)，你可以使用 RemoteSystems 和 AppServiceProvider api 远程处理运行 Windows 10 IoT 核心版的设备。 
 
在本文中，我们将介绍如何使用 Project 罗马来发现、控制和连接运行 Windows 10 IoT 核心版的设备。  
 
## <a name="discovering-iot-core-devices-with-the-remotesystem-apis"></a>通过 RemoteSystem Api 查找 IoT Core 设备 
 
设置：
* 登录到 Microsoft 帐户时，请在桌面上运行 RemoteSystems 示例。  
* 如果未在 IoT Core 上运行任何应用，请转到 Cortana 登录，登录到 Microsoft 帐户。 
 
_步骤：_
1. 在桌面上运行 RemoteSystems 示例 
2. 在 "1) 发现" 下，单击 "搜索系统" 

![搜索系统](../media/ProjectRome/SearchForSystems.gif)
 
## <a name="control-iot-core-devices-with-remotesystemslaunchuri"></a>控制包含 RemoteSystems 的 IoT 核心设备。 LaunchUri 
 
设置：
* [登录到 Microsoft 帐户](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)时，请在桌面上运行[RemoteSystems 示例](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems)。
* 如果未在 IoT Core 上运行任何应用，请转到 Cortana 登录，登录到 Microsoft 帐户。 
 
_步骤：_
1. 通过 Cortana 打开 IoT 核心虚拟机，并从 Cortana 登录 Microsoft 帐户。 
2. 在桌面上运行 RemoteSystems 示例。 
3. 在 "1) 发现" 下，单击 "搜索系统"。 
4. 在 "2) 启动 URI" 下，选择运行 Cortana 的 IoT 核心设备。 
5. 输入此 URI，然后启动。 

![启动 URI](../media/ProjectRome/LaunchURI.gif)

## <a name="connecting-to-the-remote-app-service-running-on-iot-core"></a>连接到在 IoT Core 上运行的远程应用服务 
设置：
* [登录到 Microsoft 帐户](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)时，请在桌面上运行[RemoteSystems 示例](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems)。 
* 请确保已在至少一个 IoT Core 设备上部署并运行 [AppServiceProvider 应用](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) 。 
 
_步骤：_
1. 启用 Cortana 的 IoT 核心虚拟机，并从 Cortana 登录 Microsoft 帐户。 部署 AppServiceProvider 应用，只运行一次，然后将其关闭。 
2. 在桌面上运行 RemoteSystems 示例。 
3. 在 "1) 发现" 下，单击 "搜索系统"。 
4. 在 "3) 启动应用服务" 下，选择已部署并已运行 AppServiceProvider 应用的 IoT core 设备。 
5. 生成一个随机数。  

![启动应用服务](../media/ProjectRome/LaunchAppServices.gif)
 
## <a name="controlling-other-devices-and-app-services-from-an-iot-core-device"></a>从 IoT Core 设备控制其他设备和应用服务 

设置：
* 在从 Cortana 应用[登录到 Microsoft 帐户](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)时，运行在 IoT Core 设备上部署的[RemoteSystems 示例](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/RemoteSystems)。 
* 已部署 [AppServiceProvider 应用](https://github.com/Microsoft/Windows-universal-samples/tree/dev/Samples/AppServices) 且至少运行一次的台式计算机。 
 
_步骤：_
1. 运行 RemoteSystems 示例。 
2. 在 "1) 发现" 下，单击 "搜索系统"。 
3. 在 "2) 启动 URI" 下，选择桌面计算机，然后启动。 
4. 在 "3) 启动应用服务" 下，选择桌面计算机。  
 
> [!NOTE] 
> 第一次尝试时，这可能需要很长时间。 再次尝试此重试以获得更快的响应。 
 
### <a name="helpful-links"></a>实用链接： 
* [ProjectMSDN 上的罗马文档](https://developer.microsoft.com/en-us/windows/project-rome )
* [将 Project 罗马用于 UWP](https://docs.microsoft.com/windows/uwp/launch-resume/connected-apps-and-devices )
 
