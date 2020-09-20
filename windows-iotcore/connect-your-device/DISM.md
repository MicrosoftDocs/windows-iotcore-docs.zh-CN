---
title: 使用 DISM 闪烁 Windows 10 IoT Core
author: bfjelds
ms.author: bfjelds
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 DISM 将 Windows 10 IoT Core 闪存到微型 SD 卡。
keywords: windows iot，DISM，部署映像服务管理，SD 卡，flash，OS
ms.openlocfilehash: a83b81b0f0a18625736b19429014f0e2ea222c33
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782609"
---
# <a name="use-dism-to-flash-windows-10-iot-core"></a>使用 DISM 闪烁 Windows 10 IoT Core

> [!NOTE]
> 不支持 DISM 脱机服务。 如果尝试装载 FFU for IoT Core，则会收到以下错误消息：请求不受支持。
> 该映像没有名称，可能是当前不支持的移动/Onecore FFU。
> FfuMountImage # 160 失败，0x80070032 为。

## <a name="an-alternative-method-to-iot-dashboard-for-flashing-an-ffu"></a>IoT 面板的一种替代方法，用于闪烁 FFU

你可以使用部署映像服务和管理 ( # A0) 在 SD 卡上闪存 Windows 10 IoT Core。 需要一个与设备类型相对应的 FFU 映像文件。 

* 打开管理员命令提示符并导航到包含本地 ffu 文件的文件夹。

* 将 SD 卡插入到计算机。 

* 查找计算机上 SD 卡所在的磁盘编号。  在下一步中应用映像时，将使用此项。  为此，可以使用 diskpart 实用工具。  运行以下命令：

        c:\FFUFolder>diskpart

        DISKPART>list disk

    它应该列出连接到计算机的所有存储设备。 

    ![DISM 列出磁盘](../media/Dism/DiskpartListDisk.png)

    记下磁盘号，然后键入 exit 退出 diskpart。 

        DISKPART>exit

* 使用管理员命令提示符，运行以下命令，将映像应用到 SD 卡 (确保将 PhysicalDriveN 替换为上一步中找到的值，例如，在本例中，SD 卡是磁盘号4，因此我们将使用  `/ApplyDrive:\\.\PhysicalDrive4` 以下) 

        dism.exe /Apply-Image /ImageFile:"[FULLPATH]\flash.ffu" /ApplyDrive:\\.\PhysicalDriveN /SkipPlatformCheck

* 单击任务栏中的 "安全删除硬件" 图标，然后选择 USB SD 卡读卡器以安全地将其从系统中删除。  否则，可能会导致映像损坏。
