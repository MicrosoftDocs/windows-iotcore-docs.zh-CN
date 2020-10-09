---
title: 设置 Intel 设备
ms.date: 05/22/2019
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何通过 Windows 10 IoT 核心版来设置 Intel 设备。 使用 eMMC、连接到网络，并连接到 Windows 设备门户。
keywords: Windows 10 IoT 核心版, Intel
ms.custom: RS5
ms.openlocfilehash: a3d3a35d99dd4e35b03578a5e33b5997738294f6
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91657163"
---
# <a name="setting-up-an-intel-device"></a>设置 Intel 设备

若要使用 Qualcomm 设备进行制作，请参阅 [IoT 核心版制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。 不能将创客映像用于制作。

> [!NOTE]
> 确保设备现在是从 eMMC 内存启动，方法是：再次进入 BIOS 设置，切换驱动器启动顺序，使之从硬盘驱动器加载，而不是从 USB 盘加载。

## <a name="using-emmc"></a>使用 eMMC

1. 下载并安装 [Windows 评估和部署工具包](https://docs.microsoft.com/windows-hardware/get-started/adk-install)，其中包含要运行的 Windows 10 相关版本。
2. 将 USB 盘插入计算机中。
3. 创建可从 USB 启动的 WinPE 映像：
4. 以管理员身份启动 Deployment and Imaging Tools Environment `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)`。
5. 创建 Windows PE 文件的工作副本。 指定 x86、amd64 或 ARM：`Copype amd64 C:\WINPE_amd64`
6. 将 Windows PE 安装到 U 盘，指定下面的 WinPE 驱动器号。 可在[此处](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive)找到详细信息。 `MakeWinPEMedia /UFD C:\WinPE_amd64 P:`
7. 下载 [Windows 10 IoT 核心版映像](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true)，方法是：双击下载的 ISO 文件，找到装载的虚拟 CD 驱动器。
8. 此驱动器将包含一个安装文件 (.msi)；双击它。 这样会在电脑中的 C:\Program Files (x86)\Microsoft IoT\FFU\ 下创建一个新目录，其中可以看到映像文件“flash.ffu”。
9. 下载 [eMMC 安装程序脚本](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip)，将其解压缩后连同设备的 FFU 复制到 USB 设备的根目录。
10. 将 U 盘、鼠标和键盘连接到 USB 集线器。 将 HDMI 显示器连接到设备，将设备连接到 USB 集线器，并将电源线连接到设备。
11. 转到设备的 BIOS 设置。 选择 *Windows* 作为操作系统，将设备设置为从 U 盘启动。 当系统重启后，会看到 WinPE 命令提示符。 从 WinPE 命令提示符切换到 U 盘。 该 U 盘通常为 C: 或 D:，但你可能需要尝试其他驱动器号。
12. 运行 eMMC 安装程序脚本，将 Windows 10 IoT 核心版映像安装到设备的 eMMC 内存。 完成后，按任意键运行 `wpeutil reboot`。 系统会引导到 Windows 10 IoT 核心版中，开始配置过程，并加载默认应用程序。

## <a name="connect-to-a-network"></a>连接到网络

### <a name="wired-connection"></a>有线连接
如果设备带有以太网端口或 USB 以太网适配器支持，因此可以启用有线连接，则请连接一条以太网电缆，通过它连接到网络。

### <a name="wireless-connection"></a>无线连接
如果设备支持 Wi-Fi 连接，而你已将显示器连接到设备，则需执行以下操作：

1. 进入默认应用程序，单击时钟旁边的设置按钮。
2. 在设置页上，选择“网络和 Wi-Fi”。__
3. 设备将开始扫描无线网络。
4. 你的网络显示在此列表中以后，将其选中，然后单击“连接”。__

如果尚未连接显示器，因此希望通过 Wi-Fi 进行连接，则需执行以下操作：

1. 转到 IoT 仪表板，单击“我的设备”。__
2. 从列表中找到你的未配置的板。 其名称会以“AJ_”开头（例如 AJ_58EA6C68）。 如果数分钟后仍没有看到自己的板显示，则请尝试重启你的板。
3. 单击“配置设备”，然后输入网络凭据。__ 这样就会将板连接到网络。

> [!NOTE]
> 需启用计算机上的 Wi-Fi 才能找到其他网络。

## <a name="connect-to-windows-device-portal"></a>连接到 Windows 设备门户

使用 [Windows 设备门户](../manage-your-device/DevicePortal.md)，通过 Web 浏览器来连接设备。 设备门户提供重要的配置和设备管理功能。 


