---
title: 设置 Intel 设备
ms.author: saclayt
ms.date: 05/22/2019
ms.topic: article
description: 了解有关如何设置 Intel 设备使用 Windows 10 IoT Core。
keywords: Windows 10 IoT Core Intel
ms.custom: RS5
ms.openlocfilehash: a42771d82ffbebee9a45a72c5256479f5f611388
ms.sourcegitcommit: 8aadc776da7b473159f9023cd555145819e7e952
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/23/2019
ms.locfileid: "66182179"
---
# <a name="setting-up-an-intel-device"></a>设置 Intel 设备

如果您希望通过 Qualcomm 设备制造，请参阅[IoT Core 交付厂商版指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。 创建者映像不能用于生产。

> [!NOTE]
> 请确保设备现已通过重新输入 BIOS 设置，并切换启动驱动器顺序加载从硬盘驱动器而不是从 USB 驱动器启动从 eMMC 内存。

## <a name="using-emmc"></a>使用 eMMC

1. 下载并安装[Windows 评估和部署工具包](https://docs.microsoft.com/windows-hardware/get-started/adk-install)与正在运行的 Windows 10 的相关版本。
2. 将 USB 驱动器插入计算机。
3. 创建 USB 可启动的 WinPE 映像：
4. 开始部署和映像的工具环境`(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)`以管理员身份。
5. 创建 Windows PE 文件的工作副本。 指定任一 x86 amd64 或 ARM: `Copype amd64 C:\WINPE_amd64`
6. 将 Windows PE 安装到 USB 闪存驱动器，指定以下的 WinPE 驱动器号。 可找到更多信息[此处](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive)。 `MMakeWinPEMedia /UFD C:\WinPE_amd64 P:`
7. 下载[Windows 10 IoT Core 映像](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true)通过双击已下载的 ISO 文件并查找装载的虚拟 CD 的驱动器。
8. 此驱动器将包含的安装文件 (.msi);双击它。 这将在 C:\Program Files (x86) \Microsoft IoT\FFU\ 否则 d 在其中查看图像文件，在电脑上创建一个新目录"flash.ffu"。
9. 下载、 解压缩并复制[eMMC 安装程序脚本](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip)到 USB 设备的根目录，以及设备的 FFU。
10. 连接到 USB 集线器的 USB 驱动器、 鼠标和键盘。 将向你的设备的 HDMI 显示后，该设备附加到 USB 集线器，并在设备的电源线。
11. 请转到设备的 BIOS 设置。 选择*Windows*作为从 uSB 驱动器启动操作系统并将设备设置。 当系统重新启动时，你会看到 WinPE 命令提示符。 WinPE 提示符切换到 USB 驱动器。 这通常是 c： 或 d:，但可能需要尝试其他驱动器盘符。
12. 运行 eMMC 安装程序脚本，这将在 Windows 10 IoT Core 映像安装到设备的 eMMC 内存。 操作完成时，按任意键，并运行`wpeutil reboot`。 系统应引导到 Windows 10 IoT 核心版、 启动配置过程中，并加载默认应用程序。

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


