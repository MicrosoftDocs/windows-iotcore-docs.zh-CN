---
title: 在 IoT Core 设备上安装您的应用程序
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Windows Device Portal 将应用安装或作为一部分 IoT core 映像。
keywords: windows iot，应用程序安装，Windows Device Portal 设备
ms.openlocfilehash: 23df6bec04395eb31f066eb3befc84a4ff4bbe56
ms.sourcegitcommit: 5a103405cbc5c61101139aff6aaa709bd4ef9582
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694153"
---
# <a name="install-your-app-on-an-iot-core-device"></a><span data-ttu-id="ca0fd-104">在 IoT Core 设备上安装您的应用程序</span><span class="sxs-lookup"><span data-stu-id="ca0fd-104">Install your app on an IoT Core device</span></span>
<span data-ttu-id="ca0fd-105">你可以安装应用程序使用下面列出了两种方法之一。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-105">You can install your app using one of the two methods that are listed below.</span></span>

> [!NOTE]
> <span data-ttu-id="ca0fd-106">通过 Windows Device Portal 安装应用程序仅适用于开发人员方案。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-106">Installing apps using the Windows Device Portal is only for developer scenarios.</span></span>
> <span data-ttu-id="ca0fd-107">请创建预配包，或将应用添加到 Windows IoT Core 映像对于生产方案。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-107">Please create a provisioning package or add the app to your Windows IoT Core image for production scenarios.</span></span>

## <a name="using-windows-device-portal"></a><span data-ttu-id="ca0fd-108">使用 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="ca0fd-108">Using Windows Device Portal</span></span>

> [!NOTE]
> <span data-ttu-id="ca0fd-109">需要 Windows Device Portal.appx 或.appxbundle。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-109">An .appx or .appxbundle is required for Windows Device Portal.</span></span> <span data-ttu-id="ca0fd-110">如果所需的最低目标版本的应用程序项目版本的 SDK 和工具 17763 开始 > 17763 或更高版本工具将创建[.msix 或.msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html)。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-110">Beginning with version 17763 of the SDK and tools if the minimum target version of the app project> is 17763 or greater the tools will create an [.msix or .msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html).</span></span>
> <span data-ttu-id="ca0fd-111">若要创建的最低版本为版本低于 17763 的.appx 或.appxbundle 集或[直接运行 makeappx.exe](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax)。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-111">To create an .appx or .appxbundle set the minimum version to a version less than 17763 or [run makeappx.exe directly](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax).</span></span> <span data-ttu-id="ca0fd-112">它还可以重命名为.appx 或.appxbundle 的.msixbundle.msix。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-112">It may also be possible to rename the .msix to .appx, or .msixbundle to .appxbundle.</span></span>

<span data-ttu-id="ca0fd-113">对于此方法，需要确保已连接到 internet。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-113">For this method, you will need to ensure that you are connected to the internet.</span></span> <span data-ttu-id="ca0fd-114">如果还没有 internet 访问权限，还可以在设备和不包括路径访问开放 internet 的客户端计算机之间的对等以太网连接。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-114">If you do not have access to the internet, you can also have a peer-to-peer ethernet connection between the device and a client machine that doesn't include a path to access the open internet.</span></span> <span data-ttu-id="ca0fd-115">但是，看后一种方式将安装应用，将无法启动，如果应用是应用商店签名。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-115">However, going about the latter way will install the app but will fail to launch if the app is store-signed.</span></span>

<span data-ttu-id="ca0fd-116">若要安装在设备上的应用程序请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="ca0fd-116">To install your application on the device please do the following:</span></span>

