---
title: 设置 Dragonboard
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: 了解如何设置使用 Windows 10 IoT Core 你 Dragonboard。
keywords: Windows 10 IoT Core Dragonboard
ms.custom: RS5
ms.openlocfilehash: 8e4acc77d902124934e1bdae249f76c7f76306a6
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182269"
---
# <a name="setting-up-a-dragonboard"></a>设置 Dragonboard

> [!IMPORTANT]
> 当您正在使用新 Dragonboard 时，它还提供安装 Android。 需要擦除并加载使用 eMMC 闪烁方法的设备。

> [!NOTE]
> 如果正运行带有你 DragonBoard 到任何音频相关的问题，我们建议你通读 Qualcomm 的手册[此处](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf)。 

在设置用于原型制作 Dragonboard，我们建议使用 Windows 10 IoT Core 仪表板。 但是，如果您希望与 Dragonboard 制造，请参阅[IoT Core 交付厂商版指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。 创建者映像不能用于生产。
<br>
> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

## <a name="using-the-dashboard"></a>使用仪表板

Flash，或下载，IoT 核心版到你 MinnowBoard，你将需要：
* 运行 Windows 10 的计算机 
* [Windows 10 IoT 核心版仪表板](https://docs.microsoft.com/windows/iot-core/downloads)
* MicroUSB 电缆
* 外部显示器
* 任何其他外围设备 （例如鼠标、 键盘等）

### <a name="instructions"></a>说明

1. 运行 Windows 10 IoT Core 仪表板，然后单击*设置新设备*。
2. 选择"Qualcomm [DragonBoard 410 c]"作为设备类型。
3. 连接到使用 microUSB 电缆在 compuetr DragonBoard。
4. 挂接到外部显示器你 DragongBoard。
5. 使用 12V 你 Dragonboard 开机 (> 1A) 在按下向上 （+） 的卷的电源按钮。 设备-连接到显示-时应显示一把铁锤、 闪电，齿轮图标的图像。
6. 设备现在应可以看到如下所示的仪表板上。 选择适当的设备。
7. 接受软件 licnse 条款，然后单击**下载并安装**。 你将看到 Windows 10 IoT Core 现在闪到你的设备上。

![在闪存模式下的 DragonBoard](../media/DeviceSetup/db4.png)

## <a name="connect-to-a-network"></a>连接到网络
### <a name="wired-connection"></a>有线的连接
如果你的设备附带的以太网端口或 USB 以太网适配器支持，使您的有线的连接，将附加以太网电缆连接到你的网络。

### <a name="wireless-connection"></a>无线连接
如果你的设备支持的 Wi-fi 连接，并且你已连接到它的显示，你将需要：

1. 转到默认应用程序并单击设置按钮旁边的时钟。
2. 在设置页上选择_网络和 Wi-fi_。
3. 你的设备将开始扫描无线网络。
4. 一旦你的网络会显示此列表中，选择它，然后单击_Connect_。

如果尚未连接显示，并且想要通过 Wi-fi 连接，你将需要：

1. 转到 IoT 仪表板，并单击_我的设备_。
2. 查找从列表中未配置开发板。 其名称开头"AJ_"...(例如 AJ_58EA6C68)。 如果看不到开发板出现几分钟后，请尝试重新启动你的板。
3. 单击_配置设备_并输入你的网络凭据。 这将连接到网络的开发板。

> [!NOTE]
> 您的计算机上的 Wifi 将需要打开以便找到其他网络。

## <a name="connect-to-windows-device-portal"></a>连接到 Windows Device Portal

使用[Windows Device Portal](../manage-your-device/DevicePortal.md)通过 web 浏览器连接你的设备。 设备门户提供有价值的配置和设备管理功能。 

