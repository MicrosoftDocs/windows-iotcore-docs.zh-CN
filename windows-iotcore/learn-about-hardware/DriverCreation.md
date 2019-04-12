---
title: 通用驱动程序创建
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 了解如何创建通用驱动程序以在设备上启用单个驱动程序创建包。
keywords: windows iot、 通用驱动程序，驱动程序，Windows 10，UWP
ms.openlocfilehash: 839a742598481e3ff70e3a0ccf1ff072bd62e051
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510625"
---
# <a name="universal-driver-creation"></a>通用驱动程序创建

本文档将指导你通过 IoT Core 设备创建通用驱动程序。

通用驱动程序，可以创建运行跨多个运行基于 UWP 的 Windows 10，包括 IoT Core 版本的设备类型的单个驱动程序包。

此驱动程序包包含通用 INF 文件和多个二进制文件。 每个的要求如下所示：
- 只能使用通用 INF 文件[INF 基于 UWP 的 Windows 版本上受支持的语法的子集](https://docs.microsoft.com/windows-hardware/drivers/install/using-a-universal-inf-file#which-inf-sections-are-invalid-in-a-universal-inf-file)。 在编写您的 INF 文件，使用[InfVerif 工具](https://docs.microsoft.com/windows-hardware/drivers/devtest/infverif)以验证是否在文件遵循该语法。

- 基于 UWP 的 Windows 10 （标记为通用文档参考页上） 的版本上支持的设备驱动程序接口，可以仅使用二进制文件：[KMDF](https://docs.microsoft.com/windows-hardware/drivers/wdf/index)， [UMDF 2](https://docs.microsoft.com/windows-hardware/drivers/wdf/getting-started-with-umdf-version-2)，或 Windows 驱动程序模型 (WDM)。 它们也只能调用 OneCore 子集中包括的 Api。 使用[ApiValidator 工具](https://docs.microsoft.com/windows-hardware/drivers/develop/validating-universal-drivers)以验证您的二进制文件的 Api 调用都有效。

若要了解如何**Visual Studio 中创建驱动程序包**，请访问[创建驱动程序包](https://docs.microsoft.com/windows-hardware/drivers/develop/creating-a-driver-package)

如果想要**示例，帮助你在 IoT Core 上创建通用驱动程序**，请访问我们[通用驱动程序示例](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab)

## <a name="additional-universal-driver-resources"></a>其他的通用驱动程序资源

1. 有关其他详细信息**设计原则**并**最佳做法**开发时的通用驱动程序包，请访问[通用驱动程序入门](https://docs.microsoft.com/windows-hardware/drivers/develop/getting-started-with-universal-drivers)

2. 获取帮助**调试您的通用驱动程序**，请访问[调试通用 Windows 驱动程序](https://docs.microsoft.com/windows-hardware/drivers/develop/debugging-a-universal-driver)。

