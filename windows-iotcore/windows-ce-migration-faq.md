---
title: 常见问题-CE 迁移
ms.date: 09/25/2020
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows CE 应用容器迁移技术的常见问题
keywords: Windows 10 IoT 核心版，Windows CE，应用程序迁移，cepal，Windows CE 迁移常见问题解答
ms.openlocfilehash: 7b40549773d0dff883f67dae49a8aae5dfb70c15
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230234"
---
# <a name="ce-migration---frequently-asked-questions"></a>CE 迁移-常见问题
在本部分中，我们将介绍常见问题 (常见问题解答) 有关 CE 迁移的问题。 我们将介绍产品路线图、迁移选项以及如何开始迁移过程。

## <a name="what-is-windows-ce"></a>什么是 Windows CE？  
Windows CE （也称为 Windows embedded Compact 或 Windows 嵌入式 CE）是为 Windows 嵌入式设备开发的操作系统。 Windows CE 的操作系统具有所支持的工业、医学和各种其他设备，超过20年。Microsoft 许可证 Windows CE 原始设备制造商 (oem) ，可以修改和创建自己的用户界面和体验，同时 Windows CE 提供技术基础来实现此目的。 Windows Embedded Compact 的当前版本支持将支持包 (BSP) 的 x86 和 ARM 处理器直接提供。  

## <a name="when-is-the-end-of-life-for-windows-ce"></a>Windows CE 的生命周期结束时间是多少？  
尽管 Windows CE 2013 将于晚2023结束延长支持，Microsoft 将允许许可销售人员继续 Windows Embedded Compact 2013 到2028。当然，Windows CE 设备可以继续无限期地使用。  

## <a name="what-does-that-mean-for-existing-solutions"></a>对于现有解决方案，这意味着什么？  
这可能意味着，根据你的硬件配置、公司目标和过程，现在可能是实现平台软件现代化的最佳时间。  

Microsoft 为客户提供了多个有关如何导航此过程的解决方案–迁移到[Windows 10 IoT 企业版](https://docs.microsoft.com/windows/iot-core/windows-iot-enterprise)，利用[Windows CE 应用容器](https://docs.microsoft.com/windows/iot-core/windows-ce-app-container)与 Windows 10 IoT 核心版，或继续许可 Windows CE 2013。  

## <a name="what-are-my-migration-options"></a>我的迁移选项有哪些？  
适用于你的设计的操作系统选项将取决于你的时间线，以便进行迁移和硬件要求。   

### <a name="windows-10-iot-enterprise"></a>Windows 10 IoT 企业版  
对于需要访问全套 x64 硬件的设备，ARM64 硬件（如 NXP MX8、advanced UX，或具有可在一个产品设计迭代中迁移的 CE 应用程序），最佳做法是直接迁移到 [Windows 10 IoT 企业版](https://docs.microsoft.com/windows/iot-core/windows-iot-enterprise)。 你将能够快速利用功能，并获得最大的产品支持生存期。  

### <a name="windows-10-iot-core"></a>Windows 10 IoT Core  
对于需要使用 ARM32 或拥有需要多个开发周期才能迁移的复杂 CE 应用程序的设计，具有 Windows 10 IoT 核心版 Services 的[ce 应用容器](https://docs.microsoft.com/windows/iot-core/windows-ce-app-container)   提供了一个用于逐步迁移到 Windows 10 IoT 核心版的解决方案。 [](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview)利用 Windows 10 IoT 核心服务，可以获得 Windows Embedded Compact 2013 和 Windows 10 IoT 核心版的许可证。在2029之前，IoT 核心操作系统将继续接收安全更新。  

### <a name="windows-ce-2013"></a>Windows CE 2013
当你在进行基于 Windows 10 的设计时，或者如果你需要继续为客户提供 CE 2013 设备，Microsoft 将允许许可销售继续 Windows Embedded Compact 2013 到2028。   


## <a name="will-microsoft-offer-the-option-to-pay-for-additional-support-on-windows-ce-2013-after-2023"></a>在2023后，Microsoft 是否会提供向 Windows CE 2013 支付额外支持的选项？
Microsoft 当前没有计划提供超过2023的扩展支持。  

## <a name="whats-are-the-associated-costs-with-migrating"></a>迁移的相关成本是多少？  
有关可用的各种迁移选项的特定定价，请联系你的分销商，以获得技术评估的最新 Windows 更新的访问权限。  

## <a name="what-is-ce-app-container"></a>什么是 CE 应用容器？
Windows CE 应用容器通过在 Windows 10 IoT 核心版上运行 Windows CE 2013 实例来工作。 该技术的目标是允许大多数客户在 Windows 10 IoT 上运行其现有的、未修改的 Windows CE 应用程序，同时他们会继续投入更新应用程序。 若要查看 CE 应用容器是否是适用于你的组织的正确解决方案，请查看以下 [概述文章](https://docs.microsoft.com/windows/iot-core/windows-ce-app-container)。
