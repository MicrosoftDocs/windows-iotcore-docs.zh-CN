---
title: 管理 Windows IoT Core 设备
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 了解管理 Windows 10 IoT Core 设备的不同方式，如使用支持基于证书的注册的传统 OMA DM MDM 服务器。
keywords: windows iot，设备管理，windows iot，Azure DM，Azure 集线器，Azure IoT
ms.openlocfilehash: 358338ef607bb05f4c1144e7ba9ad19d1db2018c
ms.sourcegitcommit: 05278f1a522ed498900ce15b98bdd4389b5dde55
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88081662"
---
# <a name="managing-windows-iot-core-devices"></a><span data-ttu-id="e54f8-104">管理 Windows IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="e54f8-104">Managing Windows IoT Core Devices</span></span>

<span data-ttu-id="e54f8-105">可以使用支持基于证书的注册或使用 Azure IoT 中心的设备管理的传统 OMA DM MDM 服务器来管理 Windows 10 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="e54f8-105">Windows 10 IoT Core devices can be managed using a traditional OMA DM MDM server that supports certificate based enrollment or using Azure IoT Hub's Device Management.</span></span>  

 <span data-ttu-id="e54f8-106">_[在此处](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)详细了解 MDM 和 Windows 10。_</span><span class="sxs-lookup"><span data-stu-id="e54f8-106">_Learn more about MDM and Windows 10 [here](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)._</span></span>  

