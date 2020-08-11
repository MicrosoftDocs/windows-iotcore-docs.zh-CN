---
title: Windows CE 应用容器概述
ms.date: 08/11/2020
ms.topic: article
description: Windows CE 应用容器迁移技术
keywords: Windows 10 IoT Core，Windows CE，应用程序迁移，cepal
ms.openlocfilehash: 8c64db4a4cd41217c88590600dfbb2781121f9b8
ms.sourcegitcommit: 05278f1a522ed498900ce15b98bdd4389b5dde55
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88081772"
---
# <a name="an-overview-of-the-windows-ce-app-container"></a>Windows CE 应用容器概述
Microsoft 为 embedded 设备提供了平台和操作系统，数十年。 随着 Windows 10 IoT 等新产品/服务的推出，我们的客户和合作伙伴对这些操作系统提供的高级安全性、平台和云连接功能的兴趣越来越大。 从大多数早期版本的 Windows （如 Windows XP 和 Windows 7）迁移的客户可以轻松完成此操作，因为二进制兼容的应用程序。 其他操作系统（如 Windows CE）需要设备构建者来修改源代码。 迁移此类应用程序可能会很困难。

为了帮助这些客户移动到 Windows 10 IoT 并充分利用智能边缘（包括人工智能和机器学习）的全部功能，Microsoft 开发了一项技术，使大多数客户可以在 Windows 10 IoT 上运行其现有的、未修改的 Windows CE 应用程序，同时他们会继续投入更新应用程序。 可以在 IoT Show 剧集<a href="https://channel9.msdn.com/Shows/Internet-of-Things-Show/Modernizing-Windows-CE-Devices">现代化 Windows CE 设备</a>中了解有关此技术工作原理的详细信息。


## <a name="what-are-the-platform-requirements"></a>什么是平台要求？
Windows CE 应用迁移技术的工作原理是在 Windows 10 IoT Core 之上运行 Windows CE 2013 实例。

此解决方案适用于32位应用程序代码，需要与 Windows 10 IoT Core<a href="https://docs.microsoft.com/windows/iot-core/learn-about-hardware/socsandcustomboards">兼容</a>的 ARM32 或 x64 基本平台。
你应该使用平台生成器以及为 Windows 10 IoT Core 构建映像，来熟悉如何构建 Windows CE 2013 系统映像。


## <a name="is-windows-ce-app-container-the-right-choice-for-me"></a>Windows CE 应用容器是正确的选择吗？
对于需要使用 ARM32 或拥有需要多个开发周期才能迁移的复杂 CE 应用程序的设计，具有<a href="https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview">Windows 10 IoT Core Services</a>的 Ce 应用容器为逐步迁移提供了一个很好的解决方案。

开发人员在其 IoT 核心系统映像中放置了一个特殊的 ARM32 或 x86 Windows CE2013 平台映像，这些映像在 Windows 10 IoT Core 兼容硬件上部署。 开发人员可以通过 Windows 10 层开始添加功能，如 Azure 云连接或新式外设，还可以移动 CE 应用程序的某些部分，并将其用于在2029之前完成迁移。

对于 IoT 核心服务，IoT 核心操作系统会继续接收安全更新，直至2029。 而且，通过设备更新中心等功能，Oem 可以管理操作系统更新的时间，并可以轻松地分发应用程序更新。

但是，如果现有设计只需要几年的生产，最佳做法是继续 Windows CE 2013。
