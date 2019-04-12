---
title: 使用 Windows 10 IoT Core 网络 3D 打印机
author: saraclay
ms.author: saclayt
ms.date: 09/05/17
ms.topic: article
description: 了解有关如何将 Windows 10 IoT Core 设备转换为打印服务器和 3D 打印机连接到它。
keywords: windows iot、 3D、 3D 打印机、 打印服务器、 网络 3D 打印机
ms.openlocfilehash: 7a9bcc7871c62be5a73319ca284127ee4abc42f5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510637"
---
# <a name="network-3d-printer-with-windows-10-iot-core"></a>使用 Windows 10 IoT Core 网络 3D 打印机

将变成打印服务器的 Windows 10 IoT Core 设备并连接到它的 3D 打印机。 你将能够从其他设备以无线方式访问您的打印机。

## <a name="1-install-windows-10-iot-core-on-your-device"></a>1.在设备上安装 Windows 10 IoT 核心版
___
在开始之前，你将需要：

* Windows 10 IoT Core Insider Preview 安装为最新版本看板。 请按照[入门指南](https://developer.microsoft.com/en-us/windows/iot/getstarted)获取 IoT 仪表板应用程序并安装 Windows 10 IoT Core。
* 3D 打印机与我们的网络 3D 打印机应用程序兼容：

    * Lulzbot Taz 6
    * Makergear M2
    * Printrbot Play，加上和简单
    * Prusa i3 Mk2
    * Ultimaker 原始和原始 +
    * Ultimaker 2，2 +
    * Ultimaker 2 扩展和扩展 +
    * CraftBot 2
    * CraftBot 加号
    * LulzBot Mini
    * Velleman K8200

## <a name="2-connect-your-3d-printer-to-your-device"></a>2.在 3D 打印机连接到你的设备
___
* 插件 3D 打印机在将 Windows 10 IoT 核心板使用 USB 电缆。

    ![3D 打印机连接到设备](../media/3DPrintServer/connect-3d-printer.png)

* 打开 IoT 仪表板应用和验证，你的设备显示在**我的设备**选项卡。

    ![验证在 IoT 仪表板中显示你的设备](../media/3DPrintServer/selectDevice.png)
    
## <a name="3-deploy-the-network-3d-printer-app"></a>3.部署网络 3D 打印机应用程序
___
* 在 IoT 仪表板中，单击**尝试一些示例**部分。
* 选择网络 3D 打印机示例应用程序。

   ![安装 3D 网络打印机](../media/3dprintserver/dashboard-samples.png)

* 选择 3D 打印机模型，并按**部署并运行**按钮以将应用部署到 IoT Core 设备。 

    ![安装 3D 网络打印机](../media/3dprintserver/dashboard-app.png)

    [LulzBot TAZ 6 映像](http://devel.lulzbot.com/TAZ/Olive/photos/TAZ_6_Angle_Rock2pus_transparent.png)由[Aleph 对象，Inc.](https://www.alephobjects.com/)进行许可[CC BY SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)。
    
    如果你想要自定义打印机选择"自定义"选项安装来自打印机的列表。 自定义 3d 打印机需要调用 PrintDeviceCapabilities.xml 文件以提供以正确地连接和打印到 3d 打印机配置 xml。 示例 PrintDeviceCapabilities.xml 文件可在此处找到 https://docs.microsoft.com/windows-hardware/drivers/3dprint/sample-configuration-xml
   
   您需要在 xml 文件中进行最小更改，则使用特定于兼容的打印机的正确值更新以下各节。

处理三维模型时，这些值指定为切片器在 3d 打印机的打印平台维度

    <psk3d:Job3DOutputAreaWidth>200000</psk3d:Job3DOutputAreaWidth>
    <psk3d:Job3DOutputAreaDepth>200000</psk3d:Job3DOutputAreaDepth>
    <psk3d:Job3DOutputAreaHeight>200000</psk3d:Job3DOutputAreaHeight>


Psk3dx:baudrate xml 标记中的值控制从 raspberry pi3 3d 打印机与通信时使用的特定波特率。 设置适当的波特率特定于 3d 打印机。 

```
\<psk3dx:baudrate\>115200</psk3dx:baudrate>
```

PrintDeviceCapabilities xml 中的其他值用于通知 3d 打印驱动程序中的切片器，以微调隧道与特定的兼容打印机的工作方式。
所有提供的这些值的详细信息[此处](https://docs.microsoft.com/windows-hardware/drivers/3dprint/slicer-settings)。

    
    
## <a name="4-add-your-3d-printer"></a>4.添加 3D 打印机
___
* 转到 Windows 10 电脑，转到**设置** -> **设备** -> **打印机和扫描仪**。
* 按**添加打印机或扫描仪**。

     ![Windows 设置添加设备](../media/3dprintserver/add-printer.png)

* 选择你的 3D 打印机并按**添加设备**。 将自动安装打印机。

     ![Windows 设置添加设备](../media/3dprintserver/add-device.png)

恭喜现已安装打印机和行为就完全像使用 USB 电缆连接。
现在可以使用打印[3D 生成器](https://msdn.microsoft.com/windows/hardware/mt561568.aspx)。
