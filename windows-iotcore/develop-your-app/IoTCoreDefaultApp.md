---
title: Windows 10 IoT Core 默认应用
ms.date: 08/08/2018
ms.topic: article
description: 了解 Windows 10 IoT Core 默认应用及其功能。
keywords: windows iot，windows 10 iot core，默认应用
ms.custom: RS5
ms.openlocfilehash: 730e8c386b328efdbb66092121980a42e066679c
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721492"
---
# <a name="windows-10-iot-core-default-app-overview"></a><span data-ttu-id="db750-104">Windows 10 IoT Core 默认应用概述</span><span class="sxs-lookup"><span data-stu-id="db750-104">Windows 10 IoT Core Default App Overview</span></span>

> [!TIP]
> <span data-ttu-id="db750-105">如果你发现想要查看已添加到此示例应用的功能，请在 GitHub 上提出[问题](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp)，让我们知道。</span><span class="sxs-lookup"><span data-stu-id="db750-105">If you find that you'd like to see a feature added to this sample app, [open an issue](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) on GitHub to let us know.</span></span> <span data-ttu-id="db750-106">如果你想要提交 bug，请按照[此处](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT)的反馈中心的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="db750-106">If you'd like to file a bug, follow the instructions for the Feedback Hub [here](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT).</span></span>

<span data-ttu-id="db750-107">初次刷新 Windows 10 IoT Core 时，将在启动时向你显示 Windows 10 IoT Core 默认应用，如下所示：</span><span class="sxs-lookup"><span data-stu-id="db750-107">When you initially flash Windows 10 IoT Core, you will be presented with the Windows 10 IoT Core Default App upon startup, which looks like this:</span></span>

