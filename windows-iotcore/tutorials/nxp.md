---
title: 设置 NXP 设备
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: 了解有关如何设置使用 Windows 10 IoT Core NXP 设备。
keywords: Windows 10 IoT Core NXP
ms.custom: RS5
ms.openlocfilehash: 58bed6c49a5a05afe0852572051132f8731dfcb1
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182169"
---
# <a name="setting-up-a-nxp-device"></a>设置 NXP 设备

## <a name="overview"></a>概述

> [!IMPORTANT]
> 当"格式化此磁盘"弹出最多启动后，请执行_不_格式化该磁盘。 我们正在努力修复此问题。

当设置 NXP 设备用于原型制作，我们建议使用 Windows 10 IoT Core 仪表板。 但是，如果您希望通过 NXP 设备制造，请参阅[IoT Core 交付厂商版指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。 创建者映像不能用于生产。
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a>使用仪表板

Flash，或下载，IoT 核心版到 NXP 设备，你将需要：
* 运行 Windows 10 的计算机 
* [Windows 10 IoT 核心版仪表板](https://docs.microsoft.com/windows/iot-core/downloads)
* 高性能 SD 卡，如 SanDisk SD 卡
* 外部显示器
* 任何其他外围设备 （例如鼠标、 键盘等）

### <a name="instructions"></a>说明

1. 运行 Windows 10 IOT Core 仪表板，然后单击*设置新设备*和 SD 卡插入到计算机。
2. 挂接到外部显示器 NXP 设备。
3. 填写字段。 选择"NXP [i.MX6/i.MX7]"作为设备类型。 请确保为你的设备提供新名称和密码。 否则默认凭据将保持为：

```
Device: minwinpc
Password: p@ssw0rd
```

4. 上传您使用"浏览"函数的预下载的图像文件。 有关详细信息，请参阅我们[NXP 文档](https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/iotnxp)。
5. 接受软件许可条款，然后单击*下载并安装*。 如果一切顺利，您将看到 Windows 10 IoT Core 现在闪 SD 卡。

![仪表板的屏幕截图](../media/DeviceSetup/Dashboard-Screenshot.jpg)


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

