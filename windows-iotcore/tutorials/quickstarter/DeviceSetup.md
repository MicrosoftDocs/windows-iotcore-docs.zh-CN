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
# <a name="setting-up-your-device"></a><span data-ttu-id="e5c1e-104">设置你的设备</span><span class="sxs-lookup"><span data-stu-id="e5c1e-104">Setting up your device</span></span>

<span data-ttu-id="e5c1e-105">下面您会发现闪烁，将设备与 Windows 10 IoT Core 的四种不同方式。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-105">Below you'll find four different ways to flash your device with Windows 10 IoT Core.</span></span> <span data-ttu-id="e5c1e-106">基于包含在该图表[建议用于原型制作的看板的列表](PrototypeBoards.md)，按照相应说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-106">Based on the chart included in the [list of suggested boards for prototyping](PrototypeBoards.md), follow the appropriate directions.</span></span> <span data-ttu-id="e5c1e-107">使用右侧的列的闪烁这些不同的方法之间进行导航。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-107">Use the right column to navigate between these different methods of flashing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5c1e-108">请不要将 maker 映像用于商品化。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-108">Do not use maker images for commercialization.</span></span> <span data-ttu-id="e5c1e-109">如果 commercializing 设备，则必须使用自定义 FFU 为获得最佳安全性。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-109">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="e5c1e-110">在[此处](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-110">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5c1e-111">当"格式化此磁盘"弹出最多启动后，请执行_不_格式化该磁盘。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-111">When the "format this disk" pop up comes up, do _not_ format the disk.</span></span> <span data-ttu-id="e5c1e-112">我们正在努力修复此问题。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-112">We are working on a fix for this issue.</span></span>

## <a name="using-the-iot-dashboard-raspberry-pi-minnowboard-nxp"></a><span data-ttu-id="e5c1e-113">使用 IoT 仪表板 （Raspberry Pi，MinnowBoard，NXP）</span><span class="sxs-lookup"><span data-stu-id="e5c1e-113">Using the IoT Dashboard (Raspberry Pi, MinnowBoard, NXP)</span></span>

> [!Video https://www.youtube.com/embed/JPRUbGIyODY]


> [!IMPORTANT]
> <span data-ttu-id="e5c1e-114">可以上找到最新的 64 位固件的 MinnowBoard Turbot [MinnowBoard 网站](https://minnowboard.org/tutorials/updating-the-firmware)（MinnowBoard 站点的说明，跳过第 4 步）。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-114">The latest 64-bit firmware for MinnowBoard Turbot can be found on the [MinnowBoard website](https://minnowboard.org/tutorials/updating-the-firmware) (skip step 4 on the MinnowBoard site's instructions).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5c1e-115">NXP 仅支持自定义映像。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-115">NXP only supports custom images.</span></span> <span data-ttu-id="e5c1e-116">如果您要查找闪存的自定义映像，请从操作系统内部版本下拉列表中选择"自定义"，按照说明进行操作[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)创建基本映像，并按照下面的说明来完成其余部分。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-116">If you're looking to flash a custom image, select "Custom" from the OS Build dropdown, follow the instructions [here](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) to create a basic image, and follow the rest of the instructions below to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="e5c1e-117">不能用于设置 Raspberry Pi 3B + 使用仪表板。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-117">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="e5c1e-118">如果你有 3B + 设备，则必须使用[3B + 技术预览版](https://www.microsoft.com/en-us/software-download/windowsiot)。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-118">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="e5c1e-119">请查看[已知限制](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting)的 technical preview，以确定这是否适用于你的开发。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-119">Please view the [known limitations](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!TIP]
> <span data-ttu-id="e5c1e-120">我们建议使用高性能的 SD 卡，如 SanDisk SD 卡，用于增强的稳定性，以及将设备插入到外部显示器查看默认的应用程序启动。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-120">We recommend using a high-performance SD card, such as a SanDisk SD card, for increased stability as well as plugging your device into an external display to see the default application booting up.</span></span>


1. <span data-ttu-id="e5c1e-121">下载 Windows 10 IoT Core 仪表板[此处](https://docs.microsoft.com/windows/iot-core/downloads)。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-121">Download the Windows 10 IoT Core Dashboard [here](https://docs.microsoft.com/windows/iot-core/downloads).</span></span>
2. <span data-ttu-id="e5c1e-122">下载完成后，打开仪表板，然后单击_设置新设备_和 SD 卡插入到计算机。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-122">Once downloaded, open the Dashboard and click on _set up a new device_ and insert a SD card into your computer.</span></span>
3. <span data-ttu-id="e5c1e-123">填写所有字段所示。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-123">Fill out all of the fields as indicated.</span></span>
4. <span data-ttu-id="e5c1e-124">接受软件许可条款，然后单击_下载并安装_。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-124">Accept the software license terms and click _Download and install_.</span></span> <span data-ttu-id="e5c1e-125">你将看到 Windows 10 IoT Core 现在闪 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-125">You'll see that Windows 10 IoT Core is now flashing your SD card.</span></span>


![仪表板的屏幕截图](../../media/DeviceSetup/Dashboard-Screenshot.jpg)
 

## <a name="using-the-iot-dashboard-dragonboard-410c"></a><span data-ttu-id="e5c1e-127">使用 IoT 仪表板 (DragonBoard 410 c)</span><span class="sxs-lookup"><span data-stu-id="e5c1e-127">Using the IoT Dashboard (DragonBoard 410c)</span></span>

> [!Video https://www.youtube.com/embed/iPm57hGq-Q8]

> [!TIP]
> <span data-ttu-id="e5c1e-128">我们建议将设备插入到外部显示器查看默认的应用程序启动。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-128">We recommend plugging your device into an external display to see the default application booting up.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5c1e-129">如果您要查找闪存的自定义映像，请从操作系统内部版本下拉列表中选择"自定义"，按照说明进行操作[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)创建基本映像，并按照下面的说明来完成其余部分。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-129">If you're looking to flash a custom image, select "Custom" from the OS Build dropdown, follow the instructions [here](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image) to create a basic image, and follow the rest of the instructions below to finish.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5c1e-130">当您正在使用新 Dragonboard 时，它还提供安装 Android。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-130">When you're working with a new Dragonboard, it comes with Android installed.</span></span> <span data-ttu-id="e5c1e-131">需要擦除并加载使用 eMMC 闪烁方法的设备。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-131">You will need to wipe and load the device using the eMMC flashing method.</span></span>

> [!NOTE]
> <span data-ttu-id="e5c1e-132">如果正运行带有你 DragonBoard 到任何音频相关的问题，我们建议你通读 Qualcomm 的手册[此处](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf)。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-132">If you're running into any audio-related issues with your DragonBoard, we advise that you read through Qualcomm's manual [here](https://developer.qualcomm.com/download/db410c/stereo-connector-and-audio-routing-application-note.pdf).</span></span> 

1. <span data-ttu-id="e5c1e-133">下载 Windows 10 IoT Core 仪表板[此处](https://docs.microsoft.com/windows/iot-core/downloads)。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-133">Download the Windows 10 IoT Core Dashboard [here](https://docs.microsoft.com/windows/iot-core/downloads).</span></span>
2. <span data-ttu-id="e5c1e-134">下载完成后，打开仪表板并选择"Qualcomm DragonBoard 410 c"。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-134">Once downloaded, open the Dashboard and select "Qualcomm DragonBoard 410c".</span></span> <span data-ttu-id="e5c1e-135">然后_中，以 Windows Insider 登录_。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-135">Then _sign in as a Windows Insider_.</span></span> <span data-ttu-id="e5c1e-136">您需要以 flash DragonBoard 410 c 作为内部人员登录。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-136">You need to be signed in as an insider in order to flash DragonBoard 410c.</span></span> 
3. <span data-ttu-id="e5c1e-137">Qualcomm 板连接到使用 microUSB 电缆的开发人员计算机。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-137">Connect the Qualcomm board to the developer machine using a microUSB cable.</span></span>
4. <span data-ttu-id="e5c1e-138">使用 12V 你 Dragonboard 开机 (> 1A) 在按下向上 （+） 的卷的电源按钮。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-138">Power on your Dragonboard using a 12V (>1A) power supply while holding down the volume up (+) button.</span></span> <span data-ttu-id="e5c1e-139">设备-连接到显示-时应显示一把铁锤、 闪电，齿轮图标的图像。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-139">The device - when connected to a display - should show the image of a hammer, a lightning bolt, and a cog.</span></span> 
5. <span data-ttu-id="e5c1e-140">设备现在应可以看到如下所示的仪表板上。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-140">The device should now be visible on the Dashboard as shown below.</span></span> <span data-ttu-id="e5c1e-141">选择适当的设备。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-141">Select the appropriate device.</span></span>
6. <span data-ttu-id="e5c1e-142">接受软件许可条款，然后单击_下载并安装_。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-142">Accept the software license terms and click _Download and install_.</span></span> <span data-ttu-id="e5c1e-143">你将看到 Windows 10 IoT Core 现在闪到你的设备上。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-143">You'll see that Windows 10 IoT Core is now flashing onto your device.</span></span>


![在闪存模式下的 DragonBoard](../../media/DeviceSetup/db4.png)


## <a name="flashing-with-emmc-for-dragonboard-410c-other-qualcomm-devices"></a><span data-ttu-id="e5c1e-145">使用 eMMC 闪烁 （适用于 DragonBoard 410 c 其他 Qualcomm 设备)</span><span class="sxs-lookup"><span data-stu-id="e5c1e-145">Flashing with eMMC (for DragonBoard 410c, other Qualcomm devices)</span></span>

1. <span data-ttu-id="e5c1e-146">下载并安装 DragonBoard 更新工具为你[x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip)或[x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip)机。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-146">Download and install the DragonBoard Update Tool for your [x86](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x86.zip) or [x64](https://developer.qualcomm.com/download/db410c/windows-10-iot-update-tool-dragonboard-410c-x64.zip) machine.</span></span>
2. <span data-ttu-id="e5c1e-147">下载[Windows 10 IoT 核心 DragonBoard FFU](https://developer.microsoft.com/en-us/windows/iot/Downloads)。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-147">Download the [Windows 10 IoT Core DragonBoard FFU](https://developer.microsoft.com/en-us/windows/iot/Downloads).</span></span>
3. <span data-ttu-id="e5c1e-148">双击下载的 ISO 文件并找到已装载的虚拟 CD 的驱动器。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-148">Double-click on the downloaded ISO file and locate the mounted Virtual CD-drive.</span></span> <span data-ttu-id="e5c1e-149">此驱动器将包含的安装程序文件 (.msi);双击该文件。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-149">This drive will contain an installer file (.msi); double-click on it.</span></span> <span data-ttu-id="e5c1e-150">这将创建一个新的目录下在电脑上 `C:\Program Files (x86)\Microsoft IoT\FFU\`中应看到图像文件、"flash.ffu"。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-150">This creates a new directory on your PC under `C:\Program Files (x86)\Microsoft IoT\FFU\` in which you should see an image file, "flash.ffu".</span></span>
4. <span data-ttu-id="e5c1e-151">请确保你 DragonBoard 是在下载模式下设置首次启动板上切换到 USB 启动，如下所示。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-151">Ensure your DragonBoard is in download mode by setting the first boot switch on the board to USB Boot, as shown below.</span></span> <span data-ttu-id="e5c1e-152">然后，连接 DragonBoard 宿主 PC 通过 microUSB 电缆，然后插入到 12V DragonBoard (> 1A) 电源。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-152">Then, connect DragonBoard the host PC via a microUSB cable, then plug in the DragonBoard to a 12V (> 1A) power supply.</span></span>
5. <span data-ttu-id="e5c1e-153">启动 DragonBoard 更新工具，它应检测 DragonBoard 连接到您的 PC 的绿色圆圈。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-153">Start the DragonBoard Update Tool, which should detect that the DragonBoard is connect to your PC with a green circle.</span></span> <span data-ttu-id="e5c1e-154">"浏览"到 DragonBoard FFU 下载，然后单击_程序_按钮。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-154">"Browse" to the DragonBoard's FFU that you downloaded, then click the _Program_ button.</span></span>
6. <span data-ttu-id="e5c1e-155">再次单击"浏览"，然后选择"rawprogram0.xml"已在步骤 5 中生成。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-155">Click "Browse" again and select "rawprogram0.xml" that was generated in step 5.</span></span> <span data-ttu-id="e5c1e-156">然后单击"计划"按钮。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-156">Then click the "Program" button.</span></span>
7. <span data-ttu-id="e5c1e-157">下载完成后，从 USB 启动切换回的看板和切换断开电源供应和 microUSB 线_OFF_。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-157">Once the download is complete, disconnect the power supply and microUSB cable from the board and toggle the USB Boot switch back to _OFF_.</span></span> <span data-ttu-id="e5c1e-158">连接到 DragonBoard 和 rec onnect 电源 HDMI 显示器、 鼠标和键盘。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-158">Connect a HDMI display, a mouse, and a keyboard to the DragonBoard and rec-onnect the power supply.</span></span> <span data-ttu-id="e5c1e-159">几分钟后，您应该看到 Windows 10 IoT 核心版默认应用程序。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-159">After a few minutes, you should see the Windows 10 IoT Core default application.</span></span> 

![在下载模式下的 DragonBoard](../../media/DeviceSetup/db1.png)

> [!NOTE]
> <span data-ttu-id="e5c1e-161">请确保设备现已通过重新输入 BIOS 设置，并切换启动驱动器顺序加载从硬盘驱动器而不是从 USB 驱动器启动从 eMMC 内存。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-161">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>


## <a name="flashing-with-emmc-for-up-squared-other-intel-devices"></a><span data-ttu-id="e5c1e-162">使用 eMMC 闪烁 （对于向上平方，Intel 的其他设备）</span><span class="sxs-lookup"><span data-stu-id="e5c1e-162">Flashing with eMMC (for Up Squared, other Intel devices)</span></span>

1. <span data-ttu-id="e5c1e-163">下载并安装[Windows 评估和部署工具包](https://docs.microsoft.com/windows-hardware/get-started/adk-install)与正在运行的 Windows 10 的相关版本。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-163">Download and install the [Windows Assessment and Deployment kit](https://docs.microsoft.com/windows-hardware/get-started/adk-install) with the correlating version of Windows 10 you're running.</span></span>
2. <span data-ttu-id="e5c1e-164">将 USB 驱动器插入计算机。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-164">Insert a USB drive into your machine.</span></span>
3. <span data-ttu-id="e5c1e-165">创建 USB 可启动的 WinPE 映像：</span><span class="sxs-lookup"><span data-stu-id="e5c1e-165">Create a USB-bootable WinPE image:</span></span>
4. <span data-ttu-id="e5c1e-166">开始部署和映像的工具环境`(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)`以管理员身份。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-166">Start the Deployment and Imaging Tools Environment `(C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Deployment Tools)` as an administrator.</span></span>
5. <span data-ttu-id="e5c1e-167">创建 Windows PE 文件的工作副本。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-167">Create a working copy of the Windows PE files.</span></span> <span data-ttu-id="e5c1e-168">指定任一 x86 amd64 或 ARM:</span><span class="sxs-lookup"><span data-stu-id="e5c1e-168">Specify either x86, amd64 or ARM:</span></span> `Copype amd64 C:\WINPE_amd64`
6. <span data-ttu-id="e5c1e-169">将 Windows PE 安装到 USB 闪存驱动器，指定以下的 WinPE 驱动器号。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-169">Install Windows PE to the USB flash drive, specifying the WinPE drive letter below.</span></span> <span data-ttu-id="e5c1e-170">可找到更多信息[此处](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive)。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-170">More information can be found [here](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-create-usb-bootable-drive).</span></span> `MMakeWinPEMedia /UFD C:\WinPE_amd64 P:`
7. <span data-ttu-id="e5c1e-171">下载[Windows 10 IoT Core 映像](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true)通过双击已下载的 ISO 文件并查找装载的虚拟 CD 的驱动器。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-171">Download the [Windows 10 IoT Core image](https://downloads.up-community.org/?post_type=wpdmpro&p=204&preview=true) by double-clicking on the downloaded ISO file and locating the mounted Virtual CD-drive.</span></span>
8. <span data-ttu-id="e5c1e-172">此驱动器将包含的安装文件 (.msi);双击它。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-172">This drive will contain an install file (.msi); double click it.</span></span> <span data-ttu-id="e5c1e-173">这将在 C:\Program Files (x86) \Microsoft IoT\FFU\ 否则 d 在其中查看图像文件，在电脑上创建一个新目录"flash.ffu"。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-173">This will create a new directory on your PC under C:\Program Files (x86)\Microsoft IoT\FFU\ in which you shoul d see an image file, "flash.ffu".</span></span>
9. <span data-ttu-id="e5c1e-174">下载、 解压缩并复制[eMMC 安装程序脚本](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip)到 USB 设备的根目录，以及设备的 FFU。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-174">Download, unzip and copy the [eMMC Installer script](https://github.com/ms-iot/content/blob/develop/Resources/eMMCInstaller.zip) to the USB device's root directory, along with the device's FFU.</span></span>
10. <span data-ttu-id="e5c1e-175">连接到 USB 集线器的 USB 驱动器、 鼠标和键盘。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-175">Connect the USB drive, mouse, and keyboard to the USB hub.</span></span> <span data-ttu-id="e5c1e-176">将向你的设备的 HDMI 显示后，该设备附加到 USB 集线器，并在设备的电源线。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-176">Attach the HDMI display to your device, the device to the USB hub, and the power cord to the device.</span></span>
11. <span data-ttu-id="e5c1e-177">请转到设备的 BIOS 设置。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-177">Go to the BIOS setup of the device.</span></span> <span data-ttu-id="e5c1e-178">选择*Windows*作为从 uSB 驱动器启动操作系统并将设备设置。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-178">Select *Windows* as the Operating system and set the device to boot from your uSB drive.</span></span> <span data-ttu-id="e5c1e-179">当系统重新启动时，你会看到 WinPE 命令提示符。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-179">When the system reboots, you will see the WinPE command prompt.</span></span> <span data-ttu-id="e5c1e-180">WinPE 提示符切换到 USB 驱动器。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-180">Switch the WinPE prompt to the USB Drive.</span></span> <span data-ttu-id="e5c1e-181">这通常是 c： 或 d:，但可能需要尝试其他驱动器盘符。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-181">This is usually C: or D: but you may need to try other driver letters.</span></span>
12. <span data-ttu-id="e5c1e-182">运行 eMMC 安装程序脚本，这将在 Windows 10 IoT Core 映像安装到设备的 eMMC 内存。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-182">Run the eMMC Installer script, which will install the Windows 10 IoT Core image to the device's eMMC memory.</span></span> <span data-ttu-id="e5c1e-183">操作完成时，按任意键，并运行`wpeutil reboot`。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-183">When it completes, press any key and run `wpeutil reboot`.</span></span> <span data-ttu-id="e5c1e-184">系统应引导到 Windows 10 IoT 核心版、 启动配置过程中，并加载默认应用程序。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-184">The system should boot into Windows 10 IoT Core, start the configuration process, and load the default application.</span></span>

> [!NOTE]
> <span data-ttu-id="e5c1e-185">请确保设备现已通过重新输入 BIOS 设置，并切换启动驱动器顺序加载从硬盘驱动器而不是从 USB 驱动器启动从 eMMC 内存。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-185">Make sure the device is now booting from the eMMC memory by entering the BIOS setup again and switching the Boot Drive order to load from the Hard Drive instead of from the USB Drive.</span></span>


## <a name="connecting-to-a-network"></a><span data-ttu-id="e5c1e-186">连接到网络</span><span class="sxs-lookup"><span data-stu-id="e5c1e-186">Connecting to a network</span></span>

#### <a name="wired-connection"></a><span data-ttu-id="e5c1e-187">有线的连接</span><span class="sxs-lookup"><span data-stu-id="e5c1e-187">Wired connection</span></span>
<span data-ttu-id="e5c1e-188">如果你的设备附带的以太网端口或 USB 以太网适配器支持，使您的有线的连接，将附加以太网电缆连接到你的网络。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-188">If your device comes with an Ethernet port or USB Ethernet adapter support to enable a wired connection, attach an Ethernet cable to connect it to your network.</span></span>

#### <a name="wireless-connection"></a><span data-ttu-id="e5c1e-189">无线连接</span><span class="sxs-lookup"><span data-stu-id="e5c1e-189">Wireless connection</span></span>
<span data-ttu-id="e5c1e-190">如果你的设备支持的 Wi-fi 连接，并且你已连接到它的显示，你将需要：</span><span class="sxs-lookup"><span data-stu-id="e5c1e-190">If your device supports Wi-Fi connectivity and you've connected a display to it, you'll need to:</span></span>

1. <span data-ttu-id="e5c1e-191">转到默认应用程序并单击设置按钮旁边的时钟。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-191">Go into your default application and click the settings button next to the clock.</span></span>
2. <span data-ttu-id="e5c1e-192">在设置页上选择_网络和 Wi-fi_。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-192">On the settings page, select _Network and Wi-Fi_.</span></span>
3. <span data-ttu-id="e5c1e-193">你的设备将开始扫描无线网络。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-193">Your device will begin scanning for wireless networks.</span></span>
4. <span data-ttu-id="e5c1e-194">一旦你的网络会显示此列表中，选择它，然后单击_Connect_。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-194">Once your network appears in this list, select it and click _Connect_.</span></span>

<span data-ttu-id="e5c1e-195">如果尚未连接显示，并且想要通过 Wi-fi 连接，你将需要：</span><span class="sxs-lookup"><span data-stu-id="e5c1e-195">If you haven't connected a display and would like to connect via Wi-Fi, you'll need to:</span></span>

1. <span data-ttu-id="e5c1e-196">转到 IoT 仪表板，并单击_我的设备_。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-196">Go to the IoT Dashboard and click on _My Devices_.</span></span>
2. <span data-ttu-id="e5c1e-197">查找从列表中未配置开发板。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-197">Find your unconfigured board from the list.</span></span> <span data-ttu-id="e5c1e-198">其名称开头"AJ_"...(例如 AJ_58EA6C68)。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-198">Its name will begin with "AJ_"... (e.g. AJ_58EA6C68).</span></span> <span data-ttu-id="e5c1e-199">如果看不到开发板出现几分钟后，请尝试重新启动你的板。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-199">If you don't see your board appear after a few minutes, try rebooting your board.</span></span>
3. <span data-ttu-id="e5c1e-200">单击_配置设备_并输入你的网络凭据。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-200">Click on _Configure Device_ and enter your network credentials.</span></span> <span data-ttu-id="e5c1e-201">这将连接到网络的开发板。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-201">This will connect your board to the network.</span></span>

> [!NOTE]
> <span data-ttu-id="e5c1e-202">您的计算机上的 Wifi 将需要打开以便找到其他网络。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-202">Wifi on your computer will need to be turned on in order to find other networks.</span></span>

## <a name="connecting-to-windows-device-portal"></a><span data-ttu-id="e5c1e-203">连接到 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="e5c1e-203">Connecting to Windows Device Portal</span></span>

<span data-ttu-id="e5c1e-204">使用[Windows Device Portal](../../manage-your-device/DevicePortal.md)通过 web 浏览器连接你的设备。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-204">Use the [Windows Device Portal](../../manage-your-device/DevicePortal.md) to connect your device through a web browser.</span></span> <span data-ttu-id="e5c1e-205">设备门户提供有价值的配置和设备管理功能。</span><span class="sxs-lookup"><span data-stu-id="e5c1e-205">The device portal makes valuable configuration and device management capabilities available.</span></span> 