![IoT Core 默认应用的屏幕截图](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

<span data-ttu-id="db750-109">此应用程序的目的不仅是为了让你在首次启动 Windows 10 IoT Core 时，为你提供与交互的友好 shell，但我们在[此处](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)提供了此应用程序的代码，以便你可以在自己的自定义应用程序上插入和使用这些功能。</span><span class="sxs-lookup"><span data-stu-id="db750-109">The purpose of this application is not only to provide you with a friendly shell to interact with when you first boot up Windows 10 IoT Core, but we have open-sourced the code for this application [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) so that you can plug and play with these features on your own custom application(s).</span></span>

<span data-ttu-id="db750-110">本文将为你提供 Windows 10 IoT Core 默认应用提供的不同功能的说明，以及你可以如何对自己的应用程序使用这些不同功能。</span><span class="sxs-lookup"><span data-stu-id="db750-110">This article will give you a rundown of the different features that the Windows 10 IoT Core Default App offers as well as how you can leverage these different features for your own applications.</span></span>

## <a name="leveraging-the-iot-core-default-app"></a><span data-ttu-id="db750-111">利用 IoT 核心默认应用</span><span class="sxs-lookup"><span data-stu-id="db750-111">Leveraging the IoT Core Default App</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="db750-112">请勿将创客映像用于商业化。</span><span class="sxs-lookup"><span data-stu-id="db750-112">Do not use maker images for commercialization.</span></span> <span data-ttu-id="db750-113">若要将某个设备商业化，必须使用自定义 FFU 以确保最佳安全性。</span><span class="sxs-lookup"><span data-stu-id="db750-113">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="db750-114">在[此处](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="db750-114">Learn more [here](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

<span data-ttu-id="db750-115">IoT Core 默认应用可进行自定义和扩展，也可将源代码用作你自己的应用的示例。</span><span class="sxs-lookup"><span data-stu-id="db750-115">The IoT Core Default App can be customized and extended, or you can use the source code as an example for your own app.</span></span> <span data-ttu-id="db750-116">若要亲自尝试此问题，请下载我们的示例的 zip，或在[此处](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)查看 IoT Core 默认应用的代码。</span><span class="sxs-lookup"><span data-stu-id="db750-116">To try this out for yourself, download the zip of our samples or check out the code for the IoT Core Default App [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp).</span></span> <span data-ttu-id="db750-117">如有任何问题，请在[此处](https://github.com/Microsoft/Windows-iotcore-samples/issues)提出有关示例存储库的问题。</span><span class="sxs-lookup"><span data-stu-id="db750-117">For any questions, please file an issue on our samples repo [here](https://github.com/Microsoft/Windows-iotcore-samples/issues).</span></span>

<span data-ttu-id="db750-118">如下面的[设置部分](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
)中所示，在某些情况下，你可以代表最终用户配置客户系统上的默认设置和功能。</span><span class="sxs-lookup"><span data-stu-id="db750-118">As shown under the [Settings section](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) below, in some cases, you may configure default settings and features on your customer system on behalf of the end user.</span></span> <span data-ttu-id="db750-119">但是，如果在默认情况下启用这些设置和功能，或者诊断高于 "基本" 设置，则必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="db750-119">However, if you turn these settings and features on by default or if diagnostics are above the basic setting, you must:</span></span>

* <span data-ttu-id="db750-120">通知最终用户这些功能已启用，并向最终用户提供[此处](https://go.microsoft.com/fwlink/?LinkId=521839)指向 Microsoft 隐私声明网页的链接。</span><span class="sxs-lookup"><span data-stu-id="db750-120">Notify the end user that these features have been enable and provide the end user with the link to Microsoft's Privacy Statement web page [here](https://go.microsoft.com/fwlink/?LinkId=521839).</span></span> 
* <span data-ttu-id="db750-121">在默认情况下（根据适用法律要求）启用此类功能的安全同意。</span><span class="sxs-lookup"><span data-stu-id="db750-121">Secure consent from the relevant end user to enable such features by default (as required by applicable law).</span></span>
* <span data-ttu-id="db750-122">向最终用户提供将诊断设置更改回 "基本" 设置的能力。</span><span class="sxs-lookup"><span data-stu-id="db750-122">Provide end users the ability to change the Diagnostics setting back to the basic setting.</span></span>
* <span data-ttu-id="db750-123">如果你启用 Microsoft 帐户，并且你有权访问最终用户数据，则在最终用户删除 Microsoft 帐户时，你必须在设备上启用所有最终用户的 Microsoft 帐户数据的同时删除。</span><span class="sxs-lookup"><span data-stu-id="db750-123">If you enable Microsoft Accounts and you have access to end user data, if the end user deletes the Microsoft Account, you must enable simultaneous deletion of all the end user's Microsoft Account data on the device.</span></span> 

## <a name="out-of-box-experience-oobe"></a><span data-ttu-id="db750-124">全新体验（OOBE）</span><span class="sxs-lookup"><span data-stu-id="db750-124">Out-of-Box Experience (OOBE)</span></span>

<span data-ttu-id="db750-125">IoT 核心默认应用的全新体验在获取时与之相关。</span><span class="sxs-lookup"><span data-stu-id="db750-125">The out-of-box experience for the IoT Core Default App is as lean as it gets.</span></span> <span data-ttu-id="db750-126">第一页将要求提供默认语言和 wi-fi 设置。</span><span class="sxs-lookup"><span data-stu-id="db750-126">The first pages will ask for a default language and wi-fi settings.</span></span> <span data-ttu-id="db750-127">从这里开始，你的应用程序必须与 GDPR 兼容，你必须有一个诊断数据屏幕，并且如果你计划跟踪位置，则还需要具有位置权限屏幕。</span><span class="sxs-lookup"><span data-stu-id="db750-127">From there, in order for your app to be GDPR-compliant, you must have a diagnostic data screen and, if you're planning to track location, you will need to have a location permissions screen too.</span></span> <span data-ttu-id="db750-128">下面显示了二者的示例。</span><span class="sxs-lookup"><span data-stu-id="db750-128">Examples of both are shown below.</span></span> 

<span data-ttu-id="db750-129">oobe](../media/IoTCoreDefaultApp/OOBE3.jpg)
的 ![位置设置 ![OOBE 的诊断设置](../media/IoTCoreDefaultApp/OOBE4.jpg)</span><span class="sxs-lookup"><span data-stu-id="db750-129">![Location settings for OOBE](../media/IoTCoreDefaultApp/OOBE3.jpg)
![Diagnostic settings for OOBE](../media/IoTCoreDefaultApp/OOBE4.jpg)</span></span>

## <a name="command-bar"></a><span data-ttu-id="db750-130">命令栏</span><span class="sxs-lookup"><span data-stu-id="db750-130">Command Bar</span></span>
<span data-ttu-id="db750-131">命令栏是位于屏幕底部的持久性 horizonatal 栏。</span><span class="sxs-lookup"><span data-stu-id="db750-131">The Command Bar is the persistant horizonatal bar located at the bottom of the screen.</span></span> <span data-ttu-id="db750-132">这提供了对以下有趣的轻松访问：</span><span class="sxs-lookup"><span data-stu-id="db750-132">This provides easy access to the following funtionality:</span></span>
- <span data-ttu-id="db750-133">前进和后退页面导航</span><span class="sxs-lookup"><span data-stu-id="db750-133">Forward and backward page navigation</span></span>
- <span data-ttu-id="db750-134">基本设备信息，无需离开当前页面</span><span class="sxs-lookup"><span data-stu-id="db750-134">Basic device info without leaving the current page</span></span>
- <span data-ttu-id="db750-135">打开或关闭全屏模式</span><span class="sxs-lookup"><span data-stu-id="db750-135">Turning fullscreen mode on or off</span></span>
- <span data-ttu-id="db750-136">前进快捷方式</span><span class="sxs-lookup"><span data-stu-id="db750-136">Advance shortcuts</span></span>
- <span data-ttu-id="db750-137">页面特定按钮</span><span class="sxs-lookup"><span data-stu-id="db750-137">Page specific buttons</span></span>

<span data-ttu-id="db750-138">命令栏中有很多按钮，有时这些按钮可能会令人费解或隐藏。</span><span class="sxs-lookup"><span data-stu-id="db750-138">There are a lot buttons in the Command Bar, and sometimes those buttons can be confusing or hidden.</span></span> <span data-ttu-id="db750-139">若要展开命令栏并访问这些按钮，请按下右端的菜单按钮：</span><span class="sxs-lookup"><span data-stu-id="db750-139">To expand the Command Bar and access those buttons, please press the menu button in the bottom right:</span></span>

![如何展开命令栏](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a><span data-ttu-id="db750-141">开始菜单-播放</span><span class="sxs-lookup"><span data-stu-id="db750-141">Start Menu - Play</span></span>

<span data-ttu-id="db750-142">"开始" 菜单是最活跃的即插即用功能。</span><span class="sxs-lookup"><span data-stu-id="db750-142">The Start Menu is where most plug and play features live.</span></span>

### <a name="weather"></a><span data-ttu-id="db750-143">天气</span><span class="sxs-lookup"><span data-stu-id="db750-143">Weather</span></span>
<span data-ttu-id="db750-144">使用国家天气服务中的数据，天气页面将在你的当前位置呈现天气信息。</span><span class="sxs-lookup"><span data-stu-id="db750-144">Using data from the National Weather Service, the weather page renders weather information in your current location.</span></span>

### <a name="web-browser"></a><span data-ttu-id="db750-145">Web 浏览器</span><span class="sxs-lookup"><span data-stu-id="db750-145">Web Browser</span></span>
<span data-ttu-id="db750-146">通过 web 浏览器，你可以从 web 中提取大多数站点。</span><span class="sxs-lookup"><span data-stu-id="db750-146">The web browser allows you to pull up most sites from the web.</span></span>

### <a name="music"></a><span data-ttu-id="db750-147">音乐</span><span class="sxs-lookup"><span data-stu-id="db750-147">Music</span></span>
<span data-ttu-id="db750-148">此页面将从 "**音乐库**" 播放 MP3 和 WAV 文件，可以通过[Windows 设备门户](../manage-your-device/DevicePortal.md)访问这些文件。</span><span class="sxs-lookup"><span data-stu-id="db750-148">This page will play MP3 and WAV files from the **Music Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>  <span data-ttu-id="db750-149">若要将文件上传到音乐播放机，你需要导航到 Windows 设备门户，单击 "应用" 下拉列表，导航到 "文件资源管理器"，选择 "音乐"，然后上传文件。</span><span class="sxs-lookup"><span data-stu-id="db750-149">To upload files to the music player, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Music" and upload your files from there.</span></span>


![如何上传音乐文件](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a><span data-ttu-id="db750-151">幻灯片放映</span><span class="sxs-lookup"><span data-stu-id="db750-151">Slideshow</span></span>
<span data-ttu-id="db750-152">此页将显示 "**图片库**" 中的任何 PNG 或 JPEG 图像文件，可以通过[Windows 设备门户](../manage-your-device/DevicePortal.md)进行访问。</span><span class="sxs-lookup"><span data-stu-id="db750-152">This page will display any PNG or JPEG image files from the **Pictures Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span> <span data-ttu-id="db750-153">若要将图像上传到幻灯片，你将需要导航到 Windows 设备门户，单击 "应用" 下拉列表，导航到 "文件资源管理器"，选择 "图片"，然后上传文件。</span><span class="sxs-lookup"><span data-stu-id="db750-153">To upload images to the slideshow, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Pictures" and upload your files from there.</span></span>


![如何上传音乐文件](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a><span data-ttu-id="db750-155">绘图</span><span class="sxs-lookup"><span data-stu-id="db750-155">Draw</span></span>
<span data-ttu-id="db750-156">此页面允许你测试 Windows 10 IoT Core 的墨迹功能。</span><span class="sxs-lookup"><span data-stu-id="db750-156">This page allows you to test out Windows 10 IoT Core's inking capabilities.</span></span>

## <a name="start-menu---explore"></a><span data-ttu-id="db750-157">开始菜单-浏览</span><span class="sxs-lookup"><span data-stu-id="db750-157">Start Menu - Explore</span></span> 

### <a name="apps"></a><span data-ttu-id="db750-158">“应用”</span><span class="sxs-lookup"><span data-stu-id="db750-158">Apps</span></span> 
<span data-ttu-id="db750-159">此页面允许你启动在设备上安装的其他前台应用程序。</span><span class="sxs-lookup"><span data-stu-id="db750-159">This page allows you to launch other foreground applications installed on the device.</span></span> <span data-ttu-id="db750-160">启动应用程序将挂起 IoT Core 默认应用，可通过在[Windows 设备门户](../manage-your-device/DevicePortal.md)中使用应用管理器变该应用。</span><span class="sxs-lookup"><span data-stu-id="db750-160">Launching an application will suspend IoT Core Default App, which can be relaunched by using App Manager in [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>

<span data-ttu-id="db750-161">不需要任何特殊内容即可在页面中列出前景应用程序，只需[安装](AppInstaller.md)或[部署](AppDeployment.md)应用程序即可。</span><span class="sxs-lookup"><span data-stu-id="db750-161">Nothing special is needed to have your foreground application listed in the page, simply [install](AppInstaller.md) or [deploy](AppDeployment.md) the application.</span></span> <span data-ttu-id="db750-162">成功安装或部署后，请重新导航到 "应用" 页，刷新应用程序列表。</span><span class="sxs-lookup"><span data-stu-id="db750-162">After successful installation or deployment, re-navigate to the Apps page to refresh the list of applications.</span></span>

<span data-ttu-id="db750-163">请注意，我们筛选掉了几个自动生成的操作系统相关应用程序，可以在[此处](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs)找到应用名称的列表。</span><span class="sxs-lookup"><span data-stu-id="db750-163">Note that there are a couple of auto-generated OS related applications that we filter out, you can find the list of app names [here](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs).</span></span>

### <a name="notifications"></a><span data-ttu-id="db750-164">通知</span><span class="sxs-lookup"><span data-stu-id="db750-164">Notifications</span></span>
<span data-ttu-id="db750-165">此页将列出过去20个通知，因为 IoT Core 默认应用已启动。</span><span class="sxs-lookup"><span data-stu-id="db750-165">This page will list the past 20 notifications since IoT Core Default App was launched.</span></span> <span data-ttu-id="db750-166">当 IoT 核心默认应用在调试模式下运行时，将添加用于创建测试通知的按钮。</span><span class="sxs-lookup"><span data-stu-id="db750-166">When IoT Core Default App is running in debug mode, buttons are added that will create test notifications.</span></span>

### <a name="logs"></a><span data-ttu-id="db750-167">日志</span><span class="sxs-lookup"><span data-stu-id="db750-167">Logs</span></span>
<span data-ttu-id="db750-168">此页将列出任何自动生成的崩溃或错误日志，然后可以将其移出设备并进行分析。</span><span class="sxs-lookup"><span data-stu-id="db750-168">This page will list any auto-generated crash or error logs, which then can be taken off the device and analyzed.</span></span>

### <a name="github"></a><span data-ttu-id="db750-169">GitHub</span><span class="sxs-lookup"><span data-stu-id="db750-169">GitHub</span></span>
<span data-ttu-id="db750-170">此页将转到 IoT Core 默认应用代码的开源 GitHub 位置。</span><span class="sxs-lookup"><span data-stu-id="db750-170">This page will take you to the open-sourced GitHub location of the IoT Core Default App code.</span></span>

## <a name="start-menu---windows-device-portal"></a><span data-ttu-id="db750-171">"开始" 菜单-Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="db750-171">Start Menu - Windows Device Portal</span></span>

<span data-ttu-id="db750-172">此部分中的页面利用 Windows 设备门户 REST Api，这要求你使用 Windows 设备门户凭据进行登录。</span><span class="sxs-lookup"><span data-stu-id="db750-172">The pages in this section leverage the Windows Device Portal REST APIs, which requires you to sign in using your Windows Device Portal credentials.</span></span>

## <a name="device-information"></a><span data-ttu-id="db750-173">设备信息</span><span class="sxs-lookup"><span data-stu-id="db750-173">Device Information</span></span>

<span data-ttu-id="db750-174">此页面允许你查看设备的不同功能，包括以太网、OS 版本、连接的设备等。</span><span class="sxs-lookup"><span data-stu-id="db750-174">This page allows you to see the different features for your device including Ethernet, OS version, connected devices, and more.</span></span>

## <a name="command-line"></a><span data-ttu-id="db750-175">命令行</span><span class="sxs-lookup"><span data-stu-id="db750-175">Command Line</span></span>

<span data-ttu-id="db750-176">此页面允许你直接在设备上运行命令。</span><span class="sxs-lookup"><span data-stu-id="db750-176">This page allows you to run commands directly on your device.</span></span>

<span data-ttu-id="db750-177">若要启用此功能，必须设置一个注册表项，以便应用可以运行这些命令。</span><span class="sxs-lookup"><span data-stu-id="db750-177">To enable this feature you have to set a registry key so that the app can run the commands.</span></span> <span data-ttu-id="db750-178">第一次尝试运行命令时，你将看到一个链接，该链接允许你使用对 Windows 设备门户的调用来设置注册表项。</span><span class="sxs-lookup"><span data-stu-id="db750-178">The first time you try to run a command you will see a link that allows you to set the registry key using a call to Windows Device Portal.</span></span> <span data-ttu-id="db750-179">单击链接以使你的设备能够运行命令。</span><span class="sxs-lookup"><span data-stu-id="db750-179">Click the link to enable your device to run commands.</span></span>

<span data-ttu-id="db750-180">某些命令需要管理员访问权限。</span><span class="sxs-lookup"><span data-stu-id="db750-180">Some commands require administrator access.</span></span> <span data-ttu-id="db750-181">为了安全起见，默认情况下，应用程序使用非管理员帐户运行命令。</span><span class="sxs-lookup"><span data-stu-id="db750-181">For security purposes the app uses a non-admin account by default to run commands.</span></span> <span data-ttu-id="db750-182">如果需要以管理员身份运行命令，则可以在命令行提示符中键入 "RunAsAdmin <your command>"。</span><span class="sxs-lookup"><span data-stu-id="db750-182">If you need to run a command as an admin you can type "RunAsAdmin <your command>" in the command line prompt.</span></span>

## <a name="settings"></a><span data-ttu-id="db750-183">“设置”</span><span class="sxs-lookup"><span data-stu-id="db750-183">Settings</span></span>
<span data-ttu-id="db750-184">你将能够在此处配置许多设置，包括 Wi-fi、蓝牙、电源选项等。</span><span class="sxs-lookup"><span data-stu-id="db750-184">You'll be able to configure a number of settings here including Wi-Fi, Bluetooth, power options, and more.</span></span>

### <a name="app-settings"></a><span data-ttu-id="db750-185">应用设置</span><span class="sxs-lookup"><span data-stu-id="db750-185">App Settings</span></span>
<span data-ttu-id="db750-186">"**应用设置**" 部分允许你为应用中的页面配置各种设置。</span><span class="sxs-lookup"><span data-stu-id="db750-186">The **App Settings** section allows you to configure various settings for pages in the app.</span></span>  

<span data-ttu-id="db750-187">您可以自定义的一些设置如下：</span><span class="sxs-lookup"><span data-stu-id="db750-187">Some of the settings you can customize are:</span></span>

##### <a name="general-settings"></a><span data-ttu-id="db750-188">常规设置</span><span class="sxs-lookup"><span data-stu-id="db750-188">General Settings</span></span>
* <span data-ttu-id="db750-189">设置在应用程序启动时显示的默认页面</span><span class="sxs-lookup"><span data-stu-id="db750-189">Set the default page that appears when the app is started</span></span>
* <span data-ttu-id="db750-190">启用/禁用屏幕保护程序</span><span class="sxs-lookup"><span data-stu-id="db750-190">Enable/disable the screensaver</span></span>

##### <a name="weather-settings"></a><span data-ttu-id="db750-191">天气设置</span><span class="sxs-lookup"><span data-stu-id="db750-191">Weather Settings</span></span>
* <span data-ttu-id="db750-192">更改位置</span><span class="sxs-lookup"><span data-stu-id="db750-192">Change the location</span></span>
  > <span data-ttu-id="db750-193">仅当您提供有效的[Bing 地图服务令牌](https://msdn.microsoft.com/library/ff428642.aspx)时，才会启用此功能。</span><span class="sxs-lookup"><span data-stu-id="db750-193">This feature is only enabled if you have provided a valid [Bing Map Service Token](https://msdn.microsoft.com/library/ff428642.aspx).</span></span>  <span data-ttu-id="db750-194">若要将令牌传递给应用，请在应用的 LocalState 文件夹中创建一个**MapToken**文件（例如 C:\Data\USERS\\[用户帐户] \AppData\Packages\\[包全名] \LocalState\MapToken.config），然后重新启动应用。</span><span class="sxs-lookup"><span data-stu-id="db750-194">To pass the token to the app, create a **MapToken.config** file in the LocalState folder of the app (e.g. C:\Data\USERS\\[User Account]\AppData\Packages\\[Package Full Name]\LocalState\MapToken.config) and restart the app.</span></span>
* <span data-ttu-id="db750-195">展开地图</span><span class="sxs-lookup"><span data-stu-id="db750-195">Expand the map</span></span>
* <span data-ttu-id="db750-196">启用/禁用地图翻转，使地图和天气交换机定期发生，以防屏幕烧入</span><span class="sxs-lookup"><span data-stu-id="db750-196">Enable/disable map flipping so that the map and the weather switch places periodically to prevent screen burn-in</span></span>

##### <a name="web-browser-settings"></a><span data-ttu-id="db750-197">Web 浏览器设置</span><span class="sxs-lookup"><span data-stu-id="db750-197">Web Browser Settings</span></span>
* <span data-ttu-id="db750-198">设置 Web 浏览器的主页</span><span class="sxs-lookup"><span data-stu-id="db750-198">Set the home page for the Web Browser</span></span>

##### <a name="slideshow-settings"></a><span data-ttu-id="db750-199">幻灯片放映设置</span><span class="sxs-lookup"><span data-stu-id="db750-199">Slideshow Settings</span></span>
* <span data-ttu-id="db750-200">设置幻灯片放映间隔</span><span class="sxs-lookup"><span data-stu-id="db750-200">Set the slideshow interval</span></span>

##### <a name="appearance"></a><span data-ttu-id="db750-201">外观</span><span class="sxs-lookup"><span data-stu-id="db750-201">Appearance</span></span>
* <span data-ttu-id="db750-202">为磁贴图标使用 MDL2 资产而不是表情符号</span><span class="sxs-lookup"><span data-stu-id="db750-202">Use MDL2 Assets instead of Emojis for the tile icons</span></span>
* <span data-ttu-id="db750-203">设置图块宽度和高度</span><span class="sxs-lookup"><span data-stu-id="db750-203">Set the tile width and height</span></span>
* <span data-ttu-id="db750-204">设置 UI 缩放-默认设置自动缩放</span><span class="sxs-lookup"><span data-stu-id="db750-204">Set UI scaling - Automatic scaling is set by default</span></span>
* <span data-ttu-id="db750-205">设置磁贴颜色</span><span class="sxs-lookup"><span data-stu-id="db750-205">Set the tile color</span></span>

#### <a name="system"></a><span data-ttu-id="db750-206">“系统”</span><span class="sxs-lookup"><span data-stu-id="db750-206">System</span></span>
<span data-ttu-id="db750-207">更改语言、键盘布局和时区。</span><span class="sxs-lookup"><span data-stu-id="db750-207">Change the language, keyboard layout, and time zone.</span></span>

#### <a name="network--wi-fi"></a><span data-ttu-id="db750-208">网络 & Wi-fi</span><span class="sxs-lookup"><span data-stu-id="db750-208">Network & Wi-Fi</span></span>
<span data-ttu-id="db750-209">查看网络适配器属性或连接到可用的 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="db750-209">View network adapter properties or connect to an available Wi-Fi network.</span></span>

#### <a name="bluetooth"></a><span data-ttu-id="db750-210">“蓝牙”</span><span class="sxs-lookup"><span data-stu-id="db750-210">Bluetooth</span></span>
<span data-ttu-id="db750-211">与蓝牙设备配对。</span><span class="sxs-lookup"><span data-stu-id="db750-211">Pair with a Bluetooth device.</span></span>

#### <a name="app-updates"></a><span data-ttu-id="db750-212">应用更新</span><span class="sxs-lookup"><span data-stu-id="db750-212">App Updates</span></span>
<span data-ttu-id="db750-213">检查应用更新或更改自动更新设置。</span><span class="sxs-lookup"><span data-stu-id="db750-213">Check for app updates or change automatic update settings.</span></span>

#### <a name="power-options"></a><span data-ttu-id="db750-214">电源选项</span><span class="sxs-lookup"><span data-stu-id="db750-214">Power Options</span></span>
<span data-ttu-id="db750-215">重新启动或关闭设备。</span><span class="sxs-lookup"><span data-stu-id="db750-215">Restart or shutdown the device.</span></span>

#### <a name="diagnostics"></a><span data-ttu-id="db750-216">诊断</span><span class="sxs-lookup"><span data-stu-id="db750-216">Diagnostics</span></span>
<span data-ttu-id="db750-217">选择要向 Microsoft 提供的诊断数据量。</span><span class="sxs-lookup"><span data-stu-id="db750-217">Select the amount of diagnostic data you wish to provide Microsoft.</span></span>  <span data-ttu-id="db750-218">我们鼓励用户选择**完整**的诊断数据，以便可以快速诊断问题并对产品进行改进。</span><span class="sxs-lookup"><span data-stu-id="db750-218">We encourage users to opt into **Full** diagnostic data so we can diagnose issues quickly and make improvements to the product.</span></span>

##### <a name="basic"></a><span data-ttu-id="db750-219">基本</span><span class="sxs-lookup"><span data-stu-id="db750-219">Basic</span></span> 
<span data-ttu-id="db750-220">仅发送有关你的设备的信息、其设置和功能以及它是否正确执行。</span><span class="sxs-lookup"><span data-stu-id="db750-220">Send only info about your device, its settings and capabilities, and whether it is performing properly.</span></span>

##### <a name="full"></a><span data-ttu-id="db750-221">完整</span><span class="sxs-lookup"><span data-stu-id="db750-221">Full</span></span>
<span data-ttu-id="db750-222">发送所有基本诊断数据，以及有关浏览的网站以及如何使用应用程序和功能的信息，以及有关设备运行状况、设备活动和增强的错误报告的其他信息。</span><span class="sxs-lookup"><span data-stu-id="db750-222">Send all Basic diagnostic data, along with info about websites you browse and how you use apps and features, plus additional info about device health, device activity, and enhanced error reporting.</span></span>

#### <a name="location"></a><span data-ttu-id="db750-223">位置</span><span class="sxs-lookup"><span data-stu-id="db750-223">Location</span></span>
<span data-ttu-id="db750-224">允许或拒绝应用访问你的位置。</span><span class="sxs-lookup"><span data-stu-id="db750-224">Allow or deny the app access to your location.</span></span>
