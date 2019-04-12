---
title: 管理 Windows IoT Core 设备
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 了解如何管理 Windows 10 IoT Core 设备的不同方式。
keywords: windows iot、 设备管理、 windows iot，Azure DM、 Azure 中心、 Azure IoT
ms.openlocfilehash: dbcc6858ee32ce9eb8b33c3d1831a6581a8fa3c7
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510971"
---
# <a name="managing-windows-iot-core-devices"></a><span data-ttu-id="060af-104">管理 Windows IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="060af-104">Managing Windows IoT Core Devices</span></span>

<span data-ttu-id="060af-105">Windows 10 IoT Core 设备可以使用支持基于证书注册的传统 OMA DM MDM 服务器或使用 Azure IoT 中心设备管理进行管理。</span><span class="sxs-lookup"><span data-stu-id="060af-105">Windows 10 IoT Core devices can be managed using a traditional OMA DM MDM server that supports certificate based enrollment or using Azure IoT Hub's Device Management.</span></span>  

 _<span data-ttu-id="060af-106">详细了解 MDM 和 Windows 10[此处](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="060af-106">Learn more about MDM and Windows 10 [here](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx).</span></span>_  

<span data-ttu-id="060af-107">使用 OMA DM 服务器管理的设备的 Windows 10 IoT Core 的 MDM 策略与在其他版本的 Windows 10 中受支持的策略保持一致。</span><span class="sxs-lookup"><span data-stu-id="060af-107">For devices that are managed using a OMA DM server the MDM policies for Windows 10 IoT Core align with the policies supported in other editions of Windows 10.</span></span> <span data-ttu-id="060af-108">若要了解更多的策略以及为什么可以管理在 IoT Core 设备上，请参阅适用于 Windows 10 配置服务提供程序参考[此处](https://aka.ms/csplist)。</span><span class="sxs-lookup"><span data-stu-id="060af-108">To learn more about policies as well as what can be managed on IoT Core devices, see Configuration service provider reference for Windows 10 [here](https://aka.ms/csplist).</span></span> <span data-ttu-id="060af-109">Windows 10 中的 MDM 支持基于开放移动联盟 (OMA) 设备管理 (DM) 协议 1.2.1 规范。</span><span class="sxs-lookup"><span data-stu-id="060af-109">The MDM support in Windows 10 is based on Open Mobile Alliance (OMA) Device Management (DM) protocol 1.2.1 specification.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-a-mdm"></a><span data-ttu-id="060af-110">如何到 MDM 注册 IoT Core 设备？</span><span class="sxs-lookup"><span data-stu-id="060af-110">How do I enroll an IoT Core device into a MDM?</span></span>
___
<span data-ttu-id="060af-111">MDM 注册的 IoT Core 设备被通过预配包。</span><span class="sxs-lookup"><span data-stu-id="060af-111">MDM enrollment of an IoT Core device is accomplished using a Provisioning package.</span></span> <span data-ttu-id="060af-112">可以使用 Windows 映像配置和设计器 (WICD) 创建预配包。</span><span class="sxs-lookup"><span data-stu-id="060af-112">Provisioning packages can be created using Windows Image Configuration and Designer (WICD).</span></span> <span data-ttu-id="060af-113">让我们尝试设备注册到 mdm。</span><span class="sxs-lookup"><span data-stu-id="060af-113">Let's try enrolling a device into a MDM.</span></span>

### <a name="creating-a-provisioning-package"></a><span data-ttu-id="060af-114">创建预配包</span><span class="sxs-lookup"><span data-stu-id="060af-114">Creating a Provisioning package</span></span>

#### <a name="microsoft-system-center-configuration-manager-standalone-or-sccmintune-hybrid"></a><span data-ttu-id="060af-115">Microsoft System Center Configuration Manager （独立或 SCCM + Intune 混合版）</span><span class="sxs-lookup"><span data-stu-id="060af-115">Microsoft System Center Configuration Manager (Standalone or SCCM+Intune Hybrid)</span></span>

1. <span data-ttu-id="060af-116">打开 Configuration Manager 管理控制台 （ConfigMgr 控制台）</span><span class="sxs-lookup"><span data-stu-id="060af-116">Open the Configuration Manager Management Console (ConfigMgr Console)</span></span>

2. <span data-ttu-id="060af-117">导航到_资产和符合性 > 符合性设置 > 公司资源访问 > 的证书配置文件_
   ![的证书配置文件](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)</span><span class="sxs-lookup"><span data-stu-id="060af-117">Navigate to _Assets and Compliance > Compliance Settings > Company Resource Access > Certificate Profiles_
![Certificate Profiles](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)</span></span>

3. <span data-ttu-id="060af-118">单击**创建证书配置文件**</span><span class="sxs-lookup"><span data-stu-id="060af-118">Click **Create Certificate Profile**</span></span>

4. <span data-ttu-id="060af-119">提供名称和配置文件说明</span><span class="sxs-lookup"><span data-stu-id="060af-119">Provide a name and description for the profile</span></span>
   - <span data-ttu-id="060af-120">名称：ConfigMgr 示例受信任的根证书</span><span class="sxs-lookup"><span data-stu-id="060af-120">Name: ConfigMgr Example Trusted Root Certificate</span></span>
     - <span data-ttu-id="060af-121">证书配置文件的类型：受信任的 CA 证书</span><span class="sxs-lookup"><span data-stu-id="060af-121">Type of certificate profile: Trusted CA certificate</span></span>  
     ![受信任的证书](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard.png)

5. <span data-ttu-id="060af-123">单击“下一步” 。</span><span class="sxs-lookup"><span data-stu-id="060af-123">Click **Next**.</span></span>

6. <span data-ttu-id="060af-124">导入的证书文件。</span><span class="sxs-lookup"><span data-stu-id="060af-124">Import the certificate file.</span></span>

7. <span data-ttu-id="060af-125">选择**计算机证书存储区-根**有关**目标存储区**。</span><span class="sxs-lookup"><span data-stu-id="060af-125">Select **Computer certificate store - Root** for the **Destination Store**.</span></span>

8. <span data-ttu-id="060af-126">单击“下一步” 。</span><span class="sxs-lookup"><span data-stu-id="060af-126">Click **Next**.</span></span>

9. <span data-ttu-id="060af-127">选择**全**支持的平台为![受支持的平台](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)</span><span class="sxs-lookup"><span data-stu-id="060af-127">Choose **Select all** for Supported Platforms ![Supported platforms](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)</span></span>

10. <span data-ttu-id="060af-128">单击**摘要、 下一步，并关闭**以退出向导。</span><span class="sxs-lookup"><span data-stu-id="060af-128">Click **Summary, Next, and Close** to exit the wizard.</span></span>

11. <span data-ttu-id="060af-129">右键单击刚创建的配置文件，然后单击**导出**。</span><span class="sxs-lookup"><span data-stu-id="060af-129">Right-click on the profile just created and click **Export**.</span></span>

12. <span data-ttu-id="060af-130">单击**浏览**，找到的位置，其中.ppkg 文件应导出，然后单击**保存**。</span><span class="sxs-lookup"><span data-stu-id="060af-130">Click **Browse**, find a location where the .ppkg file should be exported, and then click **Save**.</span></span>

13. <span data-ttu-id="060af-131">单击**导出**然后单击**确定**以退出向导。</span><span class="sxs-lookup"><span data-stu-id="060af-131">Click **Export** and click **OK** to exit the wizard.</span></span>

#### <a name="other-mdm-servers"></a><span data-ttu-id="060af-132">其他 MDM 服务器</span><span class="sxs-lookup"><span data-stu-id="060af-132">Other MDM Servers</span></span>

1. <span data-ttu-id="060af-133">下载并安装[Windows 评估和部署工具包 (Windows ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit)。</span><span class="sxs-lookup"><span data-stu-id="060af-133">Download and install the [Windows Assessment and Deployment Kit (Windows ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit).</span></span>

2. <span data-ttu-id="060af-134">打开 Windows 映像和配置设计器 (WICD)。</span><span class="sxs-lookup"><span data-stu-id="060af-134">Open Windows Imaging and Configuration Designer (WICD).</span></span>
   ![Windows 映像和配置设计器](../media/ManagingDevices/WICD-Start-Page.png)

3. <span data-ttu-id="060af-136">选择**高级预配**</span><span class="sxs-lookup"><span data-stu-id="060af-136">Choose **Advanced Provisioning**</span></span>

4. <span data-ttu-id="060af-137">设置包的名称。</span><span class="sxs-lookup"><span data-stu-id="060af-137">Set a name for your package.</span></span>

5. <span data-ttu-id="060af-138">选择设置普遍适用于 Windows 10 IoT Core。</span><span class="sxs-lookup"><span data-stu-id="060af-138">Choose settings common to Windows 10 IoT Core.</span></span>

6. <span data-ttu-id="060af-139">跳过导入包步骤。</span><span class="sxs-lookup"><span data-stu-id="060af-139">Skip the Import Package step.</span></span>
   ![<span data-ttu-id="060af-140">WICD-New-Project-Details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
   ![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
   ![WICD-New-Project-Import</span><span class="sxs-lookup"><span data-stu-id="060af-140">WICD-New-Project-Details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
![WICD-New-Project-Import</span></span>](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)

7. <span data-ttu-id="060af-141">导航到工作区-> 注册。</span><span class="sxs-lookup"><span data-stu-id="060af-141">Navigate to Workplace -> Enrollments.</span></span>

8. <span data-ttu-id="060af-142">UPN 字段中输入你想要注册设备下的帐户 (即trmck@contoso.co)，单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="060af-142">In the UPN field enter the account you wish to enroll your device under (i.e. trmck@contoso.co) and click **Add**.</span></span>

   ![填充工作区注册](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Filled.png)

9. <span data-ttu-id="060af-144">AuthPolicy 之间进行选择的用户名密码基于身份验证 （本地） 或基于证书的身份验证。</span><span class="sxs-lookup"><span data-stu-id="060af-144">For AuthPolicy choose between Username Password based authentication (OnPremises) or Certificate based authentication.</span></span>

10. <span data-ttu-id="060af-145">输入 MDM 服务器的发现服务 URL。</span><span class="sxs-lookup"><span data-stu-id="060af-145">Enter the Discovery Service URL for your MDM server.</span></span>

> [!NOTE]
> <span data-ttu-id="060af-146">注册服务 URL 和策略服务 URL 是可选的。</span><span class="sxs-lookup"><span data-stu-id="060af-146">Enrollment Service URL and Policy Service URL are optional.</span></span>

11. <span data-ttu-id="060af-147">有关机密的 enter 键</span><span class="sxs-lookup"><span data-stu-id="060af-147">For the Secret enter</span></span>  
    - <span data-ttu-id="060af-148">本地：要注册与帐户的密码</span><span class="sxs-lookup"><span data-stu-id="060af-148">OnPremises: The password for the account you're enrolling with</span></span>  
    - <span data-ttu-id="060af-149">证书：证书的指纹</span><span class="sxs-lookup"><span data-stu-id="060af-149">Certificate: The thumbprint of the certificate</span></span>
    
    ![填充的 OnPremise](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Details-Filled-Premise.png)  

12. <span data-ttu-id="060af-151">单击 WICD 窗口顶部**导出 > 预配包**。</span><span class="sxs-lookup"><span data-stu-id="060af-151">At the top of WICD window click **Export > Provisioning package**.</span></span>

13. <span data-ttu-id="060af-152">为包提供名称和版本，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="060af-152">Provide a name and version for your package and click **Next**.</span></span> 

> [!NOTE]
> <span data-ttu-id="060af-153">请确保递增版本号，以确保在执行更新的包。</span><span class="sxs-lookup"><span data-stu-id="060af-153">Be sure to increment the version number to ensure an updated package is executed.</span></span>

14. <span data-ttu-id="060af-154">单击**下一步**上**安全详细信息页**。</span><span class="sxs-lookup"><span data-stu-id="060af-154">Click **Next** on the **security details page**.</span></span>

15. <span data-ttu-id="060af-155">选择包将在本地计算机上单击要导出的位置**下一步**。</span><span class="sxs-lookup"><span data-stu-id="060af-155">Choose the location where the package is to be exported on the local machine and click **Next**.</span></span>

16. <span data-ttu-id="060af-156">单击**构建**，然后**完成**以退出向导。</span><span class="sxs-lookup"><span data-stu-id="060af-156">Click **Build** and then **Finish** to exit the wizard.</span></span>

### <a name="installing-the-provisioning-package"></a><span data-ttu-id="060af-157">安装预配包</span><span class="sxs-lookup"><span data-stu-id="060af-157">Installing the Provisioning package</span></span>

<span data-ttu-id="060af-158">有几种方法在其中预配包可部署到 IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="060af-158">There are a few ways in which a Provisioning package can be deployed to an IoT device.</span></span> <span data-ttu-id="060af-159">就可以通过将包复制到设备或映像创建过程中将包添加到映像部署的包。</span><span class="sxs-lookup"><span data-stu-id="060af-159">It is possible to deploy a package by copying the package to the device or adding the package to the image during the imaging process.</span></span>

#### <a name="copying-package-to-device"></a><span data-ttu-id="060af-160">将包复制到设备</span><span class="sxs-lookup"><span data-stu-id="060af-160">Copying package to device</span></span>

<span data-ttu-id="060af-161">获取已从 SCCM 或 WICD 导出预配程序包并复制到.ppkg 文件`C:\Windows\Provisioning\Packages`IoT 设备目录。</span><span class="sxs-lookup"><span data-stu-id="060af-161">Take the Provisioning package that was exported from SCCM or WICD and copy the .ppkg file to `C:\Windows\Provisioning\Packages` directory on the IoT device.</span></span> <span data-ttu-id="060af-162">在设备的重新启动时执行包，设备会开始注册过程。</span><span class="sxs-lookup"><span data-stu-id="060af-162">Upon reboot of the device the package will be executed and the device will start the enrollment process.</span></span>

#### <a name="adding-package-to-image"></a><span data-ttu-id="060af-163">将包添加到映像</span><span class="sxs-lookup"><span data-stu-id="060af-163">Adding package to image</span></span>

<span data-ttu-id="060af-164">请参阅[向映像添加预配包](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image)。</span><span class="sxs-lookup"><span data-stu-id="060af-164">See [Add a provisioning package to an image](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image).</span></span> <span data-ttu-id="060af-165">首次启动时设备将执行包并启动注册流程。</span><span class="sxs-lookup"><span data-stu-id="060af-165">Upon first boot the device will execute the package and start the enrollment process.</span></span>
