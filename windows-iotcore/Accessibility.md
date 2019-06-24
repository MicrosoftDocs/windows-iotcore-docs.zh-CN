---
title: Windows 10 IoT 的辅助功能
author: saraclay
ms.author: saclayt
ms.date: 03/8/2018
ms.topic: article
description: 了解辅助功能以及如何将这些学习知识应用到下一应用程序或设备。
keywords: Windows 10 IoT 核心版, Windows 10 IoT 企业版, 辅助功能, 颜色对比度
ms.openlocfilehash: 149c47fc9cae7fb99eb6aa190055c13284c3e197
ms.sourcegitcommit: 9ec4716afde25fdc8b94f7c0794448501f451b55
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/17/2019
ms.locfileid: "60167345"
---
# <a name="an-overview-of-accessibility-for-windows-iot"></a>Windows IoT 辅助功能概述 
 
## <a name="introduction"></a>简介 
有了辅助功能，所有人（包括残障人士）都可以直观且高效地利用应用程序或设备提供的所有功能，不管与应用程序或设备交互的是什么人。 
 
必须在产品设计阶段考虑到辅助功能，因为这样可以避免许多与辅助功能相关的潜在 Bug。 例如，在设计阶段需考虑到所用颜色和文本大小，（以及用户如何自定义它们），这样可以大大方便许多客户。 对于带键盘的设备，在设计阶段需考虑到如何通过键盘来充分利用产品中的功能，以及如何在尽量减少击键数的情况下访问最常访问的功能。  
 
对于开发人员来说，从实施角度来看，好消息是 Windows 作为一个平台已经做了大量的工作，默认提供某种级别的辅助功能。 例如，默认情况下，可以通过 UI 自动化 (UIA) API 以编程方式访问标准控件。 如果选择不使用标准控件，改为构建自定义 UI，则完成 UI 辅助功能所需的工作所耗费的时间可能远远超出直接使用平台提供的标准控件来构建应用所耗费的时间。 

## <a name="accessibility-testing"></a>辅助功能测试
下面是建议用于构建应用程序的工具。 虽然在审核自己的设计时可以借助这些工具，但请注意，你仍然需要考虑到高对比度和文本要求等情况。

### <a name="accscope"></a>AccScope
[AccScope](https://msdn.microsoft.com/library/windows/desktop/Dn433239) 工具允许开发人员和测试人员在其应用的开发和设计期间评估该应用的辅助功能，并且可能在早期原型设计阶段进行，而不是在应用开发周期的后期测试阶段。 它专门用于测试应用程序的讲述人辅助功能方案。

### <a name="inspect"></a>检查
你可以使用 [Inspect](https://msdn.microsoft.com/library/windows/desktop/Dd318521) 选择任何 UI 元素并查看其辅助功能数据。 可以查看 Microsoft UI 自动化属性和控件模式并测试 UI 自动化树中自动化元素的导航结构。 当你开发 UI 以验证如何在 UI 自动化中公开辅助功能属性时，请使用 Inspect。 在某些情况下，属性来自已经为默认 XAML 控件实现的 UI 自动化支持。 在其他情况下，属性来自已经在 XAML 标记中设置为 AutomationProperties 附加属性的特定值。

想要详细了解辅助功能测试？ 如需完整列表，请阅读[“辅助功能测试”一文](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-testing#inspect)。
 
 
## <a name="accessibility-in-uwp-apps"></a>UWP 应用中的辅助功能 
Microsoft 的 UWP 团队已经汇总了一个全面的有关辅助功能的指南，方便用户进行 UWP 应用设计和开发。 为了方便你使用，我们在下面提供了该列表，但是你也可以阅读我们的[辅助功能概述](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-overview)，了解更多信息。 
 
另外，下面还简单介绍了 UI 自动化 API 和某些可用工具，帮助你了解 UI 的程序表示形式。 
 
> [!VIDEO https://www.youtube.com/embed/6b0K2883rXA]

 
| 文章 | 描述 | 
|---------|-------------| 
| [设计非独占软件](https://docs.microsoft.com/windows/uwp/design/accessibility/designing-inclusive-software) | 了解如何改进适用于 Windows 10 的 UWP 应用的非独占设计。  以辅助功能思维设计和生成非独占软件。 | 
| [开发非独占 Windows 应用](https://docs.microsoft.com/windows/uwp/design/accessibility/developing-inclusive-windows-apps) | 本文是开发辅助 UWP 应用的路线图。 | 
| [辅助功能清单](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-checklist) | 提供了可帮助你确保 UWP 应用为辅助应用的清单。 | 
| [公开基本的辅助功能信息](https://docs.microsoft.com/windows/uwp/design/accessibility/basic-accessibility-information) | 基本的辅助功能信息通常按照名称、角色和值进行分类。 本主题介绍了可帮助应用公开辅助技术所需的基本信息的代码。 | 
| [键盘辅助功能](https://docs.microsoft.com/windows/uwp/design/accessibility/keyboard-accessibility) | 如果应用未提供良好的键盘访问，则盲人用户或行动不便的用户在使用该应用时会存在困难，或者可能根本无法使用该应用。 | 
| [高对比度主题](https://docs.microsoft.com/windows/uwp/design/accessibility/high-contrast-themes) | 介绍了为确保 UWP 应用在高对比度主题处于活动状态时可供使用所需的步骤。 | 
| [辅助文本要求](https://docs.microsoft.com/windows/uwp/design/accessibility/accessible-text-requirements) | 本主题介绍了应用中的文本的最佳辅助功能做法：确保颜色和背景满足必需的对比率。 本主题还讨论了 UWP 应用中的文本元素可以具有的 Microsoft UI 自动化角色，以及图形中文本的最佳做法。 | 
| [要避免的辅助功能做法](https://docs.microsoft.com/windows/uwp/design/accessibility/practices-to-avoid) | 列出创建辅助的 UWP 应用时应避免的做法。 | 
| [自定义自动化对等](https://docs.microsoft.com/windows/uwp/design/accessibility/custom-automation-peers) | 介绍 Microsoft UI 自动化的自动化对等概念以及如何为自己的自定义 UI 类提供自动化支持。 | 
 
