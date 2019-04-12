---
title: Windows 10 IoT 核心版默认应用程序
author: saraclay
ms.author: saclayt
ms.date: 08/08/2018
ms.topic: article
description: 了解有关 Windows 10 IoT Core 默认的应用及其功能。
keywords: windows iot、 windows 10 iot 核心版，默认的应用
ms.custom: RS5
ms.openlocfilehash: 12baa759c9085360431c2b7f87f72816cd24680b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510645"
---
# <a name="windows-10-iot-core-default-app-overview"></a><span data-ttu-id="4fa15-104">Windows 10 IoT 核心版默认应用程序概述</span><span class="sxs-lookup"><span data-stu-id="4fa15-104">Windows 10 IoT Core Default App Overview</span></span>

> [!TIP]
> <span data-ttu-id="4fa15-105">如果你想要发现某项功能添加到此示例应用，找到[提出问题](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp)GitHub，让我们了解上。</span><span class="sxs-lookup"><span data-stu-id="4fa15-105">If you find that you'd like to see a feature added to this sample app, [open an issue](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp) on GitHub to let us know.</span></span> <span data-ttu-id="4fa15-106">如果你想要提交 bug，按照说明在反馈中心[此处](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT)。</span><span class="sxs-lookup"><span data-stu-id="4fa15-106">If you'd like to file a bug, follow the instructions for the Feedback Hub [here](https://social.msdn.microsoft.com/Forums/en-US/fad1c6a0-e578-44a7-8e8d-95cc28c06ccd/need-logs-if-your-device-hasnt-updated-to-the-latest-iotcore-version?forum=WindowsIoT).</span></span>

<span data-ttu-id="4fa15-107">当最初 flash Windows 10 IoT 核心版时，你将看到与 Windows 10 IoT Core 默认应用程序启动后，其外观如下所示：</span><span class="sxs-lookup"><span data-stu-id="4fa15-107">When you initially flash Windows 10 IoT Core, you will be presented with the Windows 10 IoT Core Default App upon startup, which looks like this:</span></span>

![IoT 核心版默认应用的屏幕截图](../media/IoTCoreDefaultApp/DeviceInfoPage-Screenshot.jpg)

<span data-ttu-id="4fa15-109">此应用程序的目的不是仅为你提供友好的外壳程序，以便与当你首次启动 Windows 10 IoT 核心版，但我们已进行开源此应用程序的代码[此处](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)，以便您可以插有了这些自定义应用程序的功能。</span><span class="sxs-lookup"><span data-stu-id="4fa15-109">The purpose of this application is not only to provide you with a friendly shell to interact with when you first boot up Windows 10 IoT Core, but we have open-sourced the code for this application [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp) so that you can plug and play with these features on your own custom application(s).</span></span>

<span data-ttu-id="4fa15-110">本文将为您提供的不同功能的 Windows 10 IoT Core 默认应用还提供了如何为自己的应用程序可以利用这些不同的功能的简要介绍。</span><span class="sxs-lookup"><span data-stu-id="4fa15-110">This article will give you a rundown of the different features that the Windows 10 IoT Core Default App offers as well as how you can leverage these different features for your own applications.</span></span>

## <a name="leveraging-the-iot-core-default-app"></a><span data-ttu-id="4fa15-111">利用 IoT 核心版默认应用</span><span class="sxs-lookup"><span data-stu-id="4fa15-111">Leveraging the IoT Core Default App</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="4fa15-112">请不要将 maker 映像用于商品化。</span><span class="sxs-lookup"><span data-stu-id="4fa15-112">Do not use maker images for commercialization.</span></span> <span data-ttu-id="4fa15-113">如果 commercializing 设备，则必须使用自定义 FFU 为获得最佳安全性。</span><span class="sxs-lookup"><span data-stu-id="4fa15-113">If you are commercializing a device, you must use a custom FFU for optimal security.</span></span> <span data-ttu-id="4fa15-114">在[此处](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="4fa15-114">Learn more [here](https://docs.microsoft.com/en-us/windows-hardware/manufacture/iot/iot-core-manufacturing-guide).</span></span>

<span data-ttu-id="4fa15-115">可自定义 IoT Core 默认应用和扩展，或为你自己的应用使用作为示例的源代码。</span><span class="sxs-lookup"><span data-stu-id="4fa15-115">The IoT Core Default App can be customized and extended, or you can use the source code as an example for your own app.</span></span> <span data-ttu-id="4fa15-116">若要尝试此操作为自己，下载我们的示例的 zip 文件或签出代码 IoT Core 默认应用[此处](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp)。</span><span class="sxs-lookup"><span data-stu-id="4fa15-116">To try this out for yourself, download the zip of our samples or check out the code for the IoT Core Default App [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/IoTCoreDefaultApp).</span></span> <span data-ttu-id="4fa15-117">对于任何问题，请记录相应的问题上我们的示例存储库[此处](https://github.com/Microsoft/Windows-iotcore-samples/issues)。</span><span class="sxs-lookup"><span data-stu-id="4fa15-117">For any questions, please file an issue on our samples repo [here](https://github.com/Microsoft/Windows-iotcore-samples/issues).</span></span>

<span data-ttu-id="4fa15-118">如中所示[设置部分](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
)下面，在某些情况下，您可能会配置默认设置和功能在客户系统上代表最终用户。</span><span class="sxs-lookup"><span data-stu-id="4fa15-118">As shown under the [Settings section](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoredefaultapp#settings
) below, in some cases, you may configure default settings and features on your customer system on behalf of the end user.</span></span> <span data-ttu-id="4fa15-119">但是，如果您启用这些设置和功能在默认情况下，或如果诊断是上述基本设置，则必须：</span><span class="sxs-lookup"><span data-stu-id="4fa15-119">However, if you turn these settings and features on by default or if diagnostics are above the basic setting, you must:</span></span>

* <span data-ttu-id="4fa15-120">通知最终用户，这些功能已启用，并向最终用户提供指向 Microsoft 的隐私声明 web 页的链接[此处](http://go.microsoft.com/fwlink/?LinkId=521839)。</span><span class="sxs-lookup"><span data-stu-id="4fa15-120">Notify the end user that these features have been enable and provide the end user with the link to Microsoft's Privacy Statement web page [here](http://go.microsoft.com/fwlink/?LinkId=521839).</span></span> 
* <span data-ttu-id="4fa15-121">从相关的最终用户，默认情况下，（根据需要在适用法律） 启用此类功能安全许可。</span><span class="sxs-lookup"><span data-stu-id="4fa15-121">Secure consent from the relevant end user to enable such features by default (as required by applicable law).</span></span>
* <span data-ttu-id="4fa15-122">向最终用户能够返回到基本设置更改诊断设置。</span><span class="sxs-lookup"><span data-stu-id="4fa15-122">Provide end users the ability to change the Diagnostics setting back to the basic setting.</span></span>
* <span data-ttu-id="4fa15-123">如果启用 Microsoft 帐户，并且如果最终用户中删除 Microsoft 帐户具有对最终用户数据的访问，必须启用将要同时删除的设备上的所有最终用户的 Microsoft 帐户数据。</span><span class="sxs-lookup"><span data-stu-id="4fa15-123">If you enable Microsoft Accounts and you have access to end user data, if the end user deletes the Microsoft Account, you must enable simultaneous deletion of all the end user's Microsoft Account data on the device.</span></span> 

## <a name="out-of-box-experience-oobe"></a><span data-ttu-id="4fa15-124">开箱体验 (OOBE)</span><span class="sxs-lookup"><span data-stu-id="4fa15-124">Out-of-Box Experience (OOBE)</span></span>

<span data-ttu-id="4fa15-125">原因是它获得精益化 IoT Core 默认应用程序的开箱体验。</span><span class="sxs-lookup"><span data-stu-id="4fa15-125">The out-of-box experience for the IoT Core Default App is as lean as it gets.</span></span> <span data-ttu-id="4fa15-126">第一个页面将要求提供默认语言和 wi-fi 设置。</span><span class="sxs-lookup"><span data-stu-id="4fa15-126">The first pages will ask for a default language and wi-fi settings.</span></span> <span data-ttu-id="4fa15-127">从此处，为了使您的应用程序才能符合 GDPR 必须必须诊断数据屏幕，并且，如果您计划跟踪的位置，你将需要也有一个位置的权限屏幕。</span><span class="sxs-lookup"><span data-stu-id="4fa15-127">From there, in order for your app to be GDPR-compliant, you must have a diagnostic data screen and, if you're planning to track location, you will need to have a location permissions screen too.</span></span> <span data-ttu-id="4fa15-128">这两者的示例如下所示。</span><span class="sxs-lookup"><span data-stu-id="4fa15-128">Examples of both are shown below.</span></span> 

![<span data-ttu-id="4fa15-129">位置设置为 OOBE](../media/IoTCoreDefaultApp/OOBE3.jpg)
![OOBE 的诊断设置</span><span class="sxs-lookup"><span data-stu-id="4fa15-129">Location settings for OOBE](../media/IoTCoreDefaultApp/OOBE3.jpg)
![Diagnostic settings for OOBE</span></span>](../media/IoTCoreDefaultApp/OOBE4.jpg)

## <a name="command-bar"></a><span data-ttu-id="4fa15-130">命令栏</span><span class="sxs-lookup"><span data-stu-id="4fa15-130">Command Bar</span></span>
<span data-ttu-id="4fa15-131">在命令栏是持久性 horizonatal 栏位于屏幕的底部。</span><span class="sxs-lookup"><span data-stu-id="4fa15-131">The Command Bar is the persistant horizonatal bar located at the bottom of the screen.</span></span> <span data-ttu-id="4fa15-132">这可轻松访问以下功能：</span><span class="sxs-lookup"><span data-stu-id="4fa15-132">This provides easy access to the following funtionality:</span></span>
- <span data-ttu-id="4fa15-133">向前和向后的页导航</span><span class="sxs-lookup"><span data-stu-id="4fa15-133">Forward and backward page navigation</span></span>
- <span data-ttu-id="4fa15-134">无需离开当前页面的基本设备信息</span><span class="sxs-lookup"><span data-stu-id="4fa15-134">Basic device info without leaving the current page</span></span>
- <span data-ttu-id="4fa15-135">打开或关闭全屏幕模式</span><span class="sxs-lookup"><span data-stu-id="4fa15-135">Turning fullscreen mode on or off</span></span>
- <span data-ttu-id="4fa15-136">提前快捷方式</span><span class="sxs-lookup"><span data-stu-id="4fa15-136">Advance shortcuts</span></span>
- <span data-ttu-id="4fa15-137">特定页的按钮</span><span class="sxs-lookup"><span data-stu-id="4fa15-137">Page specific buttons</span></span>

<span data-ttu-id="4fa15-138">在命令栏中，有许多按钮，这些按钮有时可能会令人困惑的还是隐藏。</span><span class="sxs-lookup"><span data-stu-id="4fa15-138">There are a lot buttons in the Command Bar, and sometimes those buttons can be confusing or hidden.</span></span> <span data-ttu-id="4fa15-139">若要展开命令栏和访问这些按钮，请在右下方按菜单按钮：</span><span class="sxs-lookup"><span data-stu-id="4fa15-139">To expand the Command Bar and access those buttons, please press the menu button in the bottom right:</span></span>

![如何扩展命令栏](../media/IoTCoreDefaultApp/CommandBar.gif)

## <a name="start-menu---play"></a><span data-ttu-id="4fa15-141">播放开始菜单-</span><span class="sxs-lookup"><span data-stu-id="4fa15-141">Start Menu - Play</span></span>

<span data-ttu-id="4fa15-142">开始菜单是大多数插功能所在。</span><span class="sxs-lookup"><span data-stu-id="4fa15-142">The Start Menu is where most plug and play features live.</span></span>

### <a name="weather"></a><span data-ttu-id="4fa15-143">天气</span><span class="sxs-lookup"><span data-stu-id="4fa15-143">Weather</span></span>
<span data-ttu-id="4fa15-144">使用国家/地区的天气服务中的数据，天气页面会呈现天气信息在你的当前位置。</span><span class="sxs-lookup"><span data-stu-id="4fa15-144">Using data from the National Weather Service, the weather page renders weather information in your current location.</span></span>

### <a name="web-browser"></a><span data-ttu-id="4fa15-145">Web 浏览器</span><span class="sxs-lookup"><span data-stu-id="4fa15-145">Web Browser</span></span>
<span data-ttu-id="4fa15-146">Web 浏览器，可从 web 大多数站点中请求。</span><span class="sxs-lookup"><span data-stu-id="4fa15-146">The web browser allows you to pull up most sites from the web.</span></span>

### <a name="music"></a><span data-ttu-id="4fa15-147">音乐</span><span class="sxs-lookup"><span data-stu-id="4fa15-147">Music</span></span>
<span data-ttu-id="4fa15-148">此页将在播放 MP3 和 WAV 文件**音乐库**，可通过访问[Windows Device Portal](../manage-your-device/DevicePortal.md)。</span><span class="sxs-lookup"><span data-stu-id="4fa15-148">This page will play MP3 and WAV files from the **Music Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>  <span data-ttu-id="4fa15-149">若要将文件上传到音乐播放机，将需要以导航到 Windows Device Portal，单击"应用"下拉列表中，导航到"文件资源管理器"，选择"音乐"从此处将文件上传。</span><span class="sxs-lookup"><span data-stu-id="4fa15-149">To upload files to the music player, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Music" and upload your files from there.</span></span>


![如何将音乐文件上传](../media/IoTCoreDefaultApp/music.gif)

### <a name="slideshow"></a><span data-ttu-id="4fa15-151">“幻灯片放映”</span><span class="sxs-lookup"><span data-stu-id="4fa15-151">Slideshow</span></span>
<span data-ttu-id="4fa15-152">此页面将显示从任何 PNG 或 JPEG 图像文件**图片库**，可通过访问[Windows Device Portal](../manage-your-device/DevicePortal.md)。</span><span class="sxs-lookup"><span data-stu-id="4fa15-152">This page will display any PNG or JPEG image files from the **Pictures Library**, that can be accessed via the [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span> <span data-ttu-id="4fa15-153">若要将图像上载到幻灯片放映中，将需要以导航到 Windows Device Portal，单击"应用"下拉列表中，导航到"文件资源管理器"，选择"图片"从此处将文件上传。</span><span class="sxs-lookup"><span data-stu-id="4fa15-153">To upload images to the slideshow, you will need to navigate to the Windows Device Portal, click on the "Apps" dropdown, navigate to "File Explorer", select "Pictures" and upload your files from there.</span></span>


![如何将音乐文件上传](../media/IoTCoreDefaultApp/slideshow.gif)

### <a name="draw"></a><span data-ttu-id="4fa15-155">Draw</span><span class="sxs-lookup"><span data-stu-id="4fa15-155">Draw</span></span>
<span data-ttu-id="4fa15-156">此页可以查看 Windows 10 IoT Core 的墨迹功能测试。</span><span class="sxs-lookup"><span data-stu-id="4fa15-156">This page allows you to test out Windows 10 IoT Core's inking capabilities.</span></span>

## <a name="start-menu---explore"></a><span data-ttu-id="4fa15-157">开始菜单-浏览</span><span class="sxs-lookup"><span data-stu-id="4fa15-157">Start Menu - Explore</span></span> 

### <a name="apps"></a><span data-ttu-id="4fa15-158">应用</span><span class="sxs-lookup"><span data-stu-id="4fa15-158">Apps</span></span> 
<span data-ttu-id="4fa15-159">此页可以启动设备上安装其他前台应用程序。</span><span class="sxs-lookup"><span data-stu-id="4fa15-159">This page allows you to launch other foreground applications installed on the device.</span></span> <span data-ttu-id="4fa15-160">启动应用程序将挂起 IoT Core 默认应用，可以使用应用程序管理器中重新启动该应用[Windows Device Portal](../manage-your-device/DevicePortal.md)。</span><span class="sxs-lookup"><span data-stu-id="4fa15-160">Launching an application will suspend IoT Core Default App, which can be relaunched by using App Manager in [Windows Device Portal](../manage-your-device/DevicePortal.md).</span></span>

<span data-ttu-id="4fa15-161">没有任何特殊需要能够在页中，只需列出前台应用程序[安装](AppInstaller.md)或[部署](AppDeployment.md)应用程序。</span><span class="sxs-lookup"><span data-stu-id="4fa15-161">Nothing special is needed to have your foreground application listed in the page, simply [install](AppInstaller.md) or [deploy](AppDeployment.md) the application.</span></span> <span data-ttu-id="4fa15-162">成功安装或部署之后, 重新导航到应用程序页面以刷新应用程序的列表。</span><span class="sxs-lookup"><span data-stu-id="4fa15-162">After successful installation or deployment, re-navigate to the Apps page to refresh the list of applications.</span></span>

<span data-ttu-id="4fa15-163">请注意，有几个自动生成 OS 相关的我们筛选出的应用程序，则可以找到应用名称的列表[此处](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs)。</span><span class="sxs-lookup"><span data-stu-id="4fa15-163">Note that there are a couple of auto-generated OS related applications that we filter out, you can find the list of app names [here](http://github.com/Microsoft/Windows-iotcore-samples/tree/develop/Samples/IoTCoreDefaultApp/CS/Views/AppLauncherPage.xaml.cs).</span></span>

### <a name="notifications"></a><span data-ttu-id="4fa15-164">通知</span><span class="sxs-lookup"><span data-stu-id="4fa15-164">Notifications</span></span>
<span data-ttu-id="4fa15-165">此页将列出在过去 20 IoT Core 默认应用程序启动以来的通知。</span><span class="sxs-lookup"><span data-stu-id="4fa15-165">This page will list the past 20 notifications since IoT Core Default App was launched.</span></span> <span data-ttu-id="4fa15-166">当 IoT Core 默认应用在调试模式下运行时，这会创建测试通知添加按钮。</span><span class="sxs-lookup"><span data-stu-id="4fa15-166">When IoT Core Default App is running in debug mode, buttons are added that will create test notifications.</span></span>

### <a name="logs"></a><span data-ttu-id="4fa15-167">日志</span><span class="sxs-lookup"><span data-stu-id="4fa15-167">Logs</span></span>
<span data-ttu-id="4fa15-168">此页将列出任何自动生成崩溃或错误日志，然后可以从设备和分析。</span><span class="sxs-lookup"><span data-stu-id="4fa15-168">This page will list any auto-generated crash or error logs, which then can be taken off the device and analyzed.</span></span>

### <a name="github"></a><span data-ttu-id="4fa15-169">GitHub</span><span class="sxs-lookup"><span data-stu-id="4fa15-169">GitHub</span></span>
<span data-ttu-id="4fa15-170">此页将转到 IoT Core 默认应用程序代码的开放源代码 GitHub 位置。</span><span class="sxs-lookup"><span data-stu-id="4fa15-170">This page will take you to the open-sourced GitHub location of the IoT Core Default App code.</span></span>

## <a name="start-menu---windows-device-portal"></a><span data-ttu-id="4fa15-171">开始菜单-Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="4fa15-171">Start Menu - Windows Device Portal</span></span>

<span data-ttu-id="4fa15-172">在本部分页面可利用 Windows Device Portal REST Api，这要求使用 Windows Device Portal 凭据进行登录。</span><span class="sxs-lookup"><span data-stu-id="4fa15-172">The pages in this section leverage the Windows Device Portal REST APIs, which requires you to sign in using your Windows Device Portal credentials.</span></span>

## <a name="device-information"></a><span data-ttu-id="4fa15-173">设备信息</span><span class="sxs-lookup"><span data-stu-id="4fa15-173">Device Information</span></span>

<span data-ttu-id="4fa15-174">此页可以查看你的设备包括以太网、 OS 版本、 已连接的设备、 和的详细信息的不同功能。</span><span class="sxs-lookup"><span data-stu-id="4fa15-174">This page allows you to see the different features for your device including Ethernet, OS version, connected devices, and more.</span></span>

## <a name="command-line"></a><span data-ttu-id="4fa15-175">命令行</span><span class="sxs-lookup"><span data-stu-id="4fa15-175">Command Line</span></span>

<span data-ttu-id="4fa15-176">此页，可直接在你的设备上运行命令。</span><span class="sxs-lookup"><span data-stu-id="4fa15-176">This page allows you to run commands directly on your device.</span></span>

<span data-ttu-id="4fa15-177">若要启用此功能需要设置注册表项，以便应用程序可以运行命令。</span><span class="sxs-lookup"><span data-stu-id="4fa15-177">To enable this feature you have to set a registry key so that the app can run the commands.</span></span> <span data-ttu-id="4fa15-178">第一次尝试运行一个命令将看到一个链接，可以设置使用 Windows Device Portal 调用的注册表项。</span><span class="sxs-lookup"><span data-stu-id="4fa15-178">The first time you try to run a command you will see a link that allows you to set the registry key using a call to Windows Device Portal.</span></span> <span data-ttu-id="4fa15-179">单击链接以启用你的设备以运行命令。</span><span class="sxs-lookup"><span data-stu-id="4fa15-179">Click the link to enable your device to run commands.</span></span>

<span data-ttu-id="4fa15-180">某些命令需要管理员访问权限。</span><span class="sxs-lookup"><span data-stu-id="4fa15-180">Some commands require administrator access.</span></span> <span data-ttu-id="4fa15-181">出于安全考虑该应用使用非管理员帐户默认情况下运行命令。</span><span class="sxs-lookup"><span data-stu-id="4fa15-181">For security purposes the app uses a non-admin account by default to run commands.</span></span> <span data-ttu-id="4fa15-182">如果需要以管理员身份运行命令可以键入"RunAsAdmin <your command>"在命令行提示符下。</span><span class="sxs-lookup"><span data-stu-id="4fa15-182">If you need to run a command as an admin you can type "RunAsAdmin <your command>" in the command line prompt.</span></span>

## <a name="settings"></a><span data-ttu-id="4fa15-183">设置</span><span class="sxs-lookup"><span data-stu-id="4fa15-183">Settings</span></span>
<span data-ttu-id="4fa15-184">你可以配置大量设置此处包括的 Wi-fi、 蓝牙、 电源选项和的详细信息。</span><span class="sxs-lookup"><span data-stu-id="4fa15-184">You'll be able to configure a number of settings here including Wi-Fi, Bluetooth, power options, and more.</span></span>

### <a name="app-settings"></a><span data-ttu-id="4fa15-185">应用设置</span><span class="sxs-lookup"><span data-stu-id="4fa15-185">App Settings</span></span>
<span data-ttu-id="4fa15-186">**应用设置**部分允许您在应用程序配置页的各种设置。</span><span class="sxs-lookup"><span data-stu-id="4fa15-186">The **App Settings** section allows you to configure various settings for pages in the app.</span></span>  

<span data-ttu-id="4fa15-187">下面是一些你可以自定义的设置：</span><span class="sxs-lookup"><span data-stu-id="4fa15-187">Some of the settings you can customize are:</span></span>

##### <a name="general-settings"></a><span data-ttu-id="4fa15-188">常规设置</span><span class="sxs-lookup"><span data-stu-id="4fa15-188">General Settings</span></span>
* <span data-ttu-id="4fa15-189">设置显示应用程序启动时的默认页</span><span class="sxs-lookup"><span data-stu-id="4fa15-189">Set the default page that appears when the app is started</span></span>
* <span data-ttu-id="4fa15-190">启用/禁用屏幕保护程序</span><span class="sxs-lookup"><span data-stu-id="4fa15-190">Enable/disable the screensaver</span></span>

##### <a name="weather-settings"></a><span data-ttu-id="4fa15-191">天气设置</span><span class="sxs-lookup"><span data-stu-id="4fa15-191">Weather Settings</span></span>
* <span data-ttu-id="4fa15-192">更改位置</span><span class="sxs-lookup"><span data-stu-id="4fa15-192">Change the location</span></span>
  > <span data-ttu-id="4fa15-193">你提供一个有效才会启用此功能[必应地图服务令牌](https://msdn.microsoft.com/library/ff428642.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4fa15-193">This feature is only enabled if you have provided a valid [Bing Map Service Token](https://msdn.microsoft.com/library/ff428642.aspx).</span></span>  <span data-ttu-id="4fa15-194">若要将令牌传递给应用程序，创建**MapToken.config** LocalState 文件夹中的应用程序文件 (例如 C:\Data\USERS\\[User Account] \AppData\Packages\\[包的完整名称] \LocalState\MapToken.config) 并重新启动该应用程序。</span><span class="sxs-lookup"><span data-stu-id="4fa15-194">To pass the token to the app, create a **MapToken.config** file in the LocalState folder of the app (e.g. C:\Data\USERS\\[User Account]\AppData\Packages\\[Package Full Name]\LocalState\MapToken.config) and restart the app.</span></span>
* <span data-ttu-id="4fa15-195">展开代码图</span><span class="sxs-lookup"><span data-stu-id="4fa15-195">Expand the map</span></span>
* <span data-ttu-id="4fa15-196">启用/禁用映射翻转，以便将地图和天气交换机定期的放置以防止屏幕刻录中</span><span class="sxs-lookup"><span data-stu-id="4fa15-196">Enable/disable map flipping so that the map and the weather switch places periodically to prevent screen burn-in</span></span>

##### <a name="web-browser-settings"></a><span data-ttu-id="4fa15-197">Web 浏览器设置</span><span class="sxs-lookup"><span data-stu-id="4fa15-197">Web Browser Settings</span></span>
* <span data-ttu-id="4fa15-198">为 Web 浏览器设置主页页面</span><span class="sxs-lookup"><span data-stu-id="4fa15-198">Set the home page for the Web Browser</span></span>

##### <a name="slideshow-settings"></a><span data-ttu-id="4fa15-199">幻灯片放映设置</span><span class="sxs-lookup"><span data-stu-id="4fa15-199">Slideshow Settings</span></span>
* <span data-ttu-id="4fa15-200">设置幻灯片放映间隔</span><span class="sxs-lookup"><span data-stu-id="4fa15-200">Set the slideshow interval</span></span>

##### <a name="appearance"></a><span data-ttu-id="4fa15-201">外观</span><span class="sxs-lookup"><span data-stu-id="4fa15-201">Appearance</span></span>
* <span data-ttu-id="4fa15-202">MDL2 资产而不是表情符号用于磁贴图标</span><span class="sxs-lookup"><span data-stu-id="4fa15-202">Use MDL2 Assets instead of Emojis for the tile icons</span></span>
* <span data-ttu-id="4fa15-203">设置磁贴宽度和高度</span><span class="sxs-lookup"><span data-stu-id="4fa15-203">Set the tile width and height</span></span>
* <span data-ttu-id="4fa15-204">设置 UI 缩放-默认情况下自动缩放设置</span><span class="sxs-lookup"><span data-stu-id="4fa15-204">Set UI scaling - Automatic scaling is set by default</span></span>
* <span data-ttu-id="4fa15-205">设置磁贴颜色</span><span class="sxs-lookup"><span data-stu-id="4fa15-205">Set the tile color</span></span>

#### <a name="system"></a><span data-ttu-id="4fa15-206">系统</span><span class="sxs-lookup"><span data-stu-id="4fa15-206">System</span></span>
<span data-ttu-id="4fa15-207">更改语言、 键盘布局和时区。</span><span class="sxs-lookup"><span data-stu-id="4fa15-207">Change the language, keyboard layout, and time zone.</span></span>

#### <a name="network--wi-fi"></a><span data-ttu-id="4fa15-208">网络和 Wi-fi</span><span class="sxs-lookup"><span data-stu-id="4fa15-208">Network & Wi-Fi</span></span>
<span data-ttu-id="4fa15-209">查看网络适配器属性或连接到可用的 Wi-fi 网络。</span><span class="sxs-lookup"><span data-stu-id="4fa15-209">View network adapter properties or connect to an available Wi-Fi network.</span></span>

#### <a name="bluetooth"></a><span data-ttu-id="4fa15-210">蓝牙</span><span class="sxs-lookup"><span data-stu-id="4fa15-210">Bluetooth</span></span>
<span data-ttu-id="4fa15-211">与蓝牙设备配对。</span><span class="sxs-lookup"><span data-stu-id="4fa15-211">Pair with a Bluetooth device.</span></span>

#### <a name="app-updates"></a><span data-ttu-id="4fa15-212">应用更新</span><span class="sxs-lookup"><span data-stu-id="4fa15-212">App Updates</span></span>
<span data-ttu-id="4fa15-213">检查应用更新或更改自动更新设置。</span><span class="sxs-lookup"><span data-stu-id="4fa15-213">Check for app updates or change automatic update settings.</span></span>

#### <a name="power-options"></a><span data-ttu-id="4fa15-214">电源选项</span><span class="sxs-lookup"><span data-stu-id="4fa15-214">Power Options</span></span>
<span data-ttu-id="4fa15-215">重新启动或关闭设备。</span><span class="sxs-lookup"><span data-stu-id="4fa15-215">Restart or shutdown the device.</span></span>

#### <a name="diagnostics"></a><span data-ttu-id="4fa15-216">诊断</span><span class="sxs-lookup"><span data-stu-id="4fa15-216">Diagnostics</span></span>
<span data-ttu-id="4fa15-217">选择你想要提供 Microsoft 的诊断数据量。</span><span class="sxs-lookup"><span data-stu-id="4fa15-217">Select the amount of diagnostic data you wish to provide Microsoft.</span></span>  <span data-ttu-id="4fa15-218">我们鼓励用户选择加入**完整**使我们能够快速诊断问题并可对该产品的改进的诊断数据。</span><span class="sxs-lookup"><span data-stu-id="4fa15-218">We encourage users to opt into **Full** diagnostic data so we can diagnose issues quickly and make improvements to the product.</span></span>

##### <a name="basic"></a><span data-ttu-id="4fa15-219">基本</span><span class="sxs-lookup"><span data-stu-id="4fa15-219">Basic</span></span> 
<span data-ttu-id="4fa15-220">发送有关你的设备、 其设置和功能，仅信息是否正确执行。</span><span class="sxs-lookup"><span data-stu-id="4fa15-220">Send only info about your device, its settings and capabilities, and whether it is performing properly.</span></span>

##### <a name="full"></a><span data-ttu-id="4fa15-221">完全</span><span class="sxs-lookup"><span data-stu-id="4fa15-221">Full</span></span>
<span data-ttu-id="4fa15-222">发送所有基本的诊断数据，以及了解你浏览的网站以及如何使用应用程序和功能，外加有关设备运行状况、 设备活动和增强的错误报告的其他信息。</span><span class="sxs-lookup"><span data-stu-id="4fa15-222">Send all Basic diagnostic data, along with info about websites you browse and how you use apps and features, plus additional info about device health, device activity, and enhanced error reporting.</span></span>

#### <a name="location"></a><span data-ttu-id="4fa15-223">位置</span><span class="sxs-lookup"><span data-stu-id="4fa15-223">Location</span></span>
<span data-ttu-id="4fa15-224">允许或拒绝对你的位置的应用程序访问权限。</span><span class="sxs-lookup"><span data-stu-id="4fa15-224">Allow or deny the app access to your location.</span></span>
