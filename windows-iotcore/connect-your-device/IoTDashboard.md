---
title: Windows 10 IoT 核心版仪表板
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解有关 Windows 10 IoT Core 仪表板的作用以及如何开始。
keywords: windows iot、 windows 10 iot 核心版仪表板、 windows iot 仪表板、 设备
ms.openlocfilehash: d21b67dad15d510564ec7fae28a2431d28faf8be
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510973"
---
# <a name="windows-10-iot-core-dashboard"></a>Windows 10 IoT 核心版仪表板

Windows 10 IoT 核心版仪表板是最佳的方式，若要下载，请设置并连接你的 Windows 10 IoT Core 设备，所有从您的 PC。

您可以下载[IoT 核心版仪表板此处](http://go.microsoft.com/fwlink/?LinkID=708576)。

> [!NOTE]
> 如果您正在查找您将获得一个白色的屏幕，下载后打开 IoT 仪表板时，它可能是由于驱动程序问题。 若要解决此问题，您将需要下载[zip 格式](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip)Intel 图形驱动程序的手动安装的驱动程序。 

## <a name="set-up-a-new-device"></a>设置新设备

> [!NOTE]
> 不能用于设置 Raspberry Pi 3B + 使用仪表板。 如果你有 3B + 设备，则必须使用[3B + 技术预览版](https://www.microsoft.com/en-us/software-download/windowsiot)。 请查看[已知限制](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting)的 technical preview，以确定这是否适用于你的开发。

> [!NOTE]
> 目前有一个已知的问题，其中 OS 上的 SD 卡经历分区并提示格式... 特定的数据分区，不包含任何文件系统的消息。 请通过按取消，则关闭此提示。 虽然我们在一个解决方案中工作，我们建议，如果单击现在格式，您刷新使用 FFU 映像的 SD 卡再次作为更新过程，并在设备将无法更新的格式操作影响。


IoT 仪表板轻松设置新设备。 有关如何入门的详细说明，请参阅[开始](https://docs.microsoft.com/en-us/windows/iot-core/getstarted)页。

![IoT 仪表板安装程序页](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a>SD 卡
类型、 品牌和型号的 SD 卡极大地影响性能和 IoT 核心版的质量。
慢速卡可能长达五次启动比我们[建议卡](../learn-about-hardware/hardwarecompatlist.md)。
也可以不工作的较旧的、 可靠性较低的 SD 卡。 如果继续遇到安装问题，请考虑更换 SD 卡。

### <a name="device-name"></a>设备名称
默认设备名称是 minwinpc。 我们建议将其更改为的唯一名称，因为这可更轻松地查找网络上的设备。 设备名称可以在最多 15 个字符之间，并可以包含字母、 数字和以下符号: @ # $ %^ &) (。 -_ {} ~ 自动重新启动如果设置你的设备时更改 IoT 仪表板中的设备名称，将发生在设备上的第一次当您打开。

### <a name="password"></a>密码
密码是必填字段，必须设置。 在 IoT 仪表板中设置密码修改它默认情况下是管理员用户的密码"p@ssw0rd"。

### <a name="wi-fi-network-connection"></a>Wi-fi 网络连接
IoT 仪表板显示您的 PC 之前已连接到的所有可用的网络。 如果您看不到所需的 Wi-fi 网络列表上，确保您的 PC 上连接到它。
如果取消选中的框，则必须后闪烁到开发板连接以太网电缆。

### <a name="first-boot"></a>首次启动
在首次启动始终需要比所有后续启动时较长时间。 操作系统将需要一些时间来安装并连接到你的网络。
启动时可能会因极大地 SD 卡上。 例如，我们建议的 SD 卡上运行 Raspberry Pi 3 需要首次启动的 3 到 4 分钟。 使用低质量 SD 卡在同一个 pi，我们已了解了启动时间超过 15 分钟。

### <a name="connecting-to-the-internet"></a>连接到 internet
让你连接到 internet 的 IoT Core 设备是必不可少的。 许多较新板附带内置的 Wi-fi 适配器中。 如果你遇到问题，获取连接到网络，请尝试以下解决方法：

* 重启设备
* 插入以太网电缆
* 插入到设备的监视器。 这将显示有关你的设备的诊断信息

> [!NOTE]
> 连接到 Wi-fi 时，正式的 Raspberry Pi 2 Wi-fi 适配器可以是不稳定。


## <a name="my-devices"></a>我的设备
___
你的设备连接到 internet 后，IoT 仪表板将自动检测你的设备。
若要查找你的设备，请转到**我的设备**。 如果未列出你的设备，请尝试重新启动设备。 请确保，如果有多个设备在网络上，它们都具有唯一的名称。 此外，请确保你**windows10iotcoredashboard.exe**允许通过 Windows 防火墙通信通过执行以下步骤：

1. 打开**网络和共享中心**，然后找到您的 PC 所连接到网络 (域/Private/Public) 的类型。
2. 打开**Control Panel**然后单击**系统和安全**。
3. 单击**允许通过 Windows 防火墙的应用程序**下**Windows 防火墙**。
4. 单击**更改设置**。
5. 查找**windows10iotcoredashboard.exe**中**允许的应用程序和功能**，然后启用相应的网络复选框 （即在步骤 1 中找到的网络类型）。


### <a name="connect-to-your-device"></a>连接到设备

> [!NOTE]
> 如果您不能在仪表板中查找你的设备，请尝试键入你的 [IP 地址] 和 [: 8080] 到浏览器以获取 Windows Device Portal，启动并运行。 若要获取你的设备以显示在仪表板中，请尝试重新启动你的设备。


右键单击并选择**在设备门户中打开**。 这将启动[Windows Device Portal](../manage-your-device/DevicePortal.md)页以及交互并管理你的设备的最佳方式。

![IoTDashboard 查看设备](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

您还可以连接到使用 Windows PowerShell 的设备。

## <a name="connect-to-azure"></a>连接到 Azure
___
IoT 面板，您可以使用 Azure IoT 中心的 IoT Core 设备预配。 你可以阅读更多有关它在此[博客文章](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core)。

[了解如何使用 Azure IoT 仪表板](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a>快速运行的示例
___

快速运行示例并不需要任何代码编译，Visual studio 安装或下载 SDK。 它们非常适合用于快速签出 IoT 核心版可以执行的操作。

### <a name="network-3d-printer"></a>网络 3D 打印机
使用网络 3D 打印机示例连接到开发板的 3D 打印机可以使它可检测到通过您的家庭网络。 

![IoTDashboard 网络 3D 打印机](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a>Internet 广播
转变为可以控制从任意位置在家中 internet 广播你的 Windows 10 IoT Core 设备。

![IoTDashboard Internet 广播](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a>IoT 核心版 Blockly
IoT Core Blockly 示例允许程序 Raspberry Pi2 或 3 和 Raspberry Pi 意义上乘幂号的使用从浏览器的"块"编辑器。

![IoTDashboard Blockly](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
