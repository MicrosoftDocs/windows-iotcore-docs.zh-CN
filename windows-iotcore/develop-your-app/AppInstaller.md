---
title: 在 IoT Core 设备上安装应用
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Windows 设备门户或 IoT core 映像的一部分来安装应用。
keywords: windows iot，应用安装，Windows 设备门户，设备
ms.openlocfilehash: 93afe3f13e5248876303a12f34e1ab2a73f510a5
ms.sourcegitcommit: ea060254f9c4c25afcd0245c897b9e1425321859
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75721640"
---
# <a name="install-your-app-on-an-iot-core-device"></a><span data-ttu-id="e5045-104">在 IoT Core 设备上安装应用</span><span class="sxs-lookup"><span data-stu-id="e5045-104">Install your app on an IoT Core device</span></span>
<span data-ttu-id="e5045-105">可以使用下面列出的两种方法之一来安装应用。</span><span class="sxs-lookup"><span data-stu-id="e5045-105">You can install your app using one of the two methods that are listed below.</span></span>

> [!NOTE]
> <span data-ttu-id="e5045-106">使用 Windows 设备门户安装应用仅适用于开发人员方案。</span><span class="sxs-lookup"><span data-stu-id="e5045-106">Installing apps using the Windows Device Portal is only for developer scenarios.</span></span>
> <span data-ttu-id="e5045-107">请创建一个预配包，或将应用添加到用于生产方案的 Windows IoT Core 映像。</span><span class="sxs-lookup"><span data-stu-id="e5045-107">Please create a provisioning package or add the app to your Windows IoT Core image for production scenarios.</span></span>

## <a name="using-windows-device-portal"></a><span data-ttu-id="e5045-108">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="e5045-108">Using Windows Device Portal</span></span>

> [!NOTE]
> <span data-ttu-id="e5045-109">需要将 .appx 或 .appxbundle 用于 Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="e5045-109">An .appx or .appxbundle is required for Windows Device Portal.</span></span> <span data-ttu-id="e5045-110">从 SDK 和工具版本17763开始，如果应用项目的最低目标版本 > 为17763或更高版本，则工具将创建[.msix 或 .msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html)。</span><span class="sxs-lookup"><span data-stu-id="e5045-110">Beginning with version 17763 of the SDK and tools if the minimum target version of the app project> is 17763 or greater the tools will create an [.msix or .msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html).</span></span>
> <span data-ttu-id="e5045-111">若要创建 .appx 或 .appxbundle，请将最低版本设置为低于17763的版本，或[直接运行 makeappx.exe](https://docs.microsoft.com/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax)。</span><span class="sxs-lookup"><span data-stu-id="e5045-111">To create an .appx or .appxbundle set the minimum version to a version less than 17763 or [run makeappx.exe directly](https://docs.microsoft.com/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax).</span></span> <span data-ttu-id="e5045-112">也可以将 .msix 重命名为 .appx，或将 .msixbundle 重命名为 .appxbundle。</span><span class="sxs-lookup"><span data-stu-id="e5045-112">It may also be possible to rename the .msix to .appx, or .msixbundle to .appxbundle.</span></span>

<span data-ttu-id="e5045-113">对于此方法，需要确保已连接到 internet。</span><span class="sxs-lookup"><span data-stu-id="e5045-113">For this method, you will need to ensure that you are connected to the internet.</span></span> <span data-ttu-id="e5045-114">如果你无权访问 internet，则还可以在设备和客户端计算机之间建立对等以太网连接，但不包括访问开放 internet 的路径。</span><span class="sxs-lookup"><span data-stu-id="e5045-114">If you do not have access to the internet, you can also have a peer-to-peer ethernet connection between the device and a client machine that doesn't include a path to access the open internet.</span></span> <span data-ttu-id="e5045-115">但是，如果不想这样做，则会安装应用程序，但如果应用程序已进行了存储签名，则无法启动。</span><span class="sxs-lookup"><span data-stu-id="e5045-115">However, going about the latter way will install the app but will fail to launch if the app is store-signed.</span></span>

<span data-ttu-id="e5045-116">若要在设备上安装应用程序，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="e5045-116">To install your application on the device please do the following:</span></span>

1. <span data-ttu-id="e5045-117">打开 IoT 设备的[Windows 设备门户](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)。</span><span class="sxs-lookup"><span data-stu-id="e5045-117">Open the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) for your IoT device.</span></span>

2. <span data-ttu-id="e5045-118">在 "**应用**" 菜单中，选择应用文件，然后单击 "**安装**" 来安装应用。</span><span class="sxs-lookup"><span data-stu-id="e5045-118">In the **Apps** menu, install your app by selecting your app files and clicking **Install**.</span></span>

