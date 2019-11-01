---
title: 设置 Qualcomm 设备
ms.date: 05/22/2019
ms.topic: article
description: 了解如何通过 Windows 10 IoT 核心版来设置 Qualcomm 设备。
keywords: Windows 10 IoT 核心版, Qualcomm
ms.custom: RS5
ms.openlocfilehash: 9c27f6011503ea557687817bc044b08695ee7add
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918649"
---
# <a name="setting-up-a-qualcomm-device"></a>设置 Qualcomm 设备

若要使用 Qualcomm 设备进行制作，请参阅 [IoT 核心版制造指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。 不能将创客映像用于制作。

> [!NOTE]
> 确保设备现在是从 eMMC 内存启动，方法是：再次进入 BIOS 设置，切换驱动器启动顺序，使之从硬盘驱动器加载，而不是从 USB 盘加载。

## <a name="using-emmc"></a>使用 eMMC

1. 为 [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) 或 [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) 计算机下载并安装 DragonBoard Update Tool。
2. 下载 [Windows 10 IoT 核心版 DragonBoard FFU](https://docs.microsoft.com/en-us/windows/iot-core/downloads)。
3. 双击下载的 ISO 文件，找到装载的虚拟 CD 驱动器。 此驱动器将包含一个安装程序文件 (.msi)；双击它。 这样会在电脑中的 `C:\Program Files (x86)\Microsoft IoT\FFU\` 下创建一个新目录，其中可以看到映像文件“flash.ffu”。
4. 确保 DragonBoard 处于下载模式，方法是将板上的第一个启动开关设置为“USB 启动”，如下所示。 接着通过 microUSB 电缆将 DragonBoard 连接到主机，然后将 DragonBoard 连接到 12V (> 1A) 电源。
5. 启动 DragonBoard Update Tool，该工具会通过一个绿色圆圈来表示已检测到 DragonBoard 连接到电脑。 “浏览”到 DragonBoard 的已下载 FFU，然后单击“程序”按钮。 
6. 再次单击“浏览”，选择在步骤 5 创建的“rawprogram0.xml”。 然后单击“程序”按钮。
7. 下载完以后，请断开板的电源和 microUSB 电缆连接，将 USB 启动开关切换回到“关”的位置。  将 HDMI 显示器、鼠标和键盘连接到 DragonBoard，然后重新连接电源。 数分钟后，应该会看到 Windows 10 IoT 核心版默认应用程序。 

![处于下载模式的 DragonBoard](../media/DeviceSetup/db1.png)

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



