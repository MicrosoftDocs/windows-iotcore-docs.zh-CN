---
title: 在 IoT Core 设备上安装您的应用程序
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Windows Device Portal 将应用安装或作为一部分 IoT core 映像。
keywords: windows iot，应用程序安装，Windows Device Portal 设备
ms.openlocfilehash: 6e188eaef6551548c6c71ac50859516d4cbe7e9c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510801"
---
# <a name="install-your-app-on-an-iot-core-device"></a><span data-ttu-id="6e4ea-104">在 IoT Core 设备上安装您的应用程序</span><span class="sxs-lookup"><span data-stu-id="6e4ea-104">Install your app on an IoT Core device</span></span>
<span data-ttu-id="6e4ea-105">你可以安装应用程序使用下面列出了两种方法之一。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-105">You can install your app using one of the two methods that are listed below.</span></span>

> [!NOTE]
> <span data-ttu-id="6e4ea-106">使用 Windows Device Portal 方法仅适用于开发人员方案。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-106">The method using the Windows Device Portal is only for developer scenarios.</span></span> <span data-ttu-id="6e4ea-107">其他两种方法适用于生产方案。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-107">The other two methods are for production scenarios.</span></span>

## <a name="using-windows-device-portal"></a><span data-ttu-id="6e4ea-108">使用 Windows Device Portal</span><span class="sxs-lookup"><span data-stu-id="6e4ea-108">Using Windows Device Portal</span></span>

<span data-ttu-id="6e4ea-109">对于此方法，需要确保已连接到 internet。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-109">For this method, you will need to ensure that you are connected to the internet.</span></span> <span data-ttu-id="6e4ea-110">如果还没有 internet 访问权限，还可以在设备和不包括路径访问开放 internet 的客户端计算机之间的对等以太网连接。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-110">If you do not have access to the internet, you can also have a peer-to-peer ethernet connection between the device and a client machine that doesn't include a path to access the open internet.</span></span> <span data-ttu-id="6e4ea-111">但是，看后一种方式将安装应用，将无法启动，如果应用是应用商店签名。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-111">However, going about the latter way will install the app but will fail to launch if the app is store-signed.</span></span>

<span data-ttu-id="6e4ea-112">若要安装在设备上的应用程序请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="6e4ea-112">To install your application on the device please do the following:</span></span>

