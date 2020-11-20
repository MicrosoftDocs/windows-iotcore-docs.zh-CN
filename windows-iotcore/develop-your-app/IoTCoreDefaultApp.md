---
title: Windows 10 IoT Core 默认应用
ms.date: 08/08/2018
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 阅读有关 Windows 10 IoT Core 默认应用的概述。 获取有关 (OOBE) 、命令栏、开始菜单等的全新体验的信息。
keywords: windows iot，windows 10 iot core，默认应用
ms.custom: RS5
ms.openlocfilehash: c94c6d661ccde2dbda0770e0343a062ff4f09e39
ms.sourcegitcommit: 3d2e11ed186dc224672acf5ecc539fa9afd10a95
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2020
ms.locfileid: "94943080"
---
# <a name="windows-10-iot-core-default-app-overview"></a><span data-ttu-id="5bd28-105">Windows 10 IoT Core 默认应用概述</span><span class="sxs-lookup"><span data-stu-id="5bd28-105">Windows 10 IoT Core Default App Overview</span></span>
<span data-ttu-id="5bd28-106">初次刷新 Windows 10 IoT Core 时，将在启动时向你显示 Windows 10 IoT Core 默认应用，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5bd28-106">When you initially flash Windows 10 IoT Core, you will be presented with the Windows 10 IoT Core Default App upon startup, which looks like this:</span></span>

