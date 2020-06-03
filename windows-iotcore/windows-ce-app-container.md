---
title: Windows CE 应用容器概述
ms.date: 05/22/2020
ms.topic: article
description: 获取 Windows CE 应用容器的个人预览版的访问权限
keywords: Windows 10 IoT Core，Windows CE，应用程序迁移，cepal
ms.openlocfilehash: 9231e3def5c3da5efee49c1cd6026cca782058da
ms.sourcegitcommit: 7b9353b2bf60b242d70f0d2f21a4006439639194
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84274485"
---
# <a name="an-overview-of-the-windows-ce-app-container"></a>Windows CE 应用容器概述
Microsoft 为 embedded 设备提供了平台和操作系统，数十年。 随着 Windows 10 IoT 等新产品/服务的推出，我们的客户和合作伙伴对这些操作系统提供的高级安全性、平台和云连接功能的兴趣越来越大。 从大多数早期版本的 Windows （如 Windows XP 和 Windows 7）迁移的客户可以轻松完成此操作，因为二进制兼容的应用程序。 其他操作系统（如 Windows CE）需要设备构建者来修改源代码。 迁移此类应用程序可能会很困难。

为了帮助这些客户移动到 Windows 10 IoT 并充分利用智能边缘（包括人工智能和机器学习）的全部功能，Microsoft 正在开发一项技术，使大多数客户可以在 Windows 10 IoT 上运行其现有的、未修改的 Windows CE 应用程序，同时他们会继续投入更新应用程序。 可以在 IoT Show 剧集<a href="https://channel9.msdn.com/Shows/Internet-of-Things-Show/Modernizing-Windows-CE-Devices">现代化 Windows CE 设备</a>中了解有关此技术工作原理的详细信息。

## <a name="how-to-get-started-with-the-private-preview"></a>如何开始学习个人预览版

我们预计在今年晚些时候推出 Windows CE 应用容器技术作为<a href="https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iotcoreservicesoverview">Windows 10 IoT Core Services</a>的一部分。 但是，如果你是具有 Windows CE 解决方案的商业开发人员，想要开始评估该技术，请 <a href="mailto:cemigrat@microsoft.com">cemigrat@microsoft.com</a> 从你的公司电子邮件帐户联系以访问个人预览版。

## <a name="what-are-the-platform-requirements"></a>什么是平台要求？ 
Windows CE 应用迁移技术的工作原理是在 Windows 10 IoT Core 之上运行 Windows CE 2013 实例。 

此解决方案适用于32位应用程序代码，需要与 Windows 10 IoT Core<a href="https://docs.microsoft.com/en-us/windows/iot-core/learn-about-hardware/socsandcustomboards">兼容</a>的 ARM32 或 x64 基本平台。
你应该使用平台生成器以及为 Windows 10 IoT Core 构建映像，来熟悉如何构建 Windows CE 2013 系统映像。
