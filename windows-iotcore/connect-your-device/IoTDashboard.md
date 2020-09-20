---
title: Windows 10 IoT 核心版仪表板
ms.date: 08/28/2017
ms.topic: article
description: 了解 Windows 10 IoT Core 仪表板的功能以及入门方式。
keywords: windows iot，windows 10 iot 核心仪表板，windows iot 面板，设备
ms.openlocfilehash: eb8ef700ef44b0b8800af89d8b57717551be885d
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782599"
---
# <a name="windows-10-iot-core-dashboard"></a>Windows 10 IoT 核心版仪表板

Windows 10 IoT 核心仪表板是从 PC 下载、设置和连接 Windows 10 IoT 核心设备的最佳方式。

可在此处下载 [IoT 核心仪表板](https://go.microsoft.com/fwlink/?LinkID=708576)。

> [!NOTE]
> 如果您在下载后打开 IoT 面板时遇到了白屏，则可能是由于驱动程序问题所致。 若要解决此问题，需要下载 Intel 图形驱动程序的 [zip 格式](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) ，并手动安装驱动程序。 

## <a name="set-up-a-new-device"></a>设置新设备

> [!NOTE]
> 仪表板不能用来设置 Raspberry Pi 3B+。 如果有 3B+ 设备，则必须使用 [3B+ 技术预览版](https://www.microsoft.com/software-download/windowsiot)。 请查看技术预览版的[已知限制](https://docs.microsoft.com/windows/iot-core/troubleshooting)，确定它是否适合开发。

> [!NOTE]
> 目前存在一个已知问题，其中，操作系统会经历 SD 卡上的分区，并提示 "Format ..." 不包含任何文件系统的特定数据分区的消息。 请按 "取消" 以消除此提示。 当我们处理某个解决方案时，我们建议，如果你单击 "立即格式化"，则会再次使用 FFU 图像刷新 SD 卡，因为 Format 操作会影响更新过程，并且设备将无法更新。


使用 IoT 面板可以轻松地设置新设备。 有关如何入门的详细说明，请参阅[入门页。](https://docs.microsoft.com/windows/iot-core/getstarted)

![IoT 面板设置页面](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a>SD 卡
SD 卡的类型、品牌和型号极大地影响 IoT 核心的性能和质量。
比我们 [建议的卡](../learn-about-hardware/hardwarecompatlist.md)相比，慢卡的启动时间可能会长达五倍。
旧的、不太可靠的 SD 卡甚至可能不起作用。 如果继续安装时遇到问题，请考虑更换 SD 卡。

### <a name="device-name"></a>设备名称
默认设备名称为 minwinpc。 建议将其更改为唯一的内容，因为这样可以更轻松地在网络上查找设备。 设备名称的长度最长可以为15个字符，可以包含字母、数字和以下符号： @ # $% ^ & ")  (。 -_ {} ~ 如果在设置设备时在 IoT 面板中更改设备名，则在第一次打开设备电源时将自动重启。

### <a name="password"></a>密码
密码是必填字段，必须设置。 在 IoT 面板中设置密码会修改管理员用户的密码，默认值为 " p@ssw0rd "。

### <a name="wi-fi-network-connection"></a>Wi-fi 网络连接
IoT 面板显示你的电脑以前连接到的所有可用网络。 如果在列表中看不到所需的 Wi-fi 网络，请确保你已在电脑上连接到该网络。
如果取消选中此框，则必须在闪烁后将以太网电缆连接到您的面板。

### <a name="first-boot"></a>首次启动
首次启动的时间将始终比所有后续启动的时间要长。 操作系统将需要一段时间来安装和连接到你的网络。
根据 SD 卡的不同，启动时间可能会很大。 例如，在我们建议的 SD 卡上运行的 Raspberry Pi 3 在第一次启动时会花费3-4 分钟。 对于质量较差的 SD 卡，同一 Pi 上的启动时间超过15分钟。

### <a name="connecting-to-the-internet"></a>连接到 internet
将 IoT Core 设备连接到 internet 非常重要。 许多较新的板随附内置 Wi-fi 适配器。 如果在连接到网络时遇到问题，请尝试以下操作：

* 正在重启设备
* 插入以太网电缆
* 将监视器插入设备。 这会显示有关设备的诊断信息

> [!NOTE]
> 在连接到 Wi-fi 时，官方 Raspberry Pi 2 Wi-fi 适配器可能不稳定。


## <a name="my-devices"></a>我的设备
___
将设备连接到 internet 后，IoT 面板会自动检测你的设备。
若要查找你的设备，请参阅 **"我的设备**"。 如果未列出你的设备，请尝试重新启动设备。 请确保网络上有多个设备，每个设备都具有唯一的名称。 此外，请确保允许 **windows10iotcoredashboard.exe** 通过执行以下步骤，通过 Windows 防火墙进行通信：

1. 打开 " **网络和共享中心** "，然后查找计算机连接到的网络 (域/专用/公共) 的类型。
2. 打开 **"控制面板"** ，然后单击 " **系统和安全**"。
3. 在**Windows 防火墙**下，单击 "**允许应用通过 windows 防火墙**"。
4. 单击“更改设置”  。
5. 在 "**允许的应用和功能**" 中查找**windows10iotcoredashboard.exe** ，然后启用适当的网络复选框 (即你在步骤1中找到的网络类型) 。


### <a name="connect-to-your-device"></a>连接到设备

> [!NOTE]
> 如果在仪表板中找不到你的设备，请尝试在浏览器中键入 [IP 地址] 和 [： 8080] 以启动并运行 Windows 设备门户。 若要使设备在仪表板中显示，请尝试重新启动设备。


右键单击并选择 **"在设备门户中打开"**。 这将启动 [Windows 设备门户](../manage-your-device/DevicePortal.md) 页面，并且是交互和管理设备的最佳方式。

![IoTDashboard 视图设备](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

你还可以使用 Windows PowerShell 连接到设备。

## <a name="connect-to-azure"></a>连接到 Azure
___
IoT 面板允许通过 Azure IoT 中心设置 IoT 核心设备。 可在此 [博客文章](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core)中阅读更多相关信息。

[了解如何在 Azure 中使用 IoT 面板](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a>快速运行示例
___

"快速运行" 示例不需要任何代码编译、Visual studio 安装或 SDK 下载。 它们非常适用于快速查看 IoT 核心可以执行的操作。

### <a name="network-3d-printer"></a>网络3D 打印机
使用 "网络3D 打印机" 示例将3D 打印机连接到你的板，使其可通过家庭网络发现。 

![IoTDashboard 网络3D 打印机](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a>Internet 广播
将 Windows 10 IoT Core 设备转换为可从家里任意位置控制的 internet 收音机。

![IoTDashboard Internet 收音机](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a>IoT 核心 Blockly
IoT Core Blockly 示例可让你的程序 Raspberry Pi2 或3，并使用你的浏览器中的 "阻止" 编辑器。

![IoTDashboard Blockly](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
