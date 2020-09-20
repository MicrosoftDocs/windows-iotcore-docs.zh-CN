---
title: 设置默认应用程序
author: bfjelds
ms.author: bfjelds
ms.date: 09/05/2017
ms.topic: article
description: 了解如何使用 Windows 设备门户或 shell 设置默认应用程序。
keywords: windows iot，默认应用，PowerShell，iot
ms.openlocfilehash: 49a637fca3bf82a23c1fd771d61cc40d3fbf357b
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782439"
---
# <a name="set-up-a-default-app"></a><span data-ttu-id="b50b7-104">设置默认应用程序</span><span class="sxs-lookup"><span data-stu-id="b50b7-104">Set up a default app</span></span>
<span data-ttu-id="b50b7-105">在这里，你将了解将应用程序设置为默认应用程序的方式。</span><span class="sxs-lookup"><span data-stu-id="b50b7-105">Here you'll learn the ways to set your application as the default application.</span></span> <span data-ttu-id="b50b7-106">默认的应用程序是在系统启动时启动的应用程序。</span><span class="sxs-lookup"><span data-stu-id="b50b7-106">The default application is the one that is launched when the system boots.</span></span>  

> [!NOTE]
> <span data-ttu-id="b50b7-107">在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="b50b7-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

## <a name="runtime-options"></a><span data-ttu-id="b50b7-108">运行时选项</span><span class="sxs-lookup"><span data-stu-id="b50b7-108">Runtime options</span></span>

<span data-ttu-id="b50b7-109">在开发/实验阶段，可以通过以下方式更改默认应用。</span><span class="sxs-lookup"><span data-stu-id="b50b7-109">During development / experimental phases, you can change the default app by following means.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="b50b7-110">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="b50b7-110">Using Windows Device Portal</span></span>

<span data-ttu-id="b50b7-111">你可以单击对应于该应用的 **启动** 列。</span><span class="sxs-lookup"><span data-stu-id="b50b7-111">You can click on **Startup** column corresponding to the app.</span></span>
<span data-ttu-id="b50b7-112">![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)</span><span class="sxs-lookup"><span data-stu-id="b50b7-112">![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)</span></span>

### <a name="using-the-shell"></a><span data-ttu-id="b50b7-113">使用 shell</span><span class="sxs-lookup"><span data-stu-id="b50b7-113">Using the shell</span></span>

<span data-ttu-id="b50b7-114">使用 shell 设置默认应用程序的步骤</span><span class="sxs-lookup"><span data-stu-id="b50b7-114">Steps to set the default app using the shell</span></span> 

1. <span data-ttu-id="b50b7-115">通过[PowerShell](../connect-your-device/PowerShell.md)连接到设备</span><span class="sxs-lookup"><span data-stu-id="b50b7-115">Connect to the device via [PowerShell](../connect-your-device/PowerShell.md)</span></span>

2. <span data-ttu-id="b50b7-116">列出使用安装的应用程序 `iotstartup list`</span><span class="sxs-lookup"><span data-stu-id="b50b7-116">List the applications installed using `iotstartup list`</span></span>

3. <span data-ttu-id="b50b7-117">请注意要作为默认设置的应用程序的 appid，并使用对其进行设置 `iotstartup add headed <appid>` 。</span><span class="sxs-lookup"><span data-stu-id="b50b7-117">Note the appid for the application you want to make as default and set it using `iotstartup add headed <appid>`.</span></span> <span data-ttu-id="b50b7-118">对于无外设应用，应使用 `iotstartup add headless <appid>` 。</span><span class="sxs-lookup"><span data-stu-id="b50b7-118">For headless app, you should use `iotstartup add headless <appid>`.</span></span>


## <a name="build-time-option"></a><span data-ttu-id="b50b7-119">生成时间选项</span><span class="sxs-lookup"><span data-stu-id="b50b7-119">Build time option</span></span>

<span data-ttu-id="b50b7-120">对于大型部署，你可以使用预配包实现此目的</span><span class="sxs-lookup"><span data-stu-id="b50b7-120">For large deployments, you can achieve this using provisioning package</span></span>

<span data-ttu-id="b50b7-121">可以在创建预配包的过程中，在 WCD 中指定 StartupApp/Default 设置。</span><span class="sxs-lookup"><span data-stu-id="b50b7-121">You can specify the StartupApp/Default setting in the WCD during the provisioning package creation.</span></span>
<span data-ttu-id="b50b7-122">![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)</span><span class="sxs-lookup"><span data-stu-id="b50b7-122">![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)</span></span>

<span data-ttu-id="b50b7-123">请参阅 [IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) 作为示例。</span><span class="sxs-lookup"><span data-stu-id="b50b7-123">See [Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) as an example.</span></span> <span data-ttu-id="b50b7-124">你可以使用 [GetAppxInfo 工具](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe)获取应用程序用户模型 ID (APPX 的 AUMID) 。</span><span class="sxs-lookup"><span data-stu-id="b50b7-124">You can get the Application User Model ID (AUMID) of an appx using [GetAppxInfo tool](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe).</span></span>

## <a name="how-to-configure-home-key"></a><span data-ttu-id="b50b7-125">如何配置 "Home" 键</span><span class="sxs-lookup"><span data-stu-id="b50b7-125">How to configure "Home" key</span></span>

<span data-ttu-id="b50b7-126">Windows 10 IoT 周年更新 (1607) 为在另一应用程序当前运行时将默认应用程序窗口引入前台提供 shell 支持。</span><span class="sxs-lookup"><span data-stu-id="b50b7-126">Windows 10 IoT Anniversary Update (1607) provides shell support for bringing the default application window to the foreground when another application is currently running.</span></span>

<span data-ttu-id="b50b7-127">若要了解如何启用 "主页" 密钥，请访问 [IoT Shell 页面](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)</span><span class="sxs-lookup"><span data-stu-id="b50b7-127">To see how to enable the "Home" key, please visit our [IoT Shell page](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)</span></span>
