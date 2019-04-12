---
title: Windows Device Portal
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解有关如何使用 Windows Device Portal 若要配置和远程管理你的设备。
keywords: windows iot、 Windows Device Portal，远程，设备门户
ms.openlocfilehash: 715e9c138e86efcd82b485d832c5fbdd536398dd
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510646"
---
# <a name="windows-device-portal"></a>Windows Device Portal
   Windows Device Portal (WDP) 允许您配置和通过本地网络的远程管理你的设备。
主要功能已记录在[Windows Device Portal 概述页](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)

![Device Portal 主页](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> 请不要将 maker 映像用于商品化。 如果 commercializing 设备，则必须使用自定义 FFU 为获得最佳安全性。 在[此处](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。

> [!WARNING]
> 实时内核调试目前适用于 ARM 设备将失败。 我们正在努力获得修复此问题。

> [!IMPORTANT]
> 如果您正在构建商业上部署的"特定于/受限安装"将打开零售设备 （即工厂或零售商店） 的最终用户执行最终配置和文档客户，他们必须[获取它同时 WDP 和连接的浏览器和密码时更改 WDP WDP 和安装证书](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)，则此窄的商业实例中使用 WDP 是可接受。 在此方案中的零售映像也应仍然*不*包括 IOT_TOOLKIT，但应使用 IOT_WEBBEXTN 包 WDP 拉取。 

## <a name="shared-documentation"></a>共享的文档
WDP 是在所有 Windows 10 设备之间共享的开发人员工具。 每个产品都有其自己独特的功能，但核心功能是相同的。
上找到有关的主要功能的文档[Windows Device Portal 概述页](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)。 以下文档的其余部分将特定的 IoT。

## <a name="set-up"></a>设置

有两种方法可获取 Windows Device Portal，启动并运行。

### <a name="1-windows-10-iot-dashboard"></a>1.Windows 10 IoT 仪表板

首先，你将想要下载[Windows 10 IoT 仪表板](https://docs.microsoft.com/en-us/windows/iot-core/connect-your-device/iotdashboard)，可以轻松地设置新设备的开发人员工具。 一旦您使用仪表板闪烁的 Windows 10 IoT 核心版映像，到你的设备上，检查，你的设备显示在"我的设备"。 

在这里，使用省略号"操作"下的选择"打开在设备门户"。 在这里，你将转到设备门户身份验证页面，除非最初更改凭据，否则默认凭据是： 

    Username: `Administrator`<br/>
    Password: `p@ssw0rd`
 
 ### <a name="2-browser"></a>2.浏览器
如果您不能在仪表板中找到你的设备或更想跳过使用仪表板，还可以通过输入加上你设备的 IP 地址打开设备门户`:8080`到末尾。 如果操作无误，它应如下所示：


   ![IoTDashboard 查看设备](../media/deviceportal/Dashboard-Action.gif)

    
## <a name="iot-specific-features"></a>IoT 特定功能

### <a name="device-settings"></a>设备设置

IoT 核心版将添加一个复选框以启用或禁用[屏幕键盘](../develop-your-app/OnScreenKeyboard.md)
> [!NOTE]
> 此复选框都有一个已知的 bug，它将"闪烁"从检查到非检查。 请单击以确保复选框将显示你所需的状态后，刷新页面 (F5)。

### <a name="apps"></a>应用
为设备上的 AppX 程序包和捆绑包提供安装/卸载功能。
![应用列表](../media/DevicePortal/AppList.png)

IoT Core 是唯一的因为它只允许一个前台应用程序运行一次。 修改应用程序列表，以确保这种情况。 下**启动**列中，您可以选择任意多个后台应用程序启动默认情况下，但只能设置一个前台应用程序。  

### <a name="app-file-explorer"></a>应用文件资源管理器

应用文件资源管理器显示的目录，可以访问您的应用程序。

* 在所有应用之间共享 CameraRoll
* 在所有应用之间共享文档
* LocalAppData 包含特定于每个应用程序的文件夹。 此文件夹将为您的应用程序相同的名称和其他应用程序不能访问它。

### <a name="debugging"></a>调试

#### <a name="kernel-dumps"></a>内核转储
![转储的内核调试](../media/DevicePortal/Debug1.png)

将自动记录任何系统崩溃，并且可通过 Web 管理工具查看这些崩溃。  然后你可以下载内核转储，并尝试查明发生了什么情况。

#### <a name="process-dumps"></a>进程转储
![与进程转储调试](../media/DevicePortal/Debug2.png)

这类似于动态内核转储，但适用于用户模式处理。 单击**下载**按钮都将导致小型转储，，将下载该过程的整个状态。 这是适用于调试挂起进程。

#### <a name="kernel-crash-settings"></a>内核故障设置
![内核故障设置](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a>蓝牙
此页显示所有配对的蓝牙设备以及所有可发现的设备。 若要与其他蓝牙设备配对，将设备放在配对的模式下并等待它显示在可用设备列表中。  
![蓝牙设备列表](../media/DevicePortal/Bluetooth.png)

单击**对链接**配对设备。 如果设备需要 PIN 才能配对，它将弹出一个消息框，显示 PIN。 设备配对后，它将显示在成对设备列表中。 通过单击可取消对设备**删除**。 

一旦您导航到蓝牙页上，你的设备将其他设备发现。 此外可以找到从您的 PC/电话，并从该处对其进行配对。

蓝牙的详细信息可在上找到[蓝牙页](https://go.microsoft.com/fwlink/?linkid=823223)。

### <a name="iot-onboarding"></a>IoT 载入

IoT 载入配置 IoT 设备的 Wi-fi 连接选项提供支持。

**Internet 连接共享 (ICS)** Internet 连接共享，可与其他设备的 Wi-fi SoftAP 通过连接到你的设备共享您的设备的 Internet 访问权限。
若要使用此功能，你的 Windows 10 IoT 设备需要有权访问 internet （例如通过有线 LAN 连接）。  在连接-> 载入-> SoftAP 设置，请单击启用，并设置 SSID 名称和密码。  然后在连接-> Internet 连接共享为访问点适配器选择"Microsoft WI-FI Direct 虚拟适配器 #2"和共享的网络适配器中选择有线以太网适配器。  最后，单击启动共享的访问。  启动后，连接到 Windows 10 IoT 设备上 SoftAP 单独启用 Wi-fi 的设备。  建立连接后单独支持 Wi-fi 设备将能够通过 Windows 10 IoT 设备连接到 internet。

> [!NOTE]
> 在设备上存在的 Wi-fi 配置文件时，会禁用 ICS。 例如，如果您连接到 Wi-fi 访问点并检查"创建配置文件 （自动重新连接）"，则将禁用 ICS。

**SoftAP 设置**SoftAP 设置，可以控制是否启用你的设备的 SoftAP。  它还提供了一种方法用于配置 SoftAP 的 SSID 和 WPA2-PSK 密钥是从另一台设备连接 SoftAP 所必需。

**AllJoyn 载入设置**AllJoyn 载入设置允许你控制是否可以在设备的 Wi-fi 连接设备的 AllJoyn 载入制造者通过配置。  当运行应用程序连接到你的 Windows 10 IoT SoftAP AllJoyn 载入使用者的单独设备时，AllJoyn 载入使用者应用程序可以用于配置你的 IoT 设备的 Wi-fi 适配器。  启用时，AllJoyn 载入生成者应用程序 (IoTOnboarding) 使用 ECDHE_NULL 身份验证方法。 

> [!NOTE]
> 若要使用 AllJoyn 使用 Windows 10 IoT 载入生成 10.0.14393 或需要更新前面<strong>IotOnboarding</strong>示例可能[从此处下载](https://github.com/ms-iot/samples)。

![载入到 AllJoyn](../media/DevicePortal/OnboardingAllJoyn.png)
![载入到 ICS](../media/DevicePortal/OnboardingICS.png)

> [!NOTE]
> 访问点适配器是充当 （它通常具有如下 192.168.137.1 IP 地址） 的 WiFi 访问点的 WiFi 适配器。
> 共享的网络适配器是连接到 Internet 的适配器 (例如：以太网适配器）。

![载入到软亚太](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> 如果启用并使用 Wifi 适配器的 MAC 地址为后缀 AllJoyn 载入，将"AJ_"通过自动前缀 SoftAP SSID。 SoftAP 通行短语必须介于 8 到 63 个 ASCII 字符之间。


### <a name="tpm-configuration"></a>TPM 配置
受信任的平台模块 (TPM) 是包括功能的随机数字生成、 安全的加密密钥的生成和限制其使用了加密协处理器。 它还包括诸如远程证明和密封存储等功能。 若要了解有关 TPM 和 IoT Core 上的安全，请访问[构建安全的设备](../secure-your-device/BuildingSecureDevices.md)页并[TPM](../secure-your-device/TPM.md)页。

> [!IMPORTANT]
> Limpet.exe 使用是 Windows IoT Core 的一部分。 从 2018 年 10 月开始，它现已推出，在开放源代码 porject [ https://github.com/ms-iot/azure-dm-client ](https://github.com/ms-iot/azure-dm-client)。

若要使测试更加轻松，我们无签名的 Limpet.exe 可用的预建版本，并且可以直接从 WDP 下载。 只需转到 TPM 配置选项卡，然后单击安装最新按钮。 

> [!NOTE]
> 此版本的 Limpet.exe 不应随最终产品。 相反，您需要生成开放源代码项目，其签名，并将其打包与你的映像。

### <a name="azure-clients-configuration"></a>Azure 客户端配置

可以通过云服务远程管理 IoT 设备。 Azure 提供了非常丰富的服务，使这种情况。 我们已创建的设备管理客户端，它补充 Windows 平台上的 Azure 的设备预配服务 (DPS) 和 Azure 的 IoT 中心服务，还公开多个 Windows 可管理性功能。

客户端将作为开放源代码项目提供。 若要使测试更加容易，我们将提供预先生成的二进制文件。 您可以使用 Azure 客户端选项卡中 WDP 安装和运行这些测试二进制文件。

> [!NOTE]
> 此版本的工具不应随最终产品。 相反，您需要生成开放源代码项目，其签名，并将其打包与你的映像。

可供使用的开放源代码项目后，我们将更新本文档。

### <a name="remote"></a>遥控器
Windows IoT 远程服务器允许用户查看其设备无需连接到键盘的物理显示器显示。


## <a name="additional-information"></a>其他信息 

### <a name="changing-the-default-port"></a>更改默认端口
 
1. 启动 powershell 并[连接到设备。](../connect-your-device/PowerShell.md)
2. 下载[TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership)工具中，生成它，并将其复制到你的设备。 
3. 通过运行获取服务的注册表项的所有权

        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service

4. 通过修改注册表设置来设置所需的端口 

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
        
5. 重新启动 WebManagement 服务通过运行以下或通过重新启动设备

        net stop webmanagement ; net start webmanagement

### <a name="using-https"></a>使用 HTTPS 

如果你想要使用 HTTPS，首先获取注册表项的所有权上, 一节中所述并按如下所示设置 HttpsPort 和 EncryptionMode 注册表项，然后重新启动 webmanagement 服务

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement

### <a name="provisoning-device-portal-with-a-custom-ssl-certificate"></a>设置设备门户中使用自定义 SSL 证书

在 Windows 10 创意者更新，Windows Device Portal 添加了设备管理员安装使用的自定义证书中的 HTTPS 通信的方法。

若要了解更多信息，请[阅读 Windows Device Portal docs 下的文档](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)。 


## <a name="additional-resources"></a>其他资源
___ 

1. [Windows Device Portal 概述页](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