3. <span data-ttu-id="e5045-119">单击 "**选择文件**"</span><span class="sxs-lookup"><span data-stu-id="e5045-119">Click **Select File**</span></span>

4. <span data-ttu-id="e5045-120">选择 .appx 文件并单击 "**打开**"</span><span class="sxs-lookup"><span data-stu-id="e5045-120">Select your .appx file and click **Open**</span></span>

5. <span data-ttu-id="e5045-121">选中 "**允许我选择框架包**"</span><span class="sxs-lookup"><span data-stu-id="e5045-121">Check **Allow me to select framework packages**</span></span>

6. <span data-ttu-id="e5045-122">单击**下一步**</span><span class="sxs-lookup"><span data-stu-id="e5045-122">Click **Next**</span></span>

7. <span data-ttu-id="e5045-123">对于 .appx 的 "**依赖项**" 文件夹中的每个项，重复步骤7.1 和7。2</span><span class="sxs-lookup"><span data-stu-id="e5045-123">For each item in the **Dependencies** folder for your .appx repeat step 7.1 and 7.2</span></span>

    <span data-ttu-id="e5045-124">7.1 单击 "**选择文件**"</span><span class="sxs-lookup"><span data-stu-id="e5045-124">7.1 Click **Choose File**</span></span>

    <span data-ttu-id="e5045-125">7.2 选择 depenency 并单击 "**打开**"</span><span class="sxs-lookup"><span data-stu-id="e5045-125">7.2 Select the depenency .appx and click **Open**</span></span>

8. <span data-ttu-id="e5045-126">添加所有依赖项后，请单击 "**安装**"</span><span class="sxs-lookup"><span data-stu-id="e5045-126">When all of the dependencies are added click **Install**</span></span>

9. <span data-ttu-id="e5045-127">等待安装完成，然后单击 "**完成**"</span><span class="sxs-lookup"><span data-stu-id="e5045-127">Wait for the install is completed and click **Done**</span></span>

 ![安装应用](../media/AppInstaller/install-app.gif)

10. <span data-ttu-id="e5045-129">现在，应用程序将显示在设备上的应用程序列表中。</span><span class="sxs-lookup"><span data-stu-id="e5045-129">The application will now be visible on the list of applications on your device.</span></span>
 <span data-ttu-id="e5045-130">![安装应用](../media/AppInstaller/install-app.gif)</span><span class="sxs-lookup"><span data-stu-id="e5045-130">![Install App](../media/AppInstaller/install-app.gif)</span></span>


## <a name="using-provisioning-package-from-wcd"></a><span data-ttu-id="e5045-131">使用 WCD 中的预配包</span><span class="sxs-lookup"><span data-stu-id="e5045-131">Using provisioning package from WCD</span></span>
<span data-ttu-id="e5045-132">你可以使用应用创建预配包，并在设备上安装预配包。</span><span class="sxs-lookup"><span data-stu-id="e5045-132">You can create a provisioning package with the app and install the provisioning package on the device.</span></span> <span data-ttu-id="e5045-133">即使是在没有连接 internet 的设备上，也可以使用此方法，这是安装存储许可证文件的首选方法。</span><span class="sxs-lookup"><span data-stu-id="e5045-133">This method works even on devices that do not have internet connection, and is the preferred method for installing the store license file.</span></span> <span data-ttu-id="e5045-134">例如，这可以启用工厂方案，其中设备未连接到 internet，但主应用是应用商店签名的 UWP 应用。</span><span class="sxs-lookup"><span data-stu-id="e5045-134">For example, this enables factory scenarios where the device is not connected to the internet but the primary app is a store-signed UWP app.</span></span>

> [!NOTE]
> <span data-ttu-id="e5045-135">包系列名称（PFN）可在 Windows 开发人员中心中的 "应用管理" 下找到 **> 应用标识**</span><span class="sxs-lookup"><span data-stu-id="e5045-135">The Package Family Name (PFN) can be found in the Windows Dev Center under **App Management > App Identity**</span></span>

