---
title: 驱动程序部署
author: parameshbabu
ms.author: pabab
ms.date: 08/22/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 在 Windows 10 IoT Core 上构建并部署驱动程序。 配置你的 Visual Studio 驱动程序项目，以便可以编译和部署特定平台的驱动程序。
keywords: windows 10 IoT Core，驱动程序部署
ms.openlocfilehash: 772cd46022a69f68ebfd9ec79c7c2eb3fe7933c0
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655903"
---
# <a name="driver-deployment"></a><span data-ttu-id="9b8b9-105">驱动程序部署</span><span class="sxs-lookup"><span data-stu-id="9b8b9-105">Driver deployment</span></span>

<span data-ttu-id="9b8b9-106">使用 Visual Studio 在 Windows 10 IoT Core 上部署驱动程序。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-106">Deploy a driver on Windows 10 IoT Core with Visual Studio.</span></span>

<span data-ttu-id="9b8b9-107">配置你的 Visual Studio 驱动程序项目，以便可以在驱动程序开发阶段为特定平台编译和部署驱动程序。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-107">Configure your Visual Studio driver project so that you can compile and deploy a driver for a specific platform during driver development phase.</span></span>

<span data-ttu-id="9b8b9-108">对于本练习，可以使用 [gpiokmdfdemo 示例驱动程序](https://github.com/ms-iot/samples/tree/develop/DriverSamples)。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-108">For this exercise you can use the [gpiokmdfdemo sample driver](https://github.com/ms-iot/samples/tree/develop/DriverSamples).</span></span>

<span data-ttu-id="9b8b9-109">如果要将驱动程序添加到映像，请访问 [IoT 制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image)中的说明。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-109">If you're looking to add a driver to an image, please visit the instructions in our [IoT Manufacturing Guide](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-driver-to-an-image).</span></span>

## <a name="step-1-setup"></a><span data-ttu-id="9b8b9-110">步骤1：安装</span><span class="sxs-lookup"><span data-stu-id="9b8b9-110">Step 1: Setup</span></span>
___

### <a name="on-the-device"></a><span data-ttu-id="9b8b9-111">在设备上</span><span class="sxs-lookup"><span data-stu-id="9b8b9-111">On the device</span></span>

* <span data-ttu-id="9b8b9-112">请确保你的设备按照 [入门说明](https://go.microsoft.com/fwlink/?linkid=860461)安装了 IoTCore 映像。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-112">Make sure that your device has an IoTCore image installed by following the [Get Started instructions](https://go.microsoft.com/fwlink/?linkid=860461).</span></span>
* <span data-ttu-id="9b8b9-113">通过 [PowerShell](../connect-your-device/PowerShell.md)连接到你的设备。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-113">Connect to your device via [PowerShell](../connect-your-device/PowerShell.md).</span></span>

### <a name="on-the-pc"></a><span data-ttu-id="9b8b9-114">在电脑上</span><span class="sxs-lookup"><span data-stu-id="9b8b9-114">On the PC</span></span>

* <span data-ttu-id="9b8b9-115">请确保已安装 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-115">Make sure you have installed Visual Studio 2017.</span></span>
* <span data-ttu-id="9b8b9-116">安装 [Windows 驱动程序工具包](https://developer.microsoft.com/windows/hardware/windows-driver-kit)。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-116">Install the [Windows Driver Kit](https://developer.microsoft.com/windows/hardware/windows-driver-kit).</span></span>  <span data-ttu-id="9b8b9-117">你将需要安装 SDK 和 WDK。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-117">You will need to install the SDK and WDK.</span></span>
* <span data-ttu-id="9b8b9-118">安装证书，以便对驱动程序进行正确签名，并且可以在设备上运行。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-118">Install the certificates so that the driver is signed correctly and can run on your device.</span></span> <span data-ttu-id="9b8b9-119">从提升权限的命令提示符处执行下列命令：</span><span class="sxs-lookup"><span data-stu-id="9b8b9-119">From an elevated command prompt execute the commands listed below:</span></span>

    1.  `cd c:\Program Files (x86)\Windows Kits\10\Tools\bin\i386`
    2.  `set WPDKContentRoot=c:\Program Files (x86)\Windows Kits\10`
    3.  `InstallOEMCerts.cmd`

* <span data-ttu-id="9b8b9-120">应用修补程序，以从 VS 启用 F5 部署。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-120">Apply fix to enable F5 deployment from VS.</span></span> <span data-ttu-id="9b8b9-121">在提升的命令提示符下，执行以下命令：</span><span class="sxs-lookup"><span data-stu-id="9b8b9-121">In the elevated command prompt, execute the following commands:</span></span>

    1.  <span data-ttu-id="9b8b9-122">`cd %TEMP%` ( 会将目录更改为 `c:\users\<usernsme>\Appdata\Local\Temp`) </span><span class="sxs-lookup"><span data-stu-id="9b8b9-122">`cd %TEMP%` ( will change directory to `c:\users\<usernsme>\Appdata\Local\Temp`)</span></span>
    2.  <span data-ttu-id="9b8b9-123">`md “WdkTempFiles”` 手动创建 "WdkTempFiles" 目录这是工具中 bug 的一种解决方法，只需在 PC 中执行 *一次* 。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-123">`md “WdkTempFiles”` Manually create a “WdkTempFiles” directory This is a workaround for a bug in the tooling and requires to be done *only once* in the PC.</span></span>


## <a name="step-2-provision-device-with-visual-studio"></a><span data-ttu-id="9b8b9-124">步骤2：在 Visual Studio 中预配设备</span><span class="sxs-lookup"><span data-stu-id="9b8b9-124">Step 2: Provision device with Visual Studio</span></span>
___
* <span data-ttu-id="9b8b9-125">打开 Visual Studio 并选择 " **驱动程序" > 测试 > 配置设备 > 添加新设备**</span><span class="sxs-lookup"><span data-stu-id="9b8b9-125">Open Visual Studio and select **Driver > Test > Configure Devices > Add New Device**</span></span>
    * <span data-ttu-id="9b8b9-126">如果未显示 "驱动程序" 菜单选项，请检查是否安装了 SDK。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-126">If the Driver Menu option is not shown, check if SDK is installed.</span></span>

* <span data-ttu-id="9b8b9-127">在 " **设备配置** " 对话框中，</span><span class="sxs-lookup"><span data-stu-id="9b8b9-127">In the **Device Configuration** dialog,</span></span>
    * <span data-ttu-id="9b8b9-128">为目标设备输入用户友好的显示名称</span><span class="sxs-lookup"><span data-stu-id="9b8b9-128">Enter a user-friendly Display Name for your target device</span></span>
    * <span data-ttu-id="9b8b9-129">选择设备类型 = 移动</span><span class="sxs-lookup"><span data-stu-id="9b8b9-129">Select Device Type = Mobile</span></span>
    * <span data-ttu-id="9b8b9-130">在显示的列表中，按 IP 地址排序，查找 IoT 设备的地址并选择。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-130">In the list displayed, sort by IP address, and find the address for the IoT device and select.</span></span> <span data-ttu-id="9b8b9-131">如果有两个条目，请选择一个具有非零 GUID 的条目。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-131">If there are two entries, select the one with the non-zero GUID.</span></span>  <span data-ttu-id="9b8b9-132">确保行已选中–应突出显示蓝色</span><span class="sxs-lookup"><span data-stu-id="9b8b9-132">Make sure the row is selected – it should highlight blue</span></span>
    * <span data-ttu-id="9b8b9-133">对话框底部有两个单选按钮。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-133">At the bottom of the dialog are two radio buttons.</span></span>  <span data-ttu-id="9b8b9-134">选择 " **设置设备"，然后选择 "调试器设置**"。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-134">Select the one that says **Provision device and choose debugger settings**.</span></span>  <span data-ttu-id="9b8b9-135">选择“下一步”</span><span class="sxs-lookup"><span data-stu-id="9b8b9-135">Select **Next**</span></span>

* <span data-ttu-id="9b8b9-136">在 " **配置调试器设置**" 上，设置适当的设置。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-136">On the **Configure debugger settings**, set the appropriate settings.</span></span>  <span data-ttu-id="9b8b9-137">注意以下事项：</span><span class="sxs-lookup"><span data-stu-id="9b8b9-137">Note the following:</span></span>
   * <span data-ttu-id="9b8b9-138">MinnowBoardMax 可以使用网络进行调试。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-138">The MinnowBoardMax can use the network for debugging.</span></span>
       * <span data-ttu-id="9b8b9-139">使用连接类型 **网络**</span><span class="sxs-lookup"><span data-stu-id="9b8b9-139">Use connection type **Network**</span></span>
       * <span data-ttu-id="9b8b9-140">选择某个端口–默认值可以使用</span><span class="sxs-lookup"><span data-stu-id="9b8b9-140">Select some port – default can be used</span></span>
       * <span data-ttu-id="9b8b9-141">选择一些密钥-默认值可以使用</span><span class="sxs-lookup"><span data-stu-id="9b8b9-141">Select some key – default can be used</span></span>
       * <span data-ttu-id="9b8b9-142">选择运行 visual studio 的计算机的主机 IP。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-142">Select the host IP of the machine running visual studio.</span></span>  <span data-ttu-id="9b8b9-143">请勿使用 autonet (169.xxx) 地址。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-143">Do not use the autonet (169.xxx) address.</span></span>
       * <span data-ttu-id="9b8b9-144">选择“下一步”</span><span class="sxs-lookup"><span data-stu-id="9b8b9-144">Select **Next**</span></span>

  ![配置调试设置](../media/DriverDeployment/confdbgsettings.png)

    * <span data-ttu-id="9b8b9-146">Raspberry Pi 使用串行进行内核调试。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-146">The Raspberry Pi uses serial for kernel debugging.</span></span>
       *  <span data-ttu-id="9b8b9-147">将相应的串行调试电缆连接到 PI 和主机</span><span class="sxs-lookup"><span data-stu-id="9b8b9-147">Connect the appropriate serial debugging cable to the PI and the host machine</span></span>
       *  <span data-ttu-id="9b8b9-148">为连接类型选择 " **串行** "</span><span class="sxs-lookup"><span data-stu-id="9b8b9-148">Select **Serial** for the connection type</span></span>
       *  <span data-ttu-id="9b8b9-149">针对 Raspberry Pi 填写参数的其余部分。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-149">Fill out the rest of the parameters as appropriate for the Raspberry Pi.</span></span>
       *  <span data-ttu-id="9b8b9-150">选择“下一步”</span><span class="sxs-lookup"><span data-stu-id="9b8b9-150">Select **Next**</span></span>

* <span data-ttu-id="9b8b9-151">通过 VS，WDK 现在将预配 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-151">The WDK, through VS, will now provision the IoT device.</span></span>  <span data-ttu-id="9b8b9-152">将在设备上安装 TAEF 和 WDTF，并按上面提供的设置针对内核调试设置设备。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-152">TAEF and WDTF will be installed on the device, and the device will be set up for kernel debugging per the settings provided above.</span></span>

* <span data-ttu-id="9b8b9-153">完成后，设备可能会重新启动。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-153">When complete, the device may reboot.</span></span>  <span data-ttu-id="9b8b9-154">**设备配置**上的进度屏幕将提供状态，并在 IoT 设备完成安装后显示完成。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-154">The progress screen on the **Device Configuration** will provide status, and shows complete when the IoT device has completed the installation.</span></span> <span data-ttu-id="9b8b9-155">按 " **完成**"。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-155">Press **Finish**.</span></span>

![配置进度](../media/DriverDeployment/confprogress.png)

* <span data-ttu-id="9b8b9-157">设备现已设置，**设备测试配置**状态显示为 "**驱动程序测试**"</span><span class="sxs-lookup"><span data-stu-id="9b8b9-157">The device is now provisioned and the **Device test configuration** status shows **Configured for driver testing**</span></span>

![配置设备](../media/DriverDeployment/ConfigureDevices.png)

## <a name="step-3-configure-visual-studio-driver-project"></a><span data-ttu-id="9b8b9-159">步骤3：配置 Visual Studio 驱动程序项目</span><span class="sxs-lookup"><span data-stu-id="9b8b9-159">Step 3: Configure Visual Studio driver project</span></span>
___    
1. <span data-ttu-id="9b8b9-160">在管理员模式下启动 Visual Studio，然后打开 visual studio 驱动程序项目。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-160">Launch Visual Studio in the administrator mode and open the visual studio driver project.</span></span>
2. <span data-ttu-id="9b8b9-161">请确保目标平台版本与开发计算机上安装的 SDK 匹配。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-161">Make sure the Target Platform Version matches the SDK installed on your development machine.</span></span> <span data-ttu-id="9b8b9-162">从 "解决方案资源管理器" 窗口中选择 "项目属性"。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-162">Select Project Properties from the Solution Explorer window.</span></span>  <span data-ttu-id="9b8b9-163">在 "常规配置属性" 下，确保目标平台版本与开发计算机上安装的 SDK 匹配。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-163">Under General Configuration Properties assure that the Target Platform Version matches the SDK installed on your development computer.</span></span>  <span data-ttu-id="9b8b9-164">可以从 "控制面板" 中检查 SDK 的版本， **> 程序 ">" 程序和功能**"。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-164">You can check the version of the SDK from the **Control Panel > Programs > Programs and Features**.</span></span>
3. <span data-ttu-id="9b8b9-165">在 " **Project > Visual C++ > Windows 驱动程序添加新项" >**，选择 " **包清单** " 并按 " **添加**"。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-165">Under **Project > Add New Item > Visual C++ > Windows Driver**, select **Package Manifest** and Press **Add**.</span></span>

![程序包清单](../media/DriverDeployment/PackageManifest.png)

 <span data-ttu-id="9b8b9-167">`Package.pkg.xml` 文件将被添加到项目。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-167">`Package.pkg.xml` file will be added to the project.</span></span> <span data-ttu-id="9b8b9-168">在此文件中，指定所有者、平台、组件和子组件标记。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-168">In this file, specify the Owner, Platform, Component and SubComponent tags.</span></span>

![包 .pkg xml](../media/DriverDeployment/Package-pkg-xml.png)

4. <span data-ttu-id="9b8b9-170">在 **项目属性 > PackageGen > 版本**中设置包版本号。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-170">Set package version number at **Project Properties > PackageGen > Version**.</span></span> <span data-ttu-id="9b8b9-171">请注意，每次需要执行驱动程序的安装/重新安装时，此版本号必须递增。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-171">Note that every time you need to perform a Install/Reinstall of the driver, this version number has to be incremented.</span></span>

![包版本](../media/DriverDeployment/PackageVersion.png)

5. <span data-ttu-id="9b8b9-173">在 " **项目属性 > 驱动程序签名" > 测试证书**"下，选择" 测试证书 (电话 OEM 测试证书 ") </span><span class="sxs-lookup"><span data-stu-id="9b8b9-173">Under **Project Properties > Driver Signing > Test Certificate**, select test certificate (Phone OEM Test Certificate)</span></span>

![DriverSigning](../media/DriverDeployment/DriverTestSigning.png)

6. <span data-ttu-id="9b8b9-175">请参阅 **驱动程序安装** 并选择 **部署**</span><span class="sxs-lookup"><span data-stu-id="9b8b9-175">Go to **Driver Install** and select **Deployment**</span></span>

![安装选项](../media/DriverDeployment/installOptions.png)

* <span data-ttu-id="9b8b9-177">从 " **目标设备名称** " 下拉列表中，选择在预配过程中创建的目标。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-177">From the **Target Device Name** dropdown, select the target created above in the provisioning process.</span></span> <span data-ttu-id="9b8b9-178">请注意两个用于 **安装/重新** 安装和 **快速重新安装**的选项。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-178">Notice the two options for **Install / Reinstall** and **Fast Reinstall**.</span></span> <span data-ttu-id="9b8b9-179">选择一个选项，然后单击 **"确定"**。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-179">Choose an option and Click **Ok**.</span></span>
* <span data-ttu-id="9b8b9-180">**安装/重新安装** 用于向目标驱动程序的初始安装。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-180">**Install / Reinstall** is used for the initial installation of a driver to the target.</span></span>  <span data-ttu-id="9b8b9-181">这将使用 Windows 更新堆栈安装驱动程序包，可能需要几分钟时间。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-181">This installs the driver package using the Windows update stack and can take several minutes.</span></span> <span data-ttu-id="9b8b9-182">每次更改 INF 文件时都必须使用此文件。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-182">This must be used every time the INF file is changed.</span></span>

> [!TIP]
> <span data-ttu-id="9b8b9-183">在初始安装后，每次用此选项安装驱动程序时，包版本号必须递增。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-183">Every time this option is used to install a driver after the initial installation, the package version number must be incremented.</span></span>

* <span data-ttu-id="9b8b9-184">安装驱动程序后，可以使用**快速重新安装**，并且不会对驱动程序 INF 文件进行后续更改，这会影响注册表。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-184">**Fast Reinstall** can be used once a driver has been installed, and there are no subsequent changes to the drivers INF file, which affect the registry.</span></span>  <span data-ttu-id="9b8b9-185">此方法将绕过安装过程，关闭与驱动程序相关的所有 devnodes，将驱动程序复制到，并重新启动 devnode。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-185">This method bypasses the install process, shuts down all devnodes associated with the driver, copies the driver over, and restarts the devnode.</span></span>  <span data-ttu-id="9b8b9-186">这会花费几个 ( # B0 20) 秒。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-186">This takes a few (<20) seconds.</span></span>


> [!WARNING]
> <span data-ttu-id="9b8b9-187">不保证此方法成功-如果由于某种原因无法关闭 devnode 来释放驱动程序，操作将失败。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-187">This method is not guaranteed to succeed – If for some reason a devnode cannot be shutdown to release the driver, the operation will fail.</span></span>  <span data-ttu-id="9b8b9-188">这可能是由硬件故障或驱动程序的初始错误实现引起的。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-188">This can be due to faulty hardware, or an initial faulty implementation of the driver.</span></span>  <span data-ttu-id="9b8b9-189">在这种情况下，必须使用 "安装/重新安装" 选项。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-189">The Install/Reinstall option must be used in this case.</span></span>


<span data-ttu-id="9b8b9-190">你的 Visual Studio 项目现在已准备好生成驱动程序并将其部署到目标设备。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-190">Your Visual Studio project is now ready to build and deploy a driver to your target device.</span></span> <span data-ttu-id="9b8b9-191">如果使用的是示例 gpiokmdfdemo 驱动程序，则需要生成 ACPI 表，并将其复制到目标设备，然后按照在 [Visual Studio 中生成驱动程序](https://developer.microsoft.com/windows/iot/samples/driverlab2)中的步骤进行操作。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-191">If you are using the sample gpiokmdfdemo driver you need to generate ACPI table and copy to your target device, then follow the steps in [building the driver in Visual Studio](https://developer.microsoft.com/windows/iot/samples/driverlab2).</span></span>


## <a name="step-4-build-and-deploy-driver"></a><span data-ttu-id="9b8b9-192">步骤4：生成并部署驱动程序</span><span class="sxs-lookup"><span data-stu-id="9b8b9-192">Step 4: Build and deploy driver</span></span>
___
<span data-ttu-id="9b8b9-193">这可以通过两种方式来完成：使用 **F5** 键并使用 " **部署** " 选项。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-193">This can be done in two ways, using the **F5** key and using the **Deploy** option.</span></span> <span data-ttu-id="9b8b9-194">在这两种方法中，将生成并部署该驱动程序 (即，将其安装到设备) 上，然后 F5 将 Visual Studio 内核调试器附加到安装和加载的驱动程序。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-194">In both ways, the driver will be built and deployed (i.e. installs it on device) and the F5 attaches the Visual Studio kernel debugger to the installed and loaded driver.</span></span>

<span data-ttu-id="9b8b9-195">某些用户喜欢使用 **部署** 功能并附加不同的内核调试器，如 WINDBG 或 KD。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-195">Some users prefer to use the **Deploy** functionality and attach a different kernel debugger, such as WinDBG or KD.</span></span>  <span data-ttu-id="9b8b9-196">与使用 VS 调试器相比，这可以提供更大的灵活性。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-196">This can provide more flexibility than using the VS debugger.</span></span>

### <a name="deploy"></a><span data-ttu-id="9b8b9-197">部署</span><span class="sxs-lookup"><span data-stu-id="9b8b9-197">Deploy</span></span>
1.  <span data-ttu-id="9b8b9-198">右键单击解决方案资源管理器中的项目</span><span class="sxs-lookup"><span data-stu-id="9b8b9-198">Right-click on the project in the solution explorer</span></span>
2.  <span data-ttu-id="9b8b9-199">选择“部署”</span><span class="sxs-lookup"><span data-stu-id="9b8b9-199">Select **Deploy**</span></span>

![选择“部署”](../media/DriverDeployment/deploy.png)

3.  <span data-ttu-id="9b8b9-201">部署过程应继续。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-201">The deployment process should proceed.</span></span>  <span data-ttu-id="9b8b9-202">IoT 设备将在部署后重新启动，并在进行安装时显示 "齿轮" 屏幕。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-202">The IoT device will be rebooted after deployment, and should show the “Gears” screen while installation is taking place.</span></span>

<span data-ttu-id="9b8b9-203">生成输出在 " **输出** " 窗口中，安装完成后也会出现在 "输出" 窗口中，设备将再次重新启动，而 VS 输出屏幕将指示成功或失败。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-203">Build output is in the **Output** Window Deployment status is also in the output window When Installation completes, the device will reboot again, and the VS Output screen will indicate success or failure.</span></span>

### <a name="f5"></a><span data-ttu-id="9b8b9-204">F5</span><span class="sxs-lookup"><span data-stu-id="9b8b9-204">F5</span></span>

1.  <span data-ttu-id="9b8b9-205">在 "生成" 窗口中，确保配置正确– "当前生成" 与目标设备相同。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-205">From the build window, make sure that the configurations are correct – the current build arch is the same as the target device arch.</span></span>  <span data-ttu-id="9b8b9-206">在这种情况下，目标名称中的这种情况非常有用。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-206">This is where having the arch in the target name is valuable.</span></span>  <span data-ttu-id="9b8b9-207">目标将显示在 VS 中的菜单栏上的 "视图" 框中，位于右上方。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-207">The target will be displayed in the view box on the menu bar in VS on the top-middle-right.</span></span>
2.  <span data-ttu-id="9b8b9-208">按 **F5**。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-208">Press **F5**.</span></span>  <span data-ttu-id="9b8b9-209">目标将生成、部署并附加到 VS 内核调试器。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-209">The target will be built, deployed, and attached to the VS Kernel Debugger.</span></span>

* <span data-ttu-id="9b8b9-210">重新启动后，请确保 PowerShell 仍连接到它，否则，请使用 PowerShell 命令重新连接到目标设备。 `enter-pssession`</span><span class="sxs-lookup"><span data-stu-id="9b8b9-210">After the reboot, make sure PowerShell is still connected to it, otherwise, reconnect to the target device using the PowerShell `enter-pssession` command..</span></span>


## <a name="known-issues"></a><span data-ttu-id="9b8b9-211">已知问题</span><span class="sxs-lookup"><span data-stu-id="9b8b9-211">Known Issues</span></span>
___

### <a name="provisioning-errors"></a><span data-ttu-id="9b8b9-212">预配错误</span><span class="sxs-lookup"><span data-stu-id="9b8b9-212">Provisioning Errors</span></span>
<span data-ttu-id="9b8b9-213">与 MinnowBoardMax 交互过程中的争用条件可能会导致在预配过程中出现报告故障。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-213">A race condition during the interaction with MinnowBoardMax can result in a reported failure during provisioning.</span></span>  <span data-ttu-id="9b8b9-214">事实上，预配可能会成功。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-214">In fact, the provisioning most likely succeeded.</span></span>

<span data-ttu-id="9b8b9-215">**错误列表：**</span><span class="sxs-lookup"><span data-stu-id="9b8b9-215">**List of Errors:**</span></span>

* <span data-ttu-id="9b8b9-216">错误：任务 "注册 WDTF" 未能成功完成。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-216">ERROR: Task "Registering WDTF" failed to complete successfully.</span></span>
* <span data-ttu-id="9b8b9-217">错误：任务 "配置内核调试器设置 (可能重新启动) " 无法成功完成</span><span class="sxs-lookup"><span data-stu-id="9b8b9-217">ERROR: Task "Configuring kernel debugger settings (possible reboot)" failed to complete successfully</span></span>

<span data-ttu-id="9b8b9-218">**解决方法：** 几乎肯定会忽略这些错误。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-218">**Workaround:** These errors can almost certainly be ignored.</span></span>

<span data-ttu-id="9b8b9-219">**详细**</span><span class="sxs-lookup"><span data-stu-id="9b8b9-219">**Details:**</span></span>

<span data-ttu-id="9b8b9-220">**设备配置配置进度**对话框中将显示以下错误：</span><span class="sxs-lookup"><span data-stu-id="9b8b9-220">The following error will be displayed in the **Device Configuration Configuration Progress** dialog:</span></span>

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

<span data-ttu-id="9b8b9-221">此时，你可以安全地单击 " **完成** "，然后单击 " **应用** **" 和 "确定"**。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-221">At this point, you can safely click on the **Finish** and then the **Apply** and **OK**.</span></span>

<span data-ttu-id="9b8b9-222">这是由争用情况形成的良性错误，导致结果日志的格式不正确。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-222">This is a benign error formed by a race condition causing a result log to be malformed.</span></span> <span data-ttu-id="9b8b9-223">可以通过查看以下区域中的日志文件来对此进行验证：</span><span class="sxs-lookup"><span data-stu-id="9b8b9-223">This can be verified by looking at the log file in the following area:</span></span>

1. <span data-ttu-id="9b8b9-224">打开到设备 IP 的 FTP 连接 (如设备屏幕上所示) 到 `Data/test/bin/DriverTest/Run` 目录。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-224">Open an FTP connection to the IP of the device (as shown on the device screen) to the `Data/test/bin/DriverTest/Run` directory.</span></span>
<span data-ttu-id="9b8b9-225">例如，`ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`</span><span class="sxs-lookup"><span data-stu-id="9b8b9-225">e.g. `ftp://<ip address of device>/Data/test/bin/DriverTest/Run/`</span></span>

2. <span data-ttu-id="9b8b9-226">将 `Configuring_computer_settings_(possible_reboot)_identifier.wtl` 文件复制到本地计算机。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-226">copy the `Configuring_computer_settings_(possible_reboot)_identifier.wtl` file to your local machine.</span></span>  <span data-ttu-id="9b8b9-227">请注意，日志文件名称与失败的任务的名称相匹配。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-227">Note that the log file name matches the name of the failing task.</span></span>
3. <span data-ttu-id="9b8b9-228">在记事本中打开文件</span><span class="sxs-lookup"><span data-stu-id="9b8b9-228">Open the file in notepad</span></span>
4. <span data-ttu-id="9b8b9-229">滚动到日志的底部。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-229">Scroll to the bottom of the log.</span></span>  <span data-ttu-id="9b8b9-230">将显示以下文本，指示预配成功。</span><span class="sxs-lookup"><span data-stu-id="9b8b9-230">The following text will be present, indicating that the provisioning is successful.</span></span>

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