![IoT Core 默认应用的屏幕截图](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

<span data-ttu-id="5bd28-108">此应用程序的目的不仅是为了让你在首次启动 Windows 10 IoT Core 时，为你提供与交互的友好 shell，但我们在 [此处](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) 提供了此应用程序的代码，以便你可以在自己的自定义应用程序 () 上插入和使用这些功能。</span><span class="sxs-lookup"><span data-stu-id="5bd28-108">The purpose of this application is not only to provide you with a friendly shell to interact with when you first boot up Windows 10 IoT Core, but we have open-sourced the code for this application [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) so that you can plug and play with these features on your own custom application(s).</span></span>

<span data-ttu-id="5bd28-109">本文将为你提供 Windows 10 IoT Core 默认应用提供的不同功能的说明，以及你可以如何对自己的应用程序使用这些不同功能。</span><span class="sxs-lookup"><span data-stu-id="5bd28-109">This article will give you a rundown of the different features that the Windows 10 IoT Core Default App offers as well as how you can leverage these different features for your own applications.</span></span>

## <a name="leveraging-the-iot-core-default-app"></a><span data-ttu-id="5bd28-110">利用 IoT 核心默认应用</span><span class="sxs-lookup"><span data-stu-id="5bd28-110">Leveraging the IoT Core Default App</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5bd28-111">请勿将创客映像用于商业化。</span><span class="sxs-lookup"><span data-stu-id="5bd28-111">Do not use maker images for commercialization.</span></span> <span data-ttu-id="5bd28-112">若要将某个设备商业化，必须使用自定义 FFU 以确保最佳安全性。</span><span class="sxs-lookup"><span data-stu-id="5bd28-112">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="5bd28-113">在[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="5bd28-113">Learn more [here](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

<span data-ttu-id="5bd28-114">IoT Core 默认应用可进行自定义和扩展，也可将源代码用作你自己的应用的示例。</span><span class="sxs-lookup"><span data-stu-id="5bd28-114">The IoT Core Default App can be customized and extended, or you can use the source code as an example for your own app.</span></span> <span data-ttu-id="5bd28-115">若要亲自尝试此问题，请下载我们的示例的 zip，或在 [此处](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)查看 IoT Core 默认应用的代码。</span><span class="sxs-lookup"><span data-stu-id="5bd28-115">To try this out for yourself, download the zip of our samples or check out the code for the IoT Core Default App [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp).</span></span> <span data-ttu-id="5bd28-116">如有任何问题，请在 [此处](https://github.com/Microsoft/Windows-iotcore-samples/issues)提出有关示例存储库的问题。</span><span class="sxs-lookup"><span data-stu-id="5bd28-116">For any questions, please file an issue on our samples repo [here](https://github.com/Microsoft/Windows-iotcore-samples/issues).</span></span>

<span data-ttu-id="5bd28-117">如下面的 [设置部分](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) 中所示，在某些情况下，你可以代表最终用户配置客户系统上的默认设置和功能。</span><span class="sxs-lookup"><span data-stu-id="5bd28-117">As shown under the [Settings section](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) below, in some cases, you may configure default settings and features on your customer system on behalf of the end user.</span></span> <span data-ttu-id="5bd28-118">但是，如果在默认情况下启用这些设置和功能，或者诊断高于 "基本" 设置，则必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5bd28-118">However, if you turn on these settings and features by default or if diagnostics are above the basic setting, you must:</span></span>

* <span data-ttu-id="5bd28-119">通知最终用户这些功能已启用，并向最终用户提供 [此处](https://go.microsoft.com/fwlink/?LinkId=521839)指向 Microsoft 隐私声明网页的链接。</span><span class="sxs-lookup"><span data-stu-id="5bd28-119">Notify the end user that these features have been enabled, and provide the end user with the link to Microsoft's Privacy Statement web page [here](https://go.microsoft.com/fwlink/?LinkId=521839).</span></span>
* <span data-ttu-id="5bd28-120">根据适用法律) 的要求，在默认情况下启用此类功能，以确保基于相关最终用户的许可 (。</span><span class="sxs-lookup"><span data-stu-id="5bd28-120">Secure consent from the relevant end user to enable such features by default (as required by applicable law).</span></span>
* <span data-ttu-id="5bd28-121">向最终用户提供将诊断设置更改回 "基本" 设置的能力。</span><span class="sxs-lookup"><span data-stu-id="5bd28-121">Provide end users the ability to change the Diagnostics setting back to the basic setting.</span></span>
* <span data-ttu-id="5bd28-122">如果你启用 Microsoft 帐户，并且你有权访问最终用户数据，则在最终用户删除 Microsoft 帐户后，你必须在设备上启用所有最终用户的 Microsoft 帐户数据的同时删除。</span><span class="sxs-lookup"><span data-stu-id="5bd28-122">If you enable Microsoft Accounts and you have access to end-user data, if the end user deletes the Microsoft Account, you must enable simultaneous deletion of all the end user's Microsoft Account data on the device.</span></span>

## <a name="out-of-box-experience-oobe"></a><span data-ttu-id="5bd28-123"> (OOBE) 的全新体验</span><span class="sxs-lookup"><span data-stu-id="5bd28-123">Out-of-Box Experience (OOBE)</span></span>

<span data-ttu-id="5bd28-124">IoT 核心默认应用的全新体验在获取时与之相关。</span><span class="sxs-lookup"><span data-stu-id="5bd28-124">The out-of-box experience for the IoT Core Default App is as lean as it gets.</span></span> <span data-ttu-id="5bd28-125">第一页将要求提供默认语言和 wi-fi 设置。</span><span class="sxs-lookup"><span data-stu-id="5bd28-125">The first pages will ask for a default language and wi-fi settings.</span></span> <span data-ttu-id="5bd28-126">从这里开始，你的应用程序必须与 GDPR 兼容，你必须有一个诊断数据屏幕，并且如果你计划跟踪位置，则还需要具有位置权限屏幕。</span><span class="sxs-lookup"><span data-stu-id="5bd28-126">From there, in order for your app to be GDPR-compliant, you must have a diagnostic data screen and, if you're planning to track location, you will need to have a location permissions screen too.</span></span> <span data-ttu-id="5bd28-127">下面显示了二者的示例。</span><span class="sxs-lookup"><span data-stu-id="5bd28-127">Examples of both are shown below.</span></span>

<span data-ttu-id="5bd28-128">![OOBE 的 OOBE ](../media/IoTCoreDefaultApp/OOBE3.jpg)
 ![ 诊断设置的位置设置](../media/IoTCoreDefaultApp/OOBE4.jpg)</span><span class="sxs-lookup"><span data-stu-id="5bd28-128">![Location settings for OOBE](../media/IoTCoreDefaultApp/OOBE3.jpg)
![Diagnostic settings for OOBE](../media/IoTCoreDefaultApp/OOBE4.jpg)</span></span>

## <a name="command-bar"></a><span data-ttu-id="5bd28-129">命令栏</span><span class="sxs-lookup"><span data-stu-id="5bd28-129">Command Bar</span></span>
<span data-ttu-id="5bd28-130">命令栏是位于屏幕底部的持久性水平条。</span><span class="sxs-lookup"><span data-stu-id="5bd28-130">The Command Bar is the persistant horizontal bar located at the bottom of the screen.</span></span> <span data-ttu-id="5bd28-131">这样就可以轻松访问以下功能：</span><span class="sxs-lookup"><span data-stu-id="5bd28-131">This provides easy access to the following functionality:</span></span>
- <span data-ttu-id="5bd28-132">前进和后退页面导航</span><span class="sxs-lookup"><span data-stu-id="5bd28-132">Forward and backward page navigation</span></span>
- <span data-ttu-id="5bd28-133">基本设备信息，无需离开当前页面</span><span class="sxs-lookup"><span data-stu-id="5bd28-133">Basic device info without leaving the current page</span></span>
- <span data-ttu-id="5bd28-134">打开或关闭全屏模式</span><span class="sxs-lookup"><span data-stu-id="5bd28-134">Turning fullscreen mode on or off</span></span>
- <span data-ttu-id="5bd28-135">前进快捷方式</span><span class="sxs-lookup"><span data-stu-id="5bd28-135">Advance shortcuts</span></span>
- <span data-ttu-id="5bd28-136">页面特定按钮</span><span class="sxs-lookup"><span data-stu-id="5bd28-136">Page-specific buttons</span></span>

<span data-ttu-id="5bd28-137">命令栏中有许多按钮，有时这些按钮可能会令人费解或隐藏。</span><span class="sxs-lookup"><span data-stu-id="5bd28-137">There are many buttons in the Command Bar, and sometimes those buttons can be confusing or hidden.</span></span> <span data-ttu-id="5bd28-138">若要展开命令栏并访问这些按钮，请按下右端的菜单按钮：</span><span class="sxs-lookup"><span data-stu-id="5bd28-138">To expand the Command Bar and access those buttons, please press the menu button in the bottom right:</span></span>

![如何展开命令栏](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a><span data-ttu-id="5bd28-140">开始菜单-播放</span><span class="sxs-lookup"><span data-stu-id="5bd28-140">Start Menu - Play</span></span>

<span data-ttu-id="5bd28-141">"开始" 菜单是最活跃的即插即用功能。</span><span class="sxs-lookup"><span data-stu-id="5bd28-141">The Start Menu is where most plug and play features live.</span></span>

### <a name="weather"></a><span data-ttu-id="5bd28-142">天气</span><span class="sxs-lookup"><span data-stu-id="5bd28-142">Weather</span></span>
<span data-ttu-id="5bd28-143">使用国家天气服务中的数据，天气页面将在你的当前位置呈现天气信息。</span><span class="sxs-lookup"><span data-stu-id="5bd28-143">Using data from the National Weather Service, the weather page renders weather information in your current location.</span></span>

### <a name="web-browser"></a><span data-ttu-id="5bd28-144">Web 浏览器</span><span class="sxs-lookup"><span data-stu-id="5bd28-144">Web Browser</span></span>
<span data-ttu-id="5bd28-145">通过 web 浏览器，你可以从 web 中提取大多数站点。</span><span class="sxs-lookup"><span data-stu-id="5bd28-145">The web browser allows you to pull up most sites from the web.</span></span>

### <a name="music"></a><span data-ttu-id="5bd28-146">音乐</span><span class="sxs-lookup"><span data-stu-id="5bd28-146">Music</span></span>
<span data-ttu-id="5bd28-147">此页面将从 " **音乐库**" 播放 MP3 和 WAV 文件，可以通过 [Windows 设备门户](../manage-your-device/DevicePortal.md)访问这些文件。</span><span class="sxs-lookup"><span data-stu-id="5bd28-147">This page will play MP3 and WAV files from the **Music Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>  <span data-ttu-id="5bd28-148">若要将文件上传到音乐播放机，你需要导航到 Windows 设备门户，单击 "应用" 下拉列表，导航到 "文件资源管理器"，选择 "音乐"，然后上传文件。</span><span class="sxs-lookup"><span data-stu-id="5bd28-148">To upload files to the music player, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Music" and upload your files from there.</span></span>


![如何上传音乐文件](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a><span data-ttu-id="5bd28-150">幻灯片放映</span><span class="sxs-lookup"><span data-stu-id="5bd28-150">Slideshow</span></span>
<span data-ttu-id="5bd28-151">此页将显示 " **图片库**" 中的任何 PNG 或 JPEG 图像文件，可以通过 [Windows 设备门户](../manage-your-device/DevicePortal.md)进行访问。</span><span class="sxs-lookup"><span data-stu-id="5bd28-151">This page will display any PNG or JPEG image files from the **Pictures Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span> <span data-ttu-id="5bd28-152">若要将图像上传到幻灯片，你将需要导航到 Windows 设备门户，单击 "应用" 下拉列表，导航到 "文件资源管理器"，选择 "图片"，然后上传文件。</span><span class="sxs-lookup"><span data-stu-id="5bd28-152">To upload images to the slideshow, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Pictures" and upload your files from there.</span></span>


![如何上传音乐文件1](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a><span data-ttu-id="5bd28-154">绘制</span><span class="sxs-lookup"><span data-stu-id="5bd28-154">Draw</span></span>
<span data-ttu-id="5bd28-155">此页面允许你测试 Windows 10 IoT Core 的墨迹功能。</span><span class="sxs-lookup"><span data-stu-id="5bd28-155">This page allows you to test out Windows 10 IoT Core's inking capabilities.</span></span>

## <a name="start-menu---explore"></a><span data-ttu-id="5bd28-156">开始菜单-浏览</span><span class="sxs-lookup"><span data-stu-id="5bd28-156">Start Menu - Explore</span></span>

### <a name="apps"></a><span data-ttu-id="5bd28-157">“应用”</span><span class="sxs-lookup"><span data-stu-id="5bd28-157">Apps</span></span>
<span data-ttu-id="5bd28-158">此页面允许你启动在设备上安装的其他前台应用程序。</span><span class="sxs-lookup"><span data-stu-id="5bd28-158">This page allows you to launch other foreground applications installed on the device.</span></span> <span data-ttu-id="5bd28-159">启动应用程序将挂起 IoT Core 默认应用，可通过在 [Windows 设备门户](../manage-your-device/DevicePortal.md)中使用应用管理器变该应用。</span><span class="sxs-lookup"><span data-stu-id="5bd28-159">Launching an application will suspend IoT Core Default App, which can be relaunched by using App Manager in [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>

<span data-ttu-id="5bd28-160">不需要任何特殊内容即可在页面中列出前景应用程序，只需 [安装](AppInstaller.md) 或 [部署](AppDeployment.md) 应用程序即可。</span><span class="sxs-lookup"><span data-stu-id="5bd28-160">Nothing special is needed to have your foreground application listed in the page, simply [install](AppInstaller.md) or [deploy](AppDeployment.md) the application.</span></span> <span data-ttu-id="5bd28-161">成功安装或部署后，请重新导航到 "应用" 页，刷新应用程序列表。</span><span class="sxs-lookup"><span data-stu-id="5bd28-161">After successful installation or deployment, re-navigate to the Apps page to refresh the list of applications.</span></span>

<span data-ttu-id="5bd28-162">请注意，我们筛选掉了几个自动生成的与 OS 相关的应用程序，可以在 [此处](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs)找到应用名称的列表。</span><span class="sxs-lookup"><span data-stu-id="5bd28-162">Note that there are a couple of autogenerated OS-related applications that we filter out, you can find the list of app names [here](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs).</span></span>

### <a name="notifications"></a><span data-ttu-id="5bd28-163">通知</span><span class="sxs-lookup"><span data-stu-id="5bd28-163">Notifications</span></span>
<span data-ttu-id="5bd28-164">此页将列出过去20个通知，因为 IoT Core 默认应用已启动。</span><span class="sxs-lookup"><span data-stu-id="5bd28-164">This page will list the past 20 notifications since IoT Core Default App was launched.</span></span> <span data-ttu-id="5bd28-165">当 IoT 核心默认应用在调试模式下运行时，将添加用于创建测试通知的按钮。</span><span class="sxs-lookup"><span data-stu-id="5bd28-165">When IoT Core Default App is running in debug mode, buttons are added that will create test notifications.</span></span>

### <a name="logs"></a><span data-ttu-id="5bd28-166">日志</span><span class="sxs-lookup"><span data-stu-id="5bd28-166">Logs</span></span>
<span data-ttu-id="5bd28-167">此页将列出所有自动生成的崩溃或错误日志，然后可以将其移出设备并进行分析。</span><span class="sxs-lookup"><span data-stu-id="5bd28-167">This page will list any autogenerated crash or error logs, which then can be taken off the device and analyzed.</span></span>

### <a name="github"></a><span data-ttu-id="5bd28-168">GitHub</span><span class="sxs-lookup"><span data-stu-id="5bd28-168">GitHub</span></span>
<span data-ttu-id="5bd28-169">此页将转到 IoT Core 默认应用代码的开源 GitHub 位置。</span><span class="sxs-lookup"><span data-stu-id="5bd28-169">This page will take you to the open-sourced GitHub location of the IoT Core Default App code.</span></span>

## <a name="start-menu---windows-device-portal"></a><span data-ttu-id="5bd28-170">"开始" 菜单-Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="5bd28-170">Start Menu - Windows Device Portal</span></span>

<span data-ttu-id="5bd28-171">此部分中的页面利用 Windows 设备门户 REST Api，这要求你使用 Windows 设备门户凭据进行登录。</span><span class="sxs-lookup"><span data-stu-id="5bd28-171">The pages in this section leverage the Windows Device Portal REST APIs, which require you to sign in using your Windows Device Portal credentials.</span></span>

## <a name="device-information"></a><span data-ttu-id="5bd28-172">设备信息</span><span class="sxs-lookup"><span data-stu-id="5bd28-172">Device Information</span></span>

<span data-ttu-id="5bd28-173">此页面允许你查看设备的不同功能，包括以太网、OS 版本、连接的设备等。</span><span class="sxs-lookup"><span data-stu-id="5bd28-173">This page allows you to see the different features for your device including Ethernet, OS version, connected devices, and more.</span></span>

## <a name="command-line"></a><span data-ttu-id="5bd28-174">命令行</span><span class="sxs-lookup"><span data-stu-id="5bd28-174">Command Line</span></span>

<span data-ttu-id="5bd28-175">此页面允许你直接在设备上运行命令。</span><span class="sxs-lookup"><span data-stu-id="5bd28-175">This page allows you to run commands directly on your device.</span></span>

<span data-ttu-id="5bd28-176">若要启用此功能，必须设置一个注册表项，以便应用可以运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="5bd28-176">To enable this feature, you have to set a registry key so that the app can run the commands.</span></span> <span data-ttu-id="5bd28-177">第一次尝试运行命令时，你将看到一个链接，该链接允许你使用对 Windows 设备门户的调用来设置注册表项。</span><span class="sxs-lookup"><span data-stu-id="5bd28-177">The first time you try to run a command you will see a link that allows you to set the registry key using a call to Windows Device Portal.</span></span> <span data-ttu-id="5bd28-178">单击链接以使你的设备能够运行命令。</span><span class="sxs-lookup"><span data-stu-id="5bd28-178">Click the link to enable your device to run commands.</span></span>

<span data-ttu-id="5bd28-179">某些命令需要管理员访问权限。</span><span class="sxs-lookup"><span data-stu-id="5bd28-179">Some commands require administrator access.</span></span> <span data-ttu-id="5bd28-180">为了安全起见，默认情况下，应用程序使用非管理员帐户运行命令。</span><span class="sxs-lookup"><span data-stu-id="5bd28-180">For security purposes the app uses a non-admin account by default to run commands.</span></span> <span data-ttu-id="5bd28-181">如果需要以管理员身份运行命令，则可以 <your command> 在命令行提示符中键入 "RunAsAdmin"。</span><span class="sxs-lookup"><span data-stu-id="5bd28-181">If you need to run a command as an admin, you can type "RunAsAdmin <your command>" in the command line prompt.</span></span>

## <a name="settings"></a><span data-ttu-id="5bd28-182">设置</span><span class="sxs-lookup"><span data-stu-id="5bd28-182">Settings</span></span>
<span data-ttu-id="5bd28-183">你将能够在此处配置许多设置，包括 Wi-fi、蓝牙、电源选项等。</span><span class="sxs-lookup"><span data-stu-id="5bd28-183">You'll be able to configure a number of settings here including Wi-Fi, Bluetooth, power options, and more.</span></span>

### <a name="app-settings"></a><span data-ttu-id="5bd28-184">应用设置</span><span class="sxs-lookup"><span data-stu-id="5bd28-184">App Settings</span></span>
<span data-ttu-id="5bd28-185">" **应用设置** " 部分允许你为应用中的页面配置各种设置。</span><span class="sxs-lookup"><span data-stu-id="5bd28-185">The **App Settings** section allows you to configure various settings for pages in the app.</span></span>  

<span data-ttu-id="5bd28-186">您可以自定义的一些设置如下：</span><span class="sxs-lookup"><span data-stu-id="5bd28-186">Some of the settings you can customize are:</span></span>

##### <a name="general-settings"></a><span data-ttu-id="5bd28-187">常规设置</span><span class="sxs-lookup"><span data-stu-id="5bd28-187">General Settings</span></span>
* <span data-ttu-id="5bd28-188">设置在应用程序启动时显示的默认页面</span><span class="sxs-lookup"><span data-stu-id="5bd28-188">Set the default page that appears when the app is started</span></span>
* <span data-ttu-id="5bd28-189">启用/禁用屏幕保护程序</span><span class="sxs-lookup"><span data-stu-id="5bd28-189">Enable/disable the screensaver</span></span>

##### <a name="weather-settings"></a><span data-ttu-id="5bd28-190">天气设置</span><span class="sxs-lookup"><span data-stu-id="5bd28-190">Weather Settings</span></span>
* <span data-ttu-id="5bd28-191">更改位置</span><span class="sxs-lookup"><span data-stu-id="5bd28-191">Change the location</span></span>
  > <span data-ttu-id="5bd28-192">仅当您提供有效的 [Bing 地图服务令牌](https://msdn.microsoft.com/library/ff428642.aspx)时，才会启用此功能。</span><span class="sxs-lookup"><span data-stu-id="5bd28-192">This feature is only enabled if you have provided a valid [Bing Map Service Token](https://msdn.microsoft.com/library/ff428642.aspx).</span></span>  <span data-ttu-id="5bd28-193">若要将令牌传递给应用，请在应用的 LocalState 文件夹中创建 **MapToken.config** 文件 (例如 C:\Data\Users \\ [用户帐户] \AppData\Local\Packages \\ [包全名] \LocalState\MapToken.config) 并重新启动应用。</span><span class="sxs-lookup"><span data-stu-id="5bd28-193">To pass the token to the app, create a **MapToken.config** file in the LocalState folder of the app (e.g. C:\Data\Users\\[User Account]\AppData\Local\Packages\\[Package Full Name]\LocalState\MapToken.config) and restart the app.</span></span>  
<span data-ttu-id="5bd28-194"> (示例： C:\Data\Users\DefaultAccount\AppData\Local\Packages\ 16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58 \LocalState\)</span><span class="sxs-lookup"><span data-stu-id="5bd28-194">(Example: C:\Data\Users\DefaultAccount\AppData\Local\Packages\16454Windows10IOTCore.IOTCoreDefaultApplication_rz84sjny4rf58\LocalState\)</span></span>
* <span data-ttu-id="5bd28-195">展开地图</span><span class="sxs-lookup"><span data-stu-id="5bd28-195">Expand the map</span></span>
* <span data-ttu-id="5bd28-196">启用/禁用地图翻转以便定期放置地图和天气交换机，以防屏幕烧入</span><span class="sxs-lookup"><span data-stu-id="5bd28-196">Enable/disable map flipping so that the map and the weather switch place periodically to prevent screen burn-in</span></span>

##### <a name="web-browser-settings"></a><span data-ttu-id="5bd28-197">Web 浏览器设置</span><span class="sxs-lookup"><span data-stu-id="5bd28-197">Web Browser Settings</span></span>
* <span data-ttu-id="5bd28-198">设置 Web 浏览器的主页</span><span class="sxs-lookup"><span data-stu-id="5bd28-198">Set the home page for the Web Browser</span></span>

##### <a name="slideshow-settings"></a><span data-ttu-id="5bd28-199">幻灯片放映设置</span><span class="sxs-lookup"><span data-stu-id="5bd28-199">Slideshow Settings</span></span>
* <span data-ttu-id="5bd28-200">设置幻灯片放映间隔</span><span class="sxs-lookup"><span data-stu-id="5bd28-200">Set the slideshow interval</span></span>

##### <a name="appearance"></a><span data-ttu-id="5bd28-201">外观</span><span class="sxs-lookup"><span data-stu-id="5bd28-201">Appearance</span></span>
* <span data-ttu-id="5bd28-202">为磁贴图标使用 MDL2 资产而不是表情符号</span><span class="sxs-lookup"><span data-stu-id="5bd28-202">Use MDL2 Assets instead of Emojis for the tile icons</span></span>
* <span data-ttu-id="5bd28-203">设置图块宽度和高度</span><span class="sxs-lookup"><span data-stu-id="5bd28-203">Set the tile width and height</span></span>
* <span data-ttu-id="5bd28-204">设置 UI 缩放-默认设置自动缩放</span><span class="sxs-lookup"><span data-stu-id="5bd28-204">Set UI scaling - Automatic scaling is set by default</span></span>
* <span data-ttu-id="5bd28-205">设置磁贴颜色</span><span class="sxs-lookup"><span data-stu-id="5bd28-205">Set the tile color</span></span>

#### <a name="system"></a><span data-ttu-id="5bd28-206">系统</span><span class="sxs-lookup"><span data-stu-id="5bd28-206">System</span></span>
<span data-ttu-id="5bd28-207">更改语言、键盘布局和时区。</span><span class="sxs-lookup"><span data-stu-id="5bd28-207">Change the language, keyboard layout, and time zone.</span></span>

#### <a name="network--wi-fi"></a><span data-ttu-id="5bd28-208">网络 & Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="5bd28-208">Network & Wi-Fi</span></span>
<span data-ttu-id="5bd28-209">查看网络适配器属性或连接到可用的 Wi-Fi 网络。</span><span class="sxs-lookup"><span data-stu-id="5bd28-209">View network adapter properties or connect to an available Wi-Fi network.</span></span>

#### <a name="bluetooth"></a><span data-ttu-id="5bd28-210">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="5bd28-210">Bluetooth</span></span>
<span data-ttu-id="5bd28-211">与蓝牙设备配对。</span><span class="sxs-lookup"><span data-stu-id="5bd28-211">Pair with a Bluetooth device.</span></span>

#### <a name="app-updates"></a><span data-ttu-id="5bd28-212">应用更新</span><span class="sxs-lookup"><span data-stu-id="5bd28-212">App Updates</span></span>
<span data-ttu-id="5bd28-213">检查应用更新或更改自动更新设置。</span><span class="sxs-lookup"><span data-stu-id="5bd28-213">Check for app updates or change automatic update settings.</span></span>

#### <a name="power-options"></a><span data-ttu-id="5bd28-214">电源选项</span><span class="sxs-lookup"><span data-stu-id="5bd28-214">Power Options</span></span>
<span data-ttu-id="5bd28-215">重新启动或关闭设备。</span><span class="sxs-lookup"><span data-stu-id="5bd28-215">Restart or shutdown the device.</span></span>

#### <a name="diagnostics"></a><span data-ttu-id="5bd28-216">诊断</span><span class="sxs-lookup"><span data-stu-id="5bd28-216">Diagnostics</span></span>
<span data-ttu-id="5bd28-217">选择要向 Microsoft 提供的诊断数据量。</span><span class="sxs-lookup"><span data-stu-id="5bd28-217">Select the amount of diagnostic data you wish to provide Microsoft.</span></span>  <span data-ttu-id="5bd28-218">我们鼓励用户选择 **完整** 的诊断数据，以便可以快速诊断问题并对产品进行改进。</span><span class="sxs-lookup"><span data-stu-id="5bd28-218">We encourage users to opt into **Full** diagnostic data so we can diagnose issues quickly and make improvements to the product.</span></span>

##### <a name="basic"></a><span data-ttu-id="5bd28-219">基本</span><span class="sxs-lookup"><span data-stu-id="5bd28-219">Basic</span></span>
<span data-ttu-id="5bd28-220">仅发送有关你的设备的信息、其设置和功能以及它是否正确执行。</span><span class="sxs-lookup"><span data-stu-id="5bd28-220">Send only info about your device, its settings and capabilities, and whether it is performing properly.</span></span>

##### <a name="full"></a><span data-ttu-id="5bd28-221">完整</span><span class="sxs-lookup"><span data-stu-id="5bd28-221">Full</span></span>
<span data-ttu-id="5bd28-222">发送所有基本诊断数据，以及有关浏览的网站以及如何使用应用程序和功能的信息，以及有关设备运行状况、设备活动和增强的错误报告的其他信息。</span><span class="sxs-lookup"><span data-stu-id="5bd28-222">Send all Basic diagnostic data, along with info about websites you browse and how you use apps and features, plus additional info about device health, device activity, and enhanced error reporting.</span></span>

#### <a name="location"></a><span data-ttu-id="5bd28-223">位置</span><span class="sxs-lookup"><span data-stu-id="5bd28-223">Location</span></span>
<span data-ttu-id="5bd28-224">允许或拒绝应用访问你的位置。</span><span class="sxs-lookup"><span data-stu-id="5bd28-224">Allow or deny the app access to your location.</span></span>