<span data-ttu-id="e54f8-107">对于使用 OMA DM 服务器管理的设备，适用于 Windows 10 IoT Core 的 MDM 策略与其他 Windows 10 版本中支持的策略一致。</span><span class="sxs-lookup"><span data-stu-id="e54f8-107">For devices that are managed using a OMA DM server the MDM policies for Windows 10 IoT Core align with the policies supported in other editions of Windows 10.</span></span> <span data-ttu-id="e54f8-108">若要详细了解 IoT Core 设备上的策略以及可管理的内容，请参阅[此处](https://aka.ms/csplist)的 Windows 10 配置服务提供程序参考。</span><span class="sxs-lookup"><span data-stu-id="e54f8-108">To learn more about policies as well as what can be managed on IoT Core devices, see Configuration service provider reference for Windows 10 [here](https://aka.ms/csplist).</span></span> <span data-ttu-id="e54f8-109">Windows 10 中的 MDM 支持基于开放移动联盟 (OMA) 设备管理 (DM) 协议1.2.1 规范。</span><span class="sxs-lookup"><span data-stu-id="e54f8-109">The MDM support in Windows 10 is based on Open Mobile Alliance (OMA) Device Management (DM) protocol 1.2.1 specification.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-a-mdm"></a><span data-ttu-id="e54f8-110">如何实现将 IoT Core 设备注册到 MDM？</span><span class="sxs-lookup"><span data-stu-id="e54f8-110">How do I enroll an IoT Core device into a MDM?</span></span>
___
<span data-ttu-id="e54f8-111">使用预配包完成 IoT 核心设备的 MDM 注册。</span><span class="sxs-lookup"><span data-stu-id="e54f8-111">MDM enrollment of an IoT Core device is accomplished using a Provisioning package.</span></span> <span data-ttu-id="e54f8-112">可以使用 Windows 映像配置和设计器 (WICD) 创建预配包。</span><span class="sxs-lookup"><span data-stu-id="e54f8-112">Provisioning packages can be created using Windows Image Configuration and Designer (WICD).</span></span> <span data-ttu-id="e54f8-113">让我们尝试将设备注册到 MDM。</span><span class="sxs-lookup"><span data-stu-id="e54f8-113">Let's try enrolling a device into a MDM.</span></span>

### <a name="creating-a-provisioning-package"></a><span data-ttu-id="e54f8-114">创建预配包</span><span class="sxs-lookup"><span data-stu-id="e54f8-114">Creating a Provisioning package</span></span>

#### <a name="microsoft-system-center-configuration-manager-standalone-or-sccmintune-hybrid"></a><span data-ttu-id="e54f8-115">Microsoft System Center Configuration Manager (独立版或 SCCM 版 + Intune 混合) </span><span class="sxs-lookup"><span data-stu-id="e54f8-115">Microsoft System Center Configuration Manager (Standalone or SCCM+Intune Hybrid)</span></span>

1. <span data-ttu-id="e54f8-116"> (ConfigMgr 控制台中打开 Configuration Manager 管理控制台) </span><span class="sxs-lookup"><span data-stu-id="e54f8-116">Open the Configuration Manager Management Console (ConfigMgr Console)</span></span>

2. <span data-ttu-id="e54f8-117">导航到 "_资产和符合性" > 符合性设置 > 公司资源访问 > 证书配置文件_ 
    ![ 证书配置文件](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)</span><span class="sxs-lookup"><span data-stu-id="e54f8-117">Navigate to _Assets and Compliance > Compliance Settings > Company Resource Access > Certificate Profiles_
![Certificate Profiles](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)</span></span>

3. <span data-ttu-id="e54f8-118">单击 "**创建证书配置文件**"</span><span class="sxs-lookup"><span data-stu-id="e54f8-118">Click **Create Certificate Profile**</span></span>

4. <span data-ttu-id="e54f8-119">提供配置文件的名称和描述</span><span class="sxs-lookup"><span data-stu-id="e54f8-119">Provide a name and description for the profile</span></span>
   - <span data-ttu-id="e54f8-120">名称： ConfigMgr 示例受信任的根证书</span><span class="sxs-lookup"><span data-stu-id="e54f8-120">Name: ConfigMgr Example Trusted Root Certificate</span></span>
     - <span data-ttu-id="e54f8-121">证书配置文件的类型：受信任的 CA 证书</span><span class="sxs-lookup"><span data-stu-id="e54f8-121">Type of certificate profile: Trusted CA certificate</span></span>  
     ![可信证书](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard.png)

5. <span data-ttu-id="e54f8-123">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e54f8-123">Click **Next**.</span></span>

6. <span data-ttu-id="e54f8-124">导入证书文件。</span><span class="sxs-lookup"><span data-stu-id="e54f8-124">Import the certificate file.</span></span>

7. <span data-ttu-id="e54f8-125">选择 "**计算机证书存储区-** **目标存储**的根目录"。</span><span class="sxs-lookup"><span data-stu-id="e54f8-125">Select **Computer certificate store - Root** for the **Destination Store**.</span></span>

8. <span data-ttu-id="e54f8-126">单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="e54f8-126">Click **Next**.</span></span>

9. <span data-ttu-id="e54f8-127">对于支持的平台支持平台，选择 "全**选**" ![](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)</span><span class="sxs-lookup"><span data-stu-id="e54f8-127">Choose **Select all** for Supported Platforms ![Supported platforms](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)</span></span>

10. <span data-ttu-id="e54f8-128">单击 "**摘要"、"下一步"，然后单击 "关闭**" 退出向导。</span><span class="sxs-lookup"><span data-stu-id="e54f8-128">Click **Summary, Next, and Close** to exit the wizard.</span></span>

11. <span data-ttu-id="e54f8-129">右键单击刚创建的配置文件，然后单击 "**导出**"。</span><span class="sxs-lookup"><span data-stu-id="e54f8-129">Right-click on the profile just created and click **Export**.</span></span>

12. <span data-ttu-id="e54f8-130">单击 "**浏览**"，找到应导出 ppkg 文件的位置，然后单击 "**保存**"。</span><span class="sxs-lookup"><span data-stu-id="e54f8-130">Click **Browse**, find a location where the .ppkg file should be exported, and then click **Save**.</span></span>

13. <span data-ttu-id="e54f8-131">单击 "**导出**"，然后单击 **"确定"** 退出向导。</span><span class="sxs-lookup"><span data-stu-id="e54f8-131">Click **Export** and click **OK** to exit the wizard.</span></span>

#### <a name="other-mdm-servers"></a><span data-ttu-id="e54f8-132">其他 MDM 服务器</span><span class="sxs-lookup"><span data-stu-id="e54f8-132">Other MDM Servers</span></span>

1. <span data-ttu-id="e54f8-133">[ (WINDOWS ADK) 下载并安装 Windows 评估和部署工具包](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit)。</span><span class="sxs-lookup"><span data-stu-id="e54f8-133">Download and install the [Windows Assessment and Deployment Kit (Windows ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit).</span></span>

2. <span data-ttu-id="e54f8-134">打开 Windows 映像和配置设计器 (WICD) 。</span><span class="sxs-lookup"><span data-stu-id="e54f8-134">Open Windows Imaging and Configuration Designer (WICD).</span></span>
   <span data-ttu-id="e54f8-135">![Windows 映像和配置设计器](../media/ManagingDevices/WICD-Start-Page.png)</span><span class="sxs-lookup"><span data-stu-id="e54f8-135">![Windows Imaging and Configuration Designer](../media/ManagingDevices/WICD-Start-Page.png)</span></span>

3. <span data-ttu-id="e54f8-136">选择**高级设置**</span><span class="sxs-lookup"><span data-stu-id="e54f8-136">Choose **Advanced Provisioning**</span></span>

4. <span data-ttu-id="e54f8-137">设置包的名称。</span><span class="sxs-lookup"><span data-stu-id="e54f8-137">Set a name for your package.</span></span>

5. <span data-ttu-id="e54f8-138">选择 Windows 10 IoT Core 的通用设置。</span><span class="sxs-lookup"><span data-stu-id="e54f8-138">Choose settings common to Windows 10 IoT Core.</span></span>

6. <span data-ttu-id="e54f8-139">跳过 "导入包" 步骤。</span><span class="sxs-lookup"><span data-stu-id="e54f8-139">Skip the Import Package step.</span></span>
   <span data-ttu-id="e54f8-140">![WICD--WICD--新项目-WICD--新建-项目- ](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
    ![ ](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
    ![ Import](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)</span><span class="sxs-lookup"><span data-stu-id="e54f8-140">![WICD-New-Project-Details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
![WICD-New-Project-Import](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)</span></span>

7. <span data-ttu-id="e54f8-141">导航到 "工作区-> 注册"。</span><span class="sxs-lookup"><span data-stu-id="e54f8-141">Navigate to Workplace -> Enrollments.</span></span>

8. <span data-ttu-id="e54f8-142">在 "UPN" 字段中，输入要在 (上注册设备的帐户，如 trmck@contoso.co) 并单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="e54f8-142">In the UPN field enter the account you wish to enroll your device under (i.e. trmck@contoso.co) and click **Add**.</span></span>

   ![已填充工作区注册](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Filled.png)

9. <span data-ttu-id="e54f8-144">对于 AuthPolicy，请选择 "基于用户名密码 (本地) 或基于证书的身份验证之间的身份验证。</span><span class="sxs-lookup"><span data-stu-id="e54f8-144">For AuthPolicy choose between Username Password based authentication (OnPremises) or Certificate based authentication.</span></span>

10. <span data-ttu-id="e54f8-145">输入 MDM 服务器的发现服务 URL。</span><span class="sxs-lookup"><span data-stu-id="e54f8-145">Enter the Discovery Service URL for your MDM server.</span></span>

> [!NOTE]
> <span data-ttu-id="e54f8-146">注册服务 URL 和策略服务 URL 是可选的。</span><span class="sxs-lookup"><span data-stu-id="e54f8-146">Enrollment Service URL and Policy Service URL are optional.</span></span>

11. <span data-ttu-id="e54f8-147">输入密码</span><span class="sxs-lookup"><span data-stu-id="e54f8-147">For the Secret enter</span></span>  
    - <span data-ttu-id="e54f8-148">本地：要注册的帐户的密码</span><span class="sxs-lookup"><span data-stu-id="e54f8-148">OnPremises: The password for the account you're enrolling with</span></span>  
    - <span data-ttu-id="e54f8-149">证书：证书的指纹</span><span class="sxs-lookup"><span data-stu-id="e54f8-149">Certificate: The thumbprint of the certificate</span></span>
    
    ![实心 OnPremise](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Details-Filled-Premise.png)  

12. <span data-ttu-id="e54f8-151">在 WICD 窗口的顶部，单击 "**导出 > 预配包**"。</span><span class="sxs-lookup"><span data-stu-id="e54f8-151">At the top of WICD window click **Export > Provisioning package**.</span></span>

13. <span data-ttu-id="e54f8-152">提供包的名称和版本，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="e54f8-152">Provide a name and version for your package and click **Next**.</span></span> 

> [!NOTE]
> <span data-ttu-id="e54f8-153">务必递增版本号，以确保执行更新的包。</span><span class="sxs-lookup"><span data-stu-id="e54f8-153">Be sure to increment the version number to ensure an updated package is executed.</span></span>

14. <span data-ttu-id="e54f8-154">在 "**安全详细信息" 页**上单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="e54f8-154">Click **Next** on the **security details page**.</span></span>

15. <span data-ttu-id="e54f8-155">选择要在本地计算机上导出包的位置，并单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="e54f8-155">Choose the location where the package is to be exported on the local machine and click **Next**.</span></span>

16. <span data-ttu-id="e54f8-156">单击 "**生成**"，然后单击 "**完成**" 退出向导。</span><span class="sxs-lookup"><span data-stu-id="e54f8-156">Click **Build** and then **Finish** to exit the wizard.</span></span>

### <a name="installing-the-provisioning-package"></a><span data-ttu-id="e54f8-157">安装预配包</span><span class="sxs-lookup"><span data-stu-id="e54f8-157">Installing the Provisioning package</span></span>

<span data-ttu-id="e54f8-158">可通过几种方法将预配包部署到 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="e54f8-158">There are a few ways in which a Provisioning package can be deployed to an IoT device.</span></span> <span data-ttu-id="e54f8-159">可以通过将包复制到设备，或在映像过程中将包添加到映像来部署包。</span><span class="sxs-lookup"><span data-stu-id="e54f8-159">It is possible to deploy a package by copying the package to the device or adding the package to the image during the imaging process.</span></span>

#### <a name="copying-package-to-device"></a><span data-ttu-id="e54f8-160">将包复制到设备</span><span class="sxs-lookup"><span data-stu-id="e54f8-160">Copying package to device</span></span>

<span data-ttu-id="e54f8-161">获取从 SCCM 或 WICD 导出的预配包，并将 ppkg 文件复制到 `C:\Windows\Provisioning\Packages` IoT 设备上的目录。</span><span class="sxs-lookup"><span data-stu-id="e54f8-161">Take the Provisioning package that was exported from SCCM or WICD and copy the .ppkg file to `C:\Windows\Provisioning\Packages` directory on the IoT device.</span></span> <span data-ttu-id="e54f8-162">设备重新启动时，将执行包，并且设备将启动注册过程。</span><span class="sxs-lookup"><span data-stu-id="e54f8-162">Upon reboot of the device the package will be executed and the device will start the enrollment process.</span></span>

#### <a name="adding-package-to-image"></a><span data-ttu-id="e54f8-163">将包添加到映像</span><span class="sxs-lookup"><span data-stu-id="e54f8-163">Adding package to image</span></span>

<span data-ttu-id="e54f8-164">请参阅[向映像添加预配包](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image)。</span><span class="sxs-lookup"><span data-stu-id="e54f8-164">See [Add a provisioning package to an image](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image).</span></span> <span data-ttu-id="e54f8-165">首次启动时，设备将执行包并启动注册过程。</span><span class="sxs-lookup"><span data-stu-id="e54f8-165">Upon first boot the device will execute the package and start the enrollment process.</span></span>
