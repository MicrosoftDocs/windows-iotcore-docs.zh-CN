---
title: 概述Windows CE 应用容器
ms.date: 08/12/2020
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows CE 应用容器迁移技术
keywords: Windows 10 IoT 核心版、Windows CE、应用程序迁移、cepal
ms.openlocfilehash: ca48c8934cbda168a8c21dbdad727d8b7eecc5dc
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230424"
---
# <a name="an-overview-of-the-windows-ce-app-container"></a>概述Windows CE 应用容器

数十年来，Microsoft 一直为嵌入式设备提供平台和操作系统。 随着 IoT Windows 10等新产品/服务推出，我们的客户和合作伙伴对这些 OS 提供的高级安全性、平台和云连接功能越来越感兴趣。 从大多数早期版本的 Windows（如 Windows XP 和 Windows 7）迁移的客户，由于二进制兼容的应用程序，因此几乎不做任何工作。 其他操作系统（例如 Windows CE）要求设备生成器修改源代码。 移植这样的应用程序可能很有挑战性。

为了帮助这些客户移动到 Windows 10 IoT，并充分利用智能边缘（包括人工智能和机器学习）的全部功能，Microsoft 开发了一项技术，使大多数客户在 Windows 10 IoT 上运行其现有的未经修改的 Windows CE 应用程序，同时继续投资更新其应用程序。 若要详细了解此技术的工作原理，可观看 IoT 展示集现代化[Windows CE设备](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Modernizing-Windows-CE-Devices)

## <a name="what-are-the-platform-requirements"></a>平台要求是什么

应用Windows CE技术的工作原理是，在 Windows 10 IoT 核心版 上运行 Windows CE 2013 Windows 10 IoT 核心版。

该解决方案适用于 32 位应用程序代码，并且需要与 32 位应用程序代码兼容的 ARM32 或 x64 Windows 10 IoT 核心版。 [](https://docs.microsoft.com/windows/iot-core/learn-about-hardware/socsandcustomboards)
你应熟悉使用平台生成器生成 Windows CE 2013 系统映像，以及生成适用于 Windows 10 IoT 核心版。

有关要求的详细列表，可在此文章中的先决条件下找到[](https://docs.microsoft.com/windows/iot-core/windows-ce-app-container-getting-started#prerequisites)，入门[CE 应用容器 。](https://docs.microsoft.com/windows/iot-core/windows-ce-app-container-getting-started)

## <a name="is-windows-ce-app-container-the-right-choice-for-me"></a>Windows CE 应用容器适合我

对于需要利用 ARM32 或具有需要多个开发周期进行迁移的复杂 CE 应用程序的设计，包含 Windows 10 IoT 核心版 Services 的 CE[应用容器为](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview)逐步迁移提供了一个很好的解决方案。

开发人员将特殊的 ARM32 或 x86 Windows CE2013 平台映像放在其 IoT 核心系统映像中，该映像部署在Windows 10 IoT 核心版硬件上。 开发人员可以通过 Windows 10 层开始添加 Azure 云连接或新式外围设备等功能，并且可以将部分 CE 应用程序移到另一层，并可以在 2029 年之前完成迁移。

使用 IoT 核心服务，Windows 10 IoT 核心版 OS 将继续接收安全更新，直到 2029 年。 借助 设备更新中心 等功能，OEM 可以轻松管理 OS 更新的计时以及分发应用程序更新。

有关入门迁移旅程的分步指南，请查看 [使用 CE](https://docs.microsoft.com/windows/iot-core/windows-ce-app-container-getting-started) 应用容器进行迁移。

但是，如果你的现有设计只需要再进行一些年的生产，那么最好在 2013 年 1 月Windows CE。 使用 Windows 10 IoT 核心版 上的 Windows CE，进一步Windows CE 应用容器[进一步Windows 10 IoT 核心版。](https://techcommunity.microsoft.com/t5/internet-of-things/moving-forward-with-windows-ce-using-the-windows-ce-app/ba-p/1582360)
