---
title: 在 IoT Core 设备上安装应用
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 IoT 核心映像Windows 设备门户安装应用。
keywords: windows iot， 应用安装， Windows 设备门户， 设备
ms.openlocfilehash: ac0aed3e7f6f1eb630a0fda106133645fd01a1e1
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229874"
---
# <a name="install-your-app-on-an-iot-core-device"></a><span data-ttu-id="48df2-104">在 IoT Core 设备上安装应用</span><span class="sxs-lookup"><span data-stu-id="48df2-104">Install your app on an IoT Core device</span></span>
<span data-ttu-id="48df2-105">可以使用下面列出的两种方法之一安装应用。</span><span class="sxs-lookup"><span data-stu-id="48df2-105">You can install your app using one of the two methods that are listed below.</span></span>

> [!NOTE]
> <span data-ttu-id="48df2-106">使用应用程序安装Windows 设备门户仅适用于开发人员方案。</span><span class="sxs-lookup"><span data-stu-id="48df2-106">Installing apps using the Windows Device Portal is only for developer scenarios.</span></span>
> <span data-ttu-id="48df2-107">请为生产方案创建预配包或将Windows IoT 核心映像。</span><span class="sxs-lookup"><span data-stu-id="48df2-107">Please create a provisioning package or add the app to your Windows IoT Core image for production scenarios.</span></span>

## <a name="using-windows-device-portal"></a><span data-ttu-id="48df2-108">使用 Windows 设备门户</span><span class="sxs-lookup"><span data-stu-id="48df2-108">Using Windows Device Portal</span></span>

> [!NOTE]
> <span data-ttu-id="48df2-109">需要 .appx 或 .appxbundle 才能Windows 设备门户。</span><span class="sxs-lookup"><span data-stu-id="48df2-109">An .appx or .appxbundle is required for Windows Device Portal.</span></span> <span data-ttu-id="48df2-110">从 SDK 和工具版本 17763 开始，如果应用项目的最低目标版本> 为 17763 或更大，则工具将创建 [.msix 或 .msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html)。</span><span class="sxs-lookup"><span data-stu-id="48df2-110">Beginning with version 17763 of the SDK and tools if the minimum target version of the app project> is 17763 or greater the tools will create an [.msix or .msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html).</span></span>
> <span data-ttu-id="48df2-111">若要创建 .appx 或 .appxbundle，将最低版本设置为低于 17763 的版本，或直接makeappx.exe [运行](https://docs.microsoft.com/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax)。</span><span class="sxs-lookup"><span data-stu-id="48df2-111">To create an .appx or .appxbundle set the minimum version to a version less than 17763 or [run makeappx.exe directly](https://docs.microsoft.com/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax).</span></span> <span data-ttu-id="48df2-112">还可以将 .msix 重命名为 .appx，或将 .msixbundle 重命名为 .appxbundle。</span><span class="sxs-lookup"><span data-stu-id="48df2-112">It may also be possible to rename the .msix to .appx, or .msixbundle to .appxbundle.</span></span>

<span data-ttu-id="48df2-113">对于此方法，需要确保已连接到 Internet。</span><span class="sxs-lookup"><span data-stu-id="48df2-113">For this method, you will need to ensure that you are connected to the internet.</span></span> <span data-ttu-id="48df2-114">如果无法访问 Internet，则还可以在设备和不包含用于访问开放 Internet 的路径的客户端计算机之间建立对等以太网连接。</span><span class="sxs-lookup"><span data-stu-id="48df2-114">If you do not have access to the internet, you can also have a peer-to-peer ethernet connection between the device and a client machine that doesn't include a path to access the open internet.</span></span> <span data-ttu-id="48df2-115">但是，使用后一种方法将安装应用，但如果应用已进行存储签名，将无法启动。</span><span class="sxs-lookup"><span data-stu-id="48df2-115">However, going about the latter way will install the app but will fail to launch if the app is store-signed.</span></span>

<span data-ttu-id="48df2-116">若要在设备上安装应用程序，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="48df2-116">To install your application on the device please do the following:</span></span>

1. <span data-ttu-id="48df2-117">打开[Windows 设备门户](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)IoT 设备的信息。</span><span class="sxs-lookup"><span data-stu-id="48df2-117">Open the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) for your IoT device.</span></span>

2. <span data-ttu-id="48df2-118">在" **应用"** 菜单中，通过选择应用文件并单击"安装"来 **安装应用**。</span><span class="sxs-lookup"><span data-stu-id="48df2-118">In the **Apps** menu, install your app by selecting your app files and clicking **Install**.</span></span>

3. <span data-ttu-id="48df2-119">单击" **选择文件"**</span><span class="sxs-lookup"><span data-stu-id="48df2-119">Click **Select File**</span></span>

