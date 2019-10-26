---
title: 带有 Windows 10 IoT Core 的网络3D 打印机
ms.date: 09/05/2017
ms.topic: article
description: 了解如何将 Windows 10 IoT Core 设备转换为打印服务器，并将3D 打印机连接到该服务器。
keywords: windows iot，3D，3D 打印机，打印服务器，网络3D 打印机
ms.openlocfilehash: 3c11756f7832952f816978244d401d1d735a8f80
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918199"
---
# <a name="network-3d-printer-with-windows-10-iot-core"></a>带有 Windows 10 IoT Core 的网络3D 打印机

将 Windows 10 IoT Core 设备转换为打印服务器，并将3D 打印机连接到该服务器。 你将能够从其他设备通过无线方式访问打印机。

## <a name="1-install-windows-10-iot-core-on-your-device"></a>1. 在设备上安装 Windows 10 IoT Core
___
在开始之前，你将需要：

* 安装了最新版本的 Windows 10 IoT Core 内幕预览版的板。 请按照[入门指南](https://developer.microsoft.com/en-us/windows/iot/getstarted)获取 IoT 面板应用并安装 Windows 10 IoT Core。
* 与我们的网络3D 打印机应用兼容的3D 打印机：

    * Lulzbot Taz 6
    * Makergear M2
    * Printrbot 重头戏、Plus 和 Simple
    * Prusa i3 Mk2
    * Ultimaker 原始和原始 +
    * Ultimaker 2 和 2 +
    * Ultimaker 2 扩展和扩展 +
    * CraftBot 2
    * CraftBot PLUS
    * LulzBot 微型
    * Velleman K8200

## <a name="2-connect-your-3d-printer-to-your-device"></a>2. 将3D 打印机连接到设备
___
* 使用 USB 电缆将3D 打印机插入到 Windows 10 IoT 核心板。

    ![将3D 打印机连接到设备](../media/3DPrintServer/connect-3d-printer.png)

* 打开 IoT 面板应用并验证设备是否显示在 "**我的设备**" 选项卡中。

    ![验证设备是否显示在 IoT 面板中](../media/3DPrintServer/selectDevice.png)
    
## <a name="3-deploy-the-network-3d-printer-app"></a>3. 部署网络3D 打印机应用
___
* 在 IoT 面板中，单击 "**试用某些示例**" 部分。
* 选择网络3D 打印机示例应用。

   ![安装3D 网络打印机](../media/3dprintserver/dashboard-samples.png)

* 选择3D 打印机型号，并按 "**部署并运行**" 按钮，将应用部署到 IoT 核心设备。 

    ![安装3D 网络打印机](../media/3dprintserver/dashboard-app.png)

    [Aleph 对象，inc.](https://www.alephobjects.com/)的[LulzBot TAZ 6 映像](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png)是在[CC x SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)下授权的。
    
    如果要安装自定义打印机，请从打印机列表中选择 "自定义" 选项。 自定义三维打印机需要一个名为 PrintDeviceCapabilities 文件的配置 xml，以便正确连接和打印到3d 打印机。 可在此处找到示例 PrintDeviceCapabilities 文件 https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml
   
   在 xml 文件中所需的最小更改是，用特定于兼容打印机的正确值更新下列部分。

处理三维模型时，这些值指定3d 打印机的打印平台尺寸

    <psk3d:Job3DOutputAreaWidth>200000</psk3d:Job3DOutputAreaWidth>
    <psk3d:Job3DOutputAreaDepth>200000</psk3d:Job3DOutputAreaDepth>
    <psk3d:Job3DOutputAreaHeight>200000</psk3d:Job3DOutputAreaHeight>


Psk3dx：波特率 xml 标记中的值控制与 raspberry pi3 中的3d 打印机通信时要使用的特定波特率。 设置特定于3d 打印机的适当波特率。 

```
\<psk3dx:baudrate\>115200</psk3dx:baudrate>
```

PrintDeviceCapabilities xml 中的其他值用于通知3d 打印驱动程序中的切片器，以便使用您的特定兼容打印机来微调其工作方式。
[此处](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings)提供了有关所有这些值的详细信息。

    
    
## <a name="4-add-your-3d-printer"></a>4. 添加3D 打印机
___
* 请切换到 Windows 10 电脑，并 -> **设备**" -> **打印机 & 扫描仪**上的"**设置**"。
* 按 "**添加打印机或扫描程序**"。

     ![Windows 设置添加设备](../media/3dprintserver/add-printer.png)

* 选择3D 打印机并按 "**添加设备**"。 打印机将自动安装。

     ![Windows 设置添加设备](../media/3dprintserver/add-device.png)

恭喜，现在已安装打印机，其行为与使用 USB 电缆连接时的行为完全相同。
现在可以使用[三维生成器](https://msdn.microsoft.com/windows/hardware/mt561568.aspx)打印到它。
