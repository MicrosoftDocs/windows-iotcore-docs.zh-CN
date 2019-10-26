---
title: 在 Windows 10 Iot Core 设备上使用 WiFi Direct
ms.date: 08/28/2017
ms.topic: article
description: 了解如何通过启用的 USB wifi 适配器在设备上设置、测试和使用 wifi direct。
keywords: windows iot，wifi 直接，安装，wifi，设备
ms.openlocfilehash: 7355d5d0879b2a0f31f5fa89eb00e71eb0fa4e4f
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918287"
---
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a>在 Windows 10 IoT Core 设备上使用 WiFi Direct

在 Windows 10 IoT Core 设备上，通过使用 WiFi 直接启用的 USB WiFi 适配器支持 WiFi 直接。 若要确保启用 WiFi Direct，需要满足以下两个事项：
* USB WiFi 适配器的硬件需要支持 WiFi Direct，
* USB WiFi 适配器的相应驱动程序需要支持 WiFi Direct。 

WiFi Direct 为 WiFi 设备到设备连接提供了一种解决方案，无需无线接入点（无线 AP）来设置连接。 查看[WiFiDirect 命名空间](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx)中提供的 UWP api，查看可以使用 WiFiDirect 执行的操作。

## <a name="supported-adapters"></a>支持的适配器

可以在[受支持的硬件](../learn-about-hardware/HardwareCompatList.md)页上找到已在 Windows 10 IoT Core 上测试的 WiFi 适配器列表。 

## <a name="basic-sample-for-wifi-direct"></a>WiFi Direct 的基本示例

可以通过 WiFi 直接 UWP[示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)轻松测试 wifi 直接功能。 我们将使用C#版本并运行两个设备的示例。

### <a name="set-up-the-two-devices"></a>设置两个设备
* 运行 Windows 10 IoT Core 的 MinnowBoardMax （MBM）（请参阅此处的说明），其中包含 CanaKit WiFi 转换器
* 将显示器、键盘和鼠标连接到 MBM
* 运行最新 Windows 10 周年更新的 Windows 10 电脑。 电脑（或便携式计算机）需要提供 WiFi 直接支持（如 Microsoft Surface）
* 在 Windows 10 电脑上安装 Visual Studio 2017
* 克隆或下载 WiFi 直接 UWP[示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)（[此处](https://github.com/Microsoft/Windows-universal-samples)提供 GitHub 存储库的根目录）。
* 在 Visual C# Studio 2017 中加载 WIFI Direct UWP 示例的版本

#### <a name="run-the-sample-on-the-two-devices"></a>在两个设备上运行示例
* 编译该示例并在 MBM 上部署/运行它：

    * 将 "解决方案平台" 组合框设置为 "x86"
    * 从 "运行" 下拉列表中选择 "远程计算机"
    * 在不进行调试的情况下启动 MBM 上的示例（通过按 Ctrl-F5 或从 "调试" 菜单中选择 "启动（不调试）"）
    * 应会在连接到 MBM 的监视器上看到运行的 WiFi 直接示例
* 编译该示例，并在 Windows 10 电脑上部署/运行它：
    * 将 "解决方案平台" 组合框设置为 "x86"
    * 从 "运行" 下拉列表中选择 "本地"
    * 启动示例（按 F5 或 Ctrl-F5）
    * 你应看到在 Windows 10 电脑上运行的 WiFi Direct 示例

### <a name="set-up-advertiser-and-connector"></a>设置广告商和连接器
* 在 MBM 上，选择（1） "广告商"，并按 "启动广告" 按钮

    * MBM 将在 WiFi 直接通道上开始播发

        !["广告商配置" 屏幕](../media/SetupWiFiDirect/Advertiser01.png)

        请注意应用底部的 "播发状态" 横幅。
    
* 在 Windows 10 电脑上，选择（2） "连接器"，并按 "启动观察程序" 按钮 

    * Windows 10 电脑将开始扫描可用的 WiFi 直接连接
    * 扫描完成后，应会在 "发现的设备" 列表中看到 MBM 的名称

        ![连接器配置屏幕](../media/SetupWiFiDirect/Connector01.png)

        你可以看到列出了两个设备（对 "ale-mbm01" 感兴趣）和 "DeviceWatcher 枚举已完成" 消息。

### <a name="pair-the-devices"></a>配对设备
* 在 Windows 10 电脑上的 "发现的设备" 列表中，选择 MBM （在我们的示例中为 "mbm01"），然后按 "连接" 按钮
* 在 Windows 10 电脑上，按 "是" 启动配对过程

    ![连接器开始配对](../media/SetupWiFiDirect/Connector02.png)

* 在 MBM 监视器上，应使用 PIN 的消息

    ![广告商 PIN 对话框](../media/SetupWiFiDirect/Advertiser02.png)

* 在 Windows 10 电脑上，你应该会看到一个对话框，需要在其中输入 PIN

    ![连接器 PIN 对话框](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a>在频道上交谈
* 应连接两个设备。 你应在 "连接的设备" 列表中的两个屏幕上看到随机生成的设备 id （在我们的示例中为 "hqffpzhz ggg"）

    ![已连接到广告设备](../media/SetupWiFiDirect/Advertiser03.png)

    ![连接器连接设备](../media/SetupWiFiDirect/Connector04.png)

* 你现在设置了全双工通道（或套接字）

    * 在 MBM 上，从 "连接的设备" 列表中选择设备（"hqffpzhz. ggg"）
    * 在 "输入消息" 文本框中键入一条消息
    * 按 "发送" 按钮
    * 应会看到从 Windows 10 PC 接收的消息
    * 尝试将消息从 Windows 10 电脑发送到 MBM
