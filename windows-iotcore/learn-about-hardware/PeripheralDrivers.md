---
title: 安装 USB 外围设备驱动程序
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何创建驱动程序包并在设备上安装第三方驱动程序。
keywords: windows iot、 USB 驱动程序、 USB 外围设备
ms.openlocfilehash: dd7eec9defc676bb84efe988d771794d9bb7c9ef
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510939"
---
# <a name="install-usb-peripheral-drivers"></a><span data-ttu-id="3b140-104">安装 USB 外围设备驱动程序</span><span class="sxs-lookup"><span data-stu-id="3b140-104">Install USB peripheral drivers</span></span>
<span data-ttu-id="3b140-105">请按照以下步骤来添加用于外围设备，例如 USB 移动宽带调制解调器、 打印机、 扫描仪等第三方驱动程序 (usb)。</span><span class="sxs-lookup"><span data-stu-id="3b140-105">Follow the steps below to add third-party drivers (usb) for peripheral devices such as USB Mobile broadband modems, printers, scanners etc.</span></span> 

## <a name="step-1-get-drivers-from-pc"></a><span data-ttu-id="3b140-106">第 1 步：从 PC 获得驱动程序</span><span class="sxs-lookup"><span data-stu-id="3b140-106">Step 1: Get Drivers from PC</span></span>
___
<span data-ttu-id="3b140-107">此步骤将获取 x86 版本的驱动程序从 PC。</span><span class="sxs-lookup"><span data-stu-id="3b140-107">The Step is to get the x86 version of the drivers from PC.</span></span> <span data-ttu-id="3b140-108">对于 ARM，请联系外围设备的供应商来获取 sys/inf 文件。</span><span class="sxs-lookup"><span data-stu-id="3b140-108">For ARM, please contact the supplier of the peripheral to get the sys/inf files.</span></span>


1. <span data-ttu-id="3b140-109">将设备连接到 windows PC</span><span class="sxs-lookup"><span data-stu-id="3b140-109">Connect the device to the windows PC</span></span>

2. <span data-ttu-id="3b140-110">在 PC 上安装设备驱动程序</span><span class="sxs-lookup"><span data-stu-id="3b140-110">Install the driver for the device on the PC</span></span>

3. <span data-ttu-id="3b140-111">转到设备管理器中，选择此设备 （在通用串行总线控制器下所列） 和右键单击并选择属性。</span><span class="sxs-lookup"><span data-stu-id="3b140-111">Go to Device Manager, select this device (listed under Universal Serial Bus controllers) and right click and select Properties.</span></span>

4. <span data-ttu-id="3b140-112">转到属性窗口中的驱动程序选项卡，然后单击驱动程序详细信息。</span><span class="sxs-lookup"><span data-stu-id="3b140-112">Go to Driver tab in the Properties window, and click on Driver Details.</span></span> <span data-ttu-id="3b140-113">请注意那里列出的 sys 文件。</span><span class="sxs-lookup"><span data-stu-id="3b140-113">Note the sys files listed there.</span></span>

5. <span data-ttu-id="3b140-114">中的 sys 文件复制`C:\Windows\system32`和 inf 文件从还相关的`C:\Windows\Inf`。</span><span class="sxs-lookup"><span data-stu-id="3b140-114">Copy the sys files from `C:\Windows\system32` and also the related inf file from `C:\Windows\Inf`.</span></span> <span data-ttu-id="3b140-115">您可以查找的 inf 文件通过在 sys 中的文件引用`.inf`文件。</span><span class="sxs-lookup"><span data-stu-id="3b140-115">You can find the inf file by searcing for the sys file reference in the `.inf` files.</span></span> <span data-ttu-id="3b140-116">可能需要将 Inf 中列出的其他文件复制，并且将在创建时使用的 inf_filelist.txt 文件列出这些`inf2pkg.cmd`在下一步。</span><span class="sxs-lookup"><span data-stu-id="3b140-116">You may need to copy additional files listed in the Inf and these will be listed in the inf_filelist.txt file created when using  `inf2pkg.cmd` in the next step.</span></span>


## <a name="step-2-create-a-driver-package"></a><span data-ttu-id="3b140-117">步骤 2：创建驱动程序包</span><span class="sxs-lookup"><span data-stu-id="3b140-117">Step 2: Create a driver package</span></span>
___

