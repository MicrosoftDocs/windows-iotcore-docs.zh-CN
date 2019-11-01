---
title: 设置 Dragonboard
ms.date: 05/22/2019
ms.topic: article
description: 了解如何通过 Windows 10 IoT 核心版来设置 Dragonboard。
keywords: Windows 10 IoT 核心版, Dragonboard
ms.custom: RS5
ms.openlocfilehash: 0233ef4380cfb8f9fadbbd64d8e7e594cf11b0b1
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918662"
---
# <a name="setting-up-a-dragonboard"></a>设置 Dragonboard

> [!IMPORTANT]
> 使用新的 Dragonboard 时，请注意，它已经安装了 Android。 需使用[此处](https://docs.microsoft.com/en-us/windows/iot-core/tutorials/qualcomm)的 eMMC 刷写方法擦除并加载设备。

> [!NOTE]
> 如果 DragonBoard 出现任何音频相关问题，建议通读[此处](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf)提供的 Qualcomm 的手册。 

设置进行原型制作的 Dragonboard 时，建议使用 Windows 10 IoT 核心版仪表板。 但是，若要使用 Dragonboard 进行制作，请参阅 [IoT 核心版制造指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。 不能将创客映像用于制作。
<br>
> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

## <a name="using-the-dashboard"></a>使用仪表板

若要将 IoT 核心版刷写或下载到 MinnowBoard，需要以下项：
* 运行 Windows 10 的计算机 
* [Windows 10 IoT 核心版仪表板](https://docs.microsoft.com/windows/iot-core/downloads)
* MicroUSB 电缆
* 外部显示器
* 任何其他外设（例如鼠标、键盘等）

### <a name="instructions"></a>说明

1. 运行 Windows 10 IoT 核心版仪表板，然后单击“设置新设备”。 
2. 选择“Qualcomm [DragonBoard 410c]”作为设备类型。
3. 使用 microUSB 电缆将 DragonBoard 连接到计算机。
4. 将 DragongBoard 连接到外部显示器。
5. 使用 12V (>1A) 电源在按住调高音量 (+) 按钮的情况下将 Dragonboard 通电。 此设备在连接到显示器的情况下应该显示包含一个锤子、一个闪电和一个齿轮的图像。
6. 此设备现在应该在仪表板上可见，如下所示。 选择适当的设备。
7. 接受软件许可条款，然后单击“下载并安装”  。 可以看到 Windows 10 IoT 核心版此时正刷写到设备上。

![处于刷写模式的 DragonBoard](../media/DeviceSetup/db4.png)

## <a name="connect-to-a-network"></a>连接到网络
### <a name="wired-connection"></a>有线连接
如果设备带有以太网端口或 USB 以太网适配器支持，因此可以启用有线连接，则请连接一条以太网电缆，通过它连接到网络。

### <a name="wireless-connection"></a>无线连接
如果设备支持 Wi-Fi 连接，而你已将显示器连接到设备，则需执行以下操作：

1. 进入默认应用程序，单击时钟旁边的设置按钮。
2. 在设置页上，选择“网络和 Wi-Fi”。 
3. 设备将开始扫描无线网络。
4. 你的网络显示在此列表中以后，将其选中，然后单击“连接”。 

如果尚未连接显示器，因此希望通过 Wi-Fi 进行连接，则需执行以下操作：

1. 转到 IoT 仪表板，单击“我的设备”。 
2. 从列表中找到你的未配置的板。 其名称会以“AJ_”开头（例如 AJ_58EA6C68）。 如果数分钟后仍没有看到自己的板显示，则请尝试重启你的板。
3. 单击“配置设备”，然后输入网络凭据。  这样就会将板连接到网络。

> [!NOTE]
> 需启用计算机上的 Wi-Fi 才能找到其他网络。

## <a name="connect-to-windows-device-portal"></a>连接到 Windows 设备门户

使用 [Windows 设备门户](../manage-your-device/DevicePortal.md)，通过 Web 浏览器来连接设备。 设备门户提供重要的配置和设备管理功能。 

