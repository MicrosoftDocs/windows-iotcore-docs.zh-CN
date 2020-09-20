---
title: Windows 设备门户
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解如何使用 Windows 设备门户远程配置和管理你的设备。
keywords: windows iot，Windows 设备门户，远程，设备门户
ms.openlocfilehash: ef8b58d3a53b56c314b7c49855f0049866251d66
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782969"
---
# <a name="windows-device-portal"></a>Windows 设备门户
   通过 Windows 设备门户 (WDP) ，你可以通过本地网络远程配置和管理你的设备。
[Windows 设备门户](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)的 "概述" 页上介绍了主要功能

![设备门户主页](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> 请勿将创客映像用于商业化。 若要将某个设备商业化，必须使用自定义 FFU 以确保最佳安全性。 在[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。

> [!WARNING]
> 对于 ARM 设备，实时内核调试当前失败。 我们正在努力解决此情况。

> [!IMPORTANT]
> 如果要构建一个开源零售设备，用于商业部署到“特定/有限安装”（即工厂或零售商店），然后由最终用户进行最终配置，并且您要为客户登记归档，他们必须[获取 WDP 证书，并将其安装到 WDP 和联网的浏览器上，且在 WDP 更改了密码](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)，那么在这种范围狭窄的商用实例中使用 WDP 是可以接受的。 此方案中的零售映像仍 *不* 包含 IOT_TOOLKIT，但应使用 IOT_WEBBEXTN 包来请求 WDP。 

## <a name="shared-documentation"></a>共享文档
WDP 是在所有 Windows 10 设备上共享的开发人员工具。 每个产品都有其自己独特的功能，但核心功能是相同的。
有关主要功能的文档，请参阅 [Windows 设备门户](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)的 "概述" 页。 以下文档的其余部分将是特定于 IoT 的文档。

## <a name="set-up"></a>设置

可以通过两种方式启动并运行 Windows 设备门户。

### <a name="1-windows-10-iot-dashboard"></a>1. Windows 10 IoT 面板

首先，你将需要下载 [Windows 10 IoT 仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)，它是一个开发人员工具，可让你轻松地设置新设备。 使用仪表板将 Windows 10 IoT Core 映像闪存到设备后，请检查设备是否显示在 "我的设备" 下。 

在此处使用 "操作" 下的省略号选择 "在设备门户中打开"。 在这里，你将转到设备门户身份验证页面，除非最初更改了凭据，否则默认凭据为： 

    Username: `Administrator`<br/>
    Password: `p@ssw0rd`
 
 ### <a name="2-browser"></a>2. 浏览器
如果在仪表板中找不到设备或希望跳过仪表板，还可以通过输入设备的 IP 地址并 `:8080` 将其插入到末尾来打开设备门户。 正确完成后，其外观应如下所示：


   ![IoTDashboard 视图设备](../media/deviceportal/Dashboard-Action.gif)

    
## <a name="iot-specific-features"></a>IoT 特定功能

### <a name="device-settings"></a>设备设置

IoT Core 添加复选框以启用或禁用 [屏幕键盘](../develop-your-app/OnScreenKeyboard.md)
> [!NOTE]
> 此复选框有一个已知 bug，它会将 "flash" 从选中状态 "未选中"。 单击以确保该复选框显示所需状态时，请刷新 (F5) 的页面。

### <a name="apps"></a>应用
在设备上提供 AppX 包和绑定的安装/卸载功能。
![应用列表](../media/DevicePortal/AppList.png)

IoT 核心的独特之处在于，它只允许一次运行一次前台应用。 修改应用列表以确保这种情况。 在 " **启动** " 列下，可以选择默认情况下启动的多个后台应用程序，但只能设置一个前景应用程序。  

### <a name="app-file-explorer"></a>应用文件资源管理器

应用文件资源管理器显示应用可以访问的目录。

* CameraRoll 在所有应用之间共享
* 文档在所有应用中共享
* LocalAppData 包含特定于每个应用的文件夹。 此文件夹将与你的应用同名，并且其他应用无法访问该文件夹。

### <a name="debugging"></a>调试

#### <a name="kernel-dumps"></a>内核转储
![用内核转储进行调试](../media/DevicePortal/Debug1.png)

系统崩溃将自动记录并可通过 web 管理工具查看。  然后，你可以下载内核转储，尝试找出正在进行的操作。

#### <a name="process-dumps"></a>进程转储
![用进程转储进行调试](../media/DevicePortal/Debug2.png)

这类似于实时内核转储，但适用于用户模式进程。 单击 " **下载** " 按钮将导致 "小型转储"，并将下载该进程的全部状态。 这适用于调试挂起进程。

#### <a name="kernel-crash-settings"></a>内核故障设置
![内核故障设置](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a>蓝牙
此页显示所有蓝牙配对设备以及可发现的所有设备。 要与另一台蓝牙设备配对，请将设备置于配对模式，并等待它出现在 "可用设备" 列表中。  
![蓝牙设备列表](../media/DevicePortal/Bluetooth.png)

单击 " **对" 链接** 以将设备配对。 如果设备要求使用 PIN 进行配对，它将弹出一个显示该 PIN 的消息框。 设备配对后，它将显示在 "配对的设备" 列表中。 可以通过单击 " **删除**" 取消配对设备。 

导航到蓝牙页面后，其他设备将可以发现你的设备。 你还可以从你的电脑/手机中查找它，并将其配对。

有关蓝牙的详细信息，请参阅 [蓝牙页面](https://go.microsoft.com/fwlink/?linkid=823223)。

### <a name="iot-onboarding"></a>IoT 载入

IoT 载入为配置 IoT 设备的 Wi-fi 连接选项提供支持。

** (ICS) 的 Internet 连接共享 ** Internet 连接共享允许与通过 Wi-fi SoftAP 连接到设备的其他设备共享设备的 Internet 访问。
若要使用此功能，Windows 10 IoT 设备需要有权访问 internet (例如，通过有线 LAN 连接) 。  在 "连接->载入->SoftAP 设置" 中，单击 "启用" 并设置 SSID 名称和密码。  然后，在 "连接->Internet 连接共享" 中为 "访问点适配器" 选择 "Microsoft Wi-fi Direct 虚拟适配器 #2" 和 "共享网络适配器"，然后选择有线以太网适配器。  最后，单击 "启动共享访问"。  启动后，将单独的 Wi-fi 启用的设备连接到 Windows 10 IoT 设备上的 SoftAP。  建立连接后，单独的 Wi-fi 设备将能够通过 Windows 10 IoT 设备连接到 internet。

> [!NOTE]
> 当设备上存在 Wi-fi 配置文件时，ICS 处于禁用状态。 例如，如果连接到 Wi-fi 访问点并选中 "创建配置文件 (自动重新连接) "，则将禁用 ICS。

**SoftAP 设置** SoftAP 设置用于控制是否已启用设备的 SoftAP。  它还提供了一种方法，用于配置 SoftAP 的 SSID 和 WPA2-PSK 密钥，这是从其他设备连接 SoftAP 所必需的。

**AllJoyn 载入设置** 使用 AllJoyn 载入设置，可以控制是否可以通过设备的 AllJoyn 载入制造者配置设备的 Wi-fi 连接。  当运行 AllJoyn 载入使用者应用程序的单独设备连接到 Windows 10 IoT SoftAP 时，可以使用 AllJoyn 载入消费者应用程序来配置 IoT 设备的 Wi-fi 适配器。  启用后，AllJoyn 载入制造者应用 (IoTOnboarding) 使用 ECDHE_NULL 身份验证方法。 

> [!NOTE]
> 若要在 Windows 10 IoT 版本10.0.14393 或更早版本中使用 AllJoyn 载入，需要更新 <strong>IotOnboarding</strong> 示例，此示例可在 [此处下载](https://github.com/ms-iot/samples)。

![在 ICS 上加入到 AllJoyn ](../media/DevicePortal/OnboardingAllJoyn.png)
 ![ 载入](../media/DevicePortal/OnboardingICS.png)

> [!NOTE]
> 接入点适配器是作为 WiFi 接入点的 WiFi 适配器， (通常具有类似于 192.168.137.1) 的 IP 地址。
> 共享网络适配器是连接到 Internet 的适配器 (例如：以太网适配器) 。

![载入软 AP](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> 如果启用了 AllJoyn 载入并使用 Wifi 适配器的 MAC 地址后缀，SoftAP SSID 将自动以 "AJ_" 作为前缀。 SoftAP 密码必须介于8到 63 ASCII 字符之间。


### <a name="tpm-configuration"></a>TPM 配置
受信任的平台模块 (TPM) 是一种加密协处理器，其中包括用于随机编号生成的功能、安全生成的加密密钥和其使用限制。 它还包括远程证明和密封的存储等功能。 若要了解有关 IoT Core 上的 TPM 和安全性的信息，请访问 [构建安全设备](../secure-your-device/BuildingSecureDevices.md) 页面和 [TPM](../secure-your-device/TPM.md) 页面。

> [!IMPORTANT]
> Limpet.exe 用作 Windows IoT Core 的一部分。 从10月2018开始，现在可作为开源 porject [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client) 。

为了使测试更轻松，我们提供了一个未签名的预构建版本的 Limpet.exe，可以从 WDP 下载。 只需执行 "TPM 配置" 选项卡，然后单击 "安装最新的" 按钮即可。 

> [!NOTE]
> 此版本的 Limpet.exe 不应随最终产品一起提供。 相反，你需要构建开源项目，对其进行签名，然后将其与你的映像一起打包。

### <a name="azure-clients-configuration"></a>Azure 客户端配置

IoT 设备可以通过云服务进行远程管理。 Azure 提供了一组非常丰富的服务来实现此类方案。 我们创建了一个设备管理客户端，该客户端补充了 Azure 设备预配服务 (DPS) 和 Windows 平台上的 Azure IoT 中心服务，同时还公开了多个 Windows 可管理性功能。

客户端将作为开源项目提供。 为了使测试变得更容易，我们将提供预先生成的二进制文件。 可以使用 WDP 中的 "Azure 客户端" 选项卡来安装和运行这些测试二进制文件。

> [!NOTE]
> 此版本的工具不应随最终产品一起提供。 相反，你需要构建开源项目，对其进行签名，然后将其与你的映像一起打包。

当开源项目可用于使用后，我们将更新此文档。

### <a name="remote"></a>Remote
Windows IoT 远程服务器允许用户查看其设备的显示内容，而无需将物理监视器连接到键盘。


## <a name="additional-information"></a>其他信息 

### <a name="changing-the-default-port"></a>更改默认端口
 
1. 启动 PowerShell 并 [连接到你的设备。](../connect-your-device/PowerShell.md)
2. 下载 [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) 工具，生成它，然后将其复制到你的设备。 
3. 通过运行来取得服务的注册表项的所有权

        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service

4. 通过修改注册表设置来设置所需的端口 

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
        
5. 通过运行以下或重启设备重启 WebManagement 服务

        net stop webmanagement ; net start webmanagement

### <a name="using-https"></a>使用 HTTPS 

如果要使用 HTTPS，请先获取上一部分所述的注册表项的所有权，并按如下所述设置 HttpsPort 和 EncryptionMode 注册表项，然后重新启动 webmanagement 服务

        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement

### <a name="provisioning-device-portal-with-a-custom-ssl-certificate"></a>使用自定义 SSL 证书预配设备门户

在 Windows 10 创意者更新中，Windows 设备门户为设备管理员添加了一种安装自定义证书以用于 HTTPS 通信的方式。

若要了解详细信息，请 [阅读 Windows 设备门户文档下的文档](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)。 

### <a name="crash-dump-settings-for-capturing-memory-dump"></a>捕获内存转储的故障转储设置：

若要捕获完整的内存转储，请执行以下操作：

1. 通过 WDP 连接到 IoT 设备。

2. 从调试 > 调试设置-> 内核故障设置-> 故障转储类型。 

3. 选择 "使用内存) 完成内存转储 (。
    请确保设备重新启动后，设置才会生效。 
    
4. 验证 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` 是否已设置为0x1。

5. 更新 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` 为0x0。

6. 请确保设备上有足够的空间用于生成此转储。 你可以在此处配置更改 DumpFile 位置： `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`


## <a name="additional-resources"></a>其他资源
___ 

1. [Windows 设备门户的 "概述" 页](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
