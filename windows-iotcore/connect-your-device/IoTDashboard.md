---
title: Windows 10 IoT 核心版仪表板
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解Windows 10 IoT 核心版仪表板功能以及如何开始。
keywords: windows iot， windows 10 iot 核心仪表板， windows iot 仪表板， 设备
ms.openlocfilehash: 2060acaff423e2da6df23596829ae1cce1d1979d
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230024"
---
# <a name="windows-10-iot-core-dashboard"></a>Windows 10 IoT 核心版仪表板

Windows 10 IoT 核心版仪表板是从电脑下载、设置Windows 10 IoT 核心版连接设备的最佳方法。

可以在此处下载 [IoT 核心仪表板](https://go.microsoft.com/fwlink/?LinkID=708576)。

> [!NOTE]
> 如果发现在下载后打开IoT 仪表板屏幕时出现白色屏幕，原因可能是驱动程序问题。 若要解决此问题，需要下载 Intel 图形驱动程序的 [zip](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) 格式并手动安装驱动程序。 

## <a name="set-up-a-new-device"></a>设置新设备

> [!NOTE]
> 仪表板不能用来设置 Raspberry Pi 3B+。 如果有 3B+ 设备，则必须使用 [3B+ 技术预览版](https://www.microsoft.com/software-download/windowsiot)。 请查看技术预览版的[已知限制](https://docs.microsoft.com/windows/iot-core/troubleshooting)，确定它是否适合开发。

> [!NOTE]
> 当前存在一个已知问题：OS 通过 SD 卡上的分区，并提示"格式"。" 不包含任何文件系统的特定数据分区的消息。 请按"取消"关闭此提示。 在开发解决方案时，建议单击"立即格式化"，再次将 SD 卡与 FFU 映像一起切换，因为格式操作会影响更新过程，并且设备将无法更新。


使用IoT 仪表板可以轻松设置新设备。 有关如何入门的详细说明，请参阅[入门页。](https://docs.microsoft.com/windows/iot-core/getstarted)

![IoT 仪表板设置"页](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a>SD 卡
SD 卡的类型、型号和型号极大地影响了 IoT 核心的性能和质量。
慢速卡的启动时间可能长于建议卡 的 5 [倍](../learn-about-hardware/hardwarecompatlist.md)。
较旧、不太可靠的 SD 卡甚至可能不起作用。 如果安装时仍遇到问题，请考虑更换 SD 卡。

### <a name="device-name"></a>设备名称
默认设备名称为 minwinpc。 建议将设备更改为唯一内容，这样可更轻松地在网络中查找设备。 设备名称最多 15 个字符，可以包含字母、数字和以下符号：@ # $ % ^ & ' )  ( 。 - _ { } ~ 如果在设置设备IoT 仪表板更改设备名称，则首次打开设备时将发生自动重启。

### <a name="password"></a>密码
密码是必填字段，必须设置。 在 IoT 仪表板中设置密码会修改管理员用户的密码，默认为 p@ssw0rd ""。

### <a name="wi-fi-network-connection"></a>Wi-Fi网络连接
IoT 仪表板显示电脑以前连接到的所有可用网络。 如果在列表中看不到所需的Wi-Fi网络，请确保已连接到电脑上的虚拟网络。
如果取消选中该框，则必须在闪烁后将以太网电缆连接到板。

### <a name="first-boot"></a>首次启动
首次启动始终比所有后续启动时间长。 操作系统需要一些时间来安装和连接到网络。
启动时间可能会因 SD 卡而异。 例如，在建议 SD 卡上运行的 Raspberry Pi 3 首次启动需要 3-4 分钟。 在质量不佳的 SD 卡的同一 Pi 上，我们发现启动时间超过 15 分钟。

### <a name="connecting-to-the-internet"></a>连接到 Internet
让 IoT Core 设备连接到 Internet 至关重要。 许多较新的板都内置有Wi-Fi适配器。 如果在连接到网络时遇到问题，请尝试以下操作：

* 重新启动设备
* 插入以太网电缆
* 将监视器插入设备。 这会显示有关设备的诊断信息

> [!NOTE]
> 连接到 Wi-Fi 时，Wi-Fi Raspberry Pi 2 适配器可能不稳定。


## <a name="my-devices"></a>我的设备
___
设备连接到 Internet 后，IoT 仪表板会自动检测设备。
若要查找设备，请转到"**我的设备"。** 如果未列出设备，请尝试重新启动设备。 确保如果网络上存在多个设备，则每个设备都有唯一的名称。 此外，**请windows10iotcoredashboard.exe以下步骤**，确保允许Windows防火墙进行通信：

1. 打开 **网络和共享中心，** 然后找到电脑 (域/专用/公共) 网络类型。
2. 打开 **控制面板，** 然后单击"**系统和安全"。**
3. 在 **"防火墙"下，Windows应用****Windows防火墙"**。
4. 单击“更改设置”  。
5. 在 **windows10iotcoredashboard.exe"****应用** 和功能"中查找"网络"，然后启用相应的网络 (例如，在步骤 1 中的网络) 。


### <a name="connect-to-your-device"></a>连接到设备

> [!NOTE]
> 如果无法在仪表板中查找设备，请尝试在浏览器中键入 [IP 地址] 和 [：8080] ，Windows 设备门户并运行。 若要使设备显示在仪表板中，请尝试重新启动设备。


右键单击并选择"在 **中打开设备门户"。** 这会[启动Windows 设备门户页面](../manage-your-device/DevicePortal.md)，是交互和管理设备的最佳方式。

![IoTDashboard 视图设备](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

也可使用 Windows PowerShell 连接到设备。

## <a name="connect-to-azure"></a>连接到 Azure
___
IoT 仪表板使用中心预配 IoT 核心Azure IoT设备。 可在此博客文章 中阅读[有关它的内容。](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core)

[了解如何在 Azure IoT 仪表板应用](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a>快速运行示例
___

快速运行示例不需要任何代码编译、Visual Studio 安装或 SDK 下载。 它们非常适用于快速查看 IoT Core 可以执行哪些工作。

### <a name="network-3d-printer"></a>网络 3D 打印机
使用网络 3D 打印机示例将 3D 打印机连接到板，可以使它可以通过家庭网络进行发现。 

![IoTDashboard 网络 3D 打印机](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a>Internet 无线电
将Windows 10 IoT 核心版设备转换为可以从家庭任意位置控制的 Internet 无线电。

![IoTDashboard Internet 无线电](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a>IoT 核心块
IoT 核心块示例允许使用浏览器中的"块"编辑器对 Raspberry Pi2 或 3 和 Raspberry Pi Sense Hat 进行编程。

![IoTDashboard Blockly](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
