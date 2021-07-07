---
title: Windows 设备门户
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 Windows 设备门户远程配置和管理设备。
keywords: windows iot， Windows 设备门户， 远程， 设备门户
ms.openlocfilehash: 37d51ab3043630b08ea13e4c65858bcda8fbe1a1
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229474"
---
# <a name="windows-device-portal"></a>Windows 设备门户
   使用 Windows 设备门户 (WDP) ，可以远程通过本地网络配置和管理设备。
主要功能记录在Windows 设备门户[页上](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)

![设备门户主页](../media/deviceportal/deviceportal.png)

> [!IMPORTANT]
> 请勿将创客映像用于商业化。 若要将某个设备商业化，必须使用自定义 FFU 以确保最佳安全性。 在[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。

> [!WARNING]
> ARM 设备当前无法进行实时内核调试。 我们正在努力修复这一问题。

> [!IMPORTANT]
> 如果要构建一个开源零售设备，用于商业部署到“特定/有限安装”（即工厂或零售商店），然后由最终用户进行最终配置，并且您要为客户登记归档，他们必须[获取 WDP 证书，并将其安装到 WDP 和联网的浏览器上，且在 WDP 更改了密码](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)，那么在这种范围狭窄的商用实例中使用 WDP 是可以接受的。 此方案中的零售映像仍 *不应包含* IOT_TOOLKIT，但应该使用 IOT_WEBBEXTN 包来拉取 WDP。

## <a name="shared-documentation"></a>共享文档
WDP 是在所有设备之间共享的开发人员Windows 10工具。 每个产品都有其自己的独特功能，但核心功能是相同的。
有关主要功能的文档，请参阅Windows 设备门户[页](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)。 以下文档的其余部分将特定于 IoT。

## <a name="set-up"></a>设置

有两种方法可以启动Windows 设备门户运行。

### <a name="1-windows-10-iot-dashboard"></a>1.Windows 10 IoT 仪表板

首先，需要下载 Windows 10 IoT 仪表板，这是一[](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)种开发人员工具，可以轻松设置新设备。 使用仪表板将图像刷Windows 10 IoT 核心版设备后，请检查设备是否显示在"我的设备"下。

然后，使用"操作"下的省略号选择"在 设备门户 中打开"。 在这里，你将看到"设备门户"页，除非最初更改了凭据，否则默认凭据为：
```
    Username: Administrator
    Password: p@ssw0rd
```
 ### <a name="2-browser"></a>2.浏览器
如果无法在仪表板中查找设备或不想使用仪表板，则还可以在设备门户 IP 地址加上终端来打开 `:8080` 设备。 正确完成后，应如下所示：


   ![IoTDashboard 视图设备](../media/deviceportal/Dashboard-Action.gif)


## <a name="iot-specific-features"></a>IoT 特定功能

### <a name="device-settings"></a>设备设置

IoT 核心添加复选框以启用或禁用 [屏幕键盘](../develop-your-app/OnScreenKeyboard.md)
> [!NOTE]
> 此复选框有一个已知 bug，其中它将"闪烁"从选中状态"闪烁"为"未选中"。 请在单击后 (F5) 页面，以确保复选框显示所需状态。

### <a name="apps"></a>应用
为设备上 AppX 包和捆绑包提供安装/卸载功能。
![应用列表](../media/DevicePortal/AppList.png)

IoT 核心是唯一的，因为它只允许一次运行一个前台应用。 修改应用列表以确保情况如此。 在 **"启动** "列下，可以选择默认启动的后台应用程序，但只能设置一个前台应用程序。  

### <a name="app-file-explorer"></a>应用文件资源管理器

应用文件资源管理器显示应用可以访问的目录。

* CameraRoll 在所有应用之间共享
* 文档在所有应用之间共享
* LocalAppData 包含特定于每个应用的文件夹。 此文件夹与应用的名称相同，其他应用无法访问它。

### <a name="debugging"></a>调试

#### <a name="kernel-dumps"></a>内核转储
![使用内核转储进行调试](../media/DevicePortal/Debug1.png)

系统崩溃将自动记录，并且可以通过 Web 管理工具查看。  然后，可以下载内核转储，并尝试找出发生什么问题。

#### <a name="process-dumps"></a>进程转储
![使用进程转储进行调试](../media/DevicePortal/Debug2.png)

这类似于实时内核转储，但适用于用户模式进程。
单击 **下载** 按钮将导致"minidump"，并且将下载该进程的整个状态。 这适用于调试挂起的进程。

#### <a name="kernel-crash-settings"></a>内核崩溃设置
![内核崩溃设置](../media/DevicePortal/Debug3.png)

### <a name="bluetooth"></a>蓝牙
此页显示所有蓝牙配对设备和可发现的所有设备。 若要与另蓝牙设备配对，请使设备进入配对模式，并等待该设备显示在可用设备列表中。  
![蓝牙设备列表](../media/DevicePortal/Bluetooth.png)

单击" **配对"链接** 以配对设备。 如果设备需要 PIN 进行配对，它将弹出一个显示 PIN 的消息框。 设备配对后，会显示在"配对设备"列表中。 可以通过单击"删除"来对设备 **进行配对**。

导航到"蓝牙"页后，设备将被其他设备发现。 还可以从电脑/设备找到电话并在那里配对。

有关蓝牙详细信息，请参阅 [蓝牙页](https://go.microsoft.com/fwlink/?linkid=823223)。

### <a name="iot-onboarding"></a>IoT 载入

IoT 载入支持配置 IoT 设备Wi-Fi连接选项。

**Internet 连接共享 (ICS)** 使用 Internet 连接共享，你可以与通过 SoftAP 连接到设备的其他设备共享Wi-Fi Internet 访问权限。
若要使用此功能，Windows 10 IoT 设备需要有权访问 Internet (例如通过有线 LAN 连接) 。  在"Connectivity->Onboarding->SoftAP 设置"中，单击"启用"并设置 SSID 名称和密码。  然后在"连接>Internet 连接共享"中，为"接入点适配器"选择"Microsoft Wi-Fi 直接虚拟适配器 #2"，对于"共享网络适配器"，请选择有线以太网适配器。  最后，单击"启动共享访问"。  启动后，将Wi-Fi设备连接到 IoT Windows 10 SoftAP。  建立连接后，已启用Wi-Fi的设备可以通过 IoT 设备连接到Windows 10 Internet。

> [!NOTE]
> 当设备上存在一个Wi-Fi配置文件时，ICS 处于禁用状态。
>例如，如果连接到 Wi-Fi访问点并选中"创建配置文件 (自动重新连接，ICS 将) "。

**SoftAP 设置** 使用 SoftAP 设置可控制是否启用设备的 SoftAP。  它还提供了一种配置 SoftAP SSID 和 WPA2-PSK 密钥（从另一台设备连接 SoftAP 所必需的）的方式。

**AllJoyn 载入设置** AllJoyn 加入设置允许你控制是否可以通过设备的 AllJoyn Onboarding Producer 配置设备的 Wi-Fi 连接。  当运行 AllJoyn Onboarding Consumer 应用程序的单独设备连接到 Windows 10 IoT SoftAP 时，AllJoyn Onboarding Consumer 应用程序可用于配置 IoT 设备的 Wi-Fi 适配器。  启用后，IoTOnboarding (AllJoyn Onboarding 生成者) 使用 ECDHE_NULL身份验证方法。

> [!NOTE]
> 若要将 AllJoyn Onboarding 与 Windows 10 IoT 内部版本 10.0.14393 或更早版本一起使用，需要对<strong>IotOnboarding</strong>示例进行更新，该示例可在此处[下载](https://github.com/ms-iot/samples)。

![载入到 ICS 上的 AllJoyn ](../media/DevicePortal/OnboardingAllJoyn.png)
 ![ 载入](../media/DevicePortal/OnboardingICS.png)

> [!NOTE]
> 接入点适配器是充当 WiFi 接入点的 WiFi 适配器 (它通常具有类似 192.168.137.1) 。
> 共享网络适配器是连接到 Internet (，例如：以太网适配器) 。

![载入到软 AP](../media/DevicePortal/OnboardingSoftAP.png)

> [!NOTE]
> 如果启用了 AllJoyn 载入，并且已用 Wifi 适配器的 MAC 地址进行附加，SoftAP SSID 将自动以"AJ_"作为前缀。 SoftAP 通行短语必须介于 8 到 63 个 ASCII 字符之间。


### <a name="tpm-configuration"></a>TPM 配置
TPM 受信任的平台模块 (是) 处理器，包括随机数生成、加密密钥的安全生成及其使用限制等功能。 它还包括远程证明和密封存储等功能。 若要了解 IoT 核心版上的 TPM 和安全性，请访问构建 [安全设备](../secure-your-device/BuildingSecureDevices.md) 页和 [TPM](../secure-your-device/TPM.md) 页。

> [!IMPORTANT]
> Limpet.exe IoT 核心Windows一部分。 从 2018 年 10 月开始，它现已在 上作为开源项目提供 [https://github.com/ms-iot/azure-dm-client](https://github.com/ms-iot/azure-dm-client) 。

为了简化测试，我们提供了一个未签名的预生成版本Limpet.exe可从 WDP 下载。 只需转到"TPM 配置"选项卡，然后单击"安装最新"按钮。

> [!NOTE]
> 此版本的 Limpet.exe不得随最终产品一起提供。 相反，你需要生成开放源代码项目，对该项目进行签名，然后使用映像打包该项目。

### <a name="azure-clients-configuration"></a>Azure 客户端配置

可以通过云服务远程管理 IoT 设备。 Azure 提供了一组丰富的服务来启用此类方案。 我们创建了一个设备管理客户端，用于补充 Azure 的设备预配服务 (DPS) 和 Windows 平台上的 Azure IoT 中心服务，并公开了多个 Windows 可管理性功能。

客户端将作为开放源代码项目提供。 为了更轻松地测试它们，我们将提供预建的二进制文件。 可以使用 WDP 中的"Azure 客户端"选项卡来安装和运行这些测试二进制文件。

> [!NOTE]
> 此版本的工具不应随最终产品一起提供。 相反，你需要生成开放源代码项目，对该项目进行签名，然后使用映像打包该项目。

开放源代码项目可供使用后，我们将更新此文档。

### <a name="remote"></a>Remote
使用 Windows IoT 远程服务器，用户可以在不将物理监视器连接到键盘的情况下查看其设备显示内容。


## <a name="additional-information"></a>其他信息

### <a name="changing-the-default-port"></a>更改默认端口

1. 启动 PowerShell [并连接到设备。](../connect-your-device/PowerShell.md)
2. 下载 [TakeRegistryOwnership](https://github.com/ms-iot/iot-utilities/tree/master/TakeRegistryOwnership) 工具，生成该工具，并复制到设备。
3. 通过运行 来取得服务注册表项的所有权
```
        .\TakeRegistryOwnership.exe MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service
```
4. 通过修改注册表设置设置所需的端口
```
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpPort /t REG_DWORD /d <your port number>
```
5. 通过运行以下代码或重启设备来重启 WebManagement 服务
```
        net stop webmanagement ; net start webmanagement
```
### <a name="using-https"></a>使用 HTTPS

如果要使用 HTTPS，请首先获得上一部分中所述的注册表项的所有权，并设置如下所示的 HttpsPort 和 EncryptionMode 注册表项，然后重启 webmanagement 服务
```
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v EncryptionMode /t REG_DWORD /d 0x3 /f
        reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\webmanagement\service /v HttpsPort /t REG_DWORD /d <your port number> /f
        net stop webmanagement ; net start webmanagement
```
### <a name="provisioning-device-portal-with-a-custom-ssl-certificate"></a>使用设备门户 SSL 证书预配证书

在Windows 10 创意者更新中，Windows 设备门户为设备管理员添加了一种安装自定义证书以用于 HTTPS 通信的方法。

若要了解有关详细信息，[请阅读文档 下Windows 设备门户文档](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-ssl)。

### <a name="crash-dump-settings-for-capturing-memory-dump"></a>用于设置内存转储的故障转储对象：

若要捕获完整内存转储，请执行下列操作：

1. 连接 WDP 连接到 IoT 设备。

2. 从"调试>调试设置 ->内核故障设置 ->故障转储类型" 。

3. 选择：完成 (内存转储) 。
    确保重启设备，设置生效。

4. 验证 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\CrashDumpEnabled` 是否设置为 0x1。

5. 更新 `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFileSize` 到 0x0。

6. 请确保设备上有足够的空间来生成此转储。 可以从此处配置更改 DumpFile 位置： `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CrashControl\DumpFile`


## <a name="additional-resources"></a>其他资源
___

1. [Windows设备门户概述页](https://msdn.microsoft.com/windows/uwp/debug-test-perf/device-portal)
