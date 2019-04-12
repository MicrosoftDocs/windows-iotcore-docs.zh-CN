---
title: Windows 10 IoT 核心版仪表板
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解有关 Windows 10 IoT Core 仪表板的作用以及如何开始。
keywords: windows iot、 windows 10 iot 核心版仪表板、 windows iot 仪表板、 设备
ms.openlocfilehash: d21b67dad15d510564ec7fae28a2431d28faf8be
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510973"
---
# <a name="windows-10-iot-core-dashboard"></a><span data-ttu-id="f7d30-104">Windows 10 IoT 核心版仪表板</span><span class="sxs-lookup"><span data-stu-id="f7d30-104">Windows 10 IoT Core Dashboard</span></span>

<span data-ttu-id="f7d30-105">Windows 10 IoT 核心版仪表板是最佳的方式，若要下载，请设置并连接你的 Windows 10 IoT Core 设备，所有从您的 PC。</span><span class="sxs-lookup"><span data-stu-id="f7d30-105">Windows 10 IoT Core Dashboard is the best way to download, set up and connect your Windows 10 IoT Core devices, all from your PC.</span></span>

<span data-ttu-id="f7d30-106">您可以下载[IoT 核心版仪表板此处](http://go.microsoft.com/fwlink/?LinkID=708576)。</span><span class="sxs-lookup"><span data-stu-id="f7d30-106">You can download the [IoT Core Dashboard here](http://go.microsoft.com/fwlink/?LinkID=708576).</span></span>

> [!NOTE]
> <span data-ttu-id="f7d30-107">如果您正在查找您将获得一个白色的屏幕，下载后打开 IoT 仪表板时，它可能是由于驱动程序问题。</span><span class="sxs-lookup"><span data-stu-id="f7d30-107">If you're finding that you're getting a white screen when opening the IoT Dashboard after downloading, it may due to a driver issue.</span></span> <span data-ttu-id="f7d30-108">若要解决此问题，您将需要下载[zip 格式](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip)Intel 图形驱动程序的手动安装的驱动程序。</span><span class="sxs-lookup"><span data-stu-id="f7d30-108">To overcome this issue, you'll need to download the [zip format](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) of the Intel Graphics Driver and install the driver manually.</span></span> 

## <a name="set-up-a-new-device"></a><span data-ttu-id="f7d30-109">设置新设备</span><span class="sxs-lookup"><span data-stu-id="f7d30-109">Set up a new device</span></span>

> [!NOTE]
> <span data-ttu-id="f7d30-110">不能用于设置 Raspberry Pi 3B + 使用仪表板。</span><span class="sxs-lookup"><span data-stu-id="f7d30-110">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="f7d30-111">如果你有 3B + 设备，则必须使用[3B + 技术预览版](https://www.microsoft.com/en-us/software-download/windowsiot)。</span><span class="sxs-lookup"><span data-stu-id="f7d30-111">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/en-us/software-download/windowsiot).</span></span> <span data-ttu-id="f7d30-112">请查看[已知限制](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting)的 technical preview，以确定这是否适用于你的开发。</span><span class="sxs-lookup"><span data-stu-id="f7d30-112">Please view the [known limitations](https://docs.microsoft.com/en-us/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!NOTE]
> <span data-ttu-id="f7d30-113">目前有一个已知的问题，其中 OS 上的 SD 卡经历分区并提示格式...</span><span class="sxs-lookup"><span data-stu-id="f7d30-113">There is currently a known issue where the OS goes through the partitions on the SD card and prompts a 'Format ..'</span></span> <span data-ttu-id="f7d30-114">特定的数据分区，不包含任何文件系统的消息。</span><span class="sxs-lookup"><span data-stu-id="f7d30-114">message for a specific data partition that does not contain any file system.</span></span> <span data-ttu-id="f7d30-115">请通过按取消，则关闭此提示。</span><span class="sxs-lookup"><span data-stu-id="f7d30-115">Please dismiss this prompt by pressing cancel.</span></span> <span data-ttu-id="f7d30-116">虽然我们在一个解决方案中工作，我们建议，如果单击现在格式，您刷新使用 FFU 映像的 SD 卡再次作为更新过程，并在设备将无法更新的格式操作影响。</span><span class="sxs-lookup"><span data-stu-id="f7d30-116">While we work on a solution, we recommend that if you click on 'Format now,' you reflash the SD card with the FFU image again as the format action impacts the update process and the device will fail to update.</span></span>


<span data-ttu-id="f7d30-117">IoT 仪表板轻松设置新设备。</span><span class="sxs-lookup"><span data-stu-id="f7d30-117">The IoT Dashboard makes it easy to set up a new device.</span></span> <span data-ttu-id="f7d30-118">有关如何入门的详细说明，请参阅[开始](https://docs.microsoft.com/en-us/windows/iot-core/getstarted)页。</span><span class="sxs-lookup"><span data-stu-id="f7d30-118">For detailed instructions on how to get started, see the [Get Started](https://docs.microsoft.com/en-us/windows/iot-core/getstarted) page.</span></span>

![IoT 仪表板安装程序页](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a><span data-ttu-id="f7d30-120">SD 卡</span><span class="sxs-lookup"><span data-stu-id="f7d30-120">SD card</span></span>
<span data-ttu-id="f7d30-121">类型、 品牌和型号的 SD 卡极大地影响性能和 IoT 核心版的质量。</span><span class="sxs-lookup"><span data-stu-id="f7d30-121">The type, make and model of the SD card greatly affects both the performance and the quality of IoT Core.</span></span>
<span data-ttu-id="f7d30-122">慢速卡可能长达五次启动比我们[建议卡](../learn-about-hardware/hardwarecompatlist.md)。</span><span class="sxs-lookup"><span data-stu-id="f7d30-122">A slow card can take up to five times longer to boot than our [recommended cards](../learn-about-hardware/hardwarecompatlist.md).</span></span>
<span data-ttu-id="f7d30-123">也可以不工作的较旧的、 可靠性较低的 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="f7d30-123">An older, less reliable SD card may not even work.</span></span> <span data-ttu-id="f7d30-124">如果继续遇到安装问题，请考虑更换 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="f7d30-124">If you continue to run into problems installing, consider replacing the SD card.</span></span>

### <a name="device-name"></a><span data-ttu-id="f7d30-125">设备名称</span><span class="sxs-lookup"><span data-stu-id="f7d30-125">Device Name</span></span>
<span data-ttu-id="f7d30-126">默认设备名称是 minwinpc。</span><span class="sxs-lookup"><span data-stu-id="f7d30-126">The default device name is minwinpc.</span></span> <span data-ttu-id="f7d30-127">我们建议将其更改为的唯一名称，因为这可更轻松地查找网络上的设备。</span><span class="sxs-lookup"><span data-stu-id="f7d30-127">We recommend changing it to something unique as this makes it easier to find the device on the network.</span></span> <span data-ttu-id="f7d30-128">设备名称可以在最多 15 个字符之间，并可以包含字母、 数字和以下符号: @ # $ %^ &) (。</span><span class="sxs-lookup"><span data-stu-id="f7d30-128">The device name can be at most 15 characters long and can include letters, numbers and the following symbols:  @ # $ % ^ & ' ) ( .</span></span> <span data-ttu-id="f7d30-129">-_ {} ~ 自动重新启动如果设置你的设备时更改 IoT 仪表板中的设备名称，将发生在设备上的第一次当您打开。</span><span class="sxs-lookup"><span data-stu-id="f7d30-129">- _ { } ~ If you change the device name in IoT Dashboard when setting up your device, an automatic reboot will happen the first time when you power on the device.</span></span>

### <a name="password"></a><span data-ttu-id="f7d30-130">密码</span><span class="sxs-lookup"><span data-stu-id="f7d30-130">Password</span></span>
<span data-ttu-id="f7d30-131">密码是必填字段，必须设置。</span><span class="sxs-lookup"><span data-stu-id="f7d30-131">Password is a mandatory field and must be set.</span></span> <span data-ttu-id="f7d30-132">在 IoT 仪表板中设置密码修改它默认情况下是管理员用户的密码"p@ssw0rd"。</span><span class="sxs-lookup"><span data-stu-id="f7d30-132">Setting a password in IoT Dashboard modifies the password for Administrator user which by default is "p@ssw0rd".</span></span>

### <a name="wi-fi-network-connection"></a><span data-ttu-id="f7d30-133">Wi-fi 网络连接</span><span class="sxs-lookup"><span data-stu-id="f7d30-133">Wi-Fi Network connection</span></span>
<span data-ttu-id="f7d30-134">IoT 仪表板显示您的 PC 之前已连接到的所有可用的网络。</span><span class="sxs-lookup"><span data-stu-id="f7d30-134">IoT Dashboard shows all available networks that your PC has previously connected to.</span></span> <span data-ttu-id="f7d30-135">如果您看不到所需的 Wi-fi 网络列表上，确保您的 PC 上连接到它。</span><span class="sxs-lookup"><span data-stu-id="f7d30-135">If you don't see the desired Wi-Fi network on the list, ensure you're connected to it on your PC.</span></span>
<span data-ttu-id="f7d30-136">如果取消选中的框，则必须后闪烁到开发板连接以太网电缆。</span><span class="sxs-lookup"><span data-stu-id="f7d30-136">If you uncheck the box, you must connect an Ethernet cable to your board after flashing.</span></span>

### <a name="first-boot"></a><span data-ttu-id="f7d30-137">首次启动</span><span class="sxs-lookup"><span data-stu-id="f7d30-137">First boot</span></span>
<span data-ttu-id="f7d30-138">在首次启动始终需要比所有后续启动时较长时间。</span><span class="sxs-lookup"><span data-stu-id="f7d30-138">The first boot will always take longer than all subsequent boots.</span></span> <span data-ttu-id="f7d30-139">操作系统将需要一些时间来安装并连接到你的网络。</span><span class="sxs-lookup"><span data-stu-id="f7d30-139">The operating system will take some time to install and connect to your network.</span></span>
<span data-ttu-id="f7d30-140">启动时可能会因极大地 SD 卡上。</span><span class="sxs-lookup"><span data-stu-id="f7d30-140">Boot time can vary greatly based on your SD card.</span></span> <span data-ttu-id="f7d30-141">例如，我们建议的 SD 卡上运行 Raspberry Pi 3 需要首次启动的 3 到 4 分钟。</span><span class="sxs-lookup"><span data-stu-id="f7d30-141">For example, a Raspberry Pi 3 running on our recommended SD card takes 3-4 minutes for first boot.</span></span> <span data-ttu-id="f7d30-142">使用低质量 SD 卡在同一个 pi，我们已了解了启动时间超过 15 分钟。</span><span class="sxs-lookup"><span data-stu-id="f7d30-142">On the same Pi with a poor quality SD card, we have seen boot times longer than 15 minutes.</span></span>

### <a name="connecting-to-the-internet"></a><span data-ttu-id="f7d30-143">连接到 internet</span><span class="sxs-lookup"><span data-stu-id="f7d30-143">Connecting to the internet</span></span>
<span data-ttu-id="f7d30-144">让你连接到 internet 的 IoT Core 设备是必不可少的。</span><span class="sxs-lookup"><span data-stu-id="f7d30-144">Having your IoT Core device connect to the internet is essential.</span></span> <span data-ttu-id="f7d30-145">许多较新板附带内置的 Wi-fi 适配器中。</span><span class="sxs-lookup"><span data-stu-id="f7d30-145">Many of the newer boards come with built in Wi-Fi adapters.</span></span> <span data-ttu-id="f7d30-146">如果你遇到问题，获取连接到网络，请尝试以下解决方法：</span><span class="sxs-lookup"><span data-stu-id="f7d30-146">If you have trouble getting connected to your network, try the following:</span></span>

* <span data-ttu-id="f7d30-147">重启设备</span><span class="sxs-lookup"><span data-stu-id="f7d30-147">Rebooting the device</span></span>
* <span data-ttu-id="f7d30-148">插入以太网电缆</span><span class="sxs-lookup"><span data-stu-id="f7d30-148">Plugging in an Ethernet cable</span></span>
* <span data-ttu-id="f7d30-149">插入到设备的监视器。</span><span class="sxs-lookup"><span data-stu-id="f7d30-149">Plugging in a monitor to the device.</span></span> <span data-ttu-id="f7d30-150">这将显示有关你的设备的诊断信息</span><span class="sxs-lookup"><span data-stu-id="f7d30-150">This will show you diagnostic information about your device</span></span>

> [!NOTE]
> <span data-ttu-id="f7d30-151">连接到 Wi-fi 时，正式的 Raspberry Pi 2 Wi-fi 适配器可以是不稳定。</span><span class="sxs-lookup"><span data-stu-id="f7d30-151">The official Raspberry Pi 2 Wi-Fi adapter can be unstable when connecting to Wi-Fi.</span></span>


## <a name="my-devices"></a><span data-ttu-id="f7d30-152">我的设备</span><span class="sxs-lookup"><span data-stu-id="f7d30-152">My Devices</span></span>
___
<span data-ttu-id="f7d30-153">你的设备连接到 internet 后，IoT 仪表板将自动检测你的设备。</span><span class="sxs-lookup"><span data-stu-id="f7d30-153">After your device is connected to the internet, the IoT Dashboard will automatically detect your device.</span></span>
<span data-ttu-id="f7d30-154">若要查找你的设备，请转到**我的设备**。</span><span class="sxs-lookup"><span data-stu-id="f7d30-154">To find your device, go to **My Devices**.</span></span> <span data-ttu-id="f7d30-155">如果未列出你的设备，请尝试重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="f7d30-155">If your device is not listed, try rebooting the device.</span></span> <span data-ttu-id="f7d30-156">请确保，如果有多个设备在网络上，它们都具有唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="f7d30-156">Make sure that if there are more than one devices on the network, they each have a unique name.</span></span> <span data-ttu-id="f7d30-157">此外，请确保你**windows10iotcoredashboard.exe**允许通过 Windows 防火墙通信通过执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="f7d30-157">Also make sure that your **windows10iotcoredashboard.exe** is allowed to communicate through Windows Firewall by following the steps below:</span></span>

1. <span data-ttu-id="f7d30-158">打开**网络和共享中心**，然后找到您的 PC 所连接到网络 (域/Private/Public) 的类型。</span><span class="sxs-lookup"><span data-stu-id="f7d30-158">Open **Network and Sharing Center** and then find the type of network (Domain/Private/Public) your PC is connected to.</span></span>
2. <span data-ttu-id="f7d30-159">打开**Control Panel**然后单击**系统和安全**。</span><span class="sxs-lookup"><span data-stu-id="f7d30-159">Open **Control Panel** and click **System and Security**.</span></span>
3. <span data-ttu-id="f7d30-160">单击**允许通过 Windows 防火墙的应用程序**下**Windows 防火墙**。</span><span class="sxs-lookup"><span data-stu-id="f7d30-160">Click **Allow an app through Windows Firewall** under **Windows Firewall**.</span></span>
4. <span data-ttu-id="f7d30-161">单击**更改设置**。</span><span class="sxs-lookup"><span data-stu-id="f7d30-161">Click **Change settings**.</span></span>
5. <span data-ttu-id="f7d30-162">查找**windows10iotcoredashboard.exe**中**允许的应用程序和功能**，然后启用相应的网络复选框 （即在步骤 1 中找到的网络类型）。</span><span class="sxs-lookup"><span data-stu-id="f7d30-162">Find **windows10iotcoredashboard.exe** in **Allowed apps and features** and then enable the appropriate network check box (i.e. the network type you found in step 1).</span></span>


### <a name="connect-to-your-device"></a><span data-ttu-id="f7d30-163">连接到设备</span><span class="sxs-lookup"><span data-stu-id="f7d30-163">Connect to your device</span></span>

> [!NOTE]
> <span data-ttu-id="f7d30-164">如果您不能在仪表板中查找你的设备，请尝试键入你的 [IP 地址] 和 [: 8080] 到浏览器以获取 Windows Device Portal，启动并运行。</span><span class="sxs-lookup"><span data-stu-id="f7d30-164">If you are unable to find your device in the dashboard, try typing your [IP Address] and [:8080] into the browser to get Windows Device Portal up and running.</span></span> <span data-ttu-id="f7d30-165">若要获取你的设备以显示在仪表板中，请尝试重新启动你的设备。</span><span class="sxs-lookup"><span data-stu-id="f7d30-165">To get your device to show in the dashboard, try rebooting your device.</span></span>


<span data-ttu-id="f7d30-166">右键单击并选择**在设备门户中打开**。</span><span class="sxs-lookup"><span data-stu-id="f7d30-166">Right click and select **Open in Device Portal**.</span></span> <span data-ttu-id="f7d30-167">这将启动[Windows Device Portal](../manage-your-device/DevicePortal.md)页以及交互并管理你的设备的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="f7d30-167">This will launch the [Windows Device Portal](../manage-your-device/DevicePortal.md) page and is the best way to interact and manage your device.</span></span>

![IoTDashboard 查看设备](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

<span data-ttu-id="f7d30-169">您还可以连接到使用 Windows PowerShell 的设备。</span><span class="sxs-lookup"><span data-stu-id="f7d30-169">You can also connect to the device using Windows PowerShell.</span></span>

## <a name="connect-to-azure"></a><span data-ttu-id="f7d30-170">连接到 Azure</span><span class="sxs-lookup"><span data-stu-id="f7d30-170">Connect to Azure</span></span>
___
<span data-ttu-id="f7d30-171">IoT 面板，您可以使用 Azure IoT 中心的 IoT Core 设备预配。</span><span class="sxs-lookup"><span data-stu-id="f7d30-171">IoT Dashboard lets you provision IoT Core devices with Azure IoT Hub.</span></span> <span data-ttu-id="f7d30-172">你可以阅读更多有关它在此[博客文章](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core)。</span><span class="sxs-lookup"><span data-stu-id="f7d30-172">You can read more about it in this [blog post](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core).</span></span>

[<span data-ttu-id="f7d30-173">了解如何使用 Azure IoT 仪表板</span><span class="sxs-lookup"><span data-stu-id="f7d30-173">Learn how to use the IoT Dashboard with Azure</span></span>](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a><span data-ttu-id="f7d30-174">快速运行的示例</span><span class="sxs-lookup"><span data-stu-id="f7d30-174">Quick Run Samples</span></span>
___

<span data-ttu-id="f7d30-175">快速运行示例并不需要任何代码编译，Visual studio 安装或下载 SDK。</span><span class="sxs-lookup"><span data-stu-id="f7d30-175">Quick run samples do not require any code compilation, Visual studio installation or SDK download.</span></span> <span data-ttu-id="f7d30-176">它们非常适合用于快速签出 IoT 核心版可以执行的操作。</span><span class="sxs-lookup"><span data-stu-id="f7d30-176">They are great for quickly checking out what IoT Core can do.</span></span>

### <a name="network-3d-printer"></a><span data-ttu-id="f7d30-177">网络 3D 打印机</span><span class="sxs-lookup"><span data-stu-id="f7d30-177">Network 3D Printer</span></span>
<span data-ttu-id="f7d30-178">使用网络 3D 打印机示例连接到开发板的 3D 打印机可以使它可检测到通过您的家庭网络。</span><span class="sxs-lookup"><span data-stu-id="f7d30-178">Use the Network 3D Printer sample to connect your 3D Printer to your board can make it discoverable over your home network.</span></span> 

![IoTDashboard 网络 3D 打印机](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a><span data-ttu-id="f7d30-180">Internet 广播</span><span class="sxs-lookup"><span data-stu-id="f7d30-180">Internet radio</span></span>
<span data-ttu-id="f7d30-181">转变为可以控制从任意位置在家中 internet 广播你的 Windows 10 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="f7d30-181">Turn your Windows 10 IoT Core device into an internet radio that can be controlled from anywhere in your home.</span></span>

![IoTDashboard Internet 广播](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a><span data-ttu-id="f7d30-183">IoT 核心版 Blockly</span><span class="sxs-lookup"><span data-stu-id="f7d30-183">IoT Core Blockly</span></span>
<span data-ttu-id="f7d30-184">IoT Core Blockly 示例允许程序 Raspberry Pi2 或 3 和 Raspberry Pi 意义上乘幂号的使用从浏览器的"块"编辑器。</span><span class="sxs-lookup"><span data-stu-id="f7d30-184">IoT Core Blockly sample lets your program a Raspberry Pi2 or 3 and a Raspberry Pi Sense hat using a "block" editor from your browser.</span></span>

![IoTDashboard Blockly](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
