---
title: 设置 Raspberry Pi
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: 了解如何通过 Windows 10 IoT 核心版来设置 Raspberry Pi。
keywords: Windows 10 IoT 核心版, Raspberry Pi
ms.custom: RS5
ms.openlocfilehash: 3269aa2ed102b667519baa9212e604083f910783
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2019
ms.locfileid: "66182189"
---
# <a name="setting-up-a-raspberry-pi"></a>设置 Raspberry Pi

## <a name="overview"></a>概述

> [!NOTE]
> 仪表板不能用来设置 Raspberry Pi 3B+。 如果有 3B+ 设备，则必须使用 [3B+ 技术预览版](https://www.microsoft.com/en-us/software-download/windowsiot)。 请查看技术预览版的[已知限制](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting)，确定它是否适合开发。

> [!IMPORTANT]
> 出现“格式化此磁盘”弹出窗口时，请勿格式化磁盘。  我们正在修复此问题。

设置进行原型制作的 Raspberry Pi 时，建议使用 Windows 10 IoT 核心版仪表板。 但是，若要使用 Raspberry Pi 进行制作，请参阅 [IoT 核心版制造指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。 不能将创客映像用于制作。
<br>
> [!Video https://www.youtube.com/embed/JPRUbGIyODY]

## <a name="using-the-dashboard"></a>使用仪表板

若要将 IoT 核心版刷写或下载到 Raspberry Pi，需要以下项：
* 运行 Windows 10 的计算机 
* [Windows 10 IoT 核心版仪表板](https://docs.microsoft.com/windows/iot-core/downloads)
* 高性能 SD 卡，例如 SanDisk SD 卡
* 外部显示器
* 任何其他外设（例如鼠标、键盘等）

### <a name="instructions"></a>说明

1. 运行 Windows 10 IoT 核心版仪表板，单击“设置新设备”，然后将 SD 卡插入计算机中。 
2. 将 Raspberry Pi 连接到外部显示器。
3. 填写字段。 选择“Broadcomm [Raspberry Pi 2 & 3]”作为设备类型。 确保为设备提供新的名称和密码。 否则，默认凭据仍旧为：

```
Device: minwinpc
Password: p@ssw0rd
```

4. 接受软件许可条款，然后单击“下载并安装”  。 如果一切正常，则可以看到 Windows 10 IoT 核心版此时正刷写 SD 卡。

![仪表板屏幕截图](../media/DeviceSetup/Dashboard-Screenshot.jpg)

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
