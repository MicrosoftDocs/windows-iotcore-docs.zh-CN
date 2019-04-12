---
title: 针对 Windows 10 IoT 的辅助功能
author: saraclay
ms.author: saclayt
ms.date: 03/8/2018
ms.topic: article
description: 了解有关辅助功能和如何将这些知识应用于您下一步的应用程序或设备。
keywords: Windows 10 IoT 核心版、 Windows 10 IoT 企业版，可访问性，颜色对比度
ms.openlocfilehash: 149c47fc9cae7fb99eb6aa190055c13284c3e197
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510870"
---
# <a name="an-overview-of-accessibility-for-windows-iot"></a>针对 Windows IoT 的辅助功能的概述 
 
## <a name="introduction"></a>简介 
可访问性，以直观和有效地利用您的应用程序或设备产品/服务，而不考虑一个人与你的应用程序或设备进行交互的所有功能的所有功能的人。 
 
因为这会避免许多潜在的可访问性相关 bug，在该产品的设计阶段视为可访问性至关重要。 例如，在设计阶段考虑周围使用的颜色和文本 （和如何那些可能由自定义用户） 的大小可以帮助很好的很多客户。 并使用键盘，在设计阶段，围绕如何中不考虑设备键盘可用于利用产品，以及如何访问经常访问的击键备选数字最少功能中的所有功能。  
 
对于开发人员，从实现角度值得高兴的是该 Windows 如平台已经采取了大量工作来默认情况下提供一定程度的可访问性。 例如，标准控件是默认情况下通过 UI 自动化 (UIA) API 以编程方式访问。 如果您选择不使用标准控件并改为生成自定义 UI，使 UI 可访问性所需的工作可能非常更加耗时比只需构建应用程序使用平台提供的标准控件。 

## <a name="accessibility-testing"></a>辅助功能测试
以下是我们建议以生成您的应用程序时使用的工具。 尽管这些工具有助于审核您自己的设计时，请注意，您仍需要帐户功能，如高对比度和文本要求。

### <a name="accscope"></a>AccScope
[AccScope](https://msdn.microsoft.com/library/windows/desktop/Dn433239) 工具允许开发人员和测试人员在其应用的开发和设计期间评估该应用的辅助功能，并且可能在早期原型设计阶段进行，而不是在应用开发周期的后期测试阶段。 它专门用于测试应用程序的讲述人辅助功能方案。

### <a name="inspect"></a>检查
你可以使用 [Inspect](https://msdn.microsoft.com/library/windows/desktop/Dd318521) 选择任何 UI 元素并查看其辅助功能数据。 可以查看 Microsoft UI 自动化属性和控件模式并测试 UI 自动化树中自动化元素的导航结构。 当你开发 UI，以验证可访问性属性如何公开 UI 自动化中使用检查。 在某些情况下，属性来自已经为默认 XAML 控件实现的 UI 自动化支持。 在其他情况下属性来自于特定的值设置在 XAML 标记中，为 AutomationProperties 附加属性。

想要了解有关可访问性测试的详细信息？ 读取[可访问性测试项目](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-testing#inspect)的完整列表。
 
 
## <a name="accessibility-in-uwp-apps"></a>UWP 应用中的辅助功能 
Microsoft 的 UWP 团队已整理的全面指南上为 UWP 应用程序设计和开发的辅助功能。 为方便起见，我们提供了在下面列表中，但你还可以了解详细信息，请阅读我们[辅助功能的概述](https://docs.microsoft.com/windows/uwp/design/accessibility/accessibility-overview)。 
 
此外，介绍 UI 自动化 API 和一些工具可帮助您了解编程表示形式在 UI 中，为以下可用。 
 
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
| [自定义的自动化对等](https://docs.microsoft.com/windows/uwp/design/accessibility/custom-automation-peers) | 介绍 Microsoft UI 自动化的自动化对等概念以及如何为自己的自定义 UI 类提供自动化支持。 | 
 
