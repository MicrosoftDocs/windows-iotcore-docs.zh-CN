---
title: Windows 10 IoT 核心版仪表板
ms.date: 08/28/2017
ms.topic: article
description: 了解 Windows 10 IoT Core 仪表板的功能以及入门方式。
keywords: windows iot，windows 10 iot 核心仪表板，windows iot 面板，设备
ms.openlocfilehash: 53a8be4e29f93ab3f6d9979e247c598ea5e637c8
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721482"
---
# <a name="windows-10-iot-core-dashboard"></a><span data-ttu-id="b921e-104">Windows 10 IoT 核心版仪表板</span><span class="sxs-lookup"><span data-stu-id="b921e-104">Windows 10 IoT Core Dashboard</span></span>

<span data-ttu-id="b921e-105">Windows 10 IoT 核心仪表板是从 PC 下载、设置和连接 Windows 10 IoT 核心设备的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="b921e-105">Windows 10 IoT Core Dashboard is the best way to download, set up and connect your Windows 10 IoT Core devices, all from your PC.</span></span>

<span data-ttu-id="b921e-106">可在此处下载[IoT 核心仪表板](https://go.microsoft.com/fwlink/?LinkID=708576)。</span><span class="sxs-lookup"><span data-stu-id="b921e-106">You can download the [IoT Core Dashboard here](https://go.microsoft.com/fwlink/?LinkID=708576).</span></span>

> [!NOTE]
> <span data-ttu-id="b921e-107">如果您在下载后打开 IoT 面板时遇到了白屏，则可能是由于驱动程序问题所致。</span><span class="sxs-lookup"><span data-stu-id="b921e-107">If you're finding that you're getting a white screen when opening the IoT Dashboard after downloading, it may be due to a driver issue.</span></span> <span data-ttu-id="b921e-108">若要解决此问题，需要下载 Intel 图形驱动程序的[zip 格式](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip)，并手动安装驱动程序。</span><span class="sxs-lookup"><span data-stu-id="b921e-108">To overcome this issue, you'll need to download the [zip format](https://downloadmirror.intel.com/27894/a08/win64_24.20.100.6229.zip) of the Intel Graphics Driver and install the driver manually.</span></span> 

## <a name="set-up-a-new-device"></a><span data-ttu-id="b921e-109">设置新设备</span><span class="sxs-lookup"><span data-stu-id="b921e-109">Set up a new device</span></span>

> [!NOTE]
> <span data-ttu-id="b921e-110">仪表板不能用来设置 Raspberry Pi 3B+。</span><span class="sxs-lookup"><span data-stu-id="b921e-110">Dashboard cannot be used used to setup the Raspberry Pi 3B+.</span></span> <span data-ttu-id="b921e-111">如果有 3B+ 设备，则必须使用 [3B+ 技术预览版](https://www.microsoft.com/software-download/windowsiot)。</span><span class="sxs-lookup"><span data-stu-id="b921e-111">If you have a 3B+ device, you must use the [3B+ technical preview](https://www.microsoft.com/software-download/windowsiot).</span></span> <span data-ttu-id="b921e-112">请查看技术预览版的[已知限制](https://docs.microsoft.com/windows/iot-core/troubleshooting)，确定它是否适合开发。</span><span class="sxs-lookup"><span data-stu-id="b921e-112">Please view the [known limitations](https://docs.microsoft.com/windows/iot-core/troubleshooting) of the technical preview to determine if this is suitable for your development.</span></span>

> [!NOTE]
> <span data-ttu-id="b921e-113">目前存在一个已知问题，其中，操作系统会经历 SD 卡上的分区，并提示 "Format ..."</span><span class="sxs-lookup"><span data-stu-id="b921e-113">There is currently a known issue where the OS goes through the partitions on the SD card and prompts a 'Format ..'</span></span> <span data-ttu-id="b921e-114">不包含任何文件系统的特定数据分区的消息。</span><span class="sxs-lookup"><span data-stu-id="b921e-114">message for a specific data partition that does not contain any file system.</span></span> <span data-ttu-id="b921e-115">请按 "取消" 以消除此提示。</span><span class="sxs-lookup"><span data-stu-id="b921e-115">Please dismiss this prompt by pressing cancel.</span></span> <span data-ttu-id="b921e-116">当我们处理某个解决方案时，我们建议，如果你单击 "立即格式化"，则会再次使用 FFU 图像刷新 SD 卡，因为 Format 操作会影响更新过程，并且设备将无法更新。</span><span class="sxs-lookup"><span data-stu-id="b921e-116">While we work on a solution, we recommend that if you click on 'Format now,' you reflash the SD card with the FFU image again as the format action impacts the update process and the device will fail to update.</span></span>


<span data-ttu-id="b921e-117">使用 IoT 面板可以轻松地设置新设备。</span><span class="sxs-lookup"><span data-stu-id="b921e-117">The IoT Dashboard makes it easy to set up a new device.</span></span> <span data-ttu-id="b921e-118">有关如何入门的详细说明，请参阅[入门页。](https://docs.microsoft.com/windows/iot-core/getstarted)</span><span class="sxs-lookup"><span data-stu-id="b921e-118">For detailed instructions on how to get started, see the [Get Started](https://docs.microsoft.com/windows/iot-core/getstarted) page.</span></span>

![IoT 面板设置页面](../media/IoTDashboard/IoTDashboard_SetupPage.PNG)

### <a name="sd-card"></a><span data-ttu-id="b921e-120">SD 卡</span><span class="sxs-lookup"><span data-stu-id="b921e-120">SD card</span></span>
<span data-ttu-id="b921e-121">SD 卡的类型、品牌和型号极大地影响 IoT 核心的性能和质量。</span><span class="sxs-lookup"><span data-stu-id="b921e-121">The type, make and model of the SD card greatly affects both the performance and the quality of IoT Core.</span></span>
<span data-ttu-id="b921e-122">比我们[建议的卡](../learn-about-hardware/hardwarecompatlist.md)相比，慢卡的启动时间可能会长达五倍。</span><span class="sxs-lookup"><span data-stu-id="b921e-122">A slow card can take up to five times longer to boot than our [recommended cards](../learn-about-hardware/hardwarecompatlist.md).</span></span>
<span data-ttu-id="b921e-123">旧的、不太可靠的 SD 卡甚至可能不起作用。</span><span class="sxs-lookup"><span data-stu-id="b921e-123">An older, less reliable SD card may not even work.</span></span> <span data-ttu-id="b921e-124">如果继续安装时遇到问题，请考虑更换 SD 卡。</span><span class="sxs-lookup"><span data-stu-id="b921e-124">If you continue to run into problems installing, consider replacing the SD card.</span></span>

### <a name="device-name"></a><span data-ttu-id="b921e-125">设备名称</span><span class="sxs-lookup"><span data-stu-id="b921e-125">Device Name</span></span>
<span data-ttu-id="b921e-126">默认设备名称为 minwinpc。</span><span class="sxs-lookup"><span data-stu-id="b921e-126">The default device name is minwinpc.</span></span> <span data-ttu-id="b921e-127">建议将其更改为唯一的内容，因为这样可以更轻松地在网络上查找设备。</span><span class="sxs-lookup"><span data-stu-id="b921e-127">We recommend changing it to something unique as this makes it easier to find the device on the network.</span></span> <span data-ttu-id="b921e-128">设备名称的长度最长可以为15个字符，可以包含字母、数字和以下符号： @ # $% ^ & '）（。</span><span class="sxs-lookup"><span data-stu-id="b921e-128">The device name can be at most 15 characters long and can include letters, numbers and the following symbols:  @ # $ % ^ & ' ) ( .</span></span> <span data-ttu-id="b921e-129">-_ {} ~ 如果在设置设备时在 IoT 面板中更改设备名，则在第一次打开设备电源时将自动重启。</span><span class="sxs-lookup"><span data-stu-id="b921e-129">- _ { } ~ If you change the device name in IoT Dashboard when setting up your device, an automatic reboot will happen the first time when you power on the device.</span></span>

### <a name="password"></a><span data-ttu-id="b921e-130">密码</span><span class="sxs-lookup"><span data-stu-id="b921e-130">Password</span></span>
<span data-ttu-id="b921e-131">密码是必填字段，必须设置。</span><span class="sxs-lookup"><span data-stu-id="b921e-131">Password is a mandatory field and must be set.</span></span> <span data-ttu-id="b921e-132">在 IoT 面板中设置密码会修改管理员用户的密码，默认情况下为 "p@ssw0rd"。</span><span class="sxs-lookup"><span data-stu-id="b921e-132">Setting a password in IoT Dashboard modifies the password for Administrator user which by default is "p@ssw0rd".</span></span>

### <a name="wi-fi-network-connection"></a><span data-ttu-id="b921e-133">Wi-fi 网络连接</span><span class="sxs-lookup"><span data-stu-id="b921e-133">Wi-Fi Network connection</span></span>
<span data-ttu-id="b921e-134">IoT 面板显示你的电脑以前连接到的所有可用网络。</span><span class="sxs-lookup"><span data-stu-id="b921e-134">IoT Dashboard shows all available networks that your PC has previously connected to.</span></span> <span data-ttu-id="b921e-135">如果在列表中看不到所需的 Wi-fi 网络，请确保你已在电脑上连接到该网络。</span><span class="sxs-lookup"><span data-stu-id="b921e-135">If you don't see the desired Wi-Fi network on the list, ensure you're connected to it on your PC.</span></span>
<span data-ttu-id="b921e-136">如果取消选中此框，则必须在闪烁后将以太网电缆连接到您的面板。</span><span class="sxs-lookup"><span data-stu-id="b921e-136">If you uncheck the box, you must connect an Ethernet cable to your board after flashing.</span></span>

### <a name="first-boot"></a><span data-ttu-id="b921e-137">首次启动</span><span class="sxs-lookup"><span data-stu-id="b921e-137">First boot</span></span>
<span data-ttu-id="b921e-138">首次启动的时间将始终比所有后续启动的时间要长。</span><span class="sxs-lookup"><span data-stu-id="b921e-138">The first boot will always take longer than all subsequent boots.</span></span> <span data-ttu-id="b921e-139">操作系统将需要一段时间来安装和连接到你的网络。</span><span class="sxs-lookup"><span data-stu-id="b921e-139">The operating system will take some time to install and connect to your network.</span></span>
<span data-ttu-id="b921e-140">根据 SD 卡的不同，启动时间可能会很大。</span><span class="sxs-lookup"><span data-stu-id="b921e-140">Boot time can vary greatly based on your SD card.</span></span> <span data-ttu-id="b921e-141">例如，在我们建议的 SD 卡上运行的 Raspberry Pi 3 在第一次启动时会花费3-4 分钟。</span><span class="sxs-lookup"><span data-stu-id="b921e-141">For example, a Raspberry Pi 3 running on our recommended SD card takes 3-4 minutes for first boot.</span></span> <span data-ttu-id="b921e-142">对于质量较差的 SD 卡，同一 Pi 上的启动时间超过15分钟。</span><span class="sxs-lookup"><span data-stu-id="b921e-142">On the same Pi with a poor quality SD card, we have seen boot times longer than 15 minutes.</span></span>

### <a name="connecting-to-the-internet"></a><span data-ttu-id="b921e-143">连接到 internet</span><span class="sxs-lookup"><span data-stu-id="b921e-143">Connecting to the internet</span></span>
<span data-ttu-id="b921e-144">将 IoT Core 设备连接到 internet 非常重要。</span><span class="sxs-lookup"><span data-stu-id="b921e-144">Having your IoT Core device connect to the internet is essential.</span></span> <span data-ttu-id="b921e-145">许多较新的板随附内置 Wi-fi 适配器。</span><span class="sxs-lookup"><span data-stu-id="b921e-145">Many of the newer boards come with built in Wi-Fi adapters.</span></span> <span data-ttu-id="b921e-146">如果在连接到网络时遇到问题，请尝试以下操作：</span><span class="sxs-lookup"><span data-stu-id="b921e-146">If you have trouble getting connected to your network, try the following:</span></span>

* <span data-ttu-id="b921e-147">正在重启设备</span><span class="sxs-lookup"><span data-stu-id="b921e-147">Rebooting the device</span></span>
* <span data-ttu-id="b921e-148">插入以太网电缆</span><span class="sxs-lookup"><span data-stu-id="b921e-148">Plugging in an Ethernet cable</span></span>
* <span data-ttu-id="b921e-149">将监视器插入设备。</span><span class="sxs-lookup"><span data-stu-id="b921e-149">Plugging in a monitor to the device.</span></span> <span data-ttu-id="b921e-150">这会显示有关设备的诊断信息</span><span class="sxs-lookup"><span data-stu-id="b921e-150">This will show you diagnostic information about your device</span></span>

> [!NOTE]
> <span data-ttu-id="b921e-151">在连接到 Wi-fi 时，官方 Raspberry Pi 2 Wi-fi 适配器可能不稳定。</span><span class="sxs-lookup"><span data-stu-id="b921e-151">The official Raspberry Pi 2 Wi-Fi adapter can be unstable when connecting to Wi-Fi.</span></span>


## <a name="my-devices"></a><span data-ttu-id="b921e-152">我的设备</span><span class="sxs-lookup"><span data-stu-id="b921e-152">My Devices</span></span>
___
<span data-ttu-id="b921e-153">将设备连接到 internet 后，IoT 面板会自动检测你的设备。</span><span class="sxs-lookup"><span data-stu-id="b921e-153">After your device is connected to the internet, the IoT Dashboard will automatically detect your device.</span></span>
<span data-ttu-id="b921e-154">若要查找你的设备，请参阅 **"我的设备**"。</span><span class="sxs-lookup"><span data-stu-id="b921e-154">To find your device, go to **My Devices**.</span></span> <span data-ttu-id="b921e-155">如果未列出你的设备，请尝试重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="b921e-155">If your device is not listed, try rebooting the device.</span></span> <span data-ttu-id="b921e-156">请确保网络上有多个设备，每个设备都具有唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="b921e-156">Make sure that if there are more than one devices on the network, they each have a unique name.</span></span> <span data-ttu-id="b921e-157">此外，请确保你的**windows10iotcoredashboard**可以通过执行以下步骤，通过 Windows 防火墙进行通信：</span><span class="sxs-lookup"><span data-stu-id="b921e-157">Also make sure that your **windows10iotcoredashboard.exe** is allowed to communicate through Windows Firewall by following the steps below:</span></span>

1. <span data-ttu-id="b921e-158">打开 "**网络和共享中心**"，然后找到您的 PC 连接到的网络类型（域/专用/公共）。</span><span class="sxs-lookup"><span data-stu-id="b921e-158">Open **Network and Sharing Center** and then find the type of network (Domain/Private/Public) your PC is connected to.</span></span>
2. <span data-ttu-id="b921e-159">打开 **"控制面板"** ，然后单击 "**系统和安全**"。</span><span class="sxs-lookup"><span data-stu-id="b921e-159">Open **Control Panel** and click **System and Security**.</span></span>
3. <span data-ttu-id="b921e-160">在**Windows 防火墙**下，单击 "**允许应用通过 windows 防火墙**"。</span><span class="sxs-lookup"><span data-stu-id="b921e-160">Click **Allow an app through Windows Firewall** under **Windows Firewall**.</span></span>
4. <span data-ttu-id="b921e-161">单击“更改设置”。</span><span class="sxs-lookup"><span data-stu-id="b921e-161">Click **Change settings**.</span></span>
5. <span data-ttu-id="b921e-162">在 "**允许的应用和功能**" 中找到**windows10iotcoredashboard** ，然后启用适当的网络复选框（即在步骤1中找到的网络类型）。</span><span class="sxs-lookup"><span data-stu-id="b921e-162">Find **windows10iotcoredashboard.exe** in **Allowed apps and features** and then enable the appropriate network check box (i.e. the network type you found in step 1).</span></span>


### <a name="connect-to-your-device"></a><span data-ttu-id="b921e-163">连接到设备</span><span class="sxs-lookup"><span data-stu-id="b921e-163">Connect to your device</span></span>

> [!NOTE]
> <span data-ttu-id="b921e-164">如果在仪表板中找不到你的设备，请尝试在浏览器中键入 [IP 地址] 和 [： 8080] 以启动并运行 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="b921e-164">If you are unable to find your device in the dashboard, try typing your [IP Address] and [:8080] into the browser to get Windows Device Portal up and running.</span></span> <span data-ttu-id="b921e-165">若要使设备在仪表板中显示，请尝试重新启动设备。</span><span class="sxs-lookup"><span data-stu-id="b921e-165">To get your device to show in the dashboard, try rebooting your device.</span></span>


<span data-ttu-id="b921e-166">右键单击并选择 **"在设备门户中打开"** 。</span><span class="sxs-lookup"><span data-stu-id="b921e-166">Right click and select **Open in Device Portal**.</span></span> <span data-ttu-id="b921e-167">这将启动[Windows 设备门户](../manage-your-device/DevicePortal.md)页面，并且是交互和管理设备的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="b921e-167">This will launch the [Windows Device Portal](../manage-your-device/DevicePortal.md) page and is the best way to interact and manage your device.</span></span>

![IoTDashboard 视图设备](../media/IoTDashboard/IoTDashboard_RightClickMenu.PNG)

<span data-ttu-id="b921e-169">你还可以使用 Windows PowerShell 连接到设备。</span><span class="sxs-lookup"><span data-stu-id="b921e-169">You can also connect to the device using Windows PowerShell.</span></span>

## <a name="connect-to-azure"></a><span data-ttu-id="b921e-170">连接到 Azure</span><span class="sxs-lookup"><span data-stu-id="b921e-170">Connect to Azure</span></span>
___
<span data-ttu-id="b921e-171">IoT 面板允许通过 Azure IoT 中心设置 IoT 核心设备。</span><span class="sxs-lookup"><span data-stu-id="b921e-171">IoT Dashboard lets you provision IoT Core devices with Azure IoT Hub.</span></span> <span data-ttu-id="b921e-172">可在此[博客文章](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core)中阅读更多相关信息。</span><span class="sxs-lookup"><span data-stu-id="b921e-172">You can read more about it in this [blog post](https://blogs.windows.com/buildingapps/2016/07/20/building-secure-apps-for-windows-iot-core).</span></span>

[<span data-ttu-id="b921e-173">了解如何在 Azure 中使用 IoT 面板</span><span class="sxs-lookup"><span data-stu-id="b921e-173">Learn how to use the IoT Dashboard with Azure</span></span>](https://docs.microsoft.com/windows/iot-core/connect-to-cloud/connectdevicetocloud)

## <a name="quick-run-samples"></a><span data-ttu-id="b921e-174">快速运行示例</span><span class="sxs-lookup"><span data-stu-id="b921e-174">Quick Run Samples</span></span>
___

<span data-ttu-id="b921e-175">"快速运行" 示例不需要任何代码编译、Visual studio 安装或 SDK 下载。</span><span class="sxs-lookup"><span data-stu-id="b921e-175">Quick run samples do not require any code compilation, Visual studio installation or SDK download.</span></span> <span data-ttu-id="b921e-176">它们非常适用于快速查看 IoT 核心可以执行的操作。</span><span class="sxs-lookup"><span data-stu-id="b921e-176">They are great for quickly checking out what IoT Core can do.</span></span>

### <a name="network-3d-printer"></a><span data-ttu-id="b921e-177">网络3D 打印机</span><span class="sxs-lookup"><span data-stu-id="b921e-177">Network 3D Printer</span></span>
<span data-ttu-id="b921e-178">使用 "网络3D 打印机" 示例将3D 打印机连接到你的板，使其可通过家庭网络发现。</span><span class="sxs-lookup"><span data-stu-id="b921e-178">Use the Network 3D Printer sample to connect your 3D Printer to your board can make it discoverable over your home network.</span></span> 

![IoTDashboard 网络3D 打印机](../media/IoTDashboard/IoTDashboard_3DPrinter.PNG)

### <a name="internet-radio"></a><span data-ttu-id="b921e-180">Internet 广播</span><span class="sxs-lookup"><span data-stu-id="b921e-180">Internet radio</span></span>
<span data-ttu-id="b921e-181">将 Windows 10 IoT Core 设备转换为可从家里任意位置控制的 internet 收音机。</span><span class="sxs-lookup"><span data-stu-id="b921e-181">Turn your Windows 10 IoT Core device into an internet radio that can be controlled from anywhere in your home.</span></span>

![IoTDashboard Internet 收音机](../media/IoTDashboard/IoTDashboard_InternetRadio.PNG)

### <a name="iot-core-blockly"></a><span data-ttu-id="b921e-183">IoT 核心 Blockly</span><span class="sxs-lookup"><span data-stu-id="b921e-183">IoT Core Blockly</span></span>
<span data-ttu-id="b921e-184">IoT Core Blockly 示例可让你的程序 Raspberry Pi2 或3，并使用你的浏览器中的 "阻止" 编辑器。</span><span class="sxs-lookup"><span data-stu-id="b921e-184">IoT Core Blockly sample lets your program a Raspberry Pi2 or 3 and a Raspberry Pi Sense hat using a "block" editor from your browser.</span></span>

![IoTDashboard Blockly](../media/IoTDashboard/IoTDashboard_Blockly.PNG)