1. <span data-ttu-id="6e4ea-113">打开[Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-113">Open the [Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) for your IoT device.</span></span>

2. <span data-ttu-id="6e4ea-114">在中*应用*菜单中，通过上传应用包安装您的应用程序。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-114">In the *Apps* menu, install your app by uploading the app package.</span></span>
 ![安装应用](../media/AppInstaller/install-app.gif)

3. <span data-ttu-id="6e4ea-116">将应用部署。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-116">Deploy the app.</span></span>

4. <span data-ttu-id="6e4ea-117">该应用程序现在将你的设备上的应用程序列表中可见。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-117">The application will now be visible on the list of applications on your device.</span></span>
 ![应用列表](../media/AppInstaller/AppList.png)


## <a name="using-provisioning-package-from-wcd"></a><span data-ttu-id="6e4ea-119">使用从 WCD 预配包</span><span class="sxs-lookup"><span data-stu-id="6e4ea-119">Using provisioning package from WCD</span></span>
<span data-ttu-id="6e4ea-120">可以使用应用创建预配包，并在设备上安装预配包。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-120">You can create a provisioning package with the app and install the provisioning package on the device.</span></span> <span data-ttu-id="6e4ea-121">此方法甚至没有 internet 连接的设备上运行，并且是用于安装应用商店的许可证文件的首选的方法。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-121">This method works even on devices that do not have internet connection, and is the preferred method for installing the store license file.</span></span> <span data-ttu-id="6e4ea-122">例如，这样，在设备未连接到 internet 但主应用程序已签名应用商店的 UWP 应用的工厂方案。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-122">For example, this enables factory scenarios where the device is not connected to the internet but the primary app is a store-signed UWP app.</span></span>

> [!NOTE]
> <span data-ttu-id="6e4ea-123">包系列名称 (PFN) 可以位于下在 Windows 开发人员中心**应用管理 > 应用程序标识**</span><span class="sxs-lookup"><span data-stu-id="6e4ea-123">The Package Family Name (PFN) can be found in the Windows Dev Center under **App Management > App Identity**</span></span>

1. <span data-ttu-id="6e4ea-124">打开[Windows 配置设计器 (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span><span class="sxs-lookup"><span data-stu-id="6e4ea-124">Open [Windows Configuration Designer (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)</span></span>

2. <span data-ttu-id="6e4ea-125">选择**高级预配**，输入项目名称和描述</span><span class="sxs-lookup"><span data-stu-id="6e4ea-125">Select **Advanced Provisioning**, Enter the project name and a description</span></span>

3. <span data-ttu-id="6e4ea-126">为项目设置中选择 Windows 10 IoT 核心版和跳过预配包导入</span><span class="sxs-lookup"><span data-stu-id="6e4ea-126">Choose Windows 10 IoT Core for the project settings and skip the provisioning package import</span></span>

4. <span data-ttu-id="6e4ea-127">在左侧依次展开**运行时设置**，然后单击**通用应用安装 > 用户上下文应用**</span><span class="sxs-lookup"><span data-stu-id="6e4ea-127">On the left hand side expand **Runtime Settings** and click on **Universal App Install > User Context App**</span></span>

5. <span data-ttu-id="6e4ea-128">输入包系列名称的应用程序并单击**添加**</span><span class="sxs-lookup"><span data-stu-id="6e4ea-128">Enter the Package Family Name of your app and click **Add**</span></span>

6. <span data-ttu-id="6e4ea-129">在新添加的 PFN</span><span class="sxs-lookup"><span data-stu-id="6e4ea-129">Under the newly added PFN</span></span>
    - <span data-ttu-id="6e4ea-130">添加 Appx 和其依赖项</span><span class="sxs-lookup"><span data-stu-id="6e4ea-130">add the Appx and its dependencies</span></span>
    - <span data-ttu-id="6e4ea-131">设置为"强制目标应用程序关闭"DeploymentOptions</span><span class="sxs-lookup"><span data-stu-id="6e4ea-131">set the DeploymentOptions to "Force target application shutdown"</span></span>

7. <span data-ttu-id="6e4ea-132">对于存储已签名的应用，需要指定许可证。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-132">For Store signed apps, you will need to specify the license.</span></span> <span data-ttu-id="6e4ea-133">下 UserContextAppLicense，</span><span class="sxs-lookup"><span data-stu-id="6e4ea-133">Under UserContextAppLicense,</span></span>
    - <span data-ttu-id="6e4ea-134">添加 LicenseProductID （可用作 LicenseID 许可证 XML 文件中）</span><span class="sxs-lookup"><span data-stu-id="6e4ea-134">add LicenseProductID (available as LicenseID in the license XML file)</span></span>
    - <span data-ttu-id="6e4ea-135">将许可证 xml 扩展名更改为 *.ms windows 应用商店许可*。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-135">change the license xml extension to *.ms-windows-store-license*.</span></span>
    - <span data-ttu-id="6e4ea-136">选择您的左侧上的许可证产品 ID 并浏览您的许可证文件来分配 LicenseInstall 字段</span><span class="sxs-lookup"><span data-stu-id="6e4ea-136">select your License Product ID on the left hand side and browse your license file to assign LicenseInstall field</span></span>

8. <span data-ttu-id="6e4ea-137">对于非应用商店已签名应用程序，您需要添加下的 app.cer 文件**证书 > RootCertificates**</span><span class="sxs-lookup"><span data-stu-id="6e4ea-137">For non-store signed apps, you will need to add the app.cer file under **Certificates > RootCertificates**</span></span> 

9. <span data-ttu-id="6e4ea-138">导出包</span><span class="sxs-lookup"><span data-stu-id="6e4ea-138">Export the package</span></span>

10. <span data-ttu-id="6e4ea-139">将导出的.ppkg 文件复制到_C:\Windows\Provisioning\Packages_ IoT 设备使用[SSH](../connect-your-device/SSH.md)或[Powershell](../connect-your-device/powershell.md)) 并重新启动。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-139">Copy the exported .ppkg file to _C:\Windows\Provisioning\Packages_ on the IoT device using [SSH](../connect-your-device/SSH.md) or [Powershell](../connect-your-device/powershell.md)) and reboot.</span></span> <span data-ttu-id="6e4ea-140">当设备重新启动时，处理预配包和安装应用。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-140">When the device reboots, the provisioning package is processed and the app is installed.</span></span>


## <a name="add-to-the-iot-core-imageffu"></a><span data-ttu-id="6e4ea-141">将添加到 IoT core image(.ffu)</span><span class="sxs-lookup"><span data-stu-id="6e4ea-141">Add to the IoT core image(.ffu)</span></span>   
<span data-ttu-id="6e4ea-142">您可以添加该应用程序本身 IoT Core 映像的一部分。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-142">You can add the app to be part of the IoT Core image itself.</span></span> <span data-ttu-id="6e4ea-143">这是 oem 广泛使用的机制。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-143">This is the widely used mechanism for OEMs.</span></span> 

<span data-ttu-id="6e4ea-144">请参阅如何[将应用添加到你的映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)和一个[示例应用包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp)。</span><span class="sxs-lookup"><span data-stu-id="6e4ea-144">See how to [add an app to your image](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) and a [sample app package](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp).</span></span>
