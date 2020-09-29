---
title: 设置 Intel 设备
ms.date: 05/22/2019
ms.topic: article
description: 了解如何通过 Windows 10 IoT 核心版来设置 Intel 设备。 使用 eMMC、连接到网络，并连接到 Windows 设备门户。
keywords: Windows 10 IoT 核心版, Intel
ms.custom: RS5
ms.openlocfilehash: c01a9f1a92b344e9e4458ca45c62c78162c253aa
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782359"
---
# <a name="setting-up-an-intel-device"></a><span data-ttu-id="ee166-105">设置 Intel 设备</span><span class="sxs-lookup"><span data-stu-id="ee166-105">Setting up an Intel device</span></span>

<span data-ttu-id="ee166-106">若要使用 Qualcomm 设备进行制作，请参阅 [IoT 核心版制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。</span><span class="sxs-lookup"><span data-stu-id="ee166-106">If you're looking to manufacture with a Qualcomm device, please refer to the [IoT Core Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span> <span data-ttu-id="ee166-107">不能将创客映像用于制作。</span><span class="sxs-lookup"><span data-stu-id="ee166-107">You cannot use maker images for manufacturing.</span></span>

> [!NOTE]
> <span data-ttu-id="ee166-108">确保设备现在是从 eMMC 内存启动，方法是：再次进入 BIOS 设置，切换驱动器启动顺序，使之从硬盘驱动器加载，而不是从 USB 盘加载。</span><span class="sxs-lookup"><span data-stu-id="ee166-108">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>

## <a name="using-emmc"></a><span data-ttu-id="ee166-109">使用 eMMC</span><span class="sxs-lookup"><span data-stu-id="ee166-109">Using eMMC</span></span>

1. <span data-ttu-id="ee166-110">下载并安装 [Windows 评估和部署工具包](https://docs.microsoft.com/windows-hardware/get-started/adk-install)，其中包含要运行的 Windows 10 相关版本。</span><span class="sxs-lookup"><span data-stu-id="ee166-110">Download and install the [Windows Assessment and Deployment kit](https://docs.microsoft.com/windows-hardware/get-started/adk-install) with the correlating version of Windows 10 you're running.</span></span>
2. <span data-ttu-id="ee166-111">将 USB 盘插入计算机中。</span><span class="sxs-lookup"><span data-stu-id="ee166-111">Insert a USB drive into your machine.</span></span>
3. <span data-ttu-id="ee166-112">创建可从 USB 启动的 WinPE 映像：</span><span class="sxs-lookup"><span data-stu-id="ee166-112">Create a USB-bootable WinPE image:</span></span>
4. <span data-ttu-id="ee166-113">以管理员身份启动 Deployment and Imaging Tools Environment `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)`。</span><span class="sxs-lookup"><span data-stu-id="ee166-113">Start the Deployment and Imaging Tools Environment `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)` as an administrator.</span></span>
5. <span data-ttu-id="ee166-114">创建 Windows PE 文件的工作副本。</span><span class="sxs-lookup"><span data-stu-id="ee166-114">Create a working copy of the Windows PE files.</span></span> <span data-ttu-id="ee166-115">指定 x86、amd64 或 ARM：`Copype amd64 C:\WINPE_amd64`</span><span class="sxs-lookup"><span data-stu-id="ee166-115">Specify either x86, amd64 or ARM: `Copype amd64 C:\WINPE_amd64`</span></span>
6. <span data-ttu-id="ee166-116">将 Windows PE 安装到 U 盘，指定下面的 WinPE 驱动器号。</span><span class="sxs-lookup"><span data-stu-id="ee166-116">Install Windows PE to the USB flash drive, specifying the WinPE drive letter below.</span></span> <span data-ttu-id="ee166-117">可在[此处](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive)找到详细信息。</span><span class="sxs-lookup"><span data-stu-id="ee166-117">More information can be found [here](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive).</span></span> `MakeWinPEMedia /UFD C:\WinPE_amd64 P:`
7. <span data-ttu-id="ee166-118">下载 [Windows 10 IoT 核心版映像](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true)，方法是：双击下载的 ISO 文件，找到装载的虚拟 CD 驱动器。</span><span class="sxs-lookup"><span data-stu-id="ee166-118">Download the [Windows 10 IoT Core image](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) by double-clicking on the downloaded ISO file and locating the mounted Virtual CD-drive.</span></span>
8. <span data-ttu-id="ee166-119">此驱动器将包含一个安装文件 (.msi)；双击它。</span><span class="sxs-lookup"><span data-stu-id="ee166-119">This drive will contain an install file (.msi); double click it.</span></span> <span data-ttu-id="ee166-120">这样会在电脑中的 C:\Program Files (x86)\Microsoft IoT\FFU\ 下创建一个新目录，其中可以看到映像文件“flash.ffu”。</span><span class="sxs-lookup"><span data-stu-id="ee166-120">This will create a new directory on your PC under C:\Program Files (x86)\Microsoft IoT\FFU\ in which you should see an image file, "flash.ffu".</span></span>
9. <span data-ttu-id="ee166-121">下载 [eMMC 安装程序脚本](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip)，将其解压缩后连同设备的 FFU 复制到 USB 设备的根目录。</span><span class="sxs-lookup"><span data-stu-id="ee166-121">Download, unzip, and copy the [eMMC Installer script](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip) to the USB device's root directory, along with the device's FFU.</span></span>
10. <span data-ttu-id="ee166-122">将 U 盘、鼠标和键盘连接到 USB 集线器。</span><span class="sxs-lookup"><span data-stu-id="ee166-122">Connect the USB drive, mouse, and keyboard to the USB hub.</span></span> <span data-ttu-id="ee166-123">将 HDMI 显示器连接到设备，将设备连接到 USB 集线器，并将电源线连接到设备。</span><span class="sxs-lookup"><span data-stu-id="ee166-123">Attach the HDMI display to your device, the device to the USB hub, and the power cord to the device.</span></span>
11. <span data-ttu-id="ee166-124">转到设备的 BIOS 设置。</span><span class="sxs-lookup"><span data-stu-id="ee166-124">Go to the BIOS setup of the device.</span></span> <span data-ttu-id="ee166-125">选择 *Windows* 作为操作系统，将设备设置为从 U 盘启动。</span><span class="sxs-lookup"><span data-stu-id="ee166-125">Select *Windows* as the Operating system and set the device to boot from your uSB drive.</span></span> <span data-ttu-id="ee166-126">当系统重启后，会看到 WinPE 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="ee166-126">When the system reboots, you will see the WinPE command prompt.</span></span> <span data-ttu-id="ee166-127">从 WinPE 命令提示符切换到 U 盘。</span><span class="sxs-lookup"><span data-stu-id="ee166-127">Switch the WinPE prompt to the USB Drive.</span></span> <span data-ttu-id="ee166-128">该 U 盘通常为 C: 或 D:，但你可能需要尝试其他驱动器号。</span><span class="sxs-lookup"><span data-stu-id="ee166-128">This is usually C: or D: but you may need to try other driver letters.</span></span>
12. <span data-ttu-id="ee166-129">运行 eMMC 安装程序脚本，将 Windows 10 IoT 核心版映像安装到设备的 eMMC 内存。</span><span class="sxs-lookup"><span data-stu-id="ee166-129">Run the eMMC Installer script, which will install the Windows 10 IoT Core image to the device's eMMC memory.</span></span> <span data-ttu-id="ee166-130">完成后，按任意键运行 `wpeutil reboot`。</span><span class="sxs-lookup"><span data-stu-id="ee166-130">When it completes, press any key and run `wpeutil reboot`.</span></span> <span data-ttu-id="ee166-131">系统会引导到 Windows 10 IoT 核心版中，开始配置过程，并加载默认应用程序。</span><span class="sxs-lookup"><span data-stu-id="ee166-131">The system should boot into Windows 10 IoT Core, start the configuration process, and load the default application.</span></span>

## <a name="connect-to-a-network"></a><span data-ttu-id="ee166-132">连接到网络</span><span class="sxs-lookup"><span data-stu-id="ee166-132">Connect to a network</span></span>

### <a name="wired-connection"></a><span data-ttu-id="ee166-133">有线连接</span><span class="sxs-lookup"><span data-stu-id="ee166-133">Wired connection</span></span>
<span data-ttu-id="ee166-134">如果设备带有以太网端口或 USB 以太网适配器支持，因此可以启用有线连接，则请连接一条以太网电缆，通过它连接到网络。</span><span class="sxs-lookup"><span data-stu-id="ee166-134">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

### <a name="wireless-connection"></a><span data-ttu-id="ee166-135">无线连接</span><span class="sxs-lookup"><span data-stu-id="ee166-135">Wireless connection</span></span>
<span data-ttu-id="ee166-136">如果设备支持 Wi-Fi 连接，而你已将显示器连接到设备，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ee166-136">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="ee166-137">进入默认应用程序，单击时钟旁边的设置按钮。</span><span class="sxs-lookup"><span data-stu-id="ee166-137">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="ee166-138">在设置页上，选择“网络和 Wi-Fi”。__</span><span class="sxs-lookup"><span data-stu-id="ee166-138">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="ee166-139">设备将开始扫描无线网络。</span><span class="sxs-lookup"><span data-stu-id="ee166-139">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="ee166-140">你的网络显示在此列表中以后，将其选中，然后单击“连接”。__</span><span class="sxs-lookup"><span data-stu-id="ee166-140">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="ee166-141">如果尚未连接显示器，因此希望通过 Wi-Fi 进行连接，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="ee166-141">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="ee166-142">转到 IoT 仪表板，单击“我的设备”。__</span><span class="sxs-lookup"><span data-stu-id="ee166-142">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="ee166-143">从列表中找到你的未配置的板。</span><span class="sxs-lookup"><span data-stu-id="ee166-143">Find your unconfigured board from the list.</span></span> <span data-ttu-id="ee166-144">其名称会以“AJ_”开头（例如 AJ_58EA6C68）。</span><span class="sxs-lookup"><span data-stu-id="ee166-144">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="ee166-145">如果数分钟后仍没有看到自己的板显示，则请尝试重启你的板。</span><span class="sxs-lookup"><span data-stu-id="ee166-145">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="ee166-146">单击“配置设备”，然后输入网络凭据。__</span><span class="sxs-lookup"><span data-stu-id="ee166-146">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="ee166-147">这样就会将板连接到网络。</span><span class="sxs-lookup"><span data-stu-id="ee166-147">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="ee166-148">需启用计算机上的 Wi-Fi 才能找到其他网络。</span><span class="sxs-lookup"><span data-stu-id="ee166-148">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connect-to-windows-device-portal"></a><span data-ttu-id="ee166-149">连接到 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="ee166-149">Connect to Windows Device Portal</span></span>

<span data-ttu-id="ee166-150">使用 [Windows 设备门户](../manage-your-device/DevicePortal.md)，通过 Web 浏览器来连接设备。</span><span class="sxs-lookup"><span data-stu-id="ee166-150">Use the [Windows Device Portal](../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="ee166-151">设备门户提供重要的配置和设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="ee166-151">The device portal makes valuable configuration and device management capabilities available.</span></span> 


