---
title: Qualcomm 设备设置
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: 了解有关如何设置使用 Windows 10 IoT Core Qualcomm 设备。
keywords: Windows 10 IoT Core Qualcomm
ms.custom: RS5
ms.openlocfilehash: 02f6c013c428a271d3b3956c88edc1ce8f4fdbf2
ms.sourcegitcommit: fa4a29fcd5af464924a0a5ab581f08f631a3ad72
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835617"
---
# <a name="setting-up-a-qualcomm-device"></a>Qualcomm 设备设置

如果您希望通过 Qualcomm 设备制造，请参阅[IoT Core 交付厂商版指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。 创建者映像不能用于生产。

> [!NOTE]
> 请确保设备现已通过重新输入 BIOS 设置，并切换启动驱动器顺序加载从硬盘驱动器而不是从 USB 驱动器启动从 eMMC 内存。

## <a name="using-emmc"></a>使用 eMMC

1. 下载并安装 DragonBoard 更新工具为你[x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip)或[x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip)机。
2. 下载[Windows 10 IoT 核心 DragonBoard FFU](https://docs.microsoft.com/en-us/windows/iot-core/downloads)。
3. 双击下载的 ISO 文件并找到已装载的虚拟 CD 的驱动器。 此驱动器将包含的安装程序文件 (.msi);双击该文件。 这将创建一个新的目录下在电脑上 `C:\Program Files (x86)\Microsoft IoT\FFU\`中应看到图像文件、"flash.ffu"。
4. 请确保你 DragonBoard 是在下载模式下设置首次启动板上切换到 USB 启动，如下所示。 然后，将 DragonBoard 连接到宿主 PC 通过 microUSB 电缆，然后插入到 12V DragonBoard (> 1A) 电源。
5. 启动 DragonBoard 更新工具，它应检测 DragonBoard 连接到您的 PC 的绿色圆圈。 "浏览"到 DragonBoard FFU 下载，然后单击_程序_按钮。
6. 再次单击"浏览"，然后选择"rawprogram0.xml"已在步骤 5 中生成。 然后单击"计划"按钮。
7. 下载完成后，从 USB 启动切换回的看板和切换断开电源供应和 microUSB 线_OFF_。 HDMI 显示、 鼠标和键盘连接到 DragonBoard 并重新连接电源。 几分钟后，您应该看到 Windows 10 IoT 核心版默认应用程序。 

![在下载模式下的 DragonBoard](../media/DeviceSetup/db1.png)

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



