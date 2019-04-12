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
# <a name="use-dism-to-flash-windows-10-iot-core"></a>使用 DISM 闪烁，Windows 10 IoT 核心版

> [!NOTE]
> DISM 脱机处理不受支持。 如果您尝试装入 FFU IoT core，您将收到以下错误消息：不支持请求。
> 映像没有名称，并很可能是移动/Onecore FFU，目前不支持的。
> FfuMountImage #160 失败，出现 0x80070032。

## <a name="an-alternative-method-to-iot-dashboard-for-flashing-a-ffu"></a>有关闪烁 FFU 到 IoT 仪表板的替代方法

可以使用部署映像服务和 Management(Dism.exe) 闪烁 SD 卡上，Windows 10 IoT Core。 你将需要与你的设备类型相对应的 FFU 的图像文件。 

* 打开管理员命令提示符并导航到包含你的本地 flash.ffu 文件的文件夹。

* 插件在 SD 卡为你的计算机。 

* 找到 SD 卡在你的计算机上所显示的磁盘编号。  在下一步中应用映像时，将会用到此磁盘编号。  为此，你可以使用 diskpart 实用工具。  运行以下命令：

        c:\FFUFolder>diskpart

        DISKPART>list disk

    它应列出连接到计算机的所有存储设备。 

    ![DISM 列表磁盘](../media/Dism/DiskpartListDisk.png)

    请注意的磁盘编号并键入 exit 退出 diskpart。 

        DISKPART>exit

* 使用管理员命令提示符下，将此映像应用到 SD 卡通过运行以下命令 (确保 PhysicalDriveN 替换为在上一步骤中，例如找到的值，在这种情况下 SD 卡是磁盘编号 4，因此，我们将使用`/ApplyDrive:\\.\PhysicalDrive4`下图）

        dism.exe /Apply-Image /ImageFile:"[FULLPATH]\flash.ffu" /ApplyDrive:\\.\PhysicalDriveN /SkipPlatformCheck

* 单击任务栏中的“安全删除硬件”图标，然后选择你的 USB SD 读卡器以将其从系统中安全删除。  如果未正确执行此操作，可能导致映像损坏。
