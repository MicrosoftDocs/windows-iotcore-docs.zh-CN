---
title: 为 "登录" 对话框配置标题栏高度
author: johntasler
ms.author: jtasler
ms.date: 09/13/2018
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何在 Windows 10 IoT Core，版本1809中配置用于登录对话框的标题栏高度。
keywords: Windows 10 IoT Core，msa，aad，标题栏，关闭，取消，头，web，帐户，WebAccountManagement，登录，签署
ms.custom: RS5
ms.openlocfilehash: 0c867492f13dfcd69b093194661692cd9a7da310
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656113"
---
# <a name="title-bars-for-sign-in-dialogs"></a>"登录" 对话框的标题栏

按照设计，Windows 10 IoT Core 不会在应用程序窗口周围显示应用程序框架 \- 。 但是，在版本1809中，为多个系统对话框提供了一个包含 "关闭" 按钮的标题栏，以允许用户取消他们，甚至在对话框内容不提供 "取消" 按钮时也是如此。

## <a name="sign-in-dialog-boxes"></a>"登录" 对话框

添加了此功能的对话框是标识对话框-用于登录到 Microsoft 帐户 (MSA) ，Azure Active Directory (Azure AD) 。 可以在应用程序中使用这些应用程序，如[MICROSOFT UWP 应用示例](https://github.com/Microsoft/Windows-universal-samples)存储库中的[Web 帐户管理示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)中所示。

## <a name="configuring-the-title-bar-height"></a>配置标题栏高度

标题栏的默认高度为25像素，可以设置为任何大于50像素的值。 大于50的任何值都将限制到50。 高度可以小于25，但考虑到决定 "关闭" 按钮高度时，用户的体验可能会产生负面影响。

例如，若要将标题栏高度设置为32像素，请在 PowerShell 中执行以下操作：
```powershell
# Note that we're only using the variable to make the sample code more narrow
Set-Variable IoTRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension"
Set-ItemProperty -Path "$IoTRootKey\Experiences\TitleBar" -Name Height -Type DWord -Value 32
```

> [!NOTE]
> 对于创建 OEM 映像，设置注册表值的首选机制是使用 `OEMInput.xml` [运行时自定义项](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)中讨论的文件
