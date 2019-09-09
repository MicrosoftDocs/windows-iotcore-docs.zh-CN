---
title: 适用于 Arduino 的 Windows 虚拟屏蔽概述
author: saraclay
ms.author: saclayt
ms.date: 09/13/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解如何为 Arduino 设置 Windows 虚拟防护，并构建你的第一个 Windows 10 IoT Core 应用。
keywords: windows iot，WVSA，Windows 虚拟防护，Arduino，应用
ms.openlocfilehash: bd1dccd59fbc99de9076260f6e21b0ac1403660a
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60168995"
---
> [!NOTE]
> <span data-ttu-id="ce3bb-104">你正在查看存档的文档。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-104">You are viewing archived documentation.</span></span> <span data-ttu-id="ce3bb-105">Windows 10 IoT 不再支持 AllJoyn。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="ce3bb-106">如有问题，请在 GitHub 上提出问题，或在下面的评论中留下反馈。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="set-up-windows-virtual-shields-for-arduino"></a><span data-ttu-id="ce3bb-107">为 Arduino 设置 Windows 虚拟屏蔽</span><span class="sxs-lookup"><span data-stu-id="ce3bb-107">Set up Windows Virtual Shields for Arduino</span></span>

## <a name="overview"></a><span data-ttu-id="ce3bb-108">概述</span><span class="sxs-lookup"><span data-stu-id="ce3bb-108">Overview</span></span>
<span data-ttu-id="ce3bb-109">如果使用了[Arduino](https://www.arduino.cc)，则很熟悉盾牌的概念。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-109">If you’ve used an [Arduino](https://www.arduino.cc), you’re familiar with the concept of a shield.</span></span> <span data-ttu-id="ce3bb-110">每个盾牌都具有专门用途（例如温度盾牌、加速感应防护板），构建具有多个屏蔽的设备可能会很复杂、成本高且节省空间。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-110">Each shield has a specialized purpose (e.g. a temperature shield, an accelerometer shield), and building a device with multiple shields can be complex, costly, and space-inefficient.</span></span> <span data-ttu-id="ce3bb-111">现在假设你可以使用低成本的 Windows Lumia Phone 作为一组精简的防护。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-111">Now imagine that you can use a low-cost Windows Lumia Phone as a compact set of shields.</span></span> <span data-ttu-id="ce3bb-112">你的 Arduino 草图可以通过易于使用的库调用，在 Windows Phone 中访问数百美元的传感器和功能。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-112">Your Arduino sketch would be able to access hundreds of dollars worth of sensors and capabilities in your Windows Phone through easy-to-use library calls.</span></span>

<span data-ttu-id="ce3bb-113">这正是用于开发人员的适用于 Arduino 库的 Windows 虚拟屏蔽。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-113">This is exactly what the Windows Virtual Shields for Arduino library enables for developers.</span></span> <span data-ttu-id="ce3bb-114">这并不是最佳做法-这项技术在所有 Windows 10 设备上都有效，因此，您也可以在您的 PC 或表面上使用传感器和功能。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-114">And that’s not the best part - this technology works on all Windows 10 devices, so you can use the sensors and capabilities on your PC or Surface as well.</span></span> <span data-ttu-id="ce3bb-115">此外，Arduino 还可以将计算成本高昂的任务（例如语音识别和 web 分析）卸载到 Windows 10 配套设备上！</span><span class="sxs-lookup"><span data-stu-id="ce3bb-115">Also, the Arduino can offload computationally expensive tasks like speech recognition and web parsing to the Windows 10 companion device!</span></span>

<span data-ttu-id="ce3bb-116">让我们了解如何设置硬件和软件，使其适用于 Arduino 的 Windows 虚拟防护板。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-116">Let's learn how to setup hardware and software to work with Windows Virtual Shields for Arduino.</span></span>


## <a name="1-get-your-windows-10-device-ready-for-developing-projects-using-windows-virtual-shields-for-arduino"></a><span data-ttu-id="ce3bb-117">1.使用适用于 Arduino 的 Windows 虚拟防护板，让 Windows 10 设备准备好开发项目。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-117">1. Get your Windows 10 device ready for developing projects using Windows Virtual Shields for Arduino.</span></span>

<span data-ttu-id="ce3bb-118">在本教程的此部分中，你将使用 Windows 虚拟 Arduino 应用程序加载它来准备你选择的 Windows 10 设备-此通用 Windows 应用程序允许你将设备用作 Arduino 板的 "虚拟盾牌"。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-118">In this section of the tutorial, you'll prepare a Windows 10 device of your choice by loading it with the Windows Virtual Shields for Arduino application - this Universal Windows Application allows you to use your device as a "virtual shield" for an Arduino board.</span></span>  <span data-ttu-id="ce3bb-119">这会为制造商提供一些强大的功能，从而使他们能够利用语音识别、触摸屏和 Windows 的计算能力相对容易。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-119">This results in some powerful possibilities for Makers, allowing them to utilize voice recognition, touch screens, and the computational power of Windows with relative ease.</span></span>

### <a name="hardware"></a><span data-ttu-id="ce3bb-120">硬件</span><span class="sxs-lookup"><span data-stu-id="ce3bb-120">Hardware</span></span>
<span data-ttu-id="ce3bb-121">适用于 Arduino 应用程序的 Windows 虚拟防护板可在任何 Windows 10 设备上运行，但本教程将使用 Windows Phone 说明安装程序。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-121">The Windows Virtual Shields for Arduino application can run on any Windows 10 device, but this tutorial will explain setup with a Windows Phone.</span></span>

<span data-ttu-id="ce3bb-122">*所需内容*Windows Phone 运行 Windows 10-建议[Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520)或[Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635)。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-122">*What you need* Windows Phone running Windows 10 - we recommend the [Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) or [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635).</span></span>

<span data-ttu-id="ce3bb-123">*设置 Windows Phone*</span><span class="sxs-lookup"><span data-stu-id="ce3bb-123">*Set up your Windows Phone*</span></span>

<span data-ttu-id="ce3bb-124">如果你的电话还没有运行 Windows 10，则可以选择安装软件的预览版本。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-124">If your phone is not already running Windows 10, there are options to install preview versions of the software.</span></span>  <span data-ttu-id="ce3bb-125">Windows Phone 8 用户可以访问 Microsoft Store 应用下载 "Windows 预览体验" 应用程序-此应用允许用户选择接收 Windows 10 Technical preview 作为更新。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-125">Windows Phone 8 users can go to the Microsoft Store app to download the "Windows Insider" application - this app allows the user to opt into receiving Windows 10 Technical Previews as updates.</span></span>  <span data-ttu-id="ce3bb-126">打开应用后，请按照提示和说明操作，并在手机成功运行 Windows 10 后继续操作。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-126">Follow the prompts and instructions upon opening the app, and continue once your phone is successfully running Windows 10.</span></span>

### <a name="software"></a><span data-ttu-id="ce3bb-127">软件</span><span class="sxs-lookup"><span data-stu-id="ce3bb-127">Software</span></span>

<span data-ttu-id="ce3bb-128">有两个选项可用于在 Windows Phone 上安装适用于 Arduino UWP 应用的 Windows 虚拟屏蔽。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-128">There are two options for installing the Windows Virtual Shields for Arduino UWP app on your Windows Phone.</span></span>  <span data-ttu-id="ce3bb-129">下载应用程序是更简单、更快速的选择。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-129">Downloading the app is the easier, quicker choice.</span></span>

* <span data-ttu-id="ce3bb-130">从 Microsoft Store 下载应用</span><span class="sxs-lookup"><span data-stu-id="ce3bb-130">Download the app from the Microsoft Store</span></span>
* <span data-ttu-id="ce3bb-131">使用电脑和 Visual Studio 旁加载应用</span><span class="sxs-lookup"><span data-stu-id="ce3bb-131">Sideload the app using a PC and Visual Studio</span></span>

<span data-ttu-id="ce3bb-132">*选项 1：从 Microsoft Store 下载应用*</span><span class="sxs-lookup"><span data-stu-id="ce3bb-132">*Option 1: Download the app from the Microsoft Store*</span></span>

<span data-ttu-id="ce3bb-133">单击此[链接](https://www.microsoft.com/store/apps/9nblgggz0mld)可访问 Arduino 的 Windows 虚拟防护板的 "Microsoft Store" 页，下载应用程序，然后安装。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-133">Follow this [link](https://www.microsoft.com/store/apps/9nblgggz0mld) to the Microsoft Store page for Windows Virtual Shields for Arduino, download the application, and then install.</span></span> <span data-ttu-id="ce3bb-134">然后，打开应用程序以确保它可以正常运行。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-134">You can then open the application to ensure it runs properly.</span></span>  <span data-ttu-id="ce3bb-135">现在，你的设备将被设置为用于 Arduino 的 "虚拟盾牌"！</span><span class="sxs-lookup"><span data-stu-id="ce3bb-135">Your device is now setup to be used as a "virtual shield" for an Arduino!</span></span>  <span data-ttu-id="ce3bb-136">你可以进入下一页。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-136">You can proceed to the next page.</span></span>

<span data-ttu-id="ce3bb-137">*选项 2：使用电脑和 Visual Studio*
旁加载应用程序所需的_内容_</span><span class="sxs-lookup"><span data-stu-id="ce3bb-137">*Option 2: Sideload the app using a PC and Visual Studio*
_What you need_</span></span>
* <span data-ttu-id="ce3bb-138">Visual Studio 2017 将适用于 Arduino 应用程序的 Windows 虚拟防护旁加载到开发人员解锁的手机上。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-138">Visual Studio 2017 to sideload the Windows Virtual Shields for Arduino app onto a developer-unlocked phone.</span></span>
* <span data-ttu-id="ce3bb-139">此[存储库](https://github.com/ms-iot/virtual-shields-universal)包含适用于 Arduino 应用程序的 Windows 虚拟防护板的代码。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-139">This [repository](https://github.com/ms-iot/virtual-shields-universal) containing the code for the Windows Virtual Shields for Arduino application.</span></span>  <span data-ttu-id="ce3bb-140">在本地磁盘上克隆存储库或将其下载为 ZIP。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-140">Either clone the repository or download it as a ZIP on your local disk.</span></span>  <span data-ttu-id="ce3bb-141">如果你不熟悉 git 并想要执行适当的克隆，请按照[此处](https://help.github.com/articles/cloning-a-repository)的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-141">If you're not familiar with git and want to do a proper clone, follow the instructions [here](https://help.github.com/articles/cloning-a-repository).</span></span>

<span data-ttu-id="ce3bb-142">_设置 Visual Studio 2017_</span><span class="sxs-lookup"><span data-stu-id="ce3bb-142">_Set up Visual Studio 2017_</span></span>
1. <span data-ttu-id="ce3bb-143">通过[dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads)中的 Windows 10 开发人员预览版工具安装 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-143">Install Visual Studio 2017 with the Windows 10 Developer Preview tools from [dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads).</span></span>  <span data-ttu-id="ce3bb-144">建议使用免费的适用于 Visual Studio 的社区版本，但 Enterprise 和 Professional 都适用。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-144">We recommend the free Community Version of Visual Studio, but both Enterprise and Professional will work as well.</span></span>  <span data-ttu-id="ce3bb-145">如果已安装 Visual Studio，请跳到下一步。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-145">If you already have Visual Studio installed, skip to the next step.</span></span>
2. <span data-ttu-id="ce3bb-146">在 Visual Studio 中，从上面 "需要的内容" 部分下载的存储库中加载一个盾牌。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-146">In Visual Studio, load the Shield.sln from the repository downloaded in the "What you need" section above.</span></span>
3. <span data-ttu-id="ce3bb-147">确保 Windows 10 设备（在这种情况下为 Windows Phone）由开发人员解除锁定。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-147">Ensure your Windows 10 device (in this case a Windows Phone) is developer-unlocked.</span></span> <span data-ttu-id="ce3bb-148">[本页说明如何](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx)解锁8.1、8和 7.1 Windows Phone;但对于 Windows 10 手机，步骤是相同的。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-148">[This page](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) explains how to unlock Windows Phone 8.1, 8, and 7.1; however, the steps are the same for Windows 10 phones.</span></span>
4. <span data-ttu-id="ce3bb-149">将 Windows 10 设备插入到计算机中，并将盾牌程序部署到设备。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-149">Plug your Windows 10 device into your computer and deploy the Shield.sln program to your device.</span></span>  <span data-ttu-id="ce3bb-150">为此，请部署到 "本地计算机"，并确保将设备体系结构设置为 "ARM"。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-150">To do this, deploy to a "Local Machine", and be sure to set the architecture of the device as "ARM".</span></span>
5. <span data-ttu-id="ce3bb-151">在手机上运行用于 Arduino 应用程序的新安装的 Windows 虚拟防护，以确保部署成功。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-151">Run the newly-installed Windows Virtual Shields for Arduino application on your phone to ensure the deploy was successful.</span></span>  <span data-ttu-id="ce3bb-152">现在，你的 Windows 10 设备将设置为用作虚拟盾牌！</span><span class="sxs-lookup"><span data-stu-id="ce3bb-152">Your Windows 10 device is now setup to be used as a virtual shield!</span></span>

## <a name="2-set-up-your-arduino-to-use-the-windows-virtual-shields-for-arduino-library"></a><span data-ttu-id="ce3bb-153">2.将 Arduino 设置为使用 Windows 虚拟防护 Arduino 库</span><span class="sxs-lookup"><span data-stu-id="ce3bb-153">2. Set up your Arduino to use the Windows Virtual Shields for Arduino library</span></span> 
<span data-ttu-id="ce3bb-154">在正确设置 Windows 10 配套设备后，让我们的 Arduino 准备好使用 Windows 虚拟防护 Arduino 库。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-154">With our Windows 10 companion device properly set up, let's get our Arduino ready to use the Windows Virtual Shields for Arduino library.</span></span> <span data-ttu-id="ce3bb-155">可以通过 USB、Bluetooth 或 Wi-fi 在 Arduino 和 Windows 10 "虚拟盾牌" 之间建立连接。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-155">You can establish a connection between your Arduino and your Windows 10 "virtual shield" over USB, Bluetooth, or Wi-Fi.</span></span> <span data-ttu-id="ce3bb-156">本特定教程将介绍如何使用蓝牙连接完成安装程序，但可随意试用其他选项。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-156">This particular tutorial will explain how to complete setup using a Bluetooth connection, but feel free to experiment with the other options.</span></span>

### <a name="hardware"></a><span data-ttu-id="ce3bb-157">硬件</span><span class="sxs-lookup"><span data-stu-id="ce3bb-157">Hardware</span></span>
<span data-ttu-id="ce3bb-158">*所需内容*</span><span class="sxs-lookup"><span data-stu-id="ce3bb-158">*What you need*</span></span>
* <span data-ttu-id="ce3bb-159">Arduino Uno 或兼容设备</span><span class="sxs-lookup"><span data-stu-id="ce3bb-159">Arduino Uno or compatible device</span></span>
* <span data-ttu-id="ce3bb-160">线路连接</span><span class="sxs-lookup"><span data-stu-id="ce3bb-160">Connecting wires</span></span>
* <span data-ttu-id="ce3bb-161">用于上传 Arduino 草图的电脑</span><span class="sxs-lookup"><span data-stu-id="ce3bb-161">A PC used to upload your Arduino sketches</span></span>
* <span data-ttu-id="ce3bb-162">标准 A 到标准 B USB-需要将草图上传到 Arduino 设备</span><span class="sxs-lookup"><span data-stu-id="ce3bb-162">Standard A to Standard B USB - needed to upload sketches to your Arduino device</span></span>
* <span data-ttu-id="ce3bb-163">可选：仅当你选择通过蓝牙进行连接时，才需要使用蓝牙模块。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-163">Optional: Bluetooth module - only needed if you choose to connect by Bluetooth.</span></span>
* <span data-ttu-id="ce3bb-164">可选：仅当你选择通过 wi-fi 进行连接时，才需要使用 wi-fi 模块。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-164">Optional: Wi-fi module - only needed if you choose to connect by wi-fi.</span></span>

* <span data-ttu-id="ce3bb-165">设置 Arduino</span><span class="sxs-lookup"><span data-stu-id="ce3bb-165">Set up your Arduino</span></span>
* <span data-ttu-id="ce3bb-166">如有必要，请准备好蓝牙模块（蓝牙模块可能需要在其上附加标题）。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-166">Prepare the Bluetooth module if necessary (the Bluetooth module may need to have headers soldered onto it).</span></span>
* <span data-ttu-id="ce3bb-167">除了下面所述的不同之外，每个[接线图](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup)将蓝牙模块连接到 Arduino。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-167">Except for the one different noted below, connected the Bluetooth module to the Arduino per [the wiring diagram](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup).</span></span>

  * <span data-ttu-id="ce3bb-168">效果使用0和1，而不是2和3：</span><span class="sxs-lookup"><span data-stu-id="ce3bb-168">Difference: Use pins 0 and 1 instead of 2 and 3:</span></span>
    * <span data-ttu-id="ce3bb-169">蓝牙 TX 应连接到 pin 0 （Arduino RX 或 RX0）。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-169">The Bluetooth TX should connect to pin 0 (Arduino RX or RX0).</span></span>
    * <span data-ttu-id="ce3bb-170">蓝牙 RX 应连接到 pin 1 （Arduino TX 或 TX1）。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-170">The Bluetooth RX should connect to pin 1 (Arduino TX or TX1).</span></span>

### <a name="software"></a><span data-ttu-id="ce3bb-171">软件</span><span class="sxs-lookup"><span data-stu-id="ce3bb-171">Software</span></span>
<span data-ttu-id="ce3bb-172">*所需内容*</span><span class="sxs-lookup"><span data-stu-id="ce3bb-172">*What you need*</span></span>
* <span data-ttu-id="ce3bb-173">Arduino IDE 1.6 或更高</span><span class="sxs-lookup"><span data-stu-id="ce3bb-173">Arduino IDE 1.6 or better</span></span>
* <span data-ttu-id="ce3bb-174">ArduinoJSON 库</span><span class="sxs-lookup"><span data-stu-id="ce3bb-174">ArduinoJSON library</span></span>
* <span data-ttu-id="ce3bb-175">[此存储库](https://github.com/ms-iot/virtual-shields-arduino)，其中包含将在 Arduino 上运行的示例草图。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-175">[This repository](https://github.com/ms-iot/virtual-shields-arduino), which contains the example sketch which will run on the Arduino.</span></span>

<span data-ttu-id="ce3bb-176">*设置 Arduino IDE*</span><span class="sxs-lookup"><span data-stu-id="ce3bb-176">*Set up your Arduino IDE*</span></span>
* <span data-ttu-id="ce3bb-177">下载并安装 Arduino IDE，然后启动程序。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-177">Download and install the Arduino IDE, then launch the program.</span></span>
* <span data-ttu-id="ce3bb-178">验证是否在 "*工具 > 板*" 下选择了正确的 Arduino 板。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-178">Verify that you have the correct Arduino board selected under *Tools > Board*.</span></span>
* <span data-ttu-id="ce3bb-179">验证是否在 "*工具 > 端口*" 下选择了正确的 COM 端口。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-179">Verify that you have the correct COM Port selected under *Tools > Port*.</span></span> <span data-ttu-id="ce3bb-180">该板的名称应显示在每个选项旁边，使选择正确的选项变得更加容易。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-180">The name of the board should appear next to each option, making it much easier to choose the correct option.</span></span>

<span data-ttu-id="ce3bb-181">*设置 ArduinoJSON 库*</span><span class="sxs-lookup"><span data-stu-id="ce3bb-181">*Set up the ArduinoJSON library*</span></span>
* <span data-ttu-id="ce3bb-182">从 [ArduinoJson 存储库](https://github.com/bblanchon/ArduinoJson)中，克隆存储库或下载压缩文件。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-182">From the [ArduinoJson repository](https://github.com/bblanchon/ArduinoJson), clone the repository or download the zip.</span></span>
* <span data-ttu-id="ce3bb-183">将整个存储库放入库文件夹（即`Documents\Arduino\libraries\ArduinoJson\`）。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-183">Place the whole repository into your libraries folder (i.e. `Documents\Arduino\libraries\ArduinoJson\`).</span></span>

<span data-ttu-id="ce3bb-184">*为 Arduino 库设置 Windows 虚拟屏蔽*</span><span class="sxs-lookup"><span data-stu-id="ce3bb-184">*Set up the Windows Virtual Shields for Arduino Library*</span></span>
* <span data-ttu-id="ce3bb-185">克隆[此存储库](https://github.com/ms-iot/virtual-shields-arduino)或下载 ZIP。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-185">Clone [this repository](https://github.com/ms-iot/virtual-shields-arduino) or download the ZIP.</span></span> <span data-ttu-id="ce3bb-186">如果你不熟悉 git 并想要执行适当的克隆，请按照[此处](https://help.github.com/articles/cloning-a-repository/)的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-186">If you're not familiar with git and want to do a proper clone, follow the instructions [here](https://help.github.com/articles/cloning-a-repository/).</span></span>
* <span data-ttu-id="ce3bb-187">将位于刚下载的存储库的 "Arduino\Libraries" 文件夹中的 "VirtualShield" 文件夹复制到 Arduino 库文件夹（即`Documents\Arduino\libraries\VirtualShield\`）。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-187">Copy the "VirtualShield" folder, found in the "Arduino\Libraries" folder of the repository you just downloaded, to your Arduino library folder (i.e. `Documents\Arduino\libraries\VirtualShield\`).</span></span>

<span data-ttu-id="ce3bb-188">*测试您的设置*</span><span class="sxs-lookup"><span data-stu-id="ce3bb-188">*Test your setup*</span></span>
* <span data-ttu-id="ce3bb-189">在 Arduino IDE 中，转到菜单项*文件-> 示例-> 虚拟盾牌 > HelloWorld*。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-189">From the Arduino IDE, go to the menu item *File -> Examples -> Virtual Shield -> HelloWorld-Speech-Eventing*.</span></span> <span data-ttu-id="ce3bb-190">这应该会根据我们在本教程中使用的 Hello World 示例来加载语音识别。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-190">This should load the speech-recognition based Hello World example we're using for this tutorial.</span></span>
* <span data-ttu-id="ce3bb-191">将该草绘上传到 Arduino 之前，请暂时从 Arduino 中删除蓝牙 TX 和 RX 线路（USB 和蓝牙之间仅共享一个串行端口，蓝牙与上传干扰）。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-191">Before uploading the sketch to your Arduino, temporarily remove the Bluetooth TX and RX wires from the Arduino (there is only one serial port shared between the USB and Bluetooth - the Bluetooth interferes with the upload).</span></span>
* <span data-ttu-id="ce3bb-192">按 IDE 中的 "上传" 按钮上载该草绘。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-192">Upload the sketch by pressing the "Upload" button in the IDE.</span></span>
* <span data-ttu-id="ce3bb-193">将蓝牙 TX 和 RX 线路替换为 Arduino 的 pin （蓝牙 TX to Arduino RX （或 RX0），并将蓝牙 RX 替换为 Arduino TX 或（TX1））。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-193">Replace the Bluetooth TX and RX wires into the Arduino pins (Bluetooth TX to Arduino RX (or RX0) and Bluetooth RX to Arduino TX or (TX1)).</span></span>
* <span data-ttu-id="ce3bb-194">在之前的页面（或其他 Windows 设备）上，在 "蓝牙" 设置中与 Arduino 上的蓝牙设备配对。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-194">On the phone (or other Windows device) you prepared on the previous page, pair to the Bluetooth device on your Arduino in the Bluetooth settings.</span></span> <span data-ttu-id="ce3bb-195">如果使用的是 BlueSMiRF，则默认 pin 代码为1234。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-195">If you're using the BlueSMiRF, the default pin code is 1234.</span></span> 

> [!NOTE]
> <span data-ttu-id="ce3bb-196">配对成功后，BlueSMiRF 上的红色闪烁灯会继续闪烁红色。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-196">The red blinking light on the BlueSMiRF continues to blink red after a successful pairing.</span></span> <span data-ttu-id="ce3bb-197">这是预期情况。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-197">This is expected.</span></span> <span data-ttu-id="ce3bb-198">在连接到 Arduino 应用程序的 Windows 虚拟屏蔽后，它只会关闭绿色。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-198">It only turns green after a connecting with the Windows Virtual Shields for Arduino application.</span></span>


## <a name="3-write-your-first-app-hello-blinky"></a><span data-ttu-id="ce3bb-199">3.编写第一个应用：你好，Blinky！</span><span class="sxs-lookup"><span data-stu-id="ce3bb-199">3. Write your first app: Hello, Blinky!</span></span> 

### <a name="hello-world-speech-enabled-led-example"></a><span data-ttu-id="ce3bb-200">Hello World 支持语音的 LED 示例</span><span class="sxs-lookup"><span data-stu-id="ce3bb-200">Hello World speech-enabled LED example</span></span>
<span data-ttu-id="ce3bb-201">将你的 Windows Phone（或任何可能的 Windows 10 设备！）和 Arduino 按本教程的上述步骤准备就绪后，你现在便可以试用我们的示例。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-201">With your Windows Phone (or potentially any Windows 10 device!) and your Arduino prepared as detailed in the previous steps of this tutorial, you're now ready to try our sample.</span></span>

1. <span data-ttu-id="ce3bb-202">通过将带有电阻器的 LED 连接到引脚 8 来准备你的 Arduino 开发板。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-202">Prepare your Arduino board by hooking up an LED with a resistor to pin 8.</span></span>
2. <span data-ttu-id="ce3bb-203">确保你的 Arduino 仍然上载有 HelloWorld-Speech-Eventing 示例，然后将 Arduinos 插入电源。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-203">Make sure that your Arduino is still uploaded with the HelloWorld-Speech-Eventing sample, and then plug the Arduino into a power supply.</span></span>
3. <span data-ttu-id="ce3bb-204">在你以前准备的 Windows Phone 上运行 Windows Virtual Shields for Arduino 应用。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-204">Run the Windows Virtual Shields for Arduino app on the Windows Phone you prepared previously.</span></span>
4. <span data-ttu-id="ce3bb-205">如果正确完成所有设置，你的手机应连接到 Arduino 草图并使用音频提示欢迎你。</span><span class="sxs-lookup"><span data-stu-id="ce3bb-205">If everything has been setup properly, your phone should connect to your Arduino sketch and welcome you with an audio cue.</span></span> <span data-ttu-id="ce3bb-206">你现在可以通过向 Windows 10 设备说出“打开”或“关闭”来打开和关闭 Arduino 上的 LED！</span><span class="sxs-lookup"><span data-stu-id="ce3bb-206">You can now say 'on' or 'off' to your Windows 10 device to switch the LED on your Arduino between on and off!</span></span>

### <a name="arduino-wiring-sketch-hello-world-example"></a><span data-ttu-id="ce3bb-207">Arduino 接线图素描：Hello World 示例</span><span class="sxs-lookup"><span data-stu-id="ce3bb-207">Arduino Wiring Sketch: Hello World example</span></span>

```C++
#include <ArduinoJson.h>

#include <VirtualShield.h>
#include <Text.h>
#include <Speech.h>
#include <Recognition.h>

VirtualShield shield;             // identify the shield
Text screen = Text(shield);       // connect the screen
Speech speech = Speech(shield);   // connect text to speech
Recognition recognition = Recognition(shield);    // connect speech to text

int LED_PIN = 8;

void recognitionEvent(ShieldEvent* event)
{
  if (event->resultId > 0) {
    digitalWrite(LED_PIN, recognition.recognizedIndex == 1 ? HIGH : LOW);
    screen.printAt(4, "Heard " + String(recognition.recognizedIndex == 1 ? "on" : "off"));
    recognition.listenFor("on,off", false);     // reset up the recognition after each event
  }
}

// when Bluetooth connects, or the 'Refresh' button is pressed
void refresh(ShieldEvent* event)
{
  String message = "Hello Virtual Shields. Say the word 'on' or 'off' to affect the LED";

  screen.clear();
  screen.print(message);
  speech.speak(message);

  recognition.listenFor("on,off", false);   // NON-blocking instruction to recognize speech
}

void setup()
{
  pinMode(LED_PIN, OUTPUT);
  pinMode(LED_PIN, LOW);

  recognition.setOnEvent(recognitionEvent); // set up a function to handle recognition events (turns auto-blocking off)
  shield.setOnRefresh(refresh);

  // begin() communication - you may specify a baud rate here, default is 115200
  shield.begin();
}

void loop()
{
  shield.checkSensors();            // handles Virtual Shield events.
}
```


