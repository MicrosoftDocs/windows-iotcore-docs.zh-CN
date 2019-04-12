---
title: 设置你的设备
ms.author: saclayt
ms.date: 04/10/2018
ms.topic: article
description: 了解有关如何使用 Windows 10 IoT 核心版使用 SD 卡设置你的设备。
keywords: Windows 10 IoT Core、 SD 卡，Windows 10 IoT 核心版仪表板
ms.custom: RS5
ms.openlocfilehash: ece83dcc7f6961a4614db2ee0c6a1331b009bb47
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510644"
---
# <a name="setting-up-your-device"></a>设置你的设备

下面您会发现闪烁，将设备与 Windows 10 IoT Core 的四种不同方式。 基于包含在该图表[建议用于原型制作的看板的列表](PrototypeBoards.md)，按照相应说明进行操作。 使用右侧的列的闪烁这些不同的方法之间进行导航。

> [!IMPORTANT]
> 请不要将 maker 映像用于商品化。 如果 commercializing 设备，则必须使用自定义 FFU 为获得最佳安全性。 在[此处](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。

> [!IMPORTANT]
> 当"格式化此磁盘"弹出最多启动后，请执行_不_格式化该磁盘。 我们正在努力修复此问题。

## <a name="using-the-iot-dashboard-raspberry-pi-minnowboard-nxp"></a>使用 IoT 仪表板 （Raspberry Pi，MinnowBoard，NXP）

> [!Video https://www.youtube.com/embed/JPRUbGIyODY]


> [!IMPORTANT]
> 可以上找到最新的 64 位固件的 MinnowBoard Turbot [MinnowBoard 网站](https://minnowboard.org/tutorials/updating-the-firmware)（MinnowBoard 站点的说明，跳过第 4 步）。

> [!IMPORTANT]
> NXP 仅支持自定义映像。 如果您要查找闪存的自定义映像，请从操作系统内部版本下拉列表中选择"自定义"，按照说明进行操作[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)创建基本映像，并按照下面的说明来完成其余部分。

> [!NOTE]
> 不能用于设置 Raspberry Pi 3B + 使用仪表板。 如果你有 3B + 设备，则必须使用[3B + 技术预览版](https://www.microsoft.com/en-us/software-download/windowsiot)。 请查看[已知限制](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting)的 technical preview，以确定这是否适用于你的开发。

> [!TIP]
> 我们建议使用高性能的 SD 卡，如 SanDisk SD 卡，用于增强的稳定性，以及将设备插入到外部显示器查看默认的应用程序启动。


1. 下载 Windows 10 IoT Core 仪表板[此处](https://docs.microsoft.com/windows/iot-core/downloads)。
2. 下载完成后，打开仪表板，然后单击_设置新设备_和 SD 卡插入到计算机。
3. 填写所有字段所示。
4. 接受软件许可条款，然后单击_下载并安装_。 你将看到 Windows 10 IoT Core 现在闪 SD 卡。


![仪表板的屏幕截图](../../media/DeviceSetup/Dashboard-Screenshot.jpg)
 

## <a name="using-the-iot-dashboard-dragonboard-410c"></a>使用 IoT 仪表板 (DragonBoard 410 c)

> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

> [!TIP]
> 我们建议将设备插入到外部显示器查看默认的应用程序启动。

> [!IMPORTANT]
> 如果您要查找闪存的自定义映像，请从操作系统内部版本下拉列表中选择"自定义"，按照说明进行操作[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)创建基本映像，并按照下面的说明来完成其余部分。

> [!IMPORTANT]
> 当您正在使用新 Dragonboard 时，它还提供安装 Android。 需要擦除并加载使用 eMMC 闪烁方法的设备。

> [!NOTE]
> 如果正运行带有你 DragonBoard 到任何音频相关的问题，我们建议你通读 Qualcomm 的手册[此处](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf)。 

1. 下载 Windows 10 IoT Core 仪表板[此处](https://docs.microsoft.com/windows/iot-core/downloads)。
2. 下载完成后，打开仪表板并选择"Qualcomm DragonBoard 410 c"。 然后_中，以 Windows Insider 登录_。 您需要以 flash DragonBoard 410 c 作为内部人员登录。 
3. Qualcomm 板连接到使用 microUSB 电缆的开发人员计算机。
4. 使用 12V 你 Dragonboard 开机 (> 1A) 在按下向上 （+） 的卷的电源按钮。 设备-连接到显示-时应显示一把铁锤、 闪电，齿轮图标的图像。 
5. 设备现在应可以看到如下所示的仪表板上。 选择适当的设备。
6. 接受软件许可条款，然后单击_下载并安装_。 你将看到 Windows 10 IoT Core 现在闪到你的设备上。


![在闪存模式下的 DragonBoard](../../media/DeviceSetup/db4.png)


## <a name="flashing-with-emmc-for-dragonboard-410c-other-qualcomm-devices"></a>使用 eMMC 闪烁 （适用于 DragonBoard 410 c 其他 Qualcomm 设备)

1. 下载并安装 DragonBoard 更新工具为你[x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip)或[x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip)机。
2. 下载[Windows 10 IoT 核心 DragonBoard FFU](https://developer.microsoft.com/en-us/windows/iot/Downloads)。
3. 双击下载的 ISO 文件并找到已装载的虚拟 CD 的驱动器。 此驱动器将包含的安装程序文件 (.msi);双击该文件。 这将创建一个新的目录下在电脑上 `C:\Program Files (x86)\Microsoft IoT\FFU\`中应看到图像文件、"flash.ffu"。
4. 请确保你 DragonBoard 是在下载模式下设置首次启动板上切换到 USB 启动，如下所示。 然后，连接 DragonBoard 宿主 PC 通过 microUSB 电缆，然后插入到 12V DragonBoard (> 1A) 电源。
5. 启动 DragonBoard 更新工具，它应检测 DragonBoard 连接到您的 PC 的绿色圆圈。 "浏览"到 DragonBoard FFU 下载，然后单击_程序_按钮。
6. 再次单击"浏览"，然后选择"rawprogram0.xml"已在步骤 5 中生成。 然后单击"计划"按钮。
7. 下载完成后，从 USB 启动切换回的看板和切换断开电源供应和 microUSB 线_OFF_。 连接到 DragonBoard 和 rec onnect 电源 HDMI 显示器、 鼠标和键盘。 几分钟后，您应该看到 Windows 10 IoT 核心版默认应用程序。 

![在下载模式下的 DragonBoard](../../media/DeviceSetup/db1.png)

> [!NOTE]
> 请确保设备现已通过重新输入 BIOS 设置，并切换启动驱动器顺序加载从硬盘驱动器而不是从 USB 驱动器启动从 eMMC 内存。


## <a name="flashing-with-emmc-for-up-squared-other-intel-devices"></a>使用 eMMC 闪烁 （对于向上平方，Intel 的其他设备）

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

> [!NOTE]
> 请确保设备现已通过重新输入 BIOS 设置，并切换启动驱动器顺序加载从硬盘驱动器而不是从 USB 驱动器启动从 eMMC 内存。


## <a name="connecting-to-a-network"></a>连接到网络

#### <a name="wired-connection"></a>有线的连接
如果你的设备附带的以太网端口或 USB 以太网适配器支持，使您的有线的连接，将附加以太网电缆连接到你的网络。

#### <a name="wireless-connection"></a>无线连接
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

## <a name="connecting-to-windows-device-portal"></a>连接到 Windows Device Portal

使用[Windows Device Portal](../../manage-your-device/DevicePortal.md)通过 web 浏览器连接你的设备。 设备门户提供有价值的配置和设备管理功能。 

