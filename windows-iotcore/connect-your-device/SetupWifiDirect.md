---
title: 在 Windows 10 Iot Core 设备上使用 WiFi Direct
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何设置、 测试和启用了 USB wifi 适配器的设备上使用 wifi direct。
keywords: windows iot、 直接的 wifi，安装程序、 wifi、 设备
ms.openlocfilehash: 04ecf1820356c59fecea81be47f69617ab42ab36
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510894"
---
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a>在 Windows 10 IoT Core 设备上使用 WiFi Direct

支持 WiFi 直接在 Windows 10 IoT Core 上通过 WiFi 直接使用的设备启用 USB WiFi 适配器。 若要确保 WiFi 直接启用了两件事情需要为 true:
* 需要支持 WiFi Direct USB WiFi 适配器的硬件
* USB WiFi 适配器的相应驱动程序需要支持 WiFi Direct。 

WiFi 直接提供的 WiFi 设备的连接，而无需为任一无线访问点 (无线 AP) 来设置连接的解决方案。 看一看中提供的 UWP Api [Windows.Devices.WiFiDirect 命名空间](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx)若要查看对 WiFiDirect 可以执行哪些操作。

## <a name="supported-adapters"></a>支持的适配器

Windows 10 IoT Core 进行了测试的 WiFi 适配器的列表，可我们[支持硬件](../learn-about-hardware/HardwareCompatList.md)页。 

## <a name="basic-sample-for-wifi-direct"></a>WiFi 直接的基本示例

您可以轻松地测试 WiFi 直接功能使用 WiFi 直接 UWP[示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)。 我们将使用C#版本并运行两个设备的示例。

### <a name="set-up-the-two-devices"></a>设置两个设备
* MinnowBoardMax (MBM) 运行 Windows 10 IoT Core （请参阅此处的说明），与 CanaKit WiFi 硬件保护装置
* 监视器、 键盘和鼠标连接到 MBM
* 运行最新的 Windows 10 周年更新的 Windows 10 电脑。 PC （或便携式计算机） 将需要具有 WiFi 直接支持 (例如 Microsoft Surface)
* 在 Windows 10 电脑上安装 Visual Studio 2017
* 克隆或下载 WiFi 直接 UWP[示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)(GitHub 存储库的根是[此处](https://github.com/Microsoft/Windows-universal-samples))。
* 加载C#版本的 Visual Studio 2017 中的 WiFi 直接 UWP 示例

#### <a name="run-the-sample-on-the-two-devices"></a>两个设备上运行示例
* 编译该示例并部署/运行它 MBM 上：

    * 设置为"x86"的"解决方案平台"组合框
    * 从"运行"的下拉列表中选择"远程计算机"
    * 而不进行调试 （通过按 Ctrl-F5 或从"调试"菜单中选择"启动但不调试"） 上 MBM 启动示例
    * 应看到 WiFi 直接示例连接到 MBM 在监视器上运行
* 编译该示例并部署/运行其 Windows 10 电脑上：
    * 设置为"x86"的"解决方案平台"组合框
    * 从"运行"下拉列表中选择"本地"
    * 启动 （F5 或 Ctrl-F5） 示例
    * 应看到 WiFi 直接示例在 Windows 10 电脑上运行

### <a name="set-up-advertiser-and-connector"></a>将广告和连接器设置
* 在 MBM，选择 (1)"广告"并按"启动播发"按钮

    * MBM 将启动其自身公布 WiFi 直接通道上

        ![广告配置屏幕](../media/SetupWiFiDirect/Advertiser01.png)

        请注意，在应用程序底部的"播发状态"横幅。
    
* 在 Windows 10 PC 上，选择 (2)"连接器"，然后按"启动观察程序"按钮 

    * Windows 10 电脑将启动扫描提供的 WiFi 直接连接
    * 扫描完成后，您应该看到你 MBM"发现的设备"列表中的名称

        ![连接器配置屏幕](../media/SetupWiFiDirect/Connector01.png)

        可以看到列出的两个设备 （我们感兴趣"ale mbm01"），和"DeviceWatcher 枚举已完成"消息。

### <a name="pair-the-devices"></a>对设备
* 在 Windows 10 PC 上，从"发现的设备"列表中选择 MBM ("ale-mbm01"在我们的示例)，然后按"连接"按钮
* 在 Windows 10 PC 上，按"是"以启动配对过程

    ![连接器开始配对](../media/SetupWiFiDirect/Connector02.png)

* MBM 监视器上，您应该使用 PIN 的消息

    ![广告商 PIN 对话框](../media/SetupWiFiDirect/Advertiser02.png)

* 在 Windows 10 电脑，你会看到一个对话框，您需要输入 PIN

    ![连接器 PIN 对话框](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a>通信通道
* 应连接两个设备。 在"连接到设备"列表中的两个屏幕上看到一个随机生成的设备 id (在本示例中的"hqffpzhz.ggg")

    ![广告商连接的设备](../media/SetupWiFiDirect/Advertiser03.png)

    ![连接器连接的设备](../media/SetupWiFiDirect/Connector04.png)

* 现在有完全双工通道 （或套接字） 设置

    * MBM 上设备 ("hqffpzhz.ggg") 从列表中选择"连接到设备"
    * 在"输入一条消息"文本框中键入一条消息
    * 按"发送"按钮
    * 你应看到 Windows 10 电脑正在接收的消息
    * 尝试从 Windows 10 电脑的一条消息发送到 MBM