4. <span data-ttu-id="48df2-120">选择 .appx 文件，然后单击"打开 **"**</span><span class="sxs-lookup"><span data-stu-id="48df2-120">Select your .appx file and click **Open**</span></span>

5. <span data-ttu-id="48df2-121">选中 **"允许我选择框架包"**</span><span class="sxs-lookup"><span data-stu-id="48df2-121">Check **Allow me to select framework packages**</span></span>

6. <span data-ttu-id="48df2-122">点击“下一步” </span><span class="sxs-lookup"><span data-stu-id="48df2-122">Click **Next**</span></span>

7. <span data-ttu-id="48df2-123">对于 .appx **的 Dependencies** 文件夹中的每个项，重复步骤 7.1 和 7.2</span><span class="sxs-lookup"><span data-stu-id="48df2-123">For each item in the **Dependencies** folder for your .appx repeat step 7.1 and 7.2</span></span>

    <span data-ttu-id="48df2-124">7.1 单击" **选择文件"**</span><span class="sxs-lookup"><span data-stu-id="48df2-124">7.1 Click **Choose File**</span></span>

    <span data-ttu-id="48df2-125">7.2 选择依赖项 .appx，然后单击"打开 **"**</span><span class="sxs-lookup"><span data-stu-id="48df2-125">7.2 Select the dependency .appx and click **Open**</span></span>

8. <span data-ttu-id="48df2-126">添加所有依赖项后，单击"安装 **"**</span><span class="sxs-lookup"><span data-stu-id="48df2-126">When all of the dependencies are added click **Install**</span></span>

9. <span data-ttu-id="48df2-127">等待安装完成，然后单击"完成 **"**</span><span class="sxs-lookup"><span data-stu-id="48df2-127">Wait for the install is completed and click **Done**</span></span>

 ![安装应用](../media/AppInstaller/install-app.gif)

10. <span data-ttu-id="48df2-129">应用程序现在将在设备上的应用程序列表中可见。</span><span class="sxs-lookup"><span data-stu-id="48df2-129">The application will now be visible on the list of applications on your device.</span></span>
 <span data-ttu-id="48df2-130">![安装应用](../media/AppInstaller/install-app.gif)</span><span class="sxs-lookup"><span data-stu-id="48df2-130">![Install App](../media/AppInstaller/install-app.gif)</span></span>


## <a name="using-provisioning-package-from-wcd"></a><span data-ttu-id="48df2-131">使用 WCD 中的预配包</span><span class="sxs-lookup"><span data-stu-id="48df2-131">Using provisioning package from WCD</span></span>
<span data-ttu-id="48df2-132">可以使用应用创建预配包，在设备上安装预配包。</span><span class="sxs-lookup"><span data-stu-id="48df2-132">You can create a provisioning package with the app and install the provisioning package on the device.</span></span> <span data-ttu-id="48df2-133">此方法即使在没有 Internet 连接的设备上也有效，是安装应用商店许可证文件的首选方法。</span><span class="sxs-lookup"><span data-stu-id="48df2-133">This method works even on devices that do not have internet connection, and is the preferred method for installing the store license file.</span></span> <span data-ttu-id="48df2-134">例如，这样可以实现工厂方案：设备未连接到 Internet，但主应用是商店签名的 UWP 应用。</span><span class="sxs-lookup"><span data-stu-id="48df2-134">For example, this enables factory scenarios where the device is not connected to the internet but the primary app is a store-signed UWP app.</span></span>

> [!NOTE]
> <span data-ttu-id="48df2-135">"包系列名称 (PFN) 位于"应用管理"Windows 开发人员中心应用标识>**中**</span><span class="sxs-lookup"><span data-stu-id="48df2-135">The Package Family Name (PFN) can be found in the Windows Dev Center under **App Management > App Identity**</span></span>