1. <span data-ttu-id="ca0fd-117">打开[Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-117">Open the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) for your IoT device.</span></span>

2. <span data-ttu-id="ca0fd-118">在中**应用程序**菜单中，选择你的应用程序文件并单击安装您的应用程序**安装**。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-118">In the **Apps** menu, install your app by selecting your app files and clicking **Install**.</span></span>

3. <span data-ttu-id="ca0fd-119">单击**选择文件**</span><span class="sxs-lookup"><span data-stu-id="ca0fd-119">Click **Select File**</span></span>

4. <span data-ttu-id="ca0fd-120">选择您的.appx 文件，然后单击**打开**</span><span class="sxs-lookup"><span data-stu-id="ca0fd-120">Select your .appx file and click **Open**</span></span>

5. <span data-ttu-id="ca0fd-121">检查**允许我选择 framework 包**</span><span class="sxs-lookup"><span data-stu-id="ca0fd-121">Check **Allow me to select framework packages**</span></span>

6. <span data-ttu-id="ca0fd-122">单击“下一步” </span><span class="sxs-lookup"><span data-stu-id="ca0fd-122">Click **Next**</span></span>

7. <span data-ttu-id="ca0fd-123">中每一项**依赖项**文件夹为.appx 重复步骤 7.1 和 7.2</span><span class="sxs-lookup"><span data-stu-id="ca0fd-123">For each item in the **Dependencies** folder for your .appx repeat step 7.1 and 7.2</span></span>

    <span data-ttu-id="ca0fd-124">7.1 单击**选择文件**</span><span class="sxs-lookup"><span data-stu-id="ca0fd-124">7.1 Click **Choose File**</span></span>

    <span data-ttu-id="ca0fd-125">7.2 选择 depenency.appx，然后单击**打开**</span><span class="sxs-lookup"><span data-stu-id="ca0fd-125">7.2 Select the depenency .appx and click **Open**</span></span>

8. <span data-ttu-id="ca0fd-126">在所有依赖项添加单击时**安装**</span><span class="sxs-lookup"><span data-stu-id="ca0fd-126">When all of the dependencies are added click **Install**</span></span>

9. <span data-ttu-id="ca0fd-127">等待安装完成，然后单击**完成**</span><span class="sxs-lookup"><span data-stu-id="ca0fd-127">Wait for the install is completed and click **Done**</span></span>

 ![安装应用](../media/AppInstaller/install-app.gif)

10. <span data-ttu-id="ca0fd-129">该应用程序现在将你的设备上的应用程序列表中可见。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-129">The application will now be visible on the list of applications on your device.</span></span>
 <span data-ttu-id="ca0fd-130">![安装应用](../media/AppInstaller/install-app.gif)</span><span class="sxs-lookup"><span data-stu-id="ca0fd-130">![Install App](../media/AppInstaller/install-app.gif)</span></span>


## <a name="using-provisioning-package-from-wcd"></a><span data-ttu-id="ca0fd-131">使用从 WCD 预配包</span><span class="sxs-lookup"><span data-stu-id="ca0fd-131">Using provisioning package from WCD</span></span>
<span data-ttu-id="ca0fd-132">可以使用应用创建预配包，并在设备上安装预配包。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-132">You can create a provisioning package with the app and install the provisioning package on the device.</span></span> <span data-ttu-id="ca0fd-133">此方法甚至没有 internet 连接的设备上运行，并且是用于安装应用商店的许可证文件的首选的方法。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-133">This method works even on devices that do not have internet connection, and is the preferred method for installing the store license file.</span></span> <span data-ttu-id="ca0fd-134">例如，这样，在设备未连接到 internet 但主应用程序已签名应用商店的 UWP 应用的工厂方案。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-134">For example, this enables factory scenarios where the device is not connected to the internet but the primary app is a store-signed UWP app.</span></span>

> [!NOTE]
> <span data-ttu-id="ca0fd-135">包系列名称 (PFN) 可以位于下在 Windows 开发人员中心**应用管理 > 应用程序标识**</span><span class="sxs-lookup"><span data-stu-id="ca0fd-135">The Package Family Name (PFN) can be found in the Windows Dev Center under **App Management > App Identity**</span></span>

1. <span data-ttu-id="ca0fd-136">打开[Windows 配置设计器 (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span><span class="sxs-lookup"><span data-stu-id="ca0fd-136">Open [Windows Configuration Designer (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span></span>

2. <span data-ttu-id="ca0fd-137">选择**高级预配**，输入项目名称和描述</span><span class="sxs-lookup"><span data-stu-id="ca0fd-137">Select **Advanced Provisioning**, Enter the project name and a description</span></span>

3. <span data-ttu-id="ca0fd-138">为项目设置中选择 Windows 10 IoT 核心版和跳过预配包导入</span><span class="sxs-lookup"><span data-stu-id="ca0fd-138">Choose Windows 10 IoT Core for the project settings and skip the provisioning package import</span></span>

4. <span data-ttu-id="ca0fd-139">在左侧依次展开**运行时设置**，然后单击**通用应用安装 > 用户上下文应用**</span><span class="sxs-lookup"><span data-stu-id="ca0fd-139">On the left hand side expand **Runtime Settings** and click on **Universal App Install > User Context App**</span></span>

5. <span data-ttu-id="ca0fd-140">输入包系列名称的应用程序并单击**添加**</span><span class="sxs-lookup"><span data-stu-id="ca0fd-140">Enter the Package Family Name of your app and click **Add**</span></span>

6. <span data-ttu-id="ca0fd-141">在新添加的 PFN</span><span class="sxs-lookup"><span data-stu-id="ca0fd-141">Under the newly added PFN</span></span>
    - <span data-ttu-id="ca0fd-142">添加 Appx 和其依赖项</span><span class="sxs-lookup"><span data-stu-id="ca0fd-142">add the Appx and its dependencies</span></span>
    - <span data-ttu-id="ca0fd-143">设置为"强制目标应用程序关闭"DeploymentOptions</span><span class="sxs-lookup"><span data-stu-id="ca0fd-143">set the DeploymentOptions to "Force target application shutdown"</span></span>

7. <span data-ttu-id="ca0fd-144">对于存储已签名的应用，需要指定许可证。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-144">For Store signed apps, you will need to specify the license.</span></span> <span data-ttu-id="ca0fd-145">下 UserContextAppLicense，</span><span class="sxs-lookup"><span data-stu-id="ca0fd-145">Under UserContextAppLicense,</span></span>
    - <span data-ttu-id="ca0fd-146">添加 LicenseProductID （可用作 LicenseID 许可证 XML 文件中）</span><span class="sxs-lookup"><span data-stu-id="ca0fd-146">add LicenseProductID (available as LicenseID in the license XML file)</span></span>
    - <span data-ttu-id="ca0fd-147">将许可证 xml 扩展名更改为 *.ms windows 应用商店许可*。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-147">change the license xml extension to *.ms-windows-store-license*.</span></span>
    - <span data-ttu-id="ca0fd-148">选择您的左侧上的许可证产品 ID 并浏览您的许可证文件来分配 LicenseInstall 字段</span><span class="sxs-lookup"><span data-stu-id="ca0fd-148">select your License Product ID on the left hand side and browse your license file to assign LicenseInstall field</span></span>

8. <span data-ttu-id="ca0fd-149">对于非应用商店已签名应用程序，您需要添加下的 app.cer 文件**证书 > RootCertificates**</span><span class="sxs-lookup"><span data-stu-id="ca0fd-149">For non-store signed apps, you will need to add the app.cer file under **Certificates > RootCertificates**</span></span> 

9. <span data-ttu-id="ca0fd-150">导出包</span><span class="sxs-lookup"><span data-stu-id="ca0fd-150">Export the package</span></span>

10. <span data-ttu-id="ca0fd-151">将导出的.ppkg 文件复制到_C:\Windows\Provisioning\Packages_ IoT 设备使用[SSH](../connect-your-device/SSH.md)或[Powershell](../connect-your-device/powershell.md)) 并重新启动。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-151">Copy the exported .ppkg file to _C:\Windows\Provisioning\Packages_ on the IoT device using [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/powershell.md)) and reboot.</span></span> <span data-ttu-id="ca0fd-152">当设备重新启动时，处理预配包和安装应用。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-152">When the device reboots, the provisioning package is processed and the app is installed.</span></span>


## <a name="add-the-app-to-the-windows-iot-core-imageffu"></a><span data-ttu-id="ca0fd-153">将应用添加到 Windows IoT Core image(.ffu)</span><span class="sxs-lookup"><span data-stu-id="ca0fd-153">Add the app to the Windows IoT Core image(.ffu)</span></span>
<span data-ttu-id="ca0fd-154">您可以添加该应用程序 Windows IoT Core 映像本身的一部分。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-154">You can add the app to be part of the Windows IoT Core image itself.</span></span>
<span data-ttu-id="ca0fd-155">这是 Oem 可以在其设备上安装应用的首选的方法。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-155">This is the preferred method for OEMs to install apps on their devices.</span></span>

<span data-ttu-id="ca0fd-156">请参阅如何[将应用添加到你的映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)和一个[示例应用包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp)。</span><span class="sxs-lookup"><span data-stu-id="ca0fd-156">See how to [add an app to your image](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) and a [sample app package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).</span></span>
