---
title: 驱动程序部署
author: parameshbabu
ms.author: pabab
ms.date: 08/22/2017
ms.topic: article
description: 了解如何生成和部署使用 Visual Studio 的驱动程序。
keywords: windows 10 IoT Core，驱动程序部署
ms.openlocfilehash: aad50718ea44c46d676509fe2c5b408d471afc19
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510981"
---
# <a name="driver-deployment"></a><span data-ttu-id="e551f-104">驱动程序部署</span><span class="sxs-lookup"><span data-stu-id="e551f-104">Driver deployment</span></span>

<span data-ttu-id="e551f-105">部署使用 Visual Studio 的 Windows 10 IoT Core 上的驱动程序。</span><span class="sxs-lookup"><span data-stu-id="e551f-105">Deploy a driver on Windows 10 IoT Core with Visual Studio.</span></span> 

<span data-ttu-id="e551f-106">配置你的 Visual Studio 驱动程序项目，以便可以编译和部署驱动程序开发阶段的特定平台的驱动程序。</span><span class="sxs-lookup"><span data-stu-id="e551f-106">Configure your Visual Studio driver project so that you can compile and deploy a driver for a specific platform during driver development phase.</span></span> 

<span data-ttu-id="e551f-107">对于此练习中可以使用[gpiokmdfdemo 示例驱动程序](https://github.com/ms-iot/samples/tree/develop/DriverSamples)。</span><span class="sxs-lookup"><span data-stu-id="e551f-107">For this exercise you can use the [gpiokmdfdemo sample driver](https://github.com/ms-iot/samples/tree/develop/DriverSamples).</span></span>

<span data-ttu-id="e551f-108">如果您希望向映像添加驱动程序，请访问中的说明我们[IoT 制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image)。</span><span class="sxs-lookup"><span data-stu-id="e551f-108">If you're looking to add a driver to an image, please visit the instructions in our [IoT Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image).</span></span>

## <a name="step-1--setup"></a><span data-ttu-id="e551f-109">步骤 1:安装</span><span class="sxs-lookup"><span data-stu-id="e551f-109">Step 1 : Setup</span></span> 
___

### <a name="on-the-device"></a><span data-ttu-id="e551f-110">在设备上</span><span class="sxs-lookup"><span data-stu-id="e551f-110">On the device</span></span>

* <span data-ttu-id="e551f-111">请确保你的设备有 IoTCore 图像按照[入门说明](https://go.microsoft.com/fwlink/?linkid=860461)。</span><span class="sxs-lookup"><span data-stu-id="e551f-111">Make sure that your device has an IoTCore image installed by following the [Get Started instructions](https://go.microsoft.com/fwlink/?linkid=860461).</span></span>
* <span data-ttu-id="e551f-112">连接到你的设备通过[Powershell](../connect-your-device/PowerShell.md)。</span><span class="sxs-lookup"><span data-stu-id="e551f-112">Connect to your device via [Powershell](../connect-your-device/PowerShell.md).</span></span>

### <a name="on-the-pc"></a><span data-ttu-id="e551f-113">在 PC 上</span><span class="sxs-lookup"><span data-stu-id="e551f-113">On the PC</span></span>

* <span data-ttu-id="e551f-114">请确保已安装 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="e551f-114">Make sure you have installed Visual Studio 2017.</span></span>
* <span data-ttu-id="e551f-115">安装[Windows 驱动程序工具包](https://developer.microsoft.com/windows/hardware/windows-driver-kit)。</span><span class="sxs-lookup"><span data-stu-id="e551f-115">Install the [Windows Driver Kit](https://developer.microsoft.com/windows/hardware/windows-driver-kit).</span></span>  <span data-ttu-id="e551f-116">你将需要安装 SDK 和 WDK。</span><span class="sxs-lookup"><span data-stu-id="e551f-116">You will need to install the SDK and WDK.</span></span>
* <span data-ttu-id="e551f-117">安装证书，因此驱动程序签名正确，并可以在你的设备上运行。</span><span class="sxs-lookup"><span data-stu-id="e551f-117">Install the certificates so that the driver is signed correctly and can run on your device.</span></span> <span data-ttu-id="e551f-118">从提升的命令提示符执行下面列出的命令：</span><span class="sxs-lookup"><span data-stu-id="e551f-118">From an elevated command prompt execute the commands listed below:</span></span>

    1.  `cd c:\Program Files (x86)\Windows Kits\10\Tools\bin\i386` 
    2.  `set WPDKContentRoot=c:\Program Files (x86)\Windows Kits\10`
    3.  `InstallOEMCerts.cmd`
  
* <span data-ttu-id="e551f-119">将应用修复以启用从 VS F5 部署。</span><span class="sxs-lookup"><span data-stu-id="e551f-119">Apply fix to enable F5 deployment from VS.</span></span> <span data-ttu-id="e551f-120">在提升的命令提示符中，执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="e551f-120">In the elevated command prompt, execute the following commands:</span></span>

    1.  `cd %TEMP%` <span data-ttu-id="e551f-121">(将目录更改为`c:\users\<usernsme>\Appdata\Local\Temp`)</span><span class="sxs-lookup"><span data-stu-id="e551f-121">( will change directory to `c:\users\<usernsme>\Appdata\Local\Temp`)</span></span>
    2.  <span data-ttu-id="e551f-122">`md “WdkTempFiles”` 手动创建一个"WdkTempFiles"目录，这是在工具中的 bug 的解决方法，需要完成*仅一次*在 PC 中。</span><span class="sxs-lookup"><span data-stu-id="e551f-122">`md “WdkTempFiles”` Manually create a “WdkTempFiles” directory This is a workaround for a bug in the tooling and requires to be done *only once* in the PC.</span></span>


## <a name="step-2--provision-device-with-visual-studio"></a><span data-ttu-id="e551f-123">步骤 2:使用 Visual Studio 的预配设备</span><span class="sxs-lookup"><span data-stu-id="e551f-123">Step 2 : Provision device with Visual Studio</span></span> 
___
* <span data-ttu-id="e551f-124">打开 Visual Studio 并选择**驱动程序 > 测试 > 配置设备 > 添加新设备**</span><span class="sxs-lookup"><span data-stu-id="e551f-124">Open Visual Studio and select **Driver > Test > Configure Devices > Add New Device**</span></span>
    * <span data-ttu-id="e551f-125">如果未显示驱动程序菜单选项，检查是否已安装 SDK。</span><span class="sxs-lookup"><span data-stu-id="e551f-125">If the Driver Menu option is not shown, check if SDK is installed.</span></span>

* <span data-ttu-id="e551f-126">在中**设备配置**对话框中，</span><span class="sxs-lookup"><span data-stu-id="e551f-126">In the **Device Configuration** dialog,</span></span> 
    * <span data-ttu-id="e551f-127">为目标设备输入用户友好显示名称</span><span class="sxs-lookup"><span data-stu-id="e551f-127">Enter a user friendly Display Name for your target device</span></span>
    * <span data-ttu-id="e551f-128">选择设备类型 = 移动版</span><span class="sxs-lookup"><span data-stu-id="e551f-128">Select Device Type = Mobile</span></span>
    * <span data-ttu-id="e551f-129">在显示列表中，按 IP 地址进行排序和查找 IoT 设备的地址和选择。</span><span class="sxs-lookup"><span data-stu-id="e551f-129">In the list displayed, sort by IP address, and find the address for the IoT device and select.</span></span> <span data-ttu-id="e551f-130">如果有两个条目，选择具有非零 GUID。</span><span class="sxs-lookup"><span data-stu-id="e551f-130">If there are two entries, select the one with the non-zero GUID.</span></span>  <span data-ttu-id="e551f-131">请确保选择的行-它应突出显示蓝色</span><span class="sxs-lookup"><span data-stu-id="e551f-131">Make sure the row is selected – it should highlight blue</span></span>
    * <span data-ttu-id="e551f-132">在对话框的底部两个单选按钮。</span><span class="sxs-lookup"><span data-stu-id="e551f-132">At the bottom of the dialog are two radio buttons.</span></span>  <span data-ttu-id="e551f-133">选择一个指出**预配设备，并选择调试器设置**。</span><span class="sxs-lookup"><span data-stu-id="e551f-133">Select the one which says **Provision device and choose debugger settings**.</span></span>  <span data-ttu-id="e551f-134">选择**下一步**</span><span class="sxs-lookup"><span data-stu-id="e551f-134">Select **Next**</span></span>

* <span data-ttu-id="e551f-135">上**配置调试器设置**，设置合适的设置。</span><span class="sxs-lookup"><span data-stu-id="e551f-135">On the **Configure debugger settings**, set the appropriate settings.</span></span>  <span data-ttu-id="e551f-136">请注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="e551f-136">Note the following:</span></span>
   * <span data-ttu-id="e551f-137">MinnowBoardMax 可用网络来进行调试。</span><span class="sxs-lookup"><span data-stu-id="e551f-137">The MinnowBoardMax can use the network for debugging.</span></span>
       * <span data-ttu-id="e551f-138">使用连接类型**网络**</span><span class="sxs-lookup"><span data-stu-id="e551f-138">Use connection type **Network**</span></span>
       * <span data-ttu-id="e551f-139">选择某个端口-可以使用默认值</span><span class="sxs-lookup"><span data-stu-id="e551f-139">Select some port – default can be used</span></span>
       * <span data-ttu-id="e551f-140">选择一些密钥-可以使用默认值</span><span class="sxs-lookup"><span data-stu-id="e551f-140">Select some key – default can be used</span></span>
       * <span data-ttu-id="e551f-141">选择运行 visual studio 的计算机的主机 IP。</span><span class="sxs-lookup"><span data-stu-id="e551f-141">Select the host IP of the machine running visual studio.</span></span>  <span data-ttu-id="e551f-142">不要使用 autonet (169.xxx) 地址。</span><span class="sxs-lookup"><span data-stu-id="e551f-142">Do not use the autonet (169.xxx) address.</span></span>
       * <span data-ttu-id="e551f-143">选择**下一步**</span><span class="sxs-lookup"><span data-stu-id="e551f-143">Select **Next**</span></span>
       
  ![配置调试设置](../media/DriverDeployment/confdbgsettings.png)
       
    * <span data-ttu-id="e551f-145">在 Raspberry Pi 使用串行进行内核调试。</span><span class="sxs-lookup"><span data-stu-id="e551f-145">The Raspberry Pi uses serial for kernel debugging.</span></span>
       *  <span data-ttu-id="e551f-146">将相应的串行调试电缆连接到 PI，并将主机计算机</span><span class="sxs-lookup"><span data-stu-id="e551f-146">Connect the appropriate serial debugging cable to the PI and the host machine</span></span>
       *  <span data-ttu-id="e551f-147">选择**串行**的连接类型</span><span class="sxs-lookup"><span data-stu-id="e551f-147">Select **Serial** for the connection type</span></span>
       *  <span data-ttu-id="e551f-148">填写其余部分根据 Raspberry Pi 的参数。</span><span class="sxs-lookup"><span data-stu-id="e551f-148">Fill out the rest of the parameters as appropriate for the Raspberry Pi.</span></span>
       *  <span data-ttu-id="e551f-149">选择**下一步**</span><span class="sxs-lookup"><span data-stu-id="e551f-149">Select **Next**</span></span>

* <span data-ttu-id="e551f-150">WDK 通过 VS，现在将预配的 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="e551f-150">The WDK, through VS, will now provision the IoT device.</span></span>  <span data-ttu-id="e551f-151">将在设备上安装 TAEF 和 WDTF 并且为内核调试根据上面提供的设置将设置设备。</span><span class="sxs-lookup"><span data-stu-id="e551f-151">TAEF and WDTF will be installed on the device, and the device will be set up for kernel debugging per the settings provided above.</span></span>

* <span data-ttu-id="e551f-152">完成后，设备可能会重新启动。</span><span class="sxs-lookup"><span data-stu-id="e551f-152">When complete, the device may reboot.</span></span>  <span data-ttu-id="e551f-153">在进度屏幕**设备配置**将提供状态，并显示完整的 IoT 设备已完成的安装时。</span><span class="sxs-lookup"><span data-stu-id="e551f-153">The progress screen on the **Device Configuration** will provide status, and shows complete when the IoT device has completed the installation.</span></span> <span data-ttu-id="e551f-154">按**完成**。</span><span class="sxs-lookup"><span data-stu-id="e551f-154">Press **Finish**.</span></span>

![配置进度](../media/DriverDeployment/confprogress.png)

* <span data-ttu-id="e551f-156">现在已预配设备并**设备测试配置**状态显示**配置为用于驱动程序测试**</span><span class="sxs-lookup"><span data-stu-id="e551f-156">The device is now provisioned and the **Device test configuration** status shows **Configured for driver testing**</span></span>

![ConfigureDevices](../media/DriverDeployment/ConfigureDevices.png)

## <a name="step-3--configure-visual-studio-driver-project"></a><span data-ttu-id="e551f-158">步骤 3:配置 Visual Studio 驱动程序项目</span><span class="sxs-lookup"><span data-stu-id="e551f-158">Step 3 : Configure Visual Studio driver project</span></span>
___    
1. <span data-ttu-id="e551f-159">在管理员模式下启动 Visual Studio 并打开 visual studio 驱动程序项目。</span><span class="sxs-lookup"><span data-stu-id="e551f-159">Launch Visual Studio in the administrator mode and open the visual studio driver project.</span></span>
2. <span data-ttu-id="e551f-160">确保目标平台版本与安装在你的开发计算机上的 SDK 匹配。</span><span class="sxs-lookup"><span data-stu-id="e551f-160">Make sure the Target Platform Version matches the SDK installed on your development machine.</span></span> <span data-ttu-id="e551f-161">从“解决方案资源管理器”窗口中选择“项目属性”。</span><span class="sxs-lookup"><span data-stu-id="e551f-161">Select Project Properties from the Solution Explorer window.</span></span>  <span data-ttu-id="e551f-162">在“常规配置属性”下，确保目标平台版本与安装在你的开发计算机上的 SDK 匹配。</span><span class="sxs-lookup"><span data-stu-id="e551f-162">Under General Configuration Properties assure that the Target Platform Version matches the SDK installed on your development computer.</span></span>  <span data-ttu-id="e551f-163">您可以检查从 SDK 的版本**控制面板 > 程序 > 程序和功能**。</span><span class="sxs-lookup"><span data-stu-id="e551f-163">You can check the version of the SDK from the **Control Panel > Programs > Programs and Features**.</span></span>
3. <span data-ttu-id="e551f-164">下**项目 > 添加新项 > Visual C++ > Windows 驱动程序**，选择**包清单**，然后按**添加**。</span><span class="sxs-lookup"><span data-stu-id="e551f-164">Under **Project > Add New Item > Visual C++ > Windows Driver**, select **Package Manifest** and Press **Add**.</span></span>

![PackageManifest](../media/DriverDeployment/PackageManifest.png)

 `Package.pkg.xml` <span data-ttu-id="e551f-166">文件将添加到项目。</span><span class="sxs-lookup"><span data-stu-id="e551f-166">file will be added to the project.</span></span> <span data-ttu-id="e551f-167">在此文件中指定的所有者、 平台、 组件和子组件的标记。</span><span class="sxs-lookup"><span data-stu-id="e551f-167">In this file, specify the Owner, Platform, Component and SubComponent tags.</span></span> 
 
![Package-pkg-xml](../media/DriverDeployment/Package-pkg-xml.png)
 
4. <span data-ttu-id="e551f-169">设置在程序包版本号**项目属性 > PackageGen > 版本**。</span><span class="sxs-lookup"><span data-stu-id="e551f-169">Set package version number at **Project Properties > PackageGen > Version**.</span></span> <span data-ttu-id="e551f-170">请注意，每次需要执行该驱动程序安装/重新安装，此版本号会递增。</span><span class="sxs-lookup"><span data-stu-id="e551f-170">Note that every time you need to perform a Install/Reinstall of the driver, this version number has to be incremented.</span></span>

![PackageVersion](../media/DriverDeployment/PackageVersion.png)

5. <span data-ttu-id="e551f-172">下**项目属性 > 驱动程序签名 > 测试证书**，选择测试证书 （Phone OEM 测试证书）</span><span class="sxs-lookup"><span data-stu-id="e551f-172">Under **Project Properties > Driver Signing > Test Certificate**, select test certificate (Phone OEM Test Certificate)</span></span>

![DriverSigning](../media/DriverDeployment/DriverTestSigning.png)

6. <span data-ttu-id="e551f-174">转到**驱动程序安装**，然后选择**部署**</span><span class="sxs-lookup"><span data-stu-id="e551f-174">Go to **Driver Install** and select **Deployment**</span></span>

![InstallOptions](../media/DriverDeployment/installOptions.png)

* <span data-ttu-id="e551f-176">从**目标设备名称**下拉列表中，选择在预配过程中创建上述目标。</span><span class="sxs-lookup"><span data-stu-id="e551f-176">From the **Target Device Name** dropdown, select the target created above in the provisioning process.</span></span> <span data-ttu-id="e551f-177">请注意，两个选项**安装 / 重新安装**并**快速重新安装**。</span><span class="sxs-lookup"><span data-stu-id="e551f-177">Notice the two options for **Install / Reinstall** and **Fast Reinstall**.</span></span> <span data-ttu-id="e551f-178">选择选项并单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="e551f-178">Choose an option and Click **Ok**.</span></span>
* <span data-ttu-id="e551f-179">**安装 / 重新安装**用于驱动程序添加到目标的初始安装。</span><span class="sxs-lookup"><span data-stu-id="e551f-179">**Install / Reinstall** is used for the initial installation of a driver to the target.</span></span>  <span data-ttu-id="e551f-180">这将安装使用 Windows 更新堆栈的驱动程序包，并且可能需要几分钟。</span><span class="sxs-lookup"><span data-stu-id="e551f-180">This installs the driver package using the Windows update stack and can take several minutes.</span></span> <span data-ttu-id="e551f-181">这必须使用每次更改 INF 文件。</span><span class="sxs-lookup"><span data-stu-id="e551f-181">This must be used every time the INF file is changed.</span></span> 
    
> [!TIP]
> <span data-ttu-id="e551f-182">每次使用此选项在初始安装后安装驱动程序，必须递增程序包版本号。</span><span class="sxs-lookup"><span data-stu-id="e551f-182">Every time this option is used to install a driver after the initial installation, the package version number must be incremented.</span></span>

* <span data-ttu-id="e551f-183">**快速重新安装**已安装驱动程序，并没有后续更改的驱动程序 INF 文件这会影响注册表后可以使用。</span><span class="sxs-lookup"><span data-stu-id="e551f-183">**Fast Reinstall** can be used once a driver has been installed, and there are no subsequent changes to the drivers INF file which affect the registry.</span></span>  <span data-ttu-id="e551f-184">此方法会跳过安装过程，然后关闭与该驱动程序相关联的所有 devnodes、 逐过程复制驱动程序并重新启动 devnode。</span><span class="sxs-lookup"><span data-stu-id="e551f-184">This method bypasses the install process, shuts down all devnodes associated with the driver, copies the driver over, and restarts the devnode.</span></span>  <span data-ttu-id="e551f-185">这需要花费几个 (< 20) 秒。</span><span class="sxs-lookup"><span data-stu-id="e551f-185">This takes a few (<20) seconds.</span></span>

    
> [!WARNING]
> <span data-ttu-id="e551f-186">此方法是不能保证成功 – 如果 devnode 不能为关闭，以释放该驱动程序由于某种原因，则操作将失败。</span><span class="sxs-lookup"><span data-stu-id="e551f-186">This method is not guaranteed to succeed – If for some reason a devnode cannot be shutdown to release the driver, the operation will fail.</span></span>  <span data-ttu-id="e551f-187">这可能是由于硬件故障或初始发生故障的驱动程序实现。</span><span class="sxs-lookup"><span data-stu-id="e551f-187">This can be due to faulty hardware, or an initial faulty implementation of the driver.</span></span>  <span data-ttu-id="e551f-188">安装/重新安装选项，必须在这种情况下使用。</span><span class="sxs-lookup"><span data-stu-id="e551f-188">The Install/Reinstall option must be used in this case.</span></span>


<span data-ttu-id="e551f-189">你的 Visual Studio 项目现已准备就绪，可生成驱动程序并将其部署到目标设备。</span><span class="sxs-lookup"><span data-stu-id="e551f-189">Your Visual Studio project is now ready to build and deploy a driver to your target device.</span></span> <span data-ttu-id="e551f-190">如果你将需要生成 ACPI 表并复制到目标设备的示例 gpiokmdfdemo 驱动程序，然后按照中的步骤[构建 Visual Studio 中的驱动程序](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2)。</span><span class="sxs-lookup"><span data-stu-id="e551f-190">If you are using the sample gpiokmdfdemo driver you need to generate ACPI table and copy to your target device, then follow the steps in [building the driver in Visual Studio](https://developer.microsoft.com/en-us/windows/iot/samples/driverlab2).</span></span>


## <a name="step-4--build-and-deploy-driver"></a><span data-ttu-id="e551f-191">步骤 4:生成和部署驱动程序</span><span class="sxs-lookup"><span data-stu-id="e551f-191">Step 4 : Build and deploy driver</span></span>
___
<span data-ttu-id="e551f-192">这可以在两个方面，使用**F5**密钥和使用**部署**选项。</span><span class="sxs-lookup"><span data-stu-id="e551f-192">This can be done in two ways, using the **F5** key and using the **Deploy** option.</span></span> <span data-ttu-id="e551f-193">这两种方式构建和部署驱动程序 （即其设备上安装） 和 F5 将 Visual Studio 内核调试程序附加到已安装并加载驱动程序。</span><span class="sxs-lookup"><span data-stu-id="e551f-193">In both ways, the driver will be built and deployed (i.e. installs it on device) and the F5 attaches the Visual Studio kernel debugger to the installed and loaded driver.</span></span> 

<span data-ttu-id="e551f-194">某些用户更喜欢使用**部署**功能和附加不同内核调试程序，如 WinDBG 或 KD。</span><span class="sxs-lookup"><span data-stu-id="e551f-194">Some users prefer to use the **Deploy** functionality and attach a different kernel debugger, such as WinDBG or KD.</span></span>  <span data-ttu-id="e551f-195">这可以提供更大的灵活性比使用 VS 调试器。</span><span class="sxs-lookup"><span data-stu-id="e551f-195">This can provide more flexibility than using the VS debugger.</span></span>

### <a name="deploy"></a><span data-ttu-id="e551f-196">部署</span><span class="sxs-lookup"><span data-stu-id="e551f-196">Deploy</span></span>
1.  <span data-ttu-id="e551f-197">右键单击解决方案资源管理器中的项目</span><span class="sxs-lookup"><span data-stu-id="e551f-197">Right-click on the project in the solution explorer</span></span>
2.  <span data-ttu-id="e551f-198">选择**部署**</span><span class="sxs-lookup"><span data-stu-id="e551f-198">Select **Deploy**</span></span>

![部署](../media/DriverDeployment/deploy.png) 

3.  <span data-ttu-id="e551f-200">部署过程应继续进行。</span><span class="sxs-lookup"><span data-stu-id="e551f-200">The deployment process should proceed.</span></span>  <span data-ttu-id="e551f-201">IoT 设备部署后，将重启和安装正在进行时，应显示"齿轮"屏幕。</span><span class="sxs-lookup"><span data-stu-id="e551f-201">The IoT device will be rebooted after deployment, and should show the “Gears” screen while installation is taking place.</span></span>

<span data-ttu-id="e551f-202">生成输出采用**输出**窗口部署状态也是在输出窗口时安装完成，设备将再次，重新启动和 VS 输出屏幕将指示成功或失败。</span><span class="sxs-lookup"><span data-stu-id="e551f-202">Build output is in the **Output** Window Deployment status is also in the output window When Installation completes, the device will reboot again, and the VS Output screen will indicate success or failure.</span></span>

### <a name="f5"></a><span data-ttu-id="e551f-203">F5</span><span class="sxs-lookup"><span data-stu-id="e551f-203">F5</span></span>

1.  <span data-ttu-id="e551f-204">从生成窗口中，确保正确配置 – 当前生成体系结构是与目标设备体系结构相同。</span><span class="sxs-lookup"><span data-stu-id="e551f-204">From the build window, make sure that the configurations are correct – the current build arch is the same as the target device arch.</span></span>  <span data-ttu-id="e551f-205">这是其中的目标名称中具有体系结构是有价值。</span><span class="sxs-lookup"><span data-stu-id="e551f-205">This is where having the arch in the target name is valuable.</span></span>  <span data-ttu-id="e551f-206">在右上角中间在 VS 中的菜单栏上的视图框中，将显示目标。</span><span class="sxs-lookup"><span data-stu-id="e551f-206">The target will be displayed in the view box on the menu bar in VS on the top-middle-right.</span></span>
2.  <span data-ttu-id="e551f-207">按**F5**。</span><span class="sxs-lookup"><span data-stu-id="e551f-207">Press **F5**.</span></span>  <span data-ttu-id="e551f-208">目标生成、 部署，并将附加到 VS 内核调试程序。</span><span class="sxs-lookup"><span data-stu-id="e551f-208">The target will be built, deployed, and attached to the VS Kernel Debugger.</span></span>

* <span data-ttu-id="e551f-209">重新启动后，请确保 PowerShell 仍连接到它，否则，重新连接到目标设备使用 PowerShell`enter-pssession`命令...</span><span class="sxs-lookup"><span data-stu-id="e551f-209">After the reboot, make sure PowerShell is still connected to it, otherwise, re-connect to the target device using the PowerShell `enter-pssession` command..</span></span>


## <a name="known-issues"></a><span data-ttu-id="e551f-210">已知问题</span><span class="sxs-lookup"><span data-stu-id="e551f-210">Known Issues</span></span>
___

### <a name="provisioning-errors"></a><span data-ttu-id="e551f-211">预配错误</span><span class="sxs-lookup"><span data-stu-id="e551f-211">Provisioning Errors</span></span>
<span data-ttu-id="e551f-212">在与 MinnowBoardMax 交互期间的争用条件可能导致在预配期间报告失败。</span><span class="sxs-lookup"><span data-stu-id="e551f-212">A race condition during the interaction with MinnowBoardMax can result in a reported failure during provisioning.</span></span>  <span data-ttu-id="e551f-213">事实上，预配最有可能成功。</span><span class="sxs-lookup"><span data-stu-id="e551f-213">In fact, the provisioning most likely succeeded.</span></span>

**<span data-ttu-id="e551f-214">错误的列表：</span><span class="sxs-lookup"><span data-stu-id="e551f-214">List of Errors:</span></span>**
 
* <span data-ttu-id="e551f-215">错误：任务的"注册的 WDTF"无法成功完成。</span><span class="sxs-lookup"><span data-stu-id="e551f-215">ERROR: Task "Registering WDTF" failed to complete successfully.</span></span>
* <span data-ttu-id="e551f-216">错误：任务"配置内核调试程序设置 （可能需要重启）"无法成功完成</span><span class="sxs-lookup"><span data-stu-id="e551f-216">ERROR: Task "Configuring kernel debugger settings (possible reboot)" failed to complete successfully</span></span>

<span data-ttu-id="e551f-217">**解决方法：** 几乎可以肯定可以忽略这些错误。</span><span class="sxs-lookup"><span data-stu-id="e551f-217">**Workaround:** These error can almost certainly be ignored.</span></span>

**<span data-ttu-id="e551f-218">详细信息：</span><span class="sxs-lookup"><span data-stu-id="e551f-218">Details:</span></span>**

<span data-ttu-id="e551f-219">以下的错误将显示在**设备配置配置进度**对话框：</span><span class="sxs-lookup"><span data-stu-id="e551f-219">The following error will be displayed in the **Device Configuration Configuration Progress** dialog:</span></span>

```
Installing necessary components...
Removing TAEF test service
    Task "Removing TAEF test service" completed successfully
Copying required files
    Task "Copying required files" completed successfully
Registering TAEF Test Service
    Task "Registering TAEF Test Service" completed successfully
Starting TAEF Test Service
    Task "Starting TAEF Test Service" completed successfully
Registering WDTF
    Task "Registering WDTF" completed successfully 
Configuring TAEF test service to start automatically
    Task "Configuring TAEF test service to start automatically" completed successfully
Configuring kernel debugger settings (possible reboot)
    ERROR: Task "Configuring kernel debugger settings (possible reboot)" failed to complete successfully. Look at the logs in the driver test group explorer for more details on the failure.
Configuring computer settings (possible reboot)
Waiting for task to complete...
Waiting for task to complete...
    Task "Configuring computer settings (possible reboot)" completed successfully
Computer configuration log file://C:/Users/username/AppData/Roaming/Microsoft/WDKTestInfrastructure/ProvisioningLogs/Driver%20Test%20Computer%20Configuration%log
Failed installing components
```

<span data-ttu-id="e551f-220">现在你可以安全地单击**完成**，然后**应用**并**确定**。</span><span class="sxs-lookup"><span data-stu-id="e551f-220">At this point you can safely click on the **Finish** and then the **Apply** and **OK**.</span></span>

<span data-ttu-id="e551f-221">这是良性错误格式正确的结果日志格式不正确导致的争用条件。</span><span class="sxs-lookup"><span data-stu-id="e551f-221">This is a benign error formed by a race condition causing a result log to be malformed.</span></span> <span data-ttu-id="e551f-222">这可以通过查看以下区域中的日志文件进行验证：</span><span class="sxs-lookup"><span data-stu-id="e551f-222">This can be verified by looking at the log file in the following area:</span></span>

1. <span data-ttu-id="e551f-223">打开到 FTP 连接到的 IP 的设备 （如设备屏幕所示）`Data/test/bin/DriverTest/Run`目录。</span><span class="sxs-lookup"><span data-stu-id="e551f-223">Open an FTP connection to the IP of the device (as shown on the device screen) to the `Data/test/bin/DriverTest/Run` directory.</span></span>
<span data-ttu-id="e551f-224">例如</span><span class="sxs-lookup"><span data-stu-id="e551f-224">e.g.</span></span>
`ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`

2. <span data-ttu-id="e551f-225">复制`Configuring_computer_settings_(possible_reboot)_identifier.wtl`到本地计算机的文件。</span><span class="sxs-lookup"><span data-stu-id="e551f-225">copy the `Configuring_computer_settings_(possible_reboot)_identifier.wtl` file to your local machine.</span></span>  <span data-ttu-id="e551f-226">请注意日志文件名称与匹配失败任务的名称。</span><span class="sxs-lookup"><span data-stu-id="e551f-226">Note that the log file name matches the name of the failing task.</span></span>
3. <span data-ttu-id="e551f-227">在记事本中打开该文件</span><span class="sxs-lookup"><span data-stu-id="e551f-227">Open the file in notepad</span></span>
4. <span data-ttu-id="e551f-228">滚动到日志底部。</span><span class="sxs-lookup"><span data-stu-id="e551f-228">Scroll to the bottom of the log.</span></span>  <span data-ttu-id="e551f-229">下面的文本将会显示，指示已成功预配。</span><span class="sxs-lookup"><span data-stu-id="e551f-229">The following text will be present, indicating that the provisioning is successful.</span></span>

```
<PFRollup 
    Total="1" 
    Passed="1" 
    Failed="0" 
    Blocked="0" 
    Warned="0" 
    Skipped="0" CA="6191559" LA="6191619" >
    <rti id="2109770915" />
    <ctx id="384048256" />
</PFRollup>
</WTT-Logger>
```