1. <span data-ttu-id="48df2-136">打开[Windows 配置设计器 (WICD) ](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span><span class="sxs-lookup"><span data-stu-id="48df2-136">Open [Windows Configuration Designer (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span></span>

2. <span data-ttu-id="48df2-137">选择 **"高级预配"，** 输入项目名称和说明</span><span class="sxs-lookup"><span data-stu-id="48df2-137">Select **Advanced Provisioning**, Enter the project name and a description</span></span>

3. <span data-ttu-id="48df2-138">选择Windows 10 IoT 核心版设置"，并跳过预配包导入</span><span class="sxs-lookup"><span data-stu-id="48df2-138">Choose Windows 10 IoT Core for the project settings and skip the provisioning package import</span></span>

4. <span data-ttu-id="48df2-139">在左侧，展开"运行时"设置 **然后单击"** 通用 **应用安装>用户上下文应用"**</span><span class="sxs-lookup"><span data-stu-id="48df2-139">On the left hand side, expand **Runtime Settings** and click on **Universal App Install > User Context App**</span></span>

5. <span data-ttu-id="48df2-140">输入应用的包系列名称，然后单击"添加 **"**</span><span class="sxs-lookup"><span data-stu-id="48df2-140">Enter the Package Family Name of your app and click **Add**</span></span>

6. <span data-ttu-id="48df2-141">在新添加的 PFN 下</span><span class="sxs-lookup"><span data-stu-id="48df2-141">Under the newly added PFN</span></span>
    - <span data-ttu-id="48df2-142">添加 Appx 及其依赖项</span><span class="sxs-lookup"><span data-stu-id="48df2-142">add the Appx and its dependencies</span></span>
    - <span data-ttu-id="48df2-143">将 DeploymentOptions 设置为"强制目标应用程序关闭"</span><span class="sxs-lookup"><span data-stu-id="48df2-143">set the DeploymentOptions to "Force target application shutdown"</span></span>

7. <span data-ttu-id="48df2-144">对于应用商店签名的应用，需要指定许可证。</span><span class="sxs-lookup"><span data-stu-id="48df2-144">For Store signed apps, you will need to specify the license.</span></span> <span data-ttu-id="48df2-145">在 UserContextAppLicense 下，</span><span class="sxs-lookup"><span data-stu-id="48df2-145">Under UserContextAppLicense,</span></span>
    - <span data-ttu-id="48df2-146">在许可证 XML (中添加 LicenseProductID) </span><span class="sxs-lookup"><span data-stu-id="48df2-146">add LicenseProductID (available as LicenseID in the license XML file)</span></span>
    - <span data-ttu-id="48df2-147">将许可证 xml 扩展更改为 *.ms-windows-store-license*。</span><span class="sxs-lookup"><span data-stu-id="48df2-147">change the license xml extension to *.ms-windows-store-license*.</span></span>
    - <span data-ttu-id="48df2-148">选择左侧的"许可证产品 ID"，并浏览许可证文件以分配 LicenseInstall 字段</span><span class="sxs-lookup"><span data-stu-id="48df2-148">select your License Product ID on the left hand side and browse your license file to assign LicenseInstall field</span></span>

8. <span data-ttu-id="48df2-149">对于未存储签名的应用，需要在"证书""证书""根证书"下 **> app.cer 文件**</span><span class="sxs-lookup"><span data-stu-id="48df2-149">For non-store signed apps, you will need to add the app.cer file under **Certificates > RootCertificates**</span></span> 

9. <span data-ttu-id="48df2-150">导出包</span><span class="sxs-lookup"><span data-stu-id="48df2-150">Export the package</span></span>

10. <span data-ttu-id="48df2-151">使用 [SSH](../connect-your-device/SSH.md)或 [PowerShell](../connect-your-device/powershell.md)将导出的 .ppkg 文件复制到 IoT 设备上 _C：\Windows\Provisioning\Packages，_ 然后) 重启。</span><span class="sxs-lookup"><span data-stu-id="48df2-151">Copy the exported .ppkg file to _C:\Windows\Provisioning\Packages_ on the IoT device using [SSH](../connect-your-device/SSH.md) or [PowerShell](../connect-your-device/powershell.md)) and reboot.</span></span> <span data-ttu-id="48df2-152">设备重新启动时，将处理预配包并安装应用。</span><span class="sxs-lookup"><span data-stu-id="48df2-152">When the device reboots, the provisioning package is processed and the app is installed.</span></span>


## <a name="add-the-app-to-the-windows-iot-core-imageffu"></a><span data-ttu-id="48df2-153">将应用添加到 ioT 核心Windows映像 (.ffu) </span><span class="sxs-lookup"><span data-stu-id="48df2-153">Add the app to the Windows IoT Core image(.ffu)</span></span>
<span data-ttu-id="48df2-154">可以将应用添加为 IoT 核心Windows的一部分。</span><span class="sxs-lookup"><span data-stu-id="48df2-154">You can add the app to be part of the Windows IoT Core image itself.</span></span>
<span data-ttu-id="48df2-155">这是 OEM 在设备上安装应用的首选方法。</span><span class="sxs-lookup"><span data-stu-id="48df2-155">This is the preferred method for OEMs to install apps on their devices.</span></span>

<span data-ttu-id="48df2-156">了解如何将 [应用添加到映像和](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) 示例 [应用包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp)。</span><span class="sxs-lookup"><span data-stu-id="48df2-156">See how to [add an app to your image](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) and a [sample app package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).</span></span>
