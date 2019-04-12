---
title: 使用 DISM 闪烁，Windows 10 IoT 核心版
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 DISM 闪烁到 micro SD 卡上，Windows 10 IoT Core。
keywords: windows iot，DISM、 部署映像维护服务管理、 SD 卡、 flash，OS
ms.openlocfilehash: 1fd075037b97399762aea1b0b844a477337cbc5d
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59512083"
---
# <a name="use-dism-to-flash-windows-10-iot-core"></a><span data-ttu-id="712c6-104">使用 DISM 闪烁，Windows 10 IoT 核心版</span><span class="sxs-lookup"><span data-stu-id="712c6-104">Use DISM to flash Windows 10 IoT Core</span></span>

> [!NOTE]
> <span data-ttu-id="712c6-105">DISM 脱机处理不受支持。</span><span class="sxs-lookup"><span data-stu-id="712c6-105">DISM offline servicing isn't supported.</span></span> <span data-ttu-id="712c6-106">如果您尝试装入 FFU IoT core，您将收到以下错误消息：不支持请求。</span><span class="sxs-lookup"><span data-stu-id="712c6-106">You will receive the error below if you try to mount an FFU for IoT Core: The request is not supported.</span></span>
> <span data-ttu-id="712c6-107">映像没有名称，并很可能是移动/Onecore FFU，目前不支持的。</span><span class="sxs-lookup"><span data-stu-id="712c6-107">The image doesn't have a name and it's likely to be a Mobile/Onecore FFU, which is currently not supported.</span></span>
> <span data-ttu-id="712c6-108">FfuMountImage #160 失败，出现 0x80070032。</span><span class="sxs-lookup"><span data-stu-id="712c6-108">FfuMountImage#160 failed with 0x80070032.</span></span>

## <a name="an-alternative-method-to-iot-dashboard-for-flashing-a-ffu"></a><span data-ttu-id="712c6-109">有关闪烁 FFU 到 IoT 仪表板的替代方法</span><span class="sxs-lookup"><span data-stu-id="712c6-109">An alternative method to IoT Dashboard for Flashing a FFU</span></span>

<span data-ttu-id="712c6-110">可以使用部署映像服务和 Management(Dism.exe) 闪烁 SD 卡上，Windows 10 IoT Core。</span><span class="sxs-lookup"><span data-stu-id="712c6-110">You can use Deployment Image Servicing and Management(Dism.exe) to flash Windows 10 IoT Core on your SD card.</span></span> <span data-ttu-id="712c6-111">你将需要与你的设备类型相对应的 FFU 的图像文件。</span><span class="sxs-lookup"><span data-stu-id="712c6-111">You will need a FFU image file corresponding to your device type.</span></span> 

* <span data-ttu-id="712c6-112">打开管理员命令提示符并导航到包含你的本地 flash.ffu 文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="712c6-112">Open an administrator command prompt and navigate to the folder containing your local flash.ffu file.</span></span>

* <span data-ttu-id="712c6-113">插件在 SD 卡为你的计算机。</span><span class="sxs-lookup"><span data-stu-id="712c6-113">Plug-in your SD card to your machine.</span></span> 

* <span data-ttu-id="712c6-114">找到 SD 卡在你的计算机上所显示的磁盘编号。</span><span class="sxs-lookup"><span data-stu-id="712c6-114">Find the disk number that your SD card is on your computer.</span></span>  <span data-ttu-id="712c6-115">在下一步中应用映像时，将会用到此磁盘编号。</span><span class="sxs-lookup"><span data-stu-id="712c6-115">This will be used when the image is applied in the next step.</span></span>  <span data-ttu-id="712c6-116">为此，你可以使用 diskpart 实用工具。</span><span class="sxs-lookup"><span data-stu-id="712c6-116">To do this, you can use the diskpart utility.</span></span>  <span data-ttu-id="712c6-117">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="712c6-117">Run the following commands:</span></span>

        c:\FFUFolder>diskpart

        DISKPART>list disk

    <span data-ttu-id="712c6-118">它应列出连接到计算机的所有存储设备。</span><span class="sxs-lookup"><span data-stu-id="712c6-118">It should list all the storage devices attached to the computer.</span></span> 

    ![DISM 列表磁盘](../media/Dism/DiskpartListDisk.png)

    <span data-ttu-id="712c6-120">请注意的磁盘编号并键入 exit 退出 diskpart。</span><span class="sxs-lookup"><span data-stu-id="712c6-120">Note the disk number and type exit to exit diskpart.</span></span> 

        DISKPART>exit

* <span data-ttu-id="712c6-121">使用管理员命令提示符下，将此映像应用到 SD 卡通过运行以下命令 (确保 PhysicalDriveN 替换为在上一步骤中，例如找到的值，在这种情况下 SD 卡是磁盘编号 4，因此，我们将使用`/ApplyDrive:\\.\PhysicalDrive4`下图）</span><span class="sxs-lookup"><span data-stu-id="712c6-121">Using the administrator command prompt, apply the image to your SD card by running the following command (be sure to replace PhysicalDriveN with the value you found in the previous step, for example, in this case SD card is disk number 4, so we will use  `/ApplyDrive:\\.\PhysicalDrive4` below)</span></span>

        dism.exe /Apply-Image /ImageFile:"[FULLPATH]\flash.ffu" /ApplyDrive:\\.\PhysicalDriveN /SkipPlatformCheck

* <span data-ttu-id="712c6-122">单击任务栏中的“安全删除硬件”图标，然后选择你的 USB SD 读卡器以将其从系统中安全删除。</span><span class="sxs-lookup"><span data-stu-id="712c6-122">Click on the "Safely Remove Hardware" icon in your task tray and select your USB SD card reader to safely remove it from the system.</span></span>  <span data-ttu-id="712c6-123">如果未正确执行此操作，可能导致映像损坏。</span><span class="sxs-lookup"><span data-stu-id="712c6-123">Failing to do this can cause corruption of the image.</span></span>
