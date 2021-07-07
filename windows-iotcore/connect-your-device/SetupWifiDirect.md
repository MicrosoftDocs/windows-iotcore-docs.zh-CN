---
title: 在 Iot 核心设备上Windows 10 WiFi Direct
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何在具有已启用 USB wifi 适配器的设备上设置、测试和使用 wifi direct。
keywords: windows iot， wifi direct， 安装程序， wifi， 设备
ms.openlocfilehash: 2ddf06dba6fe30ed7d9152b4500177e73e9243d4
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229225"
---
# <a name="using-wifi-direct-on-your-windows-10-iot-core-device"></a>在设备设备上Windows 10 IoT 核心版 WiFi Direct

使用已启用 WiFi Direct 的 USB wiFi 适配器Windows 10 IoT 核心版设备支持 WiFi Direct。 若要确保启用 WiFi Direct，需要确保两项内容正确：
* USB WiFi 适配器的硬件需要支持 WiFi Direct，
* USB WiFi 适配器的相应驱动程序需要支持 WiFi Direct。 

WiFi Direct 提供 WiFi 设备到设备连接的解决方案，无需无线接入点 (无线 AP) 来设置连接。 查看以下资源中提供的 UWP [Windows。Devices.WiFiDirect 命名空间](https://msdn.microsoft.com/library/windows/apps/windows.devices.wifidirect.aspx)，查看可以使用 WiFiDirect 执行哪些操作。

## <a name="supported-adapters"></a>支持的适配器

可以在支持的硬件页上找到已在 Windows 10 IoT 核心版测试的[WiFi 适配器](../learn-about-hardware/HardwareCompatList.md)列表。 

## <a name="basic-sample-for-wifi-direct"></a>WiFi Direct 的基本示例

可以使用 WiFi Direct UWP 示例 轻松测试 WiFi Direct [功能](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect)。 我们将使用 C# 版本并运行两个设备的示例。

### <a name="set-up-the-two-devices"></a>设置两个设备
* MinnowBoardMax (MBM) Windows 10 IoT 核心版 (请参阅此处的说明，) CanaKit WiFi 适配器
* 连接监视器、键盘和鼠标移动到 MBM
* 运行Windows 10周年更新Windows 10电脑。 电脑 (或笔记本电脑) 需要具有 WiFi Direct 支持 (例如 Microsoft Surface) 
* 在 Visual Studio 计算机上安装 Windows 10 2017
* 在此处的根目录 (或下载 wiFi Direct [UWP](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WiFiDirect) GitHub[示例) 。](https://github.com/Microsoft/Windows-universal-samples)
* 在 2017 年 1 月加载 WiFi Direct UWP 示例的 C# Visual Studio版本

#### <a name="run-the-sample-on-the-two-devices"></a>在两个设备上运行示例
* 编译示例，在 MBM 上部署/运行它：

    * 将"解决方案平台"组合框设置为"x86"
    * 从"运行"下拉列表中选择"远程计算机"
    * 通过按 Ctrl-F5 或从"调试"菜单中选择"启动而不调试"，在 M (BM 上启动示例，而无需) 
    * 应会看到 WiFi Direct 示例在连接到 MBM 的监视器上运行
* 编译示例，在电脑上部署/Windows 10它：
    * 将"解决方案平台"组合框设置为"x86"
    * 从"运行"下拉列表中选择"本地"
    * 启动示例 (F5 或 Ctrl-F5) 
    * 应会看到 WiFi Direct 示例在 Windows 10 电脑上运行

### <a name="set-up-advertiser-and-connector"></a>设置用户和连接器
* 在 MBM 上，选择" (1") "，然后按"开始播发"按钮

    * MBM 将在 WiFi Direct 频道上开始广告自身

        !["配置"屏幕](../media/SetupWiFiDirect/Advertiser01.png)

        请注意应用底部的"播发状态&quot;横幅。
    
* 在 Windows 10 电脑上，选择&quot; (2") "连接器"，然后按"启动观察程序"按钮 

    * Windows 10电脑将开始扫描可用的 WiFi Direct 连接
    * 扫描完成后，应在"发现的设备"列表中看到 MBM 的名称

        ![连接器配置屏幕](../media/SetupWiFiDirect/Connector01.png)

        可以看到两个设备 (我们感兴趣的"ale-mbm01") 和"DeviceWatcher 枚举已完成"消息。

### <a name="pair-the-devices"></a>对设备
* 在 Windows 10 电脑上，从"发现的设备"列表中选择示例 ("ale-mbm01"中的 MBM) ，然后按"连接"按钮
* 在 Windows 10 电脑上，按"是"启动配对过程

    ![连接器开始配对](../media/SetupWiFiDirect/Connector02.png)

* 在 MBM 监视器上，应该会显示一条包含 PIN 的消息

    !["安装 PIN"对话框](../media/SetupWiFiDirect/Advertiser02.png)

* 在Windows 10电脑上，应会看到需要输入 PIN 的对话框

    !["连接器 PIN"对话框](../media/SetupWiFiDirect/Connector03.png)

### <a name="talk-on-the-channel"></a>在频道上交谈
* 两个设备应已连接。 在"已连接设备"列表的两个屏幕上 (示例中会看到随机生成的设备 ID) "hqffpzhz.ggg"

    ![已连接的设备](../media/SetupWiFiDirect/Advertiser03.png)

    ![连接器连接设备](../media/SetupWiFiDirect/Connector04.png)

* 现在，你已设置一个全双工 (或) 通道

    * 在 MBM 上，从" (&quot;列表中选择&quot;hqffpzhz.ggg") 设备
    * 在"输入消息"文本框中键入消息
    * 按"发送"按钮
    * 应会看到从计算机接收Windows 10消息
    * 尝试将消息从 Windows 10 PC 发送到 MBM
