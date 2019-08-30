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
# <a name="use-dism-to-flash-windows-10-iot-core"></a>使用 DISM 闪烁 Windows 10 IoT Core

> [!NOTE]
> 不支持 DISM 脱机服务。 如果尝试装载 FFU for IoT Core, 会收到以下错误:请求不受支持。
> 该映像没有名称, 可能是当前不支持的移动/Onecore FFU。
> FfuMountImage # 160 失败, 0x80070032 为。

## <a name="an-alternative-method-to-iot-dashboard-for-flashing-a-ffu"></a>IoT 面板的一种替代方法, 用于闪烁 FFU

你可以使用部署映像服务和管理 (Dism.exe) 在 SD 卡上闪存 Windows 10 IoT Core。 你将需要与设备类型相对应的 FFU 映像文件。 

* 打开管理员命令提示符并导航到包含本地 ffu 文件的文件夹。

* 将 SD 卡插入到计算机。 

* 找到 SD 卡在你的计算机上所显示的磁盘编号。  在下一步中应用映像时，将会用到此磁盘编号。  为此，你可以使用 diskpart 实用工具。  运行以下命令：

        c:\FFUFolder>diskpart

        DISKPART>list disk

    它应该列出连接到计算机的所有存储设备。 

    ![DISM 列出磁盘](../media/Dism/DiskpartListDisk.png)

    记下磁盘号, 然后键入 exit 退出 diskpart。 

        DISKPART>exit

* 使用管理员命令提示符, 运行以下命令, 将映像应用到 SD 卡 (请确保将 PhysicalDriveN 替换为你在上一步中找到的值, 例如, 在本例中, SD 卡是磁盘号 4, 因此我们将使用`/ApplyDrive:\\.\PhysicalDrive4`在线订购

        dism.exe /Apply-Image /ImageFile:"[FULLPATH]\flash.ffu" /ApplyDrive:\\.\PhysicalDriveN /SkipPlatformCheck

* 单击任务栏中的“安全删除硬件”图标，然后选择你的 USB SD 读卡器以将其从系统中安全删除。  如果未正确执行此操作，可能导致映像损坏。
