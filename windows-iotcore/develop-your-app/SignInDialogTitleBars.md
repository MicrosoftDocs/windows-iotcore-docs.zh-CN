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
# <a name="title-bars-for-sign-in-dialogs"></a><span data-ttu-id="9dcc9-104">登录对话框的标题栏</span><span class="sxs-lookup"><span data-stu-id="9dcc9-104">Title bars for sign in dialogs</span></span>

<span data-ttu-id="9dcc9-105">根据设计，Windows 10 IoT 核心版不会显示应用程序的窗口周围的应用程序框架\-获取整个屏幕。</span><span class="sxs-lookup"><span data-stu-id="9dcc9-105">By design, Windows 10 IoT Core does not display an application frame around your application's window \- you get the full screen.</span></span> <span data-ttu-id="9dcc9-106">但是，在版本 1809年，几个系统对话框以提供标题栏中包含关闭按钮以允许用户将取消它们，即使对话框中的内容提供了没有取消按钮。</span><span class="sxs-lookup"><span data-stu-id="9dcc9-106">However, in version 1809, several system dialog boxes have been given a title bar containing close button to allow the user to cancel out of them, even when the content of the dialog box provides no cancel button.</span></span>

## <a name="sign-in-dialog-boxes"></a><span data-ttu-id="9dcc9-107">在对话框登录</span><span class="sxs-lookup"><span data-stu-id="9dcc9-107">Sign in dialog boxes</span></span>

<span data-ttu-id="9dcc9-108">添加此功能的对话框的标识对话框-用于登录到 Microsoft 帐户 (MSA) 和 Azure Active Directory (AAD)。</span><span class="sxs-lookup"><span data-stu-id="9dcc9-108">The dialogs that have this feature added are the identity dialogs - for signing in to Microsoft Accounts (MSA) and Azure Active Directory (AAD).</span></span> <span data-ttu-id="9dcc9-109">这些可在你的应用程序中所示[Web 帐户管理示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement)中[Microsoft UWP 应用示例存储库](https://github.com/Microsoft/Windows-universal-samples)。</span><span class="sxs-lookup"><span data-stu-id="9dcc9-109">These can be used in your application as shown in the [Web Account Management sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/WebAccountManagement) in the [Microsoft UWP app samples repo](https://github.com/Microsoft/Windows-universal-samples).</span></span>

## <a name="configuring-the-title-bar-height"></a><span data-ttu-id="9dcc9-110">配置标题栏高度</span><span class="sxs-lookup"><span data-stu-id="9dcc9-110">Configuring the title bar height</span></span>

<span data-ttu-id="9dcc9-111">标题栏的默认高度为 25 像素，并且可以设置为任何更大的价值最多 50 个像素。</span><span class="sxs-lookup"><span data-stu-id="9dcc9-111">The title bar has a default height of 25 pixels, and can be set to any greater value up to 50 pixels.</span></span> <span data-ttu-id="9dcc9-112">任何大于 50 的值将被限制为 50。</span><span class="sxs-lookup"><span data-stu-id="9dcc9-112">Any value greater than 50 will be clamped to 50.</span></span> <span data-ttu-id="9dcc9-113">高度可以是小于 25，但确定关闭按钮的高度时，请考虑用户的体验可能是负面影响。</span><span class="sxs-lookup"><span data-stu-id="9dcc9-113">The height can be less than 25, but consider the possibly negative effect on the user's experience when deciding the height of the close button.</span></span>

<span data-ttu-id="9dcc9-114">例如，若要将标题栏高度设置为 32 像素，在 PowerShell 中您可以执行下列：</span><span class="sxs-lookup"><span data-stu-id="9dcc9-114">As an example, to set the title bar height to 32 pixels, in PowerShell you could do the following:</span></span>
```powershell
# Note that we're only using the variable to make the sample code more narrow
Set-Variable IoTRootKey "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension"
Set-ItemProperty -Path "$IoTRootKey\Experiences\TitleBar" -Name Height -Type DWord -Value 32
```

> [!NOTE]
> <span data-ttu-id="9dcc9-115">有关如何创建 OEM 图像，设置注册表值的首选的机制是使用`OEMInput.xml`文件中所述[运行时自定义](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)</span><span class="sxs-lookup"><span data-stu-id="9dcc9-115">For creating an OEM image, the preferred mechanism for setting registry values is with the `OEMInput.xml` file discussed in [Runtime customizations](/windows-hardware/manufacture/iot/oscustomizations#runtime-customizations)</span></span>