1. <span data-ttu-id="e5045-136">打开[Windows 配置设计器（WICD）](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span><span class="sxs-lookup"><span data-stu-id="e5045-136">Open [Windows Configuration Designer (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span></span>

2. <span data-ttu-id="e5045-137">选择 "**高级设置**"，输入项目名称和说明</span><span class="sxs-lookup"><span data-stu-id="e5045-137">Select **Advanced Provisioning**, Enter the project name and a description</span></span>

3. <span data-ttu-id="e5045-138">为项目设置选择 Windows 10 IoT Core，并跳过预配包导入</span><span class="sxs-lookup"><span data-stu-id="e5045-138">Choose Windows 10 IoT Core for the project settings and skip the provisioning package import</span></span>

4. <span data-ttu-id="e5045-139">在左侧展开 "**运行时设置**"，然后单击 "**通用应用安装 > 用户上下文应用**</span><span class="sxs-lookup"><span data-stu-id="e5045-139">On the left hand side expand **Runtime Settings** and click on **Universal App Install > User Context App**</span></span>

5. <span data-ttu-id="e5045-140">输入应用的包系列名称，并单击 "**添加**"</span><span class="sxs-lookup"><span data-stu-id="e5045-140">Enter the Package Family Name of your app and click **Add**</span></span>

6. <span data-ttu-id="e5045-141">在新添加的 PFN 下</span><span class="sxs-lookup"><span data-stu-id="e5045-141">Under the newly added PFN</span></span>
    - <span data-ttu-id="e5045-142">添加 Appx 及其依赖项</span><span class="sxs-lookup"><span data-stu-id="e5045-142">add the Appx and its dependencies</span></span>
    - <span data-ttu-id="e5045-143">将 d 设置为 "强制关闭目标应用程序"</span><span class="sxs-lookup"><span data-stu-id="e5045-143">set the DeploymentOptions to "Force target application shutdown"</span></span>

7. <span data-ttu-id="e5045-144">对于应用商店签名应用，需要指定许可证。</span><span class="sxs-lookup"><span data-stu-id="e5045-144">For Store signed apps, you will need to specify the license.</span></span> <span data-ttu-id="e5045-145">在 UserContextAppLicense 下，</span><span class="sxs-lookup"><span data-stu-id="e5045-145">Under UserContextAppLicense,</span></span>
    - <span data-ttu-id="e5045-146">添加 LicenseProductID （可用于许可证 XML 文件中的 LicenseID）</span><span class="sxs-lookup"><span data-stu-id="e5045-146">add LicenseProductID (available as LicenseID in the license XML file)</span></span>
    - <span data-ttu-id="e5045-147">将许可证 xml 扩展更改为 " *ms-windows-应用商店-许可证*"。</span><span class="sxs-lookup"><span data-stu-id="e5045-147">change the license xml extension to *.ms-windows-store-license*.</span></span>
    - <span data-ttu-id="e5045-148">选择左侧的许可证产品 ID，并浏览许可证文件以分配 LicenseInstall 字段</span><span class="sxs-lookup"><span data-stu-id="e5045-148">select your License Product ID on the left hand side and browse your license file to assign LicenseInstall field</span></span>

8. <span data-ttu-id="e5045-149">对于非应用商店签名应用，需要在 "**证书 > RootCertificates** " 下添加 app.config 文件。</span><span class="sxs-lookup"><span data-stu-id="e5045-149">For non-store signed apps, you will need to add the app.cer file under **Certificates > RootCertificates**</span></span> 

9. <span data-ttu-id="e5045-150">导出包</span><span class="sxs-lookup"><span data-stu-id="e5045-150">Export the package</span></span>

10. <span data-ttu-id="e5045-151">使用[SSH](../connect-your-device/SSH.md)或[Powershell](../connect-your-device/powershell.md)将导出的 Ppkg 文件复制到 IoT 设备上的_C:\Windows\Provisioning\Packages_ ，然后重新启动。</span><span class="sxs-lookup"><span data-stu-id="e5045-151">Copy the exported .ppkg file to _C:\Windows\Provisioning\Packages_ on the IoT device using [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/powershell.md)) and reboot.</span></span> <span data-ttu-id="e5045-152">当设备重新启动时，将处理预配包，并安装应用程序。</span><span class="sxs-lookup"><span data-stu-id="e5045-152">When the device reboots, the provisioning package is processed and the app is installed.</span></span>


## <a name="add-the-app-to-the-windows-iot-core-imageffu"></a><span data-ttu-id="e5045-153">将应用添加到 Windows IoT Core 映像（. ffu）</span><span class="sxs-lookup"><span data-stu-id="e5045-153">Add the app to the Windows IoT Core image(.ffu)</span></span>
<span data-ttu-id="e5045-154">你可以将该应用添加为 Windows IoT Core 映像自身的一部分。</span><span class="sxs-lookup"><span data-stu-id="e5045-154">You can add the app to be part of the Windows IoT Core image itself.</span></span>
<span data-ttu-id="e5045-155">这是 Oem 在其设备上安装应用程序的首选方法。</span><span class="sxs-lookup"><span data-stu-id="e5045-155">This is the preferred method for OEMs to install apps on their devices.</span></span>

<span data-ttu-id="e5045-156">请参阅如何[将应用添加到映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)和[示例应用程序包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp)。</span><span class="sxs-lookup"><span data-stu-id="e5045-156">See how to [add an app to your image](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) and a [sample app package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).</span></span>
