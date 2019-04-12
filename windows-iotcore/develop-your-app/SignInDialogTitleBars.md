---
title: 在对话框中配置登录的标题栏高度
author: johntasler
ms.author: jtasler
ms.date: 09/13/2018
ms.topic: article
description: 了解如何在 Windows 10 IoT 核心版 1809年中的对话框中配置登录的标题栏高度。
keywords: Windows 10 IoT Core，msa、 aad、 标题栏、 关闭、 取消，讨论的问题，web、 帐户、 WebAccountManagement，登录，登录
ms.custom: RS5
ms.openlocfilehash: 69f59b4416c5db39d119994139eba4907035598e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510872"
---
# <a name="title-bars-for-sign-in-dialogs"></a>登录对话框的标题栏

根据设计，Windows 10 IoT 核心版不会显示应用程序的窗口周围的应用程序框架\-获取整个屏幕。 但是，在版本 1809年，几个系统对话框以提供标题栏中包含关闭按钮以允许用户将取消它们，即使对话框中的内容提供了没有取消按钮。

## <a name="sign-in-dialog-boxes"></a>在对话框登录

添加此功能的对话框的标识对话框-用于登录到 Microsoft 帐户 (MSA) 和 Azure Active Directory (AAD)。 这些可在你的应用程序中所示[Web 帐户管理示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)中[Microsoft UWP 应用示例存储库](https://github.com/Microsoft/Windows-universal-samples)。

## <a name="configuring-the-title-bar-height"></a>配置标题栏高度

标题栏的默认高度为 25 像素，并且可以设置为任何更大的价值最多 50 个像素。 任何大于 50 的值将被限制为 50。 高度可以是小于 25，但确定关闭按钮的高度时，请考虑用户的体验可能是负面影响。

例如，若要将标题栏高度设置为 32 像素，在 PowerShell 中您可以执行下列：
```powershell
# Note that we're only using the variable to make the sample code more narrow
Set-Variable IoTRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension"
Set-ItemProperty -Path "$IoTRootKey\Experiences\TitleBar" -Name Height -Type DWord -Value 32
```

> [!NOTE]
> 有关如何创建 OEM 图像，设置注册表值的首选的机制是使用`OEMInput.xml`文件中所述[运行时自定义](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)