<span data-ttu-id="3b140-118">驱动程序包的驱动程序的 Inf 文件到包含引用 (InfSource)，并还列出了在 Inf 文件中引用的所有文件。</span><span class="sxs-lookup"><span data-stu-id="3b140-118">The Driver package contains the references(InfSource)to the Inf file for the driver and also lists all the files referenced in the Inf file.</span></span> <span data-ttu-id="3b140-119">可以编写驱动程序。 使用 wm.xml[新建 IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md)。</span><span class="sxs-lookup"><span data-stu-id="3b140-119">You can author the driver .wm.xml using [New-IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md).</span></span>

<span data-ttu-id="3b140-120">[新 IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md)创建包 xml 文件，并还直接生成 cab 文件。</span><span class="sxs-lookup"><span data-stu-id="3b140-120">[New-IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) creates the package xml file and also builds the cab file directly.</span></span>

> [!NOTE]
> <span data-ttu-id="3b140-121">仅支持 Windows IoT Core[通用 INF 和通用驱动程序](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers)。</span><span class="sxs-lookup"><span data-stu-id="3b140-121">Windows IoT Core only supports [Universal INF and Universal Drivers](https://docs.microsoft.com/en-us/windows-hardware/drivers/develop/getting-started-with-universal-drivers).</span></span>


<span data-ttu-id="3b140-122">另请参阅：[示例驱动程序包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO)</span><span class="sxs-lookup"><span data-stu-id="3b140-122">See also: [Sample Driver Package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO)</span></span> 

## <a name="step-3-install-on-device"></a><span data-ttu-id="3b140-123">步骤 3:在设备上安装</span><span class="sxs-lookup"><span data-stu-id="3b140-123">Step 3: Install on device</span></span>
___

* <span data-ttu-id="3b140-124">连接到设备 ([使用 SSH](../connect-your-device/ssh.md)或[使用 Powershell](../connect-your-device/powershell.md))</span><span class="sxs-lookup"><span data-stu-id="3b140-124">Connect to the device ([using SSH](../connect-your-device/ssh.md) or [using Powershell](../connect-your-device/powershell.md))</span></span>
* <span data-ttu-id="3b140-125">复制<filename>到目录的设备的.cab 文件说 C:\OemInstall</span><span class="sxs-lookup"><span data-stu-id="3b140-125">Copy the <filename>.cab file to the device to a directory say C:\OemInstall</span></span>
* <span data-ttu-id="3b140-126">启动包使用的临时`applyupdate -stage C:\OemInstall\<filename>.cab`。</span><span class="sxs-lookup"><span data-stu-id="3b140-126">Initiate staging of the package using `applyupdate -stage C:\OemInstall\<filename>.cab`.</span></span> <span data-ttu-id="3b140-127">请注意，此步骤被重复的每个包，当有多个包安装时。</span><span class="sxs-lookup"><span data-stu-id="3b140-127">Note that this step is be repeated for each package, when you have multiple packages to install.</span></span>
* <span data-ttu-id="3b140-128">提交使用的包`applyupdate -commit`。</span><span class="sxs-lookup"><span data-stu-id="3b140-128">Commit the packages using `applyupdate -commit`.</span></span>

<span data-ttu-id="3b140-129">设备将重新启动进入更新 OS （显示齿轮） 来安装包，并将再次重新启动到主操作系统。</span><span class="sxs-lookup"><span data-stu-id="3b140-129">The device will reboot into the update OS (showing gears) to install the packages and will reboot again to main OS.</span></span> <span data-ttu-id="3b140-130">此过程可能需要几分钟。</span><span class="sxs-lookup"><span data-stu-id="3b140-130">This process can take a few minutes.</span></span>

## <a name="step-4-check-status-of-driver"></a><span data-ttu-id="3b140-131">步骤 4：检查驱动程序的状态</span><span class="sxs-lookup"><span data-stu-id="3b140-131">Step 4: Check status of driver</span></span>
___

* <span data-ttu-id="3b140-132">启动[Powershell](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="3b140-132">Launch the [Powershell](../connect-your-device/PowerShell.md)</span></span>
* <span data-ttu-id="3b140-133">就可以使用以下 Powershell commandlet 安装驱动程序的状态</span><span class="sxs-lookup"><span data-stu-id="3b140-133">You can get the status of the installed drivers using the following Powershell commandlets</span></span>

    * [<span data-ttu-id="3b140-134">Get-PnpDevice</span><span class="sxs-lookup"><span data-stu-id="3b140-134">Get-PnpDevice</span></span>](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdevice?view=win10-ps)
    * [<span data-ttu-id="3b140-135">Get-PnpDeviceProperty</span><span class="sxs-lookup"><span data-stu-id="3b140-135">Get-PnpDeviceProperty</span></span>](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdeviceproperty?view=win10-ps)
    
