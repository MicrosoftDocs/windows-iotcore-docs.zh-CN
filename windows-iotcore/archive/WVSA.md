---
title: Windows 虚拟 Shields 为 arduino 开发概述
author: saraclay
ms.author: saclayt
ms.date: 09/13/17
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 了解如何设置 arduino 开发 Windows 虚拟 Shields 并生成首个 Windows 10 IoT 核心版应用。
keywords: windows iot，WVSA，Windows 虚拟 Shields，Arduino，应用程序
ms.openlocfilehash: bd1dccd59fbc99de9076260f6e21b0ac1403660a
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510837"
---
> [!NOTE]
> <span data-ttu-id="211b6-104">你正在查看存档的文档。</span><span class="sxs-lookup"><span data-stu-id="211b6-104">You are viewing archived documentation.</span></span> <span data-ttu-id="211b6-105">Windows 10 IoT 不再支持 AllJoyn。</span><span class="sxs-lookup"><span data-stu-id="211b6-105">AllJoyn is no longer supported by Windows 10 IoT.</span></span> <span data-ttu-id="211b6-106">如有问题，请打开在 GitHub 上或在下面的注释中留下反馈。</span><span class="sxs-lookup"><span data-stu-id="211b6-106">For questions, please open an issue on GitHub or leave us feedback in the comments below.</span></span>

# <a name="set-up-windows-virtual-shields-for-arduino"></a><span data-ttu-id="211b6-107">为 Windows 虚拟 Shields 设置 arduino 开发</span><span class="sxs-lookup"><span data-stu-id="211b6-107">Set up Windows Virtual Shields for Arduino</span></span>

