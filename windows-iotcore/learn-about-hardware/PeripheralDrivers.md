---
title: 安装 USB 外设驱动程序
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何创建驱动程序包，以及如何在设备上安装第三方驱动程序。
keywords: windows iot，USB 驱动程序，外围设备，USB
ms.openlocfilehash: 7a218be05c6bdeed29d8c8fec84b8aa7659261f2
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655784"
---
# <a name="install-usb-peripheral-drivers"></a><span data-ttu-id="8fe39-104">安装 USB 外设驱动程序</span><span class="sxs-lookup"><span data-stu-id="8fe39-104">Install USB peripheral drivers</span></span>
<span data-ttu-id="8fe39-105">按照以下步骤为外围设备（如 USB 移动宽带调制解调器、打印机、扫描仪等）添加 (USB) 的第三方驱动程序。</span><span class="sxs-lookup"><span data-stu-id="8fe39-105">Follow the steps below to add third-party drivers (USB) for peripheral devices such as USB Mobile broadband modems, printers, scanners etc.</span></span>

## <a name="step-1-get-drivers-from-pc"></a><span data-ttu-id="8fe39-106">步骤1：从电脑获取驱动程序</span><span class="sxs-lookup"><span data-stu-id="8fe39-106">Step 1: Get Drivers from PC</span></span>
___
<span data-ttu-id="8fe39-107">步骤是从 PC 获取驱动程序的 x86 版本。</span><span class="sxs-lookup"><span data-stu-id="8fe39-107">The Step is to get the x86 version of the drivers from PC.</span></span> <span data-ttu-id="8fe39-108">对于 ARM，请联系外围设备的供应商以获取 sys/inf 文件。</span><span class="sxs-lookup"><span data-stu-id="8fe39-108">For ARM, please contact the supplier of the peripheral to get the sys/inf files.</span></span>


1. <span data-ttu-id="8fe39-109">将设备连接到 windows 电脑</span><span class="sxs-lookup"><span data-stu-id="8fe39-109">Connect the device to the windows PC</span></span>

2. <span data-ttu-id="8fe39-110">在电脑上安装设备驱动程序</span><span class="sxs-lookup"><span data-stu-id="8fe39-110">Install the driver for the device on the PC</span></span>

3. <span data-ttu-id="8fe39-111">请参阅设备管理器，选择 "通用串行总线控制器" 下列出的此设备 () ，然后右键单击并选择 "属性"。</span><span class="sxs-lookup"><span data-stu-id="8fe39-111">Go to Device Manager, select this device (listed under Universal Serial Bus controllers) and right click and select Properties.</span></span>

4. <span data-ttu-id="8fe39-112">在属性窗口中转到 "驱动程序" 选项卡，然后单击 "驱动程序详细信息"。</span><span class="sxs-lookup"><span data-stu-id="8fe39-112">Go to Driver tab in the Properties window, and click on Driver Details.</span></span> <span data-ttu-id="8fe39-113">请注意列出的 sys 文件。</span><span class="sxs-lookup"><span data-stu-id="8fe39-113">Note the sys files listed there.</span></span>

5. <span data-ttu-id="8fe39-114">从复制 sys 文件 `C:\Windows\system32` ，并从中复制相关的 inf 文件 `C:\Windows\Inf` 。</span><span class="sxs-lookup"><span data-stu-id="8fe39-114">Copy the sys files from `C:\Windows\system32` and also the related inf file from `C:\Windows\Inf`.</span></span> <span data-ttu-id="8fe39-115">可以通过在文件中搜索 sys 文件引用来查找 inf 文件 `.inf` 。</span><span class="sxs-lookup"><span data-stu-id="8fe39-115">You can find the inf file by searching for the sys file reference in the `.inf` files.</span></span> <span data-ttu-id="8fe39-116">你可能需要复制 Inf 中列出的其他文件，这些文件将在  `inf2pkg.cmd` 下一步中使用时创建的 inf_filelist.txt 文件中列出。</span><span class="sxs-lookup"><span data-stu-id="8fe39-116">You may need to copy additional files listed in the Inf and these will be listed in the inf_filelist.txt file created when using  `inf2pkg.cmd` in the next step.</span></span>


## <a name="step-2-create-a-driver-package"></a><span data-ttu-id="8fe39-117">步骤2：创建驱动程序包</span><span class="sxs-lookup"><span data-stu-id="8fe39-117">Step 2: Create a driver package</span></span>
___

<span data-ttu-id="8fe39-118">驱动程序包包含 (InfSource) 到驱动程序的 Inf 文件的引用，还列出了 Inf 文件中引用的所有文件。</span><span class="sxs-lookup"><span data-stu-id="8fe39-118">The Driver package contains the references(InfSource)to the Inf file for the driver and also lists all the files referenced in the Inf file.</span></span> <span data-ttu-id="8fe39-119">您可以使用 [IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md)创作驱动程序 .wm.xml。</span><span class="sxs-lookup"><span data-stu-id="8fe39-119">You can author the driver .wm.xml using [Add-IoTDriverPackage](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/Add-IoTDriverPackage.md).</span></span>

