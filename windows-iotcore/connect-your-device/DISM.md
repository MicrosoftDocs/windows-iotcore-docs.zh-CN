---
title: 使用 DISM 闪烁 Windows 10 IoT Core
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 DISM 将 Windows 10 IoT Core 闪存到微型 SD 卡。
keywords: windows iot, DISM, 部署映像服务管理, SD 卡, flash, OS
ms.openlocfilehash: 1fd075037b97399762aea1b0b844a477337cbc5d
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168929"
---
# <a name="use-dism-to-flash-windows-10-iot-core"></a><span data-ttu-id="a84b1-104">使用 DISM 闪烁 Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="a84b1-104">Use DISM to flash Windows 10 IoT Core</span></span>

> [!NOTE]
> <span data-ttu-id="a84b1-105">不支持 DISM 脱机服务。</span><span class="sxs-lookup"><span data-stu-id="a84b1-105">DISM offline servicing isn't supported.</span></span> <span data-ttu-id="a84b1-106">如果尝试装载 FFU for IoT Core, 会收到以下错误:请求不受支持。</span><span class="sxs-lookup"><span data-stu-id="a84b1-106">You will receive the error below if you try to mount an FFU for IoT Core: The request is not supported.</span></span>
> <span data-ttu-id="a84b1-107">该映像没有名称, 可能是当前不支持的移动/Onecore FFU。</span><span class="sxs-lookup"><span data-stu-id="a84b1-107">The image doesn't have a name and it's likely to be a Mobile/Onecore FFU, which is currently not supported.</span></span>
> <span data-ttu-id="a84b1-108">FfuMountImage # 160 失败, 0x80070032 为。</span><span class="sxs-lookup"><span data-stu-id="a84b1-108">FfuMountImage#160 failed with 0x80070032.</span></span>

## <a name="an-alternative-method-to-iot-dashboard-for-flashing-a-ffu"></a><span data-ttu-id="a84b1-109">IoT 面板的一种替代方法, 用于闪烁 FFU</span><span class="sxs-lookup"><span data-stu-id="a84b1-109">An alternative method to IoT Dashboard for Flashing a FFU</span></span>

<span data-ttu-id="a84b1-110">你可以使用部署映像服务和管理 (Dism.exe) 在 SD 卡上闪存 Windows 10 IoT Core。</span><span class="sxs-lookup"><span data-stu-id="a84b1-110">You can use Deployment Image Servicing and Management(Dism.exe) to flash Windows 10 IoT Core on your SD card.</span></span> <span data-ttu-id="a84b1-111">你将需要与设备类型相对应的 FFU 映像文件。</span><span class="sxs-lookup"><span data-stu-id="a84b1-111">You will need a FFU image file corresponding to your device type.</span></span> 

* <span data-ttu-id="a84b1-112">打开管理员命令提示符并导航到包含本地 ffu 文件的文件夹。</span><span class="sxs-lookup"><span data-stu-id="a84b1-112">Open an administrator command prompt and navigate to the folder containing your local flash.ffu file.</span></span>

* <span data-ttu-id="a84b1-113">将 SD 卡插入到计算机。</span><span class="sxs-lookup"><span data-stu-id="a84b1-113">Plug-in your SD card to your machine.</span></span> 

* <span data-ttu-id="a84b1-114">找到 SD 卡在你的计算机上所显示的磁盘编号。</span><span class="sxs-lookup"><span data-stu-id="a84b1-114">Find the disk number that your SD card is on your computer.</span></span>  <span data-ttu-id="a84b1-115">在下一步中应用映像时，将会用到此磁盘编号。</span><span class="sxs-lookup"><span data-stu-id="a84b1-115">This will be used when the image is applied in the next step.</span></span>  <span data-ttu-id="a84b1-116">为此，你可以使用 diskpart 实用工具。</span><span class="sxs-lookup"><span data-stu-id="a84b1-116">To do this, you can use the diskpart utility.</span></span>  <span data-ttu-id="a84b1-117">运行以下命令：</span><span class="sxs-lookup"><span data-stu-id="a84b1-117">Run the following commands:</span></span>

        c:\FFUFolder>diskpart

        DISKPART>list disk

    <span data-ttu-id="a84b1-118">它应该列出连接到计算机的所有存储设备。</span><span class="sxs-lookup"><span data-stu-id="a84b1-118">It should list all the storage devices attached to the computer.</span></span> 

    ![DISM 列出磁盘](../media/Dism/DiskpartListDisk.png)

    <span data-ttu-id="a84b1-120">记下磁盘号, 然后键入 exit 退出 diskpart。</span><span class="sxs-lookup"><span data-stu-id="a84b1-120">Note the disk number and type exit to exit diskpart.</span></span> 

        DISKPART>exit

* <span data-ttu-id="a84b1-121">使用管理员命令提示符, 运行以下命令, 将映像应用到 SD 卡 (请确保将 PhysicalDriveN 替换为你在上一步中找到的值, 例如, 在本例中, SD 卡是磁盘号 4, 因此我们将使用`/ApplyDrive:\\.\PhysicalDrive4`在线订购</span><span class="sxs-lookup"><span data-stu-id="a84b1-121">Using the administrator command prompt, apply the image to your SD card by running the following command (be sure to replace PhysicalDriveN with the value you found in the previous step, for example, in this case SD card is disk number 4, so we will use  `/ApplyDrive:\\.\PhysicalDrive4` below)</span></span>

        dism.exe /Apply-Image /ImageFile:"[FULLPATH]\flash.ffu" /ApplyDrive:\\.\PhysicalDriveN /SkipPlatformCheck

* <span data-ttu-id="a84b1-122">单击任务栏中的“安全删除硬件”图标，然后选择你的 USB SD 读卡器以将其从系统中安全删除。</span><span class="sxs-lookup"><span data-stu-id="a84b1-122">Click on the "Safely Remove Hardware" icon in your task tray and select your USB SD card reader to safely remove it from the system.</span></span>  <span data-ttu-id="a84b1-123">如果未正确执行此操作，可能导致映像损坏。</span><span class="sxs-lookup"><span data-stu-id="a84b1-123">Failing to do this can cause corruption of the image.</span></span>
