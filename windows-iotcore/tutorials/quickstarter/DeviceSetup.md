---
title: 设置设备
ms.author: saclayt
ms.date: 04/10/2018
ms.topic: article
description: 了解如何使用 SD 卡通过 Windows 10 IoT 核心版来设置设备。
keywords: Windows 10 IoT 核心版, SD 卡, Windows 10 IoT 核心版仪表板
ms.custom: RS5
ms.openlocfilehash: 29332c99c9c2136ed8f62421972ee7fec184a9fd
ms.sourcegitcommit: 8a197111b5b7814b924d77dfea5f9d38760d4288
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2019
ms.locfileid: "67627410"
---
# <a name="setting-up-your-device"></a><span data-ttu-id="9dcf7-104">设置设备</span><span class="sxs-lookup"><span data-stu-id="9dcf7-104">Setting up your device</span></span>

<span data-ttu-id="9dcf7-105">下面介绍如何通过四种不同的方式使用 Windows 10 IoT 核心版来刷写设备。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-105">Below you'll find four different ways to flash your device with Windows 10 IoT Core.</span></span> <span data-ttu-id="9dcf7-106">根据[建议进行原型制作的板的列表](PrototypeBoards.md)中包含的图表，按相应的说明操作。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-106">Based on the chart included in the [list of suggested boards for prototyping](PrototypeBoards.md), follow the appropriate directions.</span></span> <span data-ttu-id="9dcf7-107">使用正确的列在这些不同的刷写方法之间导航。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-107">Use the right column to navigate between these different methods of flashing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9dcf7-108">请勿将创客映像用于商业化。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-108">Do not use maker images for commercialization.</span></span> <span data-ttu-id="9dcf7-109">若要将某个设备商业化，必须使用自定义 FFU 以确保最佳安全性。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-109">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="9dcf7-110">在[此处](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-110">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9dcf7-111">出现“格式化此磁盘”弹出窗口时，请勿格式化磁盘。 </span><span class="sxs-lookup"><span data-stu-id="9dcf7-111">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="9dcf7-112">我们正在修复此问题。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-112">We are working on a fix for this issue.</span></span>

## <a name="using-the-iot-dashboard-raspberry-pi-minnowboard-nxp"></a><span data-ttu-id="9dcf7-113">使用 IoT 仪表板（Raspberry Pi、MinnowBoard、NXP）</span><span class="sxs-lookup"><span data-stu-id="9dcf7-113">Using the IoT Dashboard (Raspberry Pi, MinnowBoard, NXP)</span></span>

> [!Video https://www.youtube.com/embed/JPRUbGIyODY]


> [!IMPORTANT]
> <span data-ttu-id="9dcf7-114">MinnowBoard Turbot 的最新 64 位固件可以在 [MinnowBoard 网站](https://minnowboard.org/tutorials/updating-the-firmware)上找到（跳过 MinnowBoard 站点的说明中的步骤 4）。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-114">The latest 64-bit firmware for MinnowBoard Turbot can be found on the [MinnowBoard website](https://minnowboard.org/tutorials/updating-the-firmware) (skip step 4 on the MinnowBoard site's instructions).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9dcf7-115">NXP 仅支持自定义映像。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-115">NXP only supports custom images.</span></span> <span data-ttu-id="9dcf7-116">若要刷写自定义映像，请从 OS 内部版本下拉列表中选择“自定义”，按[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)的说明创建基本映像，然后按下面的其余说明完成操作。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-116">If you're looking to flash a custom image, select "Custom" from the OS Build dropdown, follow the instructions [here](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) to create a basic image, and follow the rest of the instructions below to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="9dcf7-117">仪表板不能用来设置 Raspberry Pi 3B+。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-117">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="9dcf7-118">如果有 3B+ 设备，则必须使用 [3B+ 技术预览版](https://www.microsoft.com/en-us/software-download/windowsiot)。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-118">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="9dcf7-119">请查看技术预览版的[已知限制](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting)，确定它是否适合开发。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-119">Please view the [known limitations](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!TIP]
> <span data-ttu-id="9dcf7-120">建议使用高性能 SD 卡（例如 SanDisk SD 卡），这样可以增强稳定性，并且可以将设备连接到外部显示器来查看默认的应用程序启动。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-120">We recommend using a high-performance SD card, such as a SanDisk SD card, for increased stability as well as plugging your device into an external display to see the default application booting up.</span></span>


1. <span data-ttu-id="9dcf7-121">在[此处](https://docs.microsoft.com/windows/iot-core/downloads)下载 Windows 10 IoT 核心版仪表板。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-121">Download the Windows 10 IoT Core Dashboard [here](https://docs.microsoft.com/windows/iot-core/downloads).</span></span>
2. <span data-ttu-id="9dcf7-122">下载后，请打开仪表板，单击“设置新设备”，然后将 SD 卡插入计算机中。 </span><span class="sxs-lookup"><span data-stu-id="9dcf7-122">Once downloaded, open the Dashboard and click on _set up a new device_ and insert a SD card into your computer.</span></span>
3. <span data-ttu-id="9dcf7-123">按指示填写所有字段。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-123">Fill out all of the fields as indicated.</span></span>
4. <span data-ttu-id="9dcf7-124">接受软件许可条款，然后单击“下载并安装”  。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-124">Accept the software license terms and click _Download and install_.</span></span> <span data-ttu-id="9dcf7-125">可以看到 Windows 10 IoT 核心版此时正刷写 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-125">You'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>


![仪表板屏幕截图](../../media/DeviceSetup/Dashboard-Screenshot.jpg)
 

## <a name="using-the-iot-dashboard-dragonboard-410c"></a><span data-ttu-id="9dcf7-127">使用 IoT 仪表板 (DragonBoard 410c)</span><span class="sxs-lookup"><span data-stu-id="9dcf7-127">Using the IoT Dashboard (DragonBoard 410c)</span></span>

> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

> [!TIP]
> <span data-ttu-id="9dcf7-128">建议将设备连接到外部显示器来查看默认的应用程序启动。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-128">We recommend plugging your device into an external display to see the default application booting up.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9dcf7-129">若要刷写自定义映像，请从 OS 内部版本下拉列表中选择“自定义”，按[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)的说明创建基本映像，然后按下面的其余说明完成操作。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-129">If you're looking to flash a custom image, select "Custom" from the OS Build dropdown, follow the instructions [here](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) to create a basic image, and follow the rest of the instructions below to finish.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9dcf7-130">使用新的 Dragonboard 时，请注意，它已经安装了 Android。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-130">When you're working with a new Dragonboard, it comes with Android installed.</span></span> <span data-ttu-id="9dcf7-131">需使用 eMMC 刷写方法擦除并加载设备。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-131">You will need to wipe and load the device using the eMMC flashing method.</span></span>

> [!NOTE]
> <span data-ttu-id="9dcf7-132">如果 DragonBoard 出现任何音频相关问题，建议通读[此处](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf)提供的 Qualcomm 的手册。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-132">If you're running into any audio-related issues with your DragonBoard, we advise that you read through Qualcomm's manual [here](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf).</span></span> 

1. <span data-ttu-id="9dcf7-133">在[此处](https://docs.microsoft.com/windows/iot-core/downloads)下载 Windows 10 IoT 核心版仪表板。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-133">Download the Windows 10 IoT Core Dashboard [here](https://docs.microsoft.com/windows/iot-core/downloads).</span></span>
2. <span data-ttu-id="9dcf7-134">下载后，请打开仪表板，选择“Qualcomm DragonBoard 410c”。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-134">Once downloaded, open the Dashboard and select "Qualcomm DragonBoard 410c".</span></span> <span data-ttu-id="9dcf7-135">然后，以 Windows 预览体验成员身份登录  。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-135">Then _sign in as a Windows Insider_.</span></span> <span data-ttu-id="9dcf7-136">必须以预览体验成员身份登录才能刷写 DragonBoard 410c。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-136">You need to be signed in as an insider in order to flash DragonBoard 410c.</span></span> 
3. <span data-ttu-id="9dcf7-137">使用 microUSB 电缆将 Qualcomm 板连接到开发人员计算机。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-137">Connect the Qualcomm board to the developer machine using a microUSB cable.</span></span>
4. <span data-ttu-id="9dcf7-138">使用 12V (>1A) 电源在按住调高音量 (+) 按钮的情况下将 Dragonboard 通电。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-138">Power on your Dragonboard using a 12V (>1A) power supply while holding down the volume up (+) button.</span></span> <span data-ttu-id="9dcf7-139">此设备在连接到显示器的情况下应该显示包含一个锤子、一个闪电和一个齿轮的图像。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-139">The device - when connected to a display - should show the image of a hammer, a lightning bolt, and a cog.</span></span> 
5. <span data-ttu-id="9dcf7-140">此设备现在应该在仪表板上可见，如下所示。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-140">The device should now be visible on the Dashboard as shown below.</span></span> <span data-ttu-id="9dcf7-141">选择适当的设备。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-141">Select the appropriate device.</span></span>
6. <span data-ttu-id="9dcf7-142">接受软件许可条款，然后单击“下载并安装”  。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-142">Accept the software license terms and click _Download and install_.</span></span> <span data-ttu-id="9dcf7-143">可以看到 Windows 10 IoT 核心版此时正刷写到设备上。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-143">You'll see that Windows 10 IoT Core is now flashing onto your device.</span></span>


![处于刷写模式的 DragonBoard](../../media/DeviceSetup/db4.png)


## <a name="flashing-with-emmc-for-dragonboard-410c-other-qualcomm-devices"></a><span data-ttu-id="9dcf7-145">使用 eMMC 进行刷写（适用于 DragonBoard 410c 和其他 Qualcomm 设备）</span><span class="sxs-lookup"><span data-stu-id="9dcf7-145">Flashing with eMMC (for DragonBoard 410c, other Qualcomm devices)</span></span>

1. <span data-ttu-id="9dcf7-146">为 [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) 或 [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) 计算机下载并安装 DragonBoard Update Tool。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-146">Download and install the DragonBoard Update Tool for your [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) or [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) machine.</span></span>
2. <span data-ttu-id="9dcf7-147">下载 [Windows 10 IoT 核心版 DragonBoard FFU](https://developer.microsoft.com/en-us/windows/iot/Downloads)。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-147">Download the [Windows 10 IoT Core DragonBoard FFU](https://developer.microsoft.com/en-us/windows/iot/Downloads).</span></span>
3. <span data-ttu-id="9dcf7-148">双击下载的 ISO 文件，找到装载的虚拟 CD 驱动器。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-148">Double-click on the downloaded ISO file and locate the mounted Virtual CD-drive.</span></span> <span data-ttu-id="9dcf7-149">此驱动器将包含一个安装程序文件 (.msi)；双击它。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-149">This drive will contain an installer file (.msi); double-click on it.</span></span> <span data-ttu-id="9dcf7-150">这样会在电脑中的 `C:\Program Files (x86)\Microsoft IoT\FFU\` 下创建一个新目录，其中可以看到映像文件“flash.ffu”。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-150">This creates a new directory on your PC under `C:\Program Files (x86)\Microsoft IoT\FFU\` in which you should see an image file, "flash.ffu".</span></span>
4. <span data-ttu-id="9dcf7-151">确保 DragonBoard 处于下载模式，方法是将板上的第一个启动开关设置为“USB 启动”，如下所示。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-151">Ensure your DragonBoard is in download mode by setting the first boot switch on the board to USB Boot, as shown below.</span></span> <span data-ttu-id="9dcf7-152">接着通过 microUSB 电缆将 DragonBoard 连接到主机，然后将 DragonBoard 连接到 12V (> 1A) 电源。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-152">Then, connect DragonBoard the host PC via a microUSB cable, then plug in the DragonBoard to a 12V (> 1A) power supply.</span></span>
5. <span data-ttu-id="9dcf7-153">启动 DragonBoard Update Tool，该工具会通过一个绿色圆圈来表示已检测到 DragonBoard 连接到电脑。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-153">Start the DragonBoard Update Tool, which should detect that the DragonBoard is connect to your PC with a green circle.</span></span> <span data-ttu-id="9dcf7-154">“浏览”到 DragonBoard 的已下载 FFU，然后单击“程序”按钮。 </span><span class="sxs-lookup"><span data-stu-id="9dcf7-154">"Browse" to the DragonBoard's FFU that you downloaded, then click the _Program_ button.</span></span>
6. <span data-ttu-id="9dcf7-155">再次单击“浏览”，选择在步骤 5 创建的“rawprogram0.xml”。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-155">Click "Browse" again and select "rawprogram0.xml" that was generated in step 5.</span></span> <span data-ttu-id="9dcf7-156">然后单击“程序”按钮。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-156">Then click the "Program" button.</span></span>
7. <span data-ttu-id="9dcf7-157">下载完以后，请断开板的电源和 microUSB 电缆连接，将 USB 启动开关切换回到“关”的位置。 </span><span class="sxs-lookup"><span data-stu-id="9dcf7-157">Once the download is complete, disconnect the power supply and microUSB cable from the board and toggle the USB Boot switch back to _OFF_.</span></span> <span data-ttu-id="9dcf7-158">将 HDMI 显示器、鼠标和键盘连接到 DragonBoard，然后重新连接电源。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-158">Connect a HDMI display, a mouse, and a keyboard to the DragonBoard and re-connect the power supply.</span></span> <span data-ttu-id="9dcf7-159">数分钟后，应该会看到 Windows 10 IoT 核心版默认应用程序。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-159">After a few minutes, you should see the Windows 10 IoT Core default application.</span></span> 

![处于下载模式的 DragonBoard](../../media/DeviceSetup/db1.png)

> [!NOTE]
> <span data-ttu-id="9dcf7-161">确保设备现在是从 eMMC 内存启动，方法是：再次进入 BIOS 设置，切换驱动器启动顺序，使之从硬盘驱动器加载，而不是从 USB 盘加载。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-161">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>


## <a name="flashing-with-emmc-for-up-squared-other-intel-devices"></a><span data-ttu-id="9dcf7-162">使用 eMMC 进行刷写（适用于 Up Squared 和其他 Intel 设备）</span><span class="sxs-lookup"><span data-stu-id="9dcf7-162">Flashing with eMMC (for Up Squared, other Intel devices)</span></span>

1. <span data-ttu-id="9dcf7-163">下载并安装 [Windows 评估和部署工具包](https://docs.microsoft.com/windows-hardware/get-started/adk-install)，其中包含要运行的 Windows 10 相关版本。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-163">Download and install the [Windows Assessment and Deployment kit](https://docs.microsoft.com/windows-hardware/get-started/adk-install) with the correlating version of Windows 10 you're running.</span></span>
2. <span data-ttu-id="9dcf7-164">将 USB 盘插入计算机中。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-164">Insert a USB drive into your machine.</span></span>
3. <span data-ttu-id="9dcf7-165">创建可从 USB 启动的 WinPE 映像：</span><span class="sxs-lookup"><span data-stu-id="9dcf7-165">Create a USB-bootable WinPE image:</span></span>
4. <span data-ttu-id="9dcf7-166">以管理员身份启动 Deployment and Imaging Tools Environment `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)`。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-166">Start the Deployment and Imaging Tools Environment `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)` as an administrator.</span></span>
5. <span data-ttu-id="9dcf7-167">创建 Windows PE 文件的工作副本。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-167">Create a working copy of the Windows PE files.</span></span> <span data-ttu-id="9dcf7-168">指定 x86、amd64 或 ARM：`Copype amd64 C:\WINPE_amd64`</span><span class="sxs-lookup"><span data-stu-id="9dcf7-168">Specify either x86, amd64 or ARM: `Copype amd64 C:\WINPE_amd64`</span></span>
6. <span data-ttu-id="9dcf7-169">将 Windows PE 安装到 U 盘，指定下面的 WinPE 驱动器号。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-169">Install Windows PE to the USB flash drive, specifying the WinPE drive letter below.</span></span> <span data-ttu-id="9dcf7-170">可以在[此处](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive)查找详细信息。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-170">More information can be found [here](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive).</span></span> `MMakeWinPEMedia /UFD C:\WinPE_amd64 P:`
7. <span data-ttu-id="9dcf7-171">下载 [Windows 10 IoT 核心版映像](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true)，方法是：双击下载的 ISO 文件，找到装载的虚拟 CD 驱动器。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-171">Download the [Windows 10 IoT Core image](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) by double-clicking on the downloaded ISO file and locating the mounted Virtual CD-drive.</span></span>
8. <span data-ttu-id="9dcf7-172">此驱动器将包含一个安装文件 (.msi)；双击它。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-172">This drive will contain an install file (.msi); double click it.</span></span> <span data-ttu-id="9dcf7-173">这样会在电脑中的 C:\Program Files (x86)\Microsoft IoT\FFU\ 下创建一个新目录，其中可以看到映像文件“flash.ffu”。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-173">This will create a new directory on your PC under C:\Program Files (x86)\Microsoft IoT\FFU\ in which you shoul d see an image file, "flash.ffu".</span></span>
9. <span data-ttu-id="9dcf7-174">下载 [eMMC 安装程序脚本](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip)，将其解压缩后连同设备的 FFU 复制到 USB 设备的根目录。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-174">Download, unzip and copy the [eMMC Installer script](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip) to the USB device's root directory, along with the device's FFU.</span></span>
10. <span data-ttu-id="9dcf7-175">将 U 盘、鼠标和键盘连接到 USB 集线器。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-175">Connect the USB drive, mouse, and keyboard to the USB hub.</span></span> <span data-ttu-id="9dcf7-176">将 HDMI 显示器连接到设备，将设备连接到 USB 集线器，并将电源线连接到设备。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-176">Attach the HDMI display to your device, the device to the USB hub, and the power cord to the device.</span></span>
11. <span data-ttu-id="9dcf7-177">转到设备的 BIOS 设置。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-177">Go to the BIOS setup of the device.</span></span> <span data-ttu-id="9dcf7-178">选择 *Windows* 作为操作系统，将设备设置为从 U 盘启动。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-178">Select *Windows* as the Operating system and set the device to boot from your uSB drive.</span></span> <span data-ttu-id="9dcf7-179">当系统重启后，会看到 WinPE 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-179">When the system reboots, you will see the WinPE command prompt.</span></span> <span data-ttu-id="9dcf7-180">从 WinPE 命令提示符切换到 U 盘。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-180">Switch the WinPE prompt to the USB Drive.</span></span> <span data-ttu-id="9dcf7-181">该 U 盘通常为 C: 或 D:，但你可能需要尝试其他驱动器号。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-181">This is usually C: or D: but you may need to try other driver letters.</span></span>
12. <span data-ttu-id="9dcf7-182">运行 eMMC 安装程序脚本，将 Windows 10 IoT 核心版映像安装到设备的 eMMC 内存。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-182">Run the eMMC Installer script, which will install the Windows 10 IoT Core image to the device's eMMC memory.</span></span> <span data-ttu-id="9dcf7-183">完成后，按任意键运行 `wpeutil reboot`。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-183">When it completes, press any key and run `wpeutil reboot`.</span></span> <span data-ttu-id="9dcf7-184">系统会引导到 Windows 10 IoT 核心版中，开始配置过程，并加载默认应用程序。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-184">The system should boot into Windows 10 IoT Core, start the configuration process, and load the default application.</span></span>

> [!NOTE]
> <span data-ttu-id="9dcf7-185">确保设备现在是从 eMMC 内存启动，方法是：再次进入 BIOS 设置，切换驱动器启动顺序，使之从硬盘驱动器加载，而不是从 USB 盘加载。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-185">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>


## <a name="connecting-to-a-network"></a><span data-ttu-id="9dcf7-186">连接到网络</span><span class="sxs-lookup"><span data-stu-id="9dcf7-186">Connecting to a network</span></span>

#### <a name="wired-connection"></a><span data-ttu-id="9dcf7-187">有线连接</span><span class="sxs-lookup"><span data-stu-id="9dcf7-187">Wired connection</span></span>
<span data-ttu-id="9dcf7-188">如果设备带有以太网端口或 USB 以太网适配器支持，因此可以启用有线连接，则请连接一条以太网电缆，通过它连接到网络。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-188">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

#### <a name="wireless-connection"></a><span data-ttu-id="9dcf7-189">无线连接</span><span class="sxs-lookup"><span data-stu-id="9dcf7-189">Wireless connection</span></span>
<span data-ttu-id="9dcf7-190">如果设备支持 Wi-Fi 连接，而你已将显示器连接到设备，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="9dcf7-190">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="9dcf7-191">进入默认应用程序，单击时钟旁边的设置按钮。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-191">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="9dcf7-192">在设置页上，选择“网络和 Wi-Fi”。 </span><span class="sxs-lookup"><span data-stu-id="9dcf7-192">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="9dcf7-193">设备将开始扫描无线网络。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-193">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="9dcf7-194">你的网络显示在此列表中以后，将其选中，然后单击“连接”。 </span><span class="sxs-lookup"><span data-stu-id="9dcf7-194">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="9dcf7-195">如果尚未连接显示器，因此希望通过 Wi-Fi 进行连接，则需执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="9dcf7-195">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="9dcf7-196">转到 IoT 仪表板，单击“我的设备”。 </span><span class="sxs-lookup"><span data-stu-id="9dcf7-196">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="9dcf7-197">从列表中找到你的未配置的板。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-197">Find your unconfigured board from the list.</span></span> <span data-ttu-id="9dcf7-198">其名称会以“AJ_”开头（例如 AJ_58EA6C68）。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-198">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="9dcf7-199">如果数分钟后仍没有看到自己的板显示，则请尝试重启你的板。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-199">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="9dcf7-200">单击“配置设备”，然后输入网络凭据。 </span><span class="sxs-lookup"><span data-stu-id="9dcf7-200">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="9dcf7-201">这样就会将板连接到网络。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-201">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="9dcf7-202">需启用计算机上的 Wi-Fi 才能找到其他网络。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-202">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connecting-to-windows-device-portal"></a><span data-ttu-id="9dcf7-203">连接到 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="9dcf7-203">Connecting to Windows Device Portal</span></span>

<span data-ttu-id="9dcf7-204">使用 [Windows 设备门户](../../manage-your-device/DevicePortal.md)，通过 Web 浏览器来连接设备。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-204">Use the [Windows Device Portal](../../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="9dcf7-205">设备门户提供重要的配置和设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="9dcf7-205">The device portal makes valuable configuration and device management capabilities available.</span></span> 

