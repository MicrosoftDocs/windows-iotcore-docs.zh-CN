---
title: 安装默认应用程序
author: bfjelds
ms.author: bfjelds
ms.date: 09/05/17
ms.topic: article
description: 了解如何设置使用 Windows Device Portal 或命令行程序的默认应用程序。
keywords: windows iot，默认应用程序中，PowerShell iot
ms.openlocfilehash: f3f7a5194491250a8a0b49e81e073282c8f5660b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510874"
---
# <a name="setup-a-default-app"></a><span data-ttu-id="6f96f-104">安装默认应用程序</span><span class="sxs-lookup"><span data-stu-id="6f96f-104">Setup a default app</span></span>
<span data-ttu-id="6f96f-105">此处，您将学习如何将你的应用程序设置为默认应用程序。</span><span class="sxs-lookup"><span data-stu-id="6f96f-105">Here you'll learn the ways to set your application as the default application.</span></span> <span data-ttu-id="6f96f-106">默认应用程序是在系统启动时启动的。</span><span class="sxs-lookup"><span data-stu-id="6f96f-106">The default application is the one that is launched when the system boots.</span></span>  

> [!NOTE]
> <span data-ttu-id="6f96f-107">部署到 RS5 时，visual Studio 将生成一个含义模糊的错误 （或使用 OpenSSH RS4 启用） IoT 图像，除非已从 RS4 或更高版本的 SDK 安装 Visual Studio 可以访问。</span><span class="sxs-lookup"><span data-stu-id="6f96f-107">Visual Studio will generate a cryptic error when deploying to a RS5 (or RS4 with OpenSSH enabled) IoT image unless a SDK from RS4 or greater is installed that Visual Studio can access.</span></span>

## <a name="runtime-options"></a><span data-ttu-id="6f96f-108">运行时选项</span><span class="sxs-lookup"><span data-stu-id="6f96f-108">Runtime options</span></span>

<span data-ttu-id="6f96f-109">在开发期间 / 实验阶段，您可以通过以下方式更改默认的应用。</span><span class="sxs-lookup"><span data-stu-id="6f96f-109">During development / experimental phases, you can change the default app by following means.</span></span>

### <a name="using-windows-device-portal"></a><span data-ttu-id="6f96f-110">使用 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="6f96f-110">Using Windows Device Portal</span></span>

<span data-ttu-id="6f96f-111">你可以单击**启动**列对应于应用程序。</span><span class="sxs-lookup"><span data-stu-id="6f96f-111">You can click on **Startup** column corresponding to the app.</span></span>
![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)

### <a name="using-the-shell"></a><span data-ttu-id="6f96f-113">使用命令行程序</span><span class="sxs-lookup"><span data-stu-id="6f96f-113">Using the shell</span></span>

<span data-ttu-id="6f96f-114">使用命令行程序将默认应用程序设置的步骤</span><span class="sxs-lookup"><span data-stu-id="6f96f-114">Steps to set the default app using the shell</span></span> 

1. <span data-ttu-id="6f96f-115">连接到通过设备[Powershell](../connect-your-device/PowerShell.md)</span><span class="sxs-lookup"><span data-stu-id="6f96f-115">Connect to the device via [Powershell](../connect-your-device/PowerShell.md)</span></span>

2. <span data-ttu-id="6f96f-116">列出使用安装的应用程序</span><span class="sxs-lookup"><span data-stu-id="6f96f-116">List the applications installed using</span></span> `iotstartup list`

3. <span data-ttu-id="6f96f-117">请注意你想要使为默认值并将其使用设置的应用程序的 appid `iotstartup add headed <appid>`。</span><span class="sxs-lookup"><span data-stu-id="6f96f-117">Note the appid for the application you want to make as default and set it using `iotstartup add headed <appid>`.</span></span> <span data-ttu-id="6f96f-118">对于无外设的应用程序，应使用`iotstartup add headless <appid>`。</span><span class="sxs-lookup"><span data-stu-id="6f96f-118">For headless app, you should use `iotstartup add headless <appid>`.</span></span>


## <a name="build-time-option"></a><span data-ttu-id="6f96f-119">生成时间选项</span><span class="sxs-lookup"><span data-stu-id="6f96f-119">Build time option</span></span>

<span data-ttu-id="6f96f-120">对于大型部署，您可以实现此目的使用预配包</span><span class="sxs-lookup"><span data-stu-id="6f96f-120">For large deployments, you can achieve this using provisioning package</span></span>

<span data-ttu-id="6f96f-121">预配包创建期间，可以指定在 WCD StartupApp/默认设置。</span><span class="sxs-lookup"><span data-stu-id="6f96f-121">You can specify the StartupApp/Default setting in the WCD during the provisioning package creation.</span></span>
![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)

<span data-ttu-id="6f96f-123">请参阅[Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml)作为示例。</span><span class="sxs-lookup"><span data-stu-id="6f96f-123">See [Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) as an example.</span></span> <span data-ttu-id="6f96f-124">可以获取应用程序用户模型 ID (AUMID) 使用 appx [GetAppxInfo 工具](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe)。</span><span class="sxs-lookup"><span data-stu-id="6f96f-124">You can get the Application User Model ID (AUMID) of an appx using [GetAppxInfo tool](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe).</span></span>

## <a name="how-to-configure-home-key"></a><span data-ttu-id="6f96f-125">如何配置"Home"键</span><span class="sxs-lookup"><span data-stu-id="6f96f-125">How to configure "Home" key</span></span>

<span data-ttu-id="6f96f-126">Windows 10 IoT 周年更新 (1607) 对于将默认应用程序窗口带到前台，另一个应用程序当前正在运行时提供命令行程序支持。</span><span class="sxs-lookup"><span data-stu-id="6f96f-126">Windows 10 IoT Anniversary Update (1607) provides shell support for bringing the default application window to the foreground when another application is currently running.</span></span>

<span data-ttu-id="6f96f-127">若要查看如何启用"Home"键，请访问我们[IoT Shell 页](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)</span><span class="sxs-lookup"><span data-stu-id="6f96f-127">To see how to enable the "Home" key, please visit our [IoT Shell page](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)</span></span>