## <a name="overview"></a><span data-ttu-id="211b6-108">概述</span><span class="sxs-lookup"><span data-stu-id="211b6-108">Overview</span></span>
<span data-ttu-id="211b6-109">如果使用过[Arduino](https://www.arduino.cc)，您熟悉使用防护的概念。</span><span class="sxs-lookup"><span data-stu-id="211b6-109">If you’ve used an [Arduino](https://www.arduino.cc), you’re familiar with the concept of a shield.</span></span> <span data-ttu-id="211b6-110">每个防火墙具有专门的用途 （例如温度防护罩，加速感应器防护罩），并生成具有多个 shields 的设备会很复杂，成本高昂，而且空间效率低下。</span><span class="sxs-lookup"><span data-stu-id="211b6-110">Each shield has a specialized purpose (e.g. a temperature shield, an accelerometer shield), and building a device with multiple shields can be complex, costly, and space-inefficient.</span></span> <span data-ttu-id="211b6-111">现在，假设您可以为一组精简 shields 使用成本较低 Windows Lumia 手机。</span><span class="sxs-lookup"><span data-stu-id="211b6-111">Now imagine that you can use a low-cost Windows Lumia Phone as a compact set of shields.</span></span> <span data-ttu-id="211b6-112">Arduino 草图将能够通过易于使用库调用访问数百个传感器以及 Windows Phone 中的功能值得美元。</span><span class="sxs-lookup"><span data-stu-id="211b6-112">Your Arduino sketch would be able to access hundreds of dollars worth of sensors and capabilities in your Windows Phone through easy-to-use library calls.</span></span>

<span data-ttu-id="211b6-113">这正是 Windows 虚拟 Shields Arduino 库使开发人员。</span><span class="sxs-lookup"><span data-stu-id="211b6-113">This is exactly what the Windows Virtual Shields for Arduino library enables for developers.</span></span> <span data-ttu-id="211b6-114">并不是最好的部分-这一技术可所有 Windows 10 设备，因此您可以使用传感器和功能在电脑或图面上也。</span><span class="sxs-lookup"><span data-stu-id="211b6-114">And that’s not the best part - this technology works on all Windows 10 devices, so you can use the sensors and capabilities on your PC or Surface as well.</span></span> <span data-ttu-id="211b6-115">此外，Arduino 可以卸载占用计算资源的任务，如语音识别和 web 到 Windows 10 伴侣设备分析 ！</span><span class="sxs-lookup"><span data-stu-id="211b6-115">Also, the Arduino can offload computationally expensive tasks like speech recognition and web parsing to the Windows 10 companion device!</span></span>

<span data-ttu-id="211b6-116">让我们了解如何设置硬件和软件以使用 Windows 虚拟 Shields 适用于 arduino 开发。</span><span class="sxs-lookup"><span data-stu-id="211b6-116">Let's learn how to setup hardware and software to work with Windows Virtual Shields for Arduino.</span></span>


## <a name="1-get-your-windows-10-device-ready-for-developing-projects-using-windows-virtual-shields-for-arduino"></a><span data-ttu-id="211b6-117">1.使你的 Windows 10 设备可供开发使用 Windows 虚拟 Shields 适用于 Arduino 的项目。</span><span class="sxs-lookup"><span data-stu-id="211b6-117">1. Get your Windows 10 device ready for developing projects using Windows Virtual Shields for Arduino.</span></span>

<span data-ttu-id="211b6-118">在本教程的此部分中，你将通过使用 Arduino 应用程序的 Windows 虚拟防护加载它准备所选的 Windows 10 设备-此通用 Windows 应用程序，可使用你的设备作为"虚拟盾牌"arduino 开发板。</span><span class="sxs-lookup"><span data-stu-id="211b6-118">In this section of the tutorial, you'll prepare a Windows 10 device of your choice by loading it with the Windows Virtual Shields for Arduino application - this Universal Windows Application allows you to use your device as a "virtual shield" for an Arduino board.</span></span>  <span data-ttu-id="211b6-119">此结果中的创建者，从而允许它们使用语音识别某些强有力的可能性相对轻松地触摸屏幕和 Windows 的计算能力。</span><span class="sxs-lookup"><span data-stu-id="211b6-119">This results in some powerful possibilities for Makers, allowing them to utilize voice recognition, touch screens, and the computational power of Windows with relative ease.</span></span>

### <a name="hardware"></a><span data-ttu-id="211b6-120">硬件</span><span class="sxs-lookup"><span data-stu-id="211b6-120">Hardware</span></span>
<span data-ttu-id="211b6-121">Windows 虚拟 Shields Arduino 应用程序可以在任何 Windows 10 设备上运行，但本教程将介绍与 Windows Phone 安装程序。</span><span class="sxs-lookup"><span data-stu-id="211b6-121">The Windows Virtual Shields for Arduino application can run on any Windows 10 device, but this tutorial will explain setup with a Windows Phone.</span></span>

<span data-ttu-id="211b6-122">*所需*Windows Phone 运行 Windows 10-我们建议[Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520)或[Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635)。</span><span class="sxs-lookup"><span data-stu-id="211b6-122">*What you need* Windows Phone running Windows 10 - we recommend the [Lumia 520](http://www.microsoft.com/en-us/mobile/phone/lumia520) or [Lumia 635](http://www.microsoft.com/en-us/mobile/phone/lumia635).</span></span>

*<span data-ttu-id="211b6-123">设置 Windows Phone</span><span class="sxs-lookup"><span data-stu-id="211b6-123">Set up your Windows Phone</span></span>*

<span data-ttu-id="211b6-124">如果你的手机已不在运行 Windows 10，有选项来安装软件的预览版本。</span><span class="sxs-lookup"><span data-stu-id="211b6-124">If your phone is not already running Windows 10, there are options to install preview versions of the software.</span></span>  <span data-ttu-id="211b6-125">Windows Phone 8 用户可以转到下载"Windows Insider"应用程序的 Microsoft Store 应用-使用此应用，用户可以选择接收作为更新的 Windows 10 Technical Preview。</span><span class="sxs-lookup"><span data-stu-id="211b6-125">Windows Phone 8 users can go to the Microsoft Store app to download the "Windows Insider" application - this app allows the user to opt into receiving Windows 10 Technical Previews as updates.</span></span>  <span data-ttu-id="211b6-126">按照提示和打开应用时的说明操作并继续您的电话已成功运行 Windows 10 后。</span><span class="sxs-lookup"><span data-stu-id="211b6-126">Follow the prompts and instructions upon opening the app, and continue once your phone is successfully running Windows 10.</span></span>

### <a name="software"></a><span data-ttu-id="211b6-127">软件</span><span class="sxs-lookup"><span data-stu-id="211b6-127">Software</span></span>

<span data-ttu-id="211b6-128">有两个选项可用于在 Windows Phone 上安装 arduino 开发 UWP 应用的 Windows 虚拟防护。</span><span class="sxs-lookup"><span data-stu-id="211b6-128">There are two options for installing the Windows Virtual Shields for Arduino UWP app on your Windows Phone.</span></span>  <span data-ttu-id="211b6-129">下载应用程序是更轻松、 更快的选择。</span><span class="sxs-lookup"><span data-stu-id="211b6-129">Downloading the app is the easier, quicker choice.</span></span>

* <span data-ttu-id="211b6-130">从 Microsoft Store 下载应用</span><span class="sxs-lookup"><span data-stu-id="211b6-130">Download the app from the Microsoft Store</span></span>
* <span data-ttu-id="211b6-131">旁加载应用使用 PC 和 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="211b6-131">Sideload the app using a PC and Visual Studio</span></span>

*<span data-ttu-id="211b6-132">选项 1：从 Microsoft Store 下载应用</span><span class="sxs-lookup"><span data-stu-id="211b6-132">Option 1: Download the app from the Microsoft Store</span></span>*

<span data-ttu-id="211b6-133">按照这[链接](https://www.microsoft.com/store/apps/9nblgggz0mld)到 Windows 虚拟 arduino Shields 的 Microsoft Store 页上，下载该应用程序，并安装。</span><span class="sxs-lookup"><span data-stu-id="211b6-133">Follow this [link](https://www.microsoft.com/store/apps/9nblgggz0mld) to the Microsoft Store page for Windows Virtual Shields for Arduino, download the application, and then install.</span></span> <span data-ttu-id="211b6-134">然后，打开应用程序以确保它可以正常运行。</span><span class="sxs-lookup"><span data-stu-id="211b6-134">You can then open the application to ensure it runs properly.</span></span>  <span data-ttu-id="211b6-135">你的设备现在已设置为用作 Arduino"虚拟盾牌"！</span><span class="sxs-lookup"><span data-stu-id="211b6-135">Your device is now setup to be used as a "virtual shield" for an Arduino!</span></span>  <span data-ttu-id="211b6-136">你可以转到下一页。</span><span class="sxs-lookup"><span data-stu-id="211b6-136">You can proceed to the next page.</span></span>

<span data-ttu-id="211b6-137">*选项 2：旁加载应用使用 PC 和 Visual Studio*
_所需内容_</span><span class="sxs-lookup"><span data-stu-id="211b6-137">*Option 2: Sideload the app using a PC and Visual Studio*
_What you need_</span></span>
* <span data-ttu-id="211b6-138">旁加载 Windows 虚拟 Shields 的 Arduino 应用程序应用到开发人员解锁手机的 visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="211b6-138">Visual Studio 2017 to sideload the Windows Virtual Shields for Arduino app onto a developer-unlocked phone.</span></span>
* <span data-ttu-id="211b6-139">这[存储库](https://github.com/ms-iot/virtual-shields-universal)的 Windows 虚拟 Shields Arduino 应用程序中包含的代码。</span><span class="sxs-lookup"><span data-stu-id="211b6-139">This [repository](https://github.com/ms-iot/virtual-shields-universal) containing the code for the Windows Virtual Shields for Arduino application.</span></span>  <span data-ttu-id="211b6-140">克隆存储库，或者以本地磁盘上的 zip 格式下载它。</span><span class="sxs-lookup"><span data-stu-id="211b6-140">Either clone the repository or download it as a ZIP on your local disk.</span></span>  <span data-ttu-id="211b6-141">如果您不熟悉 git，并想要执行的正确克隆，按照的说明[此处](https://help.github.com/articles/cloning-a-repository)。</span><span class="sxs-lookup"><span data-stu-id="211b6-141">If you're not familiar with git and want to do a proper clone, follow the instructions [here](https://help.github.com/articles/cloning-a-repository).</span></span>

_<span data-ttu-id="211b6-142">设置 Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="211b6-142">Set up Visual Studio 2017</span></span>_
1. <span data-ttu-id="211b6-143">使用 Windows 10 开发人员预览版工具从安装 Visual Studio 2017 [dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads)。</span><span class="sxs-lookup"><span data-stu-id="211b6-143">Install Visual Studio 2017 with the Windows 10 Developer Preview tools from [dev.windows.com](https://developer.microsoft.com/en-us/windows/downloads).</span></span>  <span data-ttu-id="211b6-144">我们建议免费社区版本的 Visual Studio 中，但也可以 Enterprise 和 Professional。</span><span class="sxs-lookup"><span data-stu-id="211b6-144">We recommend the free Community Version of Visual Studio, but both Enterprise and Professional will work as well.</span></span>  <span data-ttu-id="211b6-145">如果已安装 Visual Studio，请跳到下一步。</span><span class="sxs-lookup"><span data-stu-id="211b6-145">If you already have Visual Studio installed, skip to the next step.</span></span>
2. <span data-ttu-id="211b6-146">在 Visual Studio 中，负载 Shield.sln 从存储库下载在"你需要什么"一节。</span><span class="sxs-lookup"><span data-stu-id="211b6-146">In Visual Studio, load the Shield.sln from the repository downloaded in the "What you need" section above.</span></span>
3. <span data-ttu-id="211b6-147">请确保 Windows 10 设备 （在本例中为 Windows Phone） 是开发人员解锁。</span><span class="sxs-lookup"><span data-stu-id="211b6-147">Ensure your Windows 10 device (in this case a Windows Phone) is developer-unlocked.</span></span> <span data-ttu-id="211b6-148">[此页](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx)介绍了如何解锁 Windows Phone 8.1、 8 和 7.1; 但是，步骤是相同的适用于 Windows 10 手机。</span><span class="sxs-lookup"><span data-stu-id="211b6-148">[This page](https://msdn.microsoft.com/library/windows/apps/dn614128.aspx) explains how to unlock Windows Phone 8.1, 8, and 7.1; however, the steps are the same for Windows 10 phones.</span></span>
4. <span data-ttu-id="211b6-149">在 Windows 10 设备插入计算机并将 Shield.sln 程序部署到你的设备。</span><span class="sxs-lookup"><span data-stu-id="211b6-149">Plug your Windows 10 device into your computer and deploy the Shield.sln program to your device.</span></span>  <span data-ttu-id="211b6-150">若要执行此操作，将部署到"本地计算机"并确保设置"ARM"作为设备的体系结构。</span><span class="sxs-lookup"><span data-stu-id="211b6-150">To do this, deploy to a "Local Machine", and be sure to set the architecture of the device as "ARM".</span></span>
5. <span data-ttu-id="211b6-151">运行新安装 Arduino 应用程序在手机上，以确保部署的 Windows 虚拟防护已成功完成。</span><span class="sxs-lookup"><span data-stu-id="211b6-151">Run the newly-installed Windows Virtual Shields for Arduino application on your phone to ensure the deploy was successful.</span></span>  <span data-ttu-id="211b6-152">在 Windows 10 设备现在已设置要用作虚拟防护罩 ！</span><span class="sxs-lookup"><span data-stu-id="211b6-152">Your Windows 10 device is now setup to be used as a virtual shield!</span></span>

## <a name="2-set-up-your-arduino-to-use-the-windows-virtual-shields-for-arduino-library"></a><span data-ttu-id="211b6-153">2.设置在 Arduino，Arduino 库要使用的 Windows 虚拟 Shields</span><span class="sxs-lookup"><span data-stu-id="211b6-153">2. Set up your Arduino to use the Windows Virtual Shields for Arduino library</span></span> 
<span data-ttu-id="211b6-154">与我们的 Windows 10 伴侣设备正确设置，让我们开始我们 Arduino Arduino 库要使用的 Windows 虚拟 Shields。</span><span class="sxs-lookup"><span data-stu-id="211b6-154">With our Windows 10 companion device properly set up, let's get our Arduino ready to use the Windows Virtual Shields for Arduino library.</span></span> <span data-ttu-id="211b6-155">您可以通过 USB、 蓝牙或 Wi-fi 在 arduino 开发和 Windows 10"虚拟盾牌"之间建立连接。</span><span class="sxs-lookup"><span data-stu-id="211b6-155">You can establish a connection between your Arduino and your Windows 10 "virtual shield" over USB, Bluetooth, or Wi-Fi.</span></span> <span data-ttu-id="211b6-156">本特定教程将介绍如何完成安装程序使用蓝牙连接，但随意尝试其他选项。</span><span class="sxs-lookup"><span data-stu-id="211b6-156">This particular tutorial will explain how to complete setup using a Bluetooth connection, but feel free to experiment with the other options.</span></span>

### <a name="hardware"></a><span data-ttu-id="211b6-157">硬件</span><span class="sxs-lookup"><span data-stu-id="211b6-157">Hardware</span></span>
*<span data-ttu-id="211b6-158">需要具备的条件</span><span class="sxs-lookup"><span data-stu-id="211b6-158">What you need</span></span>*
* <span data-ttu-id="211b6-159">Arduino Uno 或兼容的设备</span><span class="sxs-lookup"><span data-stu-id="211b6-159">Arduino Uno or compatible device</span></span>
* <span data-ttu-id="211b6-160">连线</span><span class="sxs-lookup"><span data-stu-id="211b6-160">Connecting wires</span></span>
* <span data-ttu-id="211b6-161">用于上传 Arduino 草图 PC</span><span class="sxs-lookup"><span data-stu-id="211b6-161">A PC used to upload your Arduino sketches</span></span>
* <span data-ttu-id="211b6-162">与标准 B USB-将草图上传到你的 Arduino 设备所需的标准 A</span><span class="sxs-lookup"><span data-stu-id="211b6-162">Standard A to Standard B USB - needed to upload sketches to your Arduino device</span></span>
* <span data-ttu-id="211b6-163">可选：蓝牙模块-如果选择通过蓝牙连接，才需要。</span><span class="sxs-lookup"><span data-stu-id="211b6-163">Optional: Bluetooth module - only needed if you choose to connect by Bluetooth.</span></span>
* <span data-ttu-id="211b6-164">可选：Wi-fi 模块-如果你选择的 wi-fi 连接，才需要。</span><span class="sxs-lookup"><span data-stu-id="211b6-164">Optional: Wi-fi module - only needed if you choose to connect by wi-fi.</span></span>

* <span data-ttu-id="211b6-165">设置 Arduino</span><span class="sxs-lookup"><span data-stu-id="211b6-165">Set up your Arduino</span></span>
* <span data-ttu-id="211b6-166">如有必要，请准备好蓝牙模块（蓝牙模块可能需要在其上附加标题）。</span><span class="sxs-lookup"><span data-stu-id="211b6-166">Prepare the Bluetooth module if necessary (the Bluetooth module may need to have headers soldered onto it).</span></span>
* <span data-ttu-id="211b6-167">除不同如下所示，连接到每个 Arduino 蓝牙模块[线图表](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup)。</span><span class="sxs-lookup"><span data-stu-id="211b6-167">Except for the one different noted below, connected the Bluetooth module to the Arduino per [the wiring diagram](https://learn.sparkfun.com/tutorials/using-the-bluesmirf/hardware-hookup).</span></span>

  * <span data-ttu-id="211b6-168">差异：使用而不是 2 和 3 引脚 0 和 1:</span><span class="sxs-lookup"><span data-stu-id="211b6-168">Difference: Use pins 0 and 1 instead of 2 and 3:</span></span>
    * <span data-ttu-id="211b6-169">蓝牙 TX 应连接到 pin 0 （Arduino RX 或 RX0）。</span><span class="sxs-lookup"><span data-stu-id="211b6-169">The Bluetooth TX should connect to pin 0 (Arduino RX or RX0).</span></span>
    * <span data-ttu-id="211b6-170">蓝牙 RX 应连接到 1 （Arduino TX 或 TX1） 的 pin。</span><span class="sxs-lookup"><span data-stu-id="211b6-170">The Bluetooth RX should connect to pin 1 (Arduino TX or TX1).</span></span>

### <a name="software"></a><span data-ttu-id="211b6-171">软件</span><span class="sxs-lookup"><span data-stu-id="211b6-171">Software</span></span>
*<span data-ttu-id="211b6-172">需要具备的条件</span><span class="sxs-lookup"><span data-stu-id="211b6-172">What you need</span></span>*
* <span data-ttu-id="211b6-173">Arduino IDE 版本 1.6 或更高</span><span class="sxs-lookup"><span data-stu-id="211b6-173">Arduino IDE 1.6 or better</span></span>
* <span data-ttu-id="211b6-174">ArduinoJSON 库</span><span class="sxs-lookup"><span data-stu-id="211b6-174">ArduinoJSON library</span></span>
* <span data-ttu-id="211b6-175">[此存储库](https://github.com/ms-iot/virtual-shields-arduino)，其中包含将在 Arduino 上运行该示例草图。</span><span class="sxs-lookup"><span data-stu-id="211b6-175">[This repository](https://github.com/ms-iot/virtual-shields-arduino), which contains the example sketch which will run on the Arduino.</span></span>

*<span data-ttu-id="211b6-176">设置 Arduino IDE</span><span class="sxs-lookup"><span data-stu-id="211b6-176">Set up your Arduino IDE</span></span>*
* <span data-ttu-id="211b6-177">下载并安装 Arduino IDE 中，然后启动程序。</span><span class="sxs-lookup"><span data-stu-id="211b6-177">Download and install the Arduino IDE, then launch the program.</span></span>
* <span data-ttu-id="211b6-178">验证是否具有正确的 arduino 开发板下选择*工具 > 板*。</span><span class="sxs-lookup"><span data-stu-id="211b6-178">Verify that you have the correct Arduino board selected under *Tools > Board*.</span></span>
* <span data-ttu-id="211b6-179">请确保您有下选择了正确的 COM 端口*工具 > 端口*。</span><span class="sxs-lookup"><span data-stu-id="211b6-179">Verify that you have the correct COM Port selected under *Tools > Port*.</span></span> <span data-ttu-id="211b6-180">每个选项，使其更易于选择正确的选项旁边应显示的看板的名称。</span><span class="sxs-lookup"><span data-stu-id="211b6-180">The name of the board should appear next to each option, making it much easier to choose the correct option.</span></span>

*<span data-ttu-id="211b6-181">设置 ArduinoJSON 库</span><span class="sxs-lookup"><span data-stu-id="211b6-181">Set up the ArduinoJSON library</span></span>*
* <span data-ttu-id="211b6-182">从 [ArduinoJson 存储库](https://github.com/bblanchon/ArduinoJson)中，克隆存储库或下载压缩文件。</span><span class="sxs-lookup"><span data-stu-id="211b6-182">From the [ArduinoJson repository](https://github.com/bblanchon/ArduinoJson), clone the repository or download the zip.</span></span>
* <span data-ttu-id="211b6-183">将整个存储库放入您的库文件夹 (即`Documents\Arduino\libraries\ArduinoJson\`)。</span><span class="sxs-lookup"><span data-stu-id="211b6-183">Place the whole repository into your libraries folder (i.e. `Documents\Arduino\libraries\ArduinoJson\`).</span></span>

*<span data-ttu-id="211b6-184">为 Windows 虚拟 Shields 设置 Arduino 库</span><span class="sxs-lookup"><span data-stu-id="211b6-184">Set up the Windows Virtual Shields for Arduino Library</span></span>*
* <span data-ttu-id="211b6-185">克隆[此存储库](https://github.com/ms-iot/virtual-shields-arduino)或下载 zip 文件。</span><span class="sxs-lookup"><span data-stu-id="211b6-185">Clone [this repository](https://github.com/ms-iot/virtual-shields-arduino) or download the ZIP.</span></span> <span data-ttu-id="211b6-186">如果您不熟悉 git，并想要执行的正确克隆，按照的说明[此处](https://help.github.com/articles/cloning-a-repository/)。</span><span class="sxs-lookup"><span data-stu-id="211b6-186">If you're not familiar with git and want to do a proper clone, follow the instructions [here](https://help.github.com/articles/cloning-a-repository/).</span></span>
* <span data-ttu-id="211b6-187">复制"VirtualShield"文件夹，你只需下载，请到 Arduino 库文件夹的存储库的"Arduino\Libraries"文件夹中找到 (即`Documents\Arduino\libraries\VirtualShield\`)。</span><span class="sxs-lookup"><span data-stu-id="211b6-187">Copy the "VirtualShield" folder, found in the "Arduino\Libraries" folder of the repository you just downloaded, to your Arduino library folder (i.e. `Documents\Arduino\libraries\VirtualShield\`).</span></span>

*<span data-ttu-id="211b6-188">测试设置</span><span class="sxs-lookup"><span data-stu-id="211b6-188">Test your setup</span></span>*
* <span data-ttu-id="211b6-189">从 Arduino IDE 中，转到菜单项*文件-> 示例-> 虚拟盾牌-> 事件处理语音 HelloWorld*。</span><span class="sxs-lookup"><span data-stu-id="211b6-189">From the Arduino IDE, go to the menu item *File -> Examples -> Virtual Shield -> HelloWorld-Speech-Eventing*.</span></span> <span data-ttu-id="211b6-190">这应加载的语音识别基于 Hello World 示例，我们使用在本教程。</span><span class="sxs-lookup"><span data-stu-id="211b6-190">This should load the speech-recognition based Hello World example we're using for this tutorial.</span></span>
* <span data-ttu-id="211b6-191">上载到你 Arduino 草图之前, 暂时移除蓝牙 TX 和 RX 电线的 Arduino （只有一个 USB 和蓝牙-蓝牙之间共享的串行端口会影响上传没有）。</span><span class="sxs-lookup"><span data-stu-id="211b6-191">Before uploading the sketch to your Arduino, temporarily remove the Bluetooth TX and RX wires from the Arduino (there is only one serial port shared between the USB and Bluetooth - the Bluetooth interferes with the upload).</span></span>
* <span data-ttu-id="211b6-192">通过在 IDE 中按"上传"按钮上, 传草图。</span><span class="sxs-lookup"><span data-stu-id="211b6-192">Upload the sketch by pressing the "Upload" button in the IDE.</span></span>
* <span data-ttu-id="211b6-193">替换为蓝牙 TX 和 RX 电线到 arduino 开发插针 (蓝牙 TX 到 arduino 开发 RX （或 RX0） 和蓝牙到 arduino 开发 TX RX 或 (TX1))。</span><span class="sxs-lookup"><span data-stu-id="211b6-193">Replace the Bluetooth TX and RX wires into the Arduino pins (Bluetooth TX to Arduino RX (or RX0) and Bluetooth RX to Arduino TX or (TX1)).</span></span>
* <span data-ttu-id="211b6-194">在手机 （或其他 Windows 设备） 上你准备在上一页上，在 arduino 开发中的蓝牙设置上的蓝牙设备配对。</span><span class="sxs-lookup"><span data-stu-id="211b6-194">On the phone (or other Windows device) you prepared on the previous page, pair to the Bluetooth device on your Arduino in the Bluetooth settings.</span></span> <span data-ttu-id="211b6-195">如果使用的 BlueSMiRF，默认 pin 代码是 1234年。</span><span class="sxs-lookup"><span data-stu-id="211b6-195">If you're using the BlueSMiRF, the default pin code is 1234.</span></span> 

> [!NOTE]
> <span data-ttu-id="211b6-196">配对成功后，BlueSMiRF 上的红色闪烁灯会继续闪烁红色。</span><span class="sxs-lookup"><span data-stu-id="211b6-196">The red blinking light on the BlueSMiRF continues to blink red after a successful pairing.</span></span> <span data-ttu-id="211b6-197">这是预期情况。</span><span class="sxs-lookup"><span data-stu-id="211b6-197">This is expected.</span></span> <span data-ttu-id="211b6-198">它仅将变为绿色后使用 Windows 虚拟 Shields Arduino 应用程序进行连接。</span><span class="sxs-lookup"><span data-stu-id="211b6-198">It only turns green after a connecting with the Windows Virtual Shields for Arduino application.</span></span>


## <a name="3-write-your-first-app-hello-blinky"></a><span data-ttu-id="211b6-199">3.编写第一个应用：Hello，灾难从天而降 ！</span><span class="sxs-lookup"><span data-stu-id="211b6-199">3. Write your first app: Hello, Blinky!</span></span> 

### <a name="hello-world-speech-enabled-led-example"></a><span data-ttu-id="211b6-200">Hello World 支持语音的 LED 示例</span><span class="sxs-lookup"><span data-stu-id="211b6-200">Hello World speech-enabled LED example</span></span>
<span data-ttu-id="211b6-201">将你的 Windows Phone（或任何可能的 Windows 10 设备！）和 Arduino 按本教程的上述步骤准备就绪后，你现在便可以试用我们的示例。</span><span class="sxs-lookup"><span data-stu-id="211b6-201">With your Windows Phone (or potentially any Windows 10 device!) and your Arduino prepared as detailed in the previous steps of this tutorial, you're now ready to try our sample.</span></span>

1. <span data-ttu-id="211b6-202">通过将带有电阻器的 LED 连接到引脚 8 来准备你的 Arduino 开发板。</span><span class="sxs-lookup"><span data-stu-id="211b6-202">Prepare your Arduino board by hooking up an LED with a resistor to pin 8.</span></span>
2. <span data-ttu-id="211b6-203">确保你的 Arduino 仍然上载有 HelloWorld-Speech-Eventing 示例，然后将 Arduinos 插入电源。</span><span class="sxs-lookup"><span data-stu-id="211b6-203">Make sure that your Arduino is still uploaded with the HelloWorld-Speech-Eventing sample, and then plug the Arduino into a power supply.</span></span>
3. <span data-ttu-id="211b6-204">在你以前准备的 Windows Phone 上运行 Windows Virtual Shields for Arduino 应用。</span><span class="sxs-lookup"><span data-stu-id="211b6-204">Run the Windows Virtual Shields for Arduino app on the Windows Phone you prepared previously.</span></span>
4. <span data-ttu-id="211b6-205">如果正确完成所有设置，你的手机应连接到 Arduino 草图并使用音频提示欢迎你。</span><span class="sxs-lookup"><span data-stu-id="211b6-205">If everything has been setup properly, your phone should connect to your Arduino sketch and welcome you with an audio cue.</span></span> <span data-ttu-id="211b6-206">你现在可以通过向 Windows 10 设备说出“打开”或“关闭”来打开和关闭 Arduino 上的 LED！</span><span class="sxs-lookup"><span data-stu-id="211b6-206">You can now say 'on' or 'off' to your Windows 10 device to switch the LED on your Arduino between on and off!</span></span>

### <a name="arduino-wiring-sketch-hello-world-example"></a><span data-ttu-id="211b6-207">Arduino 草图绑定：Hello World 示例</span><span class="sxs-lookup"><span data-stu-id="211b6-207">Arduino Wiring Sketch: Hello World example</span></span>

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


