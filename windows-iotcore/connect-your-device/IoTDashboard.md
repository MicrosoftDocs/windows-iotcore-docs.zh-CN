---
title: Windows 10 IoT 核心版仪表板
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解Windows 10 IoT 核心版仪表板功能以及如何开始。
keywords: windows iot， windows 10 iot 核心仪表板， windows iot 仪表板， 设备
ms.openlocfilehash: 2060acaff423e2da6df23596829ae1cce1d1979d
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230024"
---
# <a name="windows-10-iot-core-dashboard"></a><span data-ttu-id="ee954-104">Windows 10 IoT 核心版仪表板</span><span class="sxs-lookup"><span data-stu-id="ee954-104">Windows 10 IoT Core Dashboard</span></span>

<span data-ttu-id="ee954-105">Windows 10 IoT 核心版仪表板是从电脑下载、设置Windows 10 IoT 核心版连接设备的最佳方法。</span><span class="sxs-lookup"><span data-stu-id="ee954-105">Windows 10 IoT Core Dashboard is the best way to download, set up and connect your Windows 10 IoT Core devices, all from your PC.</span></span>

<span data-ttu-id="ee954-106">可以在此处下载 [IoT 核心仪表板](https://go.microsoft.com/fwlink/?LinkID=708576)。</span><span class="sxs-lookup"><span data-stu-id="ee954-106">You can download the [IoT Core Dashboard here](https://go.microsoft.com/fwlink/?LinkID=708576).</span></span>

> [!NOTE]
> <span data-ttu-id="ee954-107">如果发现在下载后打开IoT 仪表板屏幕时出现白色屏幕，原因可能是驱动程序问题。</span><span class="sxs-lookup"><span data-stu-id="ee954-107">If you're finding that you're getting a white screen when opening the IoT Dashboard after downloading, it may be due to a driver issue.</span></span> <span data-ttu-id="ee954-108">若要解决此问题，需要下载 Intel 图形驱动程序的 [zip](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) 格式并手动安装驱动程序。</span><span class="sxs-lookup"><span data-stu-id="ee954-108">To overcome this issue, you'll need to download the [zip format](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) of the Intel Graphics Driver and install the driver manually.</span></span> 

## <a name="set-up-a-new-device"></a><span data-ttu-id="ee954-109">设置新设备</span><span class="sxs-lookup"><span data-stu-id="ee954-109">Set up a new device</span></span>

> [!NOTE]
> <span data-ttu-id="ee954-110">仪表板不能用来设置 Raspberry Pi 3B+。</span><span class="sxs-lookup"><span data-stu-id="ee954-110">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="ee954-111">如果有 3B+ 设备，则必须使用 [3B+ 技术预览版](https://www.microsoft.com/software-download/windowsiot)。</span><span class="sxs-lookup"><span data-stu-id="ee954-111">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/software-download/windowsiot).</span></span> <span data-ttu-id="ee954-112">请查看技术预览版的[已知限制](https://docs.microsoft.com/windows/iot-core/troubleshooting)，确定它是否适合开发。</span><span class="sxs-lookup"><span data-stu-id="ee954-112">Please view the [known limitations](https://docs.microsoft.com/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!NOTE]
> <span data-ttu-id="ee954-113">当前存在一个已知问题：OS 通过 SD 卡上的分区，并提示"格式"。"</span><span class="sxs-lookup"><span data-stu-id="ee954-113">There is currently a known issue where the OS goes through the partitions on the SD card and prompts a 'Format ..'</span></span> <span data-ttu-id="ee954-114">不包含任何文件系统的特定数据分区的消息。</span><span class="sxs-lookup"><span data-stu-id="ee954-114">message for a specific data partition that does not contain any file system.</span></span> <span data-ttu-id="ee954-115">请按"取消"关闭此提示。</span><span class="sxs-lookup"><span data-stu-id="ee954-115">Please dismiss this prompt by pressing cancel.</span></span> <span data-ttu-id="ee954-116">在开发解决方案时，建议单击"立即格式化"，再次将 SD 卡与 FFU 映像一起切换，因为格式操作会影响更新过程，并且设备将无法更新。</span><span class="sxs-lookup"><span data-stu-id="ee954-116">While we work on a solution, we recommend that if you click on 'Format now,' you reflash the SD card with the FFU image again as the format action impacts the update process and the device will fail to update.</span></span>


<span data-ttu-id="ee954-117">使用IoT 仪表板可以轻松设置新设备。</span><span class="sxs-lookup"><span data-stu-id="ee954-117">The IoT Dashboard makes it easy to set up a new device.</span></span> <span data-ttu-id="ee954-118">有关如何入门的详细说明，请参阅[入门页。](https://docs.microsoft.com/windows/iot-core/getstarted)</span><span class="sxs-lookup"><span data-stu-id="ee954-118">For detailed instructions on how to get started, see the [Get Started](https://docs.microsoft.com/windows/iot-core/getstarted) page.</span></span>

![IoT 仪表板设置"页](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a><span data-ttu-id="ee954-120">SD 卡</span><span class="sxs-lookup"><span data-stu-id="ee954-120">SD card</span></span>
<span data-ttu-id="ee954-121">SD 卡的类型、型号和型号极大地影响了 IoT 核心的性能和质量。</span><span class="sxs-lookup"><span data-stu-id="ee954-121">The type, make, and model of the SD card greatly affects both the performance and the quality of IoT Core.</span></span>
<span data-ttu-id="ee954-122">慢速卡的启动时间可能长于建议卡 的 5 [倍](../learn-about-hardware/hardwarecompatlist.md)。</span><span class="sxs-lookup"><span data-stu-id="ee954-122">A slow card can take up to five times longer to boot than our [recommended cards](../learn-about-hardware/hardwarecompatlist.md).</span></span>
<span data-ttu-id="ee954-123">较旧、不太可靠的 SD 卡甚至可能不起作用。</span><span class="sxs-lookup"><span data-stu-id="ee954-123">An older, less reliable SD card may not even work.</span></span> <span data-ttu-id="ee954-124">如果安装时仍遇到问题，请考虑更换 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="ee954-124">If you continue to run into problems installing, consider replacing the SD card.</span></span>

### <a name="device-name"></a><span data-ttu-id="ee954-125">设备名称</span><span class="sxs-lookup"><span data-stu-id="ee954-125">Device Name</span></span>
<span data-ttu-id="ee954-126">默认设备名称为 minwinpc。</span><span class="sxs-lookup"><span data-stu-id="ee954-126">The default device name is minwinpc.</span></span> <span data-ttu-id="ee954-127">建议将设备更改为唯一内容，这样可更轻松地在网络中查找设备。</span><span class="sxs-lookup"><span data-stu-id="ee954-127">We recommend changing it to something unique as this makes it easier to find the device on the network.</span></span> <span data-ttu-id="ee954-128">设备名称最多 15 个字符，可以包含字母、数字和以下符号：@ # $ % ^ & ' )  ( 。</span><span class="sxs-lookup"><span data-stu-id="ee954-128">The device name can be at most 15 characters long and can include letters, numbers, and the following symbols:  @ # $ % ^ & ' ) ( .</span></span> <span data-ttu-id="ee954-129">- _ { } ~ 如果在设置设备IoT 仪表板更改设备名称，则首次打开设备时将发生自动重启。</span><span class="sxs-lookup"><span data-stu-id="ee954-129">- _ { } ~ If you change the device name in IoT Dashboard when setting up your device, an automatic reboot will happen the first time when you power on the device.</span></span>

### <a name="password"></a><span data-ttu-id="ee954-130">密码</span><span class="sxs-lookup"><span data-stu-id="ee954-130">Password</span></span>
<span data-ttu-id="ee954-131">密码是必填字段，必须设置。</span><span class="sxs-lookup"><span data-stu-id="ee954-131">Password is a mandatory field and must be set.</span></span> <span data-ttu-id="ee954-132">在 IoT 仪表板中设置密码会修改管理员用户的密码，默认为 p@ssw0rd ""。</span><span class="sxs-lookup"><span data-stu-id="ee954-132">Setting a password in IoT Dashboard modifies the password for Administrator user, which by default is "p@ssw0rd".</span></span>

### <a name="wi-fi-network-connection"></a><span data-ttu-id="ee954-133">Wi-Fi网络连接</span><span class="sxs-lookup"><span data-stu-id="ee954-133">Wi-Fi Network connection</span></span>
<span data-ttu-id="ee954-134">IoT 仪表板显示电脑以前连接到的所有可用网络。</span><span class="sxs-lookup"><span data-stu-id="ee954-134">IoT Dashboard shows all available networks that your PC has previously connected to.</span></span> <span data-ttu-id="ee954-135">如果在列表中看不到所需的Wi-Fi网络，请确保已连接到电脑上的虚拟网络。</span><span class="sxs-lookup"><span data-stu-id="ee954-135">If you don't see the desired Wi-Fi network on the list, ensure you're connected to it on your PC.</span></span>
<span data-ttu-id="ee954-136">如果取消选中该框，则必须在闪烁后将以太网电缆连接到板。</span><span class="sxs-lookup"><span data-stu-id="ee954-136">If you uncheck the box, you must connect an Ethernet cable to your board after flashing.</span></span>

### <a name="first-boot"></a><span data-ttu-id="ee954-137">首次启动</span><span class="sxs-lookup"><span data-stu-id="ee954-137">First boot</span></span>
<span data-ttu-id="ee954-138">首次启动始终比所有后续启动时间长。</span><span class="sxs-lookup"><span data-stu-id="ee954-138">The first boot will always take longer than all subsequent boots.</span></span> <span data-ttu-id="ee954-139">操作系统需要一些时间来安装和连接到网络。</span><span class="sxs-lookup"><span data-stu-id="ee954-139">The operating system will take some time to install and connect to your network.</span></span>
<span data-ttu-id="ee954-140">启动时间可能会因 SD 卡而异。</span><span class="sxs-lookup"><span data-stu-id="ee954-140">Boot time can vary greatly based on your SD card.</span></span> <span data-ttu-id="ee954-141">例如，在建议 SD 卡上运行的 Raspberry Pi 3 首次启动需要 3-4 分钟。</span><span class="sxs-lookup"><span data-stu-id="ee954-141">For example, a Raspberry Pi 3 running on our recommended SD card takes 3-4 minutes for first boot.</span></span> <span data-ttu-id="ee954-142">在质量不佳的 SD 卡的同一 Pi 上，我们发现启动时间超过 15 分钟。</span><span class="sxs-lookup"><span data-stu-id="ee954-142">On the same Pi with a poor quality SD card, we have seen boot times longer than 15 minutes.</span></span>

### <a name="connecting-to-the-internet"></a><span data-ttu-id="ee954-143">连接到 Internet</span><span class="sxs-lookup"><span data-stu-id="ee954-143">Connecting to the internet</span></span>
<span data-ttu-id="ee954-144">让 IoT Core 设备连接到 Internet 至关重要。</span><span class="sxs-lookup"><span data-stu-id="ee954-144">Having your IoT Core device connect to the internet is essential.</span></span> <span data-ttu-id="ee954-145">许多较新的板都内置有Wi-Fi适配器。</span><span class="sxs-lookup"><span data-stu-id="ee954-145">Many of the newer boards come with built-in Wi-Fi adapters.</span></span> <span data-ttu-id="ee954-146">如果在连接到网络时遇到问题，请尝试以下操作：</span><span class="sxs-lookup"><span data-stu-id="ee954-146">If you have trouble getting connected to your network, try the following:</span></span>

* <span data-ttu-id="ee954-147">重新启动设备</span><span class="sxs-lookup"><span data-stu-id="ee954-147">Rebooting the device</span></span>
* <span data-ttu-id="ee954-148">插入以太网电缆</span><span class="sxs-lookup"><span data-stu-id="ee954-148">Plugging in an Ethernet cable</span></span>
* <span data-ttu-id="ee954-149">将监视器插入设备。</span><span class="sxs-lookup"><span data-stu-id="ee954-149">Plugging in a monitor to the device.</span></span> <span data-ttu-id="ee954-150">这会显示有关设备的诊断信息</span><span class="sxs-lookup"><span data-stu-id="ee954-150">This will show you diagnostic information about your device</span></span>

> [!NOTE]
> <span data-ttu-id="ee954-151">连接到 Wi-Fi 时，Wi-Fi Raspberry Pi 2 适配器可能不稳定。</span><span class="sxs-lookup"><span data-stu-id="ee954-151">The official Raspberry Pi 2 Wi-Fi adapter can be unstable when connecting to Wi-Fi.</span></span>


## <a name="my-devices"></a><span data-ttu-id="ee954-152">我的设备</span><span class="sxs-lookup"><span data-stu-id="ee954-152">My Devices</span></span>
___
<span data-ttu-id="ee954-153">设备连接到 Internet 后，IoT 仪表板会自动检测设备。</span><span class="sxs-lookup"><span data-stu-id="ee954-153">After your device is connected to the internet, the IoT Dashboard will automatically detect your device.</span></span>
<span data-ttu-id="ee954-154">若要查找设备，请转到"**我的设备"。**</span><span class="sxs-lookup"><span data-stu-id="ee954-154">To find your device, go to **My Devices**.</span></span> <span data-ttu-id="ee954-155">如果未列出设备，请尝试重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="ee954-155">If your device is not listed, try rebooting the device.</span></span> <span data-ttu-id="ee954-156">确保如果网络上存在多个设备，则每个设备都有唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="ee954-156">Make sure that if there are more than one device on the network, they each have a unique name.</span></span> <span data-ttu-id="ee954-157">此外，**请windows10iotcoredashboard.exe以下步骤**，确保允许Windows防火墙进行通信：</span><span class="sxs-lookup"><span data-stu-id="ee954-157">Also make sure that your **windows10iotcoredashboard.exe** is allowed to communicate through Windows Firewall by following the steps below:</span></span>

1. <span data-ttu-id="ee954-158">打开 **网络和共享中心，** 然后找到电脑 (域/专用/公共) 网络类型。</span><span class="sxs-lookup"><span data-stu-id="ee954-158">Open **Network and Sharing Center** and then find the type of network (Domain/Private/Public) your PC is connected to.</span></span>
2. <span data-ttu-id="ee954-159">打开 **控制面板，** 然后单击"**系统和安全"。**</span><span class="sxs-lookup"><span data-stu-id="ee954-159">Open **Control Panel** and click **System and Security**.</span></span>
3. <span data-ttu-id="ee954-160">在 **"防火墙"下，Windows应用\*\*\*\*Windows防火墙"**。</span><span class="sxs-lookup"><span data-stu-id="ee954-160">Click **Allow an app through Windows Firewall** under **Windows Firewall**.</span></span>
4. <span data-ttu-id="ee954-161">单击“更改设置”  。</span><span class="sxs-lookup"><span data-stu-id="ee954-161">Click **Change settings**.</span></span>
5. <span data-ttu-id="ee954-162">在 **windows10iotcoredashboard.exe"\*\*\*\*应用** 和功能"中查找"网络"，然后启用相应的网络 (例如，在步骤 1 中的网络) 。</span><span class="sxs-lookup"><span data-stu-id="ee954-162">Find **windows10iotcoredashboard.exe** in **Allowed apps and features** and then enable the appropriate network check box (i.e. the network type you found in step 1).</span></span>


### <a name="connect-to-your-device"></a><span data-ttu-id="ee954-163">连接到设备</span><span class="sxs-lookup"><span data-stu-id="ee954-163">Connect to your device</span></span>

> [!NOTE]
> <span data-ttu-id="ee954-164">如果无法在仪表板中查找设备，请尝试在浏览器中键入 [IP 地址] 和 [：8080] ，Windows 设备门户并运行。</span><span class="sxs-lookup"><span data-stu-id="ee954-164">If you are unable to find your device in the dashboard, try typing your [IP Address] and [:8080] into the browser to get Windows Device Portal up and running.</span></span> <span data-ttu-id="ee954-165">若要使设备显示在仪表板中，请尝试重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="ee954-165">To get your device to show in the dashboard, try rebooting your device.</span></span>


<span data-ttu-id="ee954-166">右键单击并选择"在 **中打开设备门户"。**</span><span class="sxs-lookup"><span data-stu-id="ee954-166">Right-click and select **Open in Device Portal**.</span></span> <span data-ttu-id="ee954-167">这会[启动Windows 设备门户页面](../manage-your-device/DevicePortal.md)，是交互和管理设备的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="ee954-167">This will launch the [Windows Device Portal](../manage-your-device/DevicePortal.md) page and is the best way to interact and manage your device.</span></span>

![IoTDashboard 视图设备](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

<span data-ttu-id="ee954-169">也可使用 Windows PowerShell 连接到设备。</span><span class="sxs-lookup"><span data-stu-id="ee954-169">You can also connect to the device using Windows PowerShell.</span></span>

## <a name="connect-to-azure"></a><span data-ttu-id="ee954-170">连接到 Azure</span><span class="sxs-lookup"><span data-stu-id="ee954-170">Connect to Azure</span></span>
___
<span data-ttu-id="ee954-171">IoT 仪表板使用中心预配 IoT 核心Azure IoT设备。</span><span class="sxs-lookup"><span data-stu-id="ee954-171">IoT Dashboard lets you provision IoT Core devices with Azure IoT Hub.</span></span> <span data-ttu-id="ee954-172">可在此博客文章 中阅读[有关它的内容。](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core)</span><span class="sxs-lookup"><span data-stu-id="ee954-172">You can read more about it in this [blog post](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core).</span></span>

[<span data-ttu-id="ee954-173">了解如何在 Azure IoT 仪表板应用</span><span class="sxs-lookup"><span data-stu-id="ee954-173">Learn how to use the IoT Dashboard with Azure</span></span>](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a><span data-ttu-id="ee954-174">快速运行示例</span><span class="sxs-lookup"><span data-stu-id="ee954-174">Quick Run Samples</span></span>
___

<span data-ttu-id="ee954-175">快速运行示例不需要任何代码编译、Visual Studio 安装或 SDK 下载。</span><span class="sxs-lookup"><span data-stu-id="ee954-175">Quick run samples do not require any code compilation, Visual studio installation, or SDK download.</span></span> <span data-ttu-id="ee954-176">它们非常适用于快速查看 IoT Core 可以执行哪些工作。</span><span class="sxs-lookup"><span data-stu-id="ee954-176">They are great for quickly checking out what IoT Core can do.</span></span>

### <a name="network-3d-printer"></a><span data-ttu-id="ee954-177">网络 3D 打印机</span><span class="sxs-lookup"><span data-stu-id="ee954-177">Network 3D Printer</span></span>
<span data-ttu-id="ee954-178">使用网络 3D 打印机示例将 3D 打印机连接到板，可以使它可以通过家庭网络进行发现。</span><span class="sxs-lookup"><span data-stu-id="ee954-178">Use the Network 3D Printer sample to connect your 3D Printer to your board can make it discoverable over your home network.</span></span> 

![IoTDashboard 网络 3D 打印机](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a><span data-ttu-id="ee954-180">Internet 无线电</span><span class="sxs-lookup"><span data-stu-id="ee954-180">Internet radio</span></span>
<span data-ttu-id="ee954-181">将Windows 10 IoT 核心版设备转换为可以从家庭任意位置控制的 Internet 无线电。</span><span class="sxs-lookup"><span data-stu-id="ee954-181">Turn your Windows 10 IoT Core device into an internet radio that can be controlled from anywhere in your home.</span></span>

![IoTDashboard Internet 无线电](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a><span data-ttu-id="ee954-183">IoT 核心块</span><span class="sxs-lookup"><span data-stu-id="ee954-183">IoT Core Blockly</span></span>
<span data-ttu-id="ee954-184">IoT 核心块示例允许使用浏览器中的"块"编辑器对 Raspberry Pi2 或 3 和 Raspberry Pi Sense Hat 进行编程。</span><span class="sxs-lookup"><span data-stu-id="ee954-184">IoT Core Blockly sample lets your program a Raspberry Pi2 or 3 and a Raspberry Pi Sense hat using a "block" editor from your browser.</span></span>

![IoTDashboard Blockly](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
