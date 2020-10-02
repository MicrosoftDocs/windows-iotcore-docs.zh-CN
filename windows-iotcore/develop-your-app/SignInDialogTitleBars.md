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
# <a name="title-bars-for-sign-in-dialogs"></a><span data-ttu-id="bdd9f-104">"登录" 对话框的标题栏</span><span class="sxs-lookup"><span data-stu-id="bdd9f-104">Title bars for sign in dialogs</span></span>

<span data-ttu-id="bdd9f-105">按照设计，Windows 10 IoT Core 不会在应用程序窗口周围显示应用程序框架 \- 。</span><span class="sxs-lookup"><span data-stu-id="bdd9f-105">By design, Windows 10 IoT Core does not display an application frame around your application's window \- you get the full screen.</span></span> <span data-ttu-id="bdd9f-106">但是，在版本1809中，为多个系统对话框提供了一个包含 "关闭" 按钮的标题栏，以允许用户取消他们，甚至在对话框内容不提供 "取消" 按钮时也是如此。</span><span class="sxs-lookup"><span data-stu-id="bdd9f-106">However, in version 1809, several system dialog boxes have been given a title bar containing close button to allow the user to cancel out of them, even when the content of the dialog box provides no cancel button.</span></span>

## <a name="sign-in-dialog-boxes"></a><span data-ttu-id="bdd9f-107">"登录" 对话框</span><span class="sxs-lookup"><span data-stu-id="bdd9f-107">Sign in dialog boxes</span></span>

<span data-ttu-id="bdd9f-108">添加了此功能的对话框是标识对话框-用于登录到 Microsoft 帐户 (MSA) ，Azure Active Directory (Azure AD) 。</span><span class="sxs-lookup"><span data-stu-id="bdd9f-108">The dialogs that have this feature added are the identity dialogs - for signing in to Microsoft Accounts (MSA) and Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="bdd9f-109">可以在应用程序中使用这些应用程序，如[MICROSOFT UWP 应用示例](https://github.com/Microsoft/Windows-universal-samples)存储库中的[Web 帐户管理示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)中所示。</span><span class="sxs-lookup"><span data-stu-id="bdd9f-109">These can be used in your application as shown in the [Web Account Management sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) in the [Microsoft UWP app samples repo](https://github.com/Microsoft/Windows-universal-samples).</span></span>

## <a name="configuring-the-title-bar-height"></a><span data-ttu-id="bdd9f-110">配置标题栏高度</span><span class="sxs-lookup"><span data-stu-id="bdd9f-110">Configuring the title bar height</span></span>

<span data-ttu-id="bdd9f-111">标题栏的默认高度为25像素，可以设置为任何大于50像素的值。</span><span class="sxs-lookup"><span data-stu-id="bdd9f-111">The title bar has a default height of 25 pixels, and can be set to any greater value up to 50 pixels.</span></span> <span data-ttu-id="bdd9f-112">大于50的任何值都将限制到50。</span><span class="sxs-lookup"><span data-stu-id="bdd9f-112">Any value greater than 50 will be clamped to 50.</span></span> <span data-ttu-id="bdd9f-113">高度可以小于25，但考虑到决定 "关闭" 按钮高度时，用户的体验可能会产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="bdd9f-113">The height can be less than 25, but consider the possibly negative effect on the user's experience when deciding the height of the close button.</span></span>

<span data-ttu-id="bdd9f-114">例如，若要将标题栏高度设置为32像素，请在 PowerShell 中执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="bdd9f-114">As an example, to set the title bar height to 32 pixels, in PowerShell you could do the following:</span></span>
```powershell
# Note that we're only using the variable to make the sample code more narrow
Set-Variable IoTRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension"
Set-ItemProperty -Path "$IoTRootKey\Experiences\TitleBar" -Name Height -Type DWord -Value 32
```

> [!NOTE]
> <span data-ttu-id="bdd9f-115">对于创建 OEM 映像，设置注册表值的首选机制是使用 `OEMInput.xml` [运行时自定义项](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)中讨论的文件</span><span class="sxs-lookup"><span data-stu-id="bdd9f-115">For creating an OEM image, the preferred mechanism for setting registry values is with the `OEMInput.xml` file discussed in [Runtime customizations](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)</span></span>