<span data-ttu-id="8fe39-120">[IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) 创建包 xml 文件，还直接生成 cab 文件。</span><span class="sxs-lookup"><span data-stu-id="8fe39-120">[New-IoTInf2Cab](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/IoTCoreImaging/Docs/New-IoTInf2Cab.md) creates the package xml file and also builds the cab file directly.</span></span>

> [!NOTE]
> <span data-ttu-id="8fe39-121">Windows IoT Core 仅支持 [通用 INF 和通用驱动程序](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)。</span><span class="sxs-lookup"><span data-stu-id="8fe39-121">Windows IoT Core only supports [Universal INF and Universal Drivers](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers).</span></span>


<span data-ttu-id="8fe39-122">另请参阅： [示例驱动程序包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO)</span><span class="sxs-lookup"><span data-stu-id="8fe39-122">See also: [Sample Driver Package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/BSP/CustomRpi2/Packages/CustomRPi2.GPIO)</span></span>

## <a name="step-3-install-on-device"></a><span data-ttu-id="8fe39-123">步骤3：在设备上安装</span><span class="sxs-lookup"><span data-stu-id="8fe39-123">Step 3: Install on device</span></span>
___

* <span data-ttu-id="8fe39-124">[使用 SSH](../connect-your-device/ssh.md)或[PowerShell](../connect-your-device/powershell.md)连接到设备 () </span><span class="sxs-lookup"><span data-stu-id="8fe39-124">Connect to the device ([using SSH](../connect-your-device/ssh.md) or [using PowerShell](../connect-your-device/powershell.md))</span></span>
* <span data-ttu-id="8fe39-125">将 <filename> .cab 文件复制到该目录中，如 C:\OemInstall</span><span class="sxs-lookup"><span data-stu-id="8fe39-125">Copy the <filename>.cab file to the device to a directory say C:\OemInstall</span></span>
* <span data-ttu-id="8fe39-126">使用启动包的临时 `applyupdate -stage C:\OemInstall\<filename>.cab` 。</span><span class="sxs-lookup"><span data-stu-id="8fe39-126">Initiate staging of the package using `applyupdate -stage C:\OemInstall\<filename>.cab`.</span></span> <span data-ttu-id="8fe39-127">请注意，当你有多个要安装的包时，将对每个包重复此步骤。</span><span class="sxs-lookup"><span data-stu-id="8fe39-127">Note that this step is be repeated for each package, when you have multiple packages to install.</span></span>
* <span data-ttu-id="8fe39-128">使用提交包 `applyupdate -commit` 。</span><span class="sxs-lookup"><span data-stu-id="8fe39-128">Commit the packages using `applyupdate -commit`.</span></span>

<span data-ttu-id="8fe39-129">设备将重新启动到更新 OS (显示齿轮) 来安装包，并再次重新启动到主操作系统。</span><span class="sxs-lookup"><span data-stu-id="8fe39-129">The device will reboot into the update OS (showing gears) to install the packages and will reboot again to main OS.</span></span> <span data-ttu-id="8fe39-130">此过程会花费几分钟时间。</span><span class="sxs-lookup"><span data-stu-id="8fe39-130">This process can take a few minutes.</span></span>

## <a name="step-4-check-status-of-driver"></a><span data-ttu-id="8fe39-131">步骤4：检查驱动程序的状态</span><span class="sxs-lookup"><span data-stu-id="8fe39-131">Step 4: Check status of driver</span></span>
___

* <span data-ttu-id="8fe39-132">启动 [PowerShell](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="8fe39-132">Launch the [PowerShell](../connect-your-device/PowerShell.md)</span></span>
* <span data-ttu-id="8fe39-133">可以使用以下 PowerShell commandlet 获取已安装驱动程序的状态</span><span class="sxs-lookup"><span data-stu-id="8fe39-133">You can get the status of the installed drivers using the following PowerShell commandlets</span></span>

    * [<span data-ttu-id="8fe39-134">Pnp 设备</span><span class="sxs-lookup"><span data-stu-id="8fe39-134">Get-PnpDevice</span></span>](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdevice?view=win10-ps&preserve-view=true)
    * [<span data-ttu-id="8fe39-135">PnpDeviceProperty</span><span class="sxs-lookup"><span data-stu-id="8fe39-135">Get-PnpDeviceProperty</span></span>](https://docs.microsoft.com/powershell/module/pnpdevice/get-pnpdeviceproperty?view=win10-ps&preserve-view=true)
