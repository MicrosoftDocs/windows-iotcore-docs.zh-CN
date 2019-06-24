---
title: 设置设备
ms.author: saclayt
ms.date: 04/10/2018
ms.topic: article
description: 了解如何使用 SD 卡通过 Windows 10 IoT 核心版来设置设备。
keywords: Windows 10 IoT 核心版, SD 卡, Windows 10 IoT 核心版仪表板
ms.custom: RS5
ms.openlocfilehash: ece83dcc7f6961a4614db2ee0c6a1331b009bb47
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2019
ms.locfileid: "60167706"
---
# <a name="setting-up-your-device"></a>设置设备

下面介绍如何通过四种不同的方式使用 Windows 10 IoT 核心版来刷写设备。 根据[建议进行原型制作的板的列表](PrototypeBoards.md)中包含的图表，按相应的说明操作。 使用正确的列在这些不同的刷写方法之间导航。

> [!IMPORTANT]
> 请勿将创客映像用于商业化。 若要将某个设备商业化，必须使用自定义 FFU 以确保最佳安全性。 在[此处](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。

> [!IMPORTANT]
> 出现“格式化此磁盘”弹出窗口时，请勿格式化磁盘。  我们正在修复此问题。

## <a name="using-the-iot-dashboard-raspberry-pi-minnowboard-nxp"></a>使用 IoT 仪表板（Raspberry Pi、MinnowBoard、NXP）

> [!Video https://www.youtube.com/embed/JPRUbGIyODY]


> [!IMPORTANT]
> MinnowBoard Turbot 的最新 64 位固件可以在 [MinnowBoard 网站](https://minnowboard.org/tutorials/updating-the-firmware)上找到（跳过 MinnowBoard 站点的说明中的步骤 4）。

> [!IMPORTANT]
> NXP 仅支持自定义映像。 若要刷写自定义映像，请从 OS 内部版本下拉列表中选择“自定义”，按[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)的说明创建基本映像，然后按下面的其余说明完成操作。

> [!NOTE]
> 仪表板不能用来设置 Raspberry Pi 3B+。 如果有 3B+ 设备，则必须使用 [3B+ 技术预览版](https://www.microsoft.com/en-us/software-download/windowsiot)。 请查看技术预览版的[已知限制](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting)，确定它是否适合开发。

> [!TIP]
> 建议使用高性能 SD 卡（例如 SanDisk SD 卡），这样可以增强稳定性，并且可以将设备连接到外部显示器来查看默认的应用程序启动。


1. 在[此处](https://docs.microsoft.com/windows/iot-core/downloads)下载 Windows 10 IoT 核心版仪表板。
2. 下载后，请打开仪表板，单击“设置新设备”，然后将 SD 卡插入计算机中。 
3. 按指示填写所有字段。
4. 接受软件许可条款，然后单击“下载并安装”  。 可以看到 Windows 10 IoT 核心版此时正刷写 SD 卡。


![仪表板屏幕截图](../../media/DeviceSetup/Dashboard-Screenshot.jpg)
 

## <a name="using-the-iot-dashboard-dragonboard-410c"></a>使用 IoT 仪表板 (DragonBoard 410c)

> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

> [!TIP]
> 建议将设备连接到外部显示器来查看默认的应用程序启动。

> [!IMPORTANT]
> 若要刷写自定义映像，请从 OS 内部版本下拉列表中选择“自定义”，按[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)的说明创建基本映像，然后按下面的其余说明完成操作。

> [!IMPORTANT]
> 使用新的 Dragonboard 时，请注意，它已经安装了 Android。 需使用 eMMC 刷写方法擦除并加载设备。

> [!NOTE]
> 如果 DragonBoard 出现任何音频相关问题，建议通读[此处](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf)提供的 Qualcomm 的手册。 

1. 在[此处](https://docs.microsoft.com/windows/iot-core/downloads)下载 Windows 10 IoT 核心版仪表板。
2. 下载后，请打开仪表板，选择“Qualcomm DragonBoard 410c”。 然后，以 Windows 预览体验成员身份登录  。 必须以预览体验成员身份登录才能刷写 DragonBoard 410c。 
3. 使用 microUSB 电缆将 Qualcomm 板连接到开发人员计算机。
4. 使用 12V (>1A) 电源在按住调高音量 (+) 按钮的情况下将 Dragonboard 通电。 此设备在连接到显示器的情况下应该显示包含一个锤子、一个闪电和一个齿轮的图像。 
5. 此设备现在应该在仪表板上可见，如下所示。 选择适当的设备。
6. 接受软件许可条款，然后单击“下载并安装”  。 可以看到 Windows 10 IoT 核心版此时正刷写到设备上。


![处于刷写模式的 DragonBoard](../../media/DeviceSetup/db4.png)


## <a name="flashing-with-emmc-for-dragonboard-410c-other-qualcomm-devices"></a>使用 eMMC 进行刷写（适用于 DragonBoard 410c 和其他 Qualcomm 设备）

1. 为 [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) 或 [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) 计算机下载并安装 DragonBoard Update Tool。
2. 下载 [Windows 10 IoT 核心版 DragonBoard FFU](https://developer.microsoft.com/en-us/windows/iot/Downloads)。
3. 双击下载的 ISO 文件，找到装载的虚拟 CD 驱动器。 此驱动器将包含一个安装程序文件 (.msi)；双击它。 这样会在电脑中的 `C:\Program Files (x86)\Microsoft IoT\FFU\` 下创建一个新目录，其中可以看到映像文件“flash.ffu”。
4. 确保 DragonBoard 处于下载模式，方法是将板上的第一个启动开关设置为“USB 启动”，如下所示。 接着通过 microUSB 电缆将 DragonBoard 连接到主机，然后将 DragonBoard 连接到 12V (> 1A) 电源。
5. 启动 DragonBoard Update Tool，该工具会通过一个绿色圆圈来表示已检测到 DragonBoard 连接到电脑。 “浏览”到 DragonBoard 的已下载 FFU，然后单击“程序”按钮。 
6. 再次单击“浏览”，选择在步骤 5 创建的“rawprogram0.xml”。 然后单击“程序”按钮。
7. 下载完以后，请断开板的电源和 microUSB 电缆连接，将 USB 启动开关切换回到“关”的位置。  将 HDMI 显示器、鼠标和键盘连接到 DragonBoard，然后重新连接电源。 数分钟后，应该会看到 Windows 10 IoT 核心版默认应用程序。 

![处于下载模式的 DragonBoard](../../media/DeviceSetup/db1.png)

> [!NOTE]
> 确保设备现在是从 eMMC 内存启动，方法是：再次进入 BIOS 设置，切换驱动器启动顺序，使之从硬盘驱动器加载，而不是从 USB 盘加载。


## <a name="flashing-with-emmc-for-up-squared-other-intel-devices"></a>使用 eMMC 进行刷写（适用于 Up Squared 和其他 Intel 设备）

1. 下载并安装 [Windows 评估和部署工具包](https://docs.microsoft.com/windows-hardware/get-started/adk-install)，其中包含要运行的 Windows 10 相关版本。
2. 将 USB 盘插入计算机中。
3. 创建可从 USB 启动的 WinPE 映像：
4. 以管理员身份启动 Deployment and Imaging Tools Environment `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)`。
5. 创建 Windows PE 文件的工作副本。 指定 x86、amd64 或 ARM：`Copype amd64 C:\WINPE_amd64`
6. 将 Windows PE 安装到 U 盘，指定下面的 WinPE 驱动器号。 可以在[此处](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive)查找详细信息。 `MMakeWinPEMedia /UFD C:\WinPE_amd64 P:`
7. 下载 [Windows 10 IoT 核心版映像](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true)，方法是：双击下载的 ISO 文件，找到装载的虚拟 CD 驱动器。
8. 此驱动器将包含一个安装文件 (.msi)；双击它。 这样会在电脑中的 C:\Program Files (x86)\Microsoft IoT\FFU\ 下创建一个新目录，其中可以看到映像文件“flash.ffu”。
9. 下载 [eMMC 安装程序脚本](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip)，将其解压缩后连同设备的 FFU 复制到 USB 设备的根目录。
10. 将 U 盘、鼠标和键盘连接到 USB 集线器。 将 HDMI 显示器连接到设备，将设备连接到 USB 集线器，并将电源线连接到设备。
11. 转到设备的 BIOS 设置。 选择 *Windows* 作为操作系统，将设备设置为从 U 盘启动。 当系统重启后，会看到 WinPE 命令提示符。 从 WinPE 命令提示符切换到 U 盘。 该 U 盘通常为 C: 或 D:，但你可能需要尝试其他驱动器号。
12. 运行 eMMC 安装程序脚本，将 Windows 10 IoT 核心版映像安装到设备的 eMMC 内存。 完成后，按任意键运行 `wpeutil reboot`。 系统会引导到 Windows 10 IoT 核心版中，开始配置过程，并加载默认应用程序。

> [!NOTE]
> 确保设备现在是从 eMMC 内存启动，方法是：再次进入 BIOS 设置，切换驱动器启动顺序，使之从硬盘驱动器加载，而不是从 USB 盘加载。


## <a name="connecting-to-a-network"></a>连接到网络

#### <a name="wired-connection"></a>有线连接
如果设备带有以太网端口或 USB 以太网适配器支持，因此可以启用有线连接，则请连接一条以太网电缆，通过它连接到网络。

#### <a name="wireless-connection"></a>无线连接
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

## <a name="connecting-to-windows-device-portal"></a>连接到 Windows 设备门户

使用 [Windows 设备门户](../../manage-your-device/DevicePortal.md)，通过 Web 浏览器来连接设备。 设备门户提供重要的配置和设备管理功能。 

