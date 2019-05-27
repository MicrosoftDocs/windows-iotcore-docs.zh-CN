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
# <a name="setting-up-an-intel-device"></a><span data-ttu-id="bbff5-104">设置 Intel 设备</span><span class="sxs-lookup"><span data-stu-id="bbff5-104">Setting up an Intel device</span></span>

<span data-ttu-id="bbff5-105">如果您希望通过 Qualcomm 设备制造，请参阅[IoT Core 交付厂商版指南](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="bbff5-105">If you're looking to manufacture with a Qualcomm device, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="bbff5-106">创建者映像不能用于生产。</span><span class="sxs-lookup"><span data-stu-id="bbff5-106">You cannot use maker images for manufacturing.</span></span>

> [!NOTE]
> <span data-ttu-id="bbff5-107">请确保设备现已通过重新输入 BIOS 设置，并切换启动驱动器顺序加载从硬盘驱动器而不是从 USB 驱动器启动从 eMMC 内存。</span><span class="sxs-lookup"><span data-stu-id="bbff5-107">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>

## <a name="using-emmc"></a><span data-ttu-id="bbff5-108">使用 eMMC</span><span class="sxs-lookup"><span data-stu-id="bbff5-108">Using eMMC</span></span>

1. <span data-ttu-id="bbff5-109">下载并安装[Windows 评估和部署工具包](https://docs.microsoft.com/windows-hardware/get-started/adk-install)与正在运行的 Windows 10 的相关版本。</span><span class="sxs-lookup"><span data-stu-id="bbff5-109">Download and install the [Windows Assessment and Deployment kit](https://docs.microsoft.com/windows-hardware/get-started/adk-install) with the correlating version of Windows 10 you're running.</span></span>
2. <span data-ttu-id="bbff5-110">将 USB 驱动器插入计算机。</span><span class="sxs-lookup"><span data-stu-id="bbff5-110">Insert a USB drive into your machine.</span></span>
3. <span data-ttu-id="bbff5-111">创建 USB 可启动的 WinPE 映像：</span><span class="sxs-lookup"><span data-stu-id="bbff5-111">Create a USB-bootable WinPE image:</span></span>
4. <span data-ttu-id="bbff5-112">开始部署和映像的工具环境`(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)`以管理员身份。</span><span class="sxs-lookup"><span data-stu-id="bbff5-112">Start the Deployment and Imaging Tools Environment `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)` as an administrator.</span></span>
5. <span data-ttu-id="bbff5-113">创建 Windows PE 文件的工作副本。</span><span class="sxs-lookup"><span data-stu-id="bbff5-113">Create a working copy of the Windows PE files.</span></span> <span data-ttu-id="bbff5-114">指定任一 x86 amd64 或 ARM: `Copype amd64 C:\WINPE_amd64`</span><span class="sxs-lookup"><span data-stu-id="bbff5-114">Specify either x86, amd64 or ARM: `Copype amd64 C:\WINPE_amd64`</span></span>
6. <span data-ttu-id="bbff5-115">将 Windows PE 安装到 USB 闪存驱动器，指定以下的 WinPE 驱动器号。</span><span class="sxs-lookup"><span data-stu-id="bbff5-115">Install Windows PE to the USB flash drive, specifying the WinPE drive letter below.</span></span> <span data-ttu-id="bbff5-116">可找到更多信息[此处](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive)。</span><span class="sxs-lookup"><span data-stu-id="bbff5-116">More information can be found [here](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive).</span></span> `MMakeWinPEMedia /UFD C:\WinPE_amd64 P:`
7. <span data-ttu-id="bbff5-117">下载[Windows 10 IoT Core 映像](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true)通过双击已下载的 ISO 文件并查找装载的虚拟 CD 的驱动器。</span><span class="sxs-lookup"><span data-stu-id="bbff5-117">Download the [Windows 10 IoT Core image](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) by double-clicking on the downloaded ISO file and locating the mounted Virtual CD-drive.</span></span>
8. <span data-ttu-id="bbff5-118">此驱动器将包含的安装文件 (.msi);双击它。</span><span class="sxs-lookup"><span data-stu-id="bbff5-118">This drive will contain an install file (.msi); double click it.</span></span> <span data-ttu-id="bbff5-119">这将在 C:\Program Files (x86) \Microsoft IoT\FFU\ 否则 d 在其中查看图像文件，在电脑上创建一个新目录"flash.ffu"。</span><span class="sxs-lookup"><span data-stu-id="bbff5-119">This will create a new directory on your PC under C:\Program Files (x86)\Microsoft IoT\FFU\ in which you shoul d see an image file, "flash.ffu".</span></span>
9. <span data-ttu-id="bbff5-120">下载、 解压缩并复制[eMMC 安装程序脚本](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip)到 USB 设备的根目录，以及设备的 FFU。</span><span class="sxs-lookup"><span data-stu-id="bbff5-120">Download, unzip and copy the [eMMC Installer script](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip) to the USB device's root directory, along with the device's FFU.</span></span>
10. <span data-ttu-id="bbff5-121">连接到 USB 集线器的 USB 驱动器、 鼠标和键盘。</span><span class="sxs-lookup"><span data-stu-id="bbff5-121">Connect the USB drive, mouse, and keyboard to the USB hub.</span></span> <span data-ttu-id="bbff5-122">将向你的设备的 HDMI 显示后，该设备附加到 USB 集线器，并在设备的电源线。</span><span class="sxs-lookup"><span data-stu-id="bbff5-122">Attach the HDMI display to your device, the device to the USB hub, and the power cord to the device.</span></span>
11. <span data-ttu-id="bbff5-123">请转到设备的 BIOS 设置。</span><span class="sxs-lookup"><span data-stu-id="bbff5-123">Go to the BIOS setup of the device.</span></span> <span data-ttu-id="bbff5-124">选择*Windows*作为从 uSB 驱动器启动操作系统并将设备设置。</span><span class="sxs-lookup"><span data-stu-id="bbff5-124">Select *Windows* as the Operating system and set the device to boot from your uSB drive.</span></span> <span data-ttu-id="bbff5-125">当系统重新启动时，你会看到 WinPE 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="bbff5-125">When the system reboots, you will see the WinPE command prompt.</span></span> <span data-ttu-id="bbff5-126">WinPE 提示符切换到 USB 驱动器。</span><span class="sxs-lookup"><span data-stu-id="bbff5-126">Switch the WinPE prompt to the USB Drive.</span></span> <span data-ttu-id="bbff5-127">这通常是 c： 或 d:，但可能需要尝试其他驱动器盘符。</span><span class="sxs-lookup"><span data-stu-id="bbff5-127">This is usually C: or D: but you may need to try other driver letters.</span></span>
12. <span data-ttu-id="bbff5-128">运行 eMMC 安装程序脚本，这将在 Windows 10 IoT Core 映像安装到设备的 eMMC 内存。</span><span class="sxs-lookup"><span data-stu-id="bbff5-128">Run the eMMC Installer script, which will install the Windows 10 IoT Core image to the device's eMMC memory.</span></span> <span data-ttu-id="bbff5-129">操作完成时，按任意键，并运行`wpeutil reboot`。</span><span class="sxs-lookup"><span data-stu-id="bbff5-129">When it completes, press any key and run `wpeutil reboot`.</span></span> <span data-ttu-id="bbff5-130">系统应引导到 Windows 10 IoT 核心版、 启动配置过程中，并加载默认应用程序。</span><span class="sxs-lookup"><span data-stu-id="bbff5-130">The system should boot into Windows 10 IoT Core, start the configuration process, and load the default application.</span></span>

## <a name="connect-to-a-network"></a><span data-ttu-id="bbff5-131">连接到网络</span><span class="sxs-lookup"><span data-stu-id="bbff5-131">Connect to a network</span></span>

### <a name="wired-connection"></a><span data-ttu-id="bbff5-132">有线的连接</span><span class="sxs-lookup"><span data-stu-id="bbff5-132">Wired connection</span></span>
<span data-ttu-id="bbff5-133">如果你的设备附带的以太网端口或 USB 以太网适配器支持，使您的有线的连接，将附加以太网电缆连接到你的网络。</span><span class="sxs-lookup"><span data-stu-id="bbff5-133">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="bbff5-134">无线连接</span><span class="sxs-lookup"><span data-stu-id="bbff5-134">Wireless connection</span></span>
<span data-ttu-id="bbff5-135">如果你的设备支持的 Wi-fi 连接，并且你已连接到它的显示，你将需要：</span><span class="sxs-lookup"><span data-stu-id="bbff5-135">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="bbff5-136">转到默认应用程序并单击设置按钮旁边的时钟。</span><span class="sxs-lookup"><span data-stu-id="bbff5-136">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="bbff5-137">在设置页上选择_网络和 Wi-fi_。</span><span class="sxs-lookup"><span data-stu-id="bbff5-137">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="bbff5-138">你的设备将开始扫描无线网络。</span><span class="sxs-lookup"><span data-stu-id="bbff5-138">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="bbff5-139">一旦你的网络会显示此列表中，选择它，然后单击_Connect_。</span><span class="sxs-lookup"><span data-stu-id="bbff5-139">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="bbff5-140">如果尚未连接显示，并且想要通过 Wi-fi 连接，你将需要：</span><span class="sxs-lookup"><span data-stu-id="bbff5-140">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="bbff5-141">转到 IoT 仪表板，并单击_我的设备_。</span><span class="sxs-lookup"><span data-stu-id="bbff5-141">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="bbff5-142">查找从列表中未配置开发板。</span><span class="sxs-lookup"><span data-stu-id="bbff5-142">Find your unconfigured board from the list.</span></span> <span data-ttu-id="bbff5-143">其名称开头"AJ_"...(例如 AJ_58EA6C68)。</span><span class="sxs-lookup"><span data-stu-id="bbff5-143">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="bbff5-144">如果看不到开发板出现几分钟后，请尝试重新启动你的板。</span><span class="sxs-lookup"><span data-stu-id="bbff5-144">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="bbff5-145">单击_配置设备_并输入你的网络凭据。</span><span class="sxs-lookup"><span data-stu-id="bbff5-145">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="bbff5-146">这将连接到网络的开发板。</span><span class="sxs-lookup"><span data-stu-id="bbff5-146">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="bbff5-147">您的计算机上的 Wifi 将需要打开以便找到其他网络。</span><span class="sxs-lookup"><span data-stu-id="bbff5-147">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="bbff5-148">连接到 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="bbff5-148">Connect to Windows Device Portal</span></span>

<span data-ttu-id="bbff5-149">使用[Windows Device Portal](../manage-your-device/DevicePortal.md)通过 web 浏览器连接你的设备。</span><span class="sxs-lookup"><span data-stu-id="bbff5-149">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="bbff5-150">设备门户提供有价值的配置和设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="bbff5-150">The device portal makes valuable configuration and device management capabilities available.</span></span> 


