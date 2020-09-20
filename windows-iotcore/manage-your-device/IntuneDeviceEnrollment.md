---
title: 在 Intune 中注册 Windows IoT Core 设备
author: msmimart
ms.author: mimart
ms.date: 05/08/2018
ms.topic: article
description: 了解如何使用 Microsoft Intune 设备管理和 Windows IoT 来管理设备。
keywords: windows iot，Azure IoT，Intune 设备管理，设备管理
ms.openlocfilehash: 03eda1fdd88e5a5b1114ee54397541f35fb85ec3
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782449"
---
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a><span data-ttu-id="e2c76-104">在 Microsoft Intune 中注册 Windows IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="e2c76-104">Enrolling Windows IoT Core devices in Microsoft Intune</span></span>

<span data-ttu-id="e2c76-105">你的公司可以管理 IoT 核心设备以及其他所有托管设备。</span><span class="sxs-lookup"><span data-stu-id="e2c76-105">Your company can manage IoT Core devices alongside all of your other managed devices.</span></span> <span data-ttu-id="e2c76-106">这为你提供了使用 Intune 管理 IoT Core、IoT Enterprise 和其他 Windows 设备的一致方式。</span><span class="sxs-lookup"><span data-stu-id="e2c76-106">This gives you a consistent way to manage IoT Core, IoT Enterprise, and other Windows devices using Intune.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a><span data-ttu-id="e2c76-107">如何实现将 IoT Core 设备注册到 Intune？</span><span class="sxs-lookup"><span data-stu-id="e2c76-107">How do I enroll an IoT Core device into Intune?</span></span>

<span data-ttu-id="e2c76-108">通过使用 Windows IoT 核心仪表板准备设备，然后使用 Windows 配置设计器创建预配包，可以完成 IoT 核心设备的 Intune 注册。</span><span class="sxs-lookup"><span data-stu-id="e2c76-108">Intune enrollment of an IoT Core device is accomplished by using the Windows IoT Core Dashboard to prepare the device, and then using Windows Configuration Designer to create a provisioning package.</span></span>

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a><span data-ttu-id="e2c76-109">在 Azure AD 中更改 Intune MDM 用户范围</span><span class="sxs-lookup"><span data-stu-id="e2c76-109">Change the Intune MDM user scope in Azure AD</span></span>

1. <span data-ttu-id="e2c76-110">登录到 [Azure 门户](https://portal.azure.com)，然后选择“Azure Active Directory”。</span><span class="sxs-lookup"><span data-stu-id="e2c76-110">Sign in to the [Azure portal](https://portal.azure.com), and then select **Azure Active Directory**.</span></span>
2. <span data-ttu-id="e2c76-111">选择“移动性 (MDM 和 MAM)”。</span><span class="sxs-lookup"><span data-stu-id="e2c76-111">Select **Mobility (MDM and MAM)**.</span></span>

     ![选择移动性和 Microsoft Intune](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)

3. <span data-ttu-id="e2c76-113">选择“Microsoft Intune”。</span><span class="sxs-lookup"><span data-stu-id="e2c76-113">Select **Microsoft Intune**.</span></span> <span data-ttu-id="e2c76-114">在 " **配置 Microsoft Intune** " 页上的 " **MDM 用户范围**" 旁边，选择 " **全部**"。</span><span class="sxs-lookup"><span data-stu-id="e2c76-114">On the **Configure Microsoft Intune** page, next to **MDM user scope**, select **All**.</span></span> <span data-ttu-id="e2c76-115">这将允许在加入 Azure AD 后，在 Intune 中注册 IoT Core 设备用户。</span><span class="sxs-lookup"><span data-stu-id="e2c76-115">This will allow your IoT Core device user to be enrolled in Intune after joining Azure AD.</span></span>

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a><span data-ttu-id="e2c76-116">为 IoT 核心设备创建安装 SD 卡</span><span class="sxs-lookup"><span data-stu-id="e2c76-116">Create a setup SD card for the IoT Core device</span></span>

1. <span data-ttu-id="e2c76-117">将 microSD 卡插入到电脑上的读卡器中。</span><span class="sxs-lookup"><span data-stu-id="e2c76-117">Insert a microSD card into the card reader on your PC.</span></span>
     > [!NOTE]
     > <span data-ttu-id="e2c76-118">在此过程中，将会设置 microSD 卡的格式，因此卡上的所有数据都将被删除。</span><span class="sxs-lookup"><span data-stu-id="e2c76-118">The microSD card will be formatted during this process, so any data on the card will be deleted.</span></span>
2. <span data-ttu-id="e2c76-119">请参阅 " [Windows IoT 核心" 仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) 以下载并安装仪表板。</span><span class="sxs-lookup"><span data-stu-id="e2c76-119">Go to [Windows IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) to download and install the dashboard.</span></span>
3. <span data-ttu-id="e2c76-120">安装仪表板后，将其打开，然后选择 " **设置新设备**"。</span><span class="sxs-lookup"><span data-stu-id="e2c76-120">After the dashboard installs, open it and select **Set up a new device**.</span></span>

     ![Windows IoT 核心仪表板](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. <span data-ttu-id="e2c76-122">键入 **设备名称**。</span><span class="sxs-lookup"><span data-stu-id="e2c76-122">Type a **Device name**.</span></span>
5. <span data-ttu-id="e2c76-123">输入新的管理员密码。</span><span class="sxs-lookup"><span data-stu-id="e2c76-123">Enter a new administrator password.</span></span>
6. <span data-ttu-id="e2c76-124">如果要为设备启用 Wi-fi，请选中 " **Wi-fi 网络连接** " 复选框。</span><span class="sxs-lookup"><span data-stu-id="e2c76-124">If you want to enable Wi-Fi for the device, select the **Wi-Fi Network Connection** checkbox.</span></span> <span data-ttu-id="e2c76-125">如果设备仅使用以太网网络连接，则跳过此。</span><span class="sxs-lookup"><span data-stu-id="e2c76-125">Skip this if the device will use an ethernet network connection only.</span></span>

     ![IoT 面板上的 "wi-fi" 复选框](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. <span data-ttu-id="e2c76-127">选中 " **我接受软件许可条款** " 复选框，然后选择 " **下载并安装**"。</span><span class="sxs-lookup"><span data-stu-id="e2c76-127">Select the **I accept the software license terms** checkbox, and then select **Download and Install**.</span></span>
8. <span data-ttu-id="e2c76-128">出现确认消息时，请选择用于 **格式化** SD 卡的选项。</span><span class="sxs-lookup"><span data-stu-id="e2c76-128">When the confirmation message appears, select the option to **Format** the SD Card.</span></span>
     > [!NOTE]
     > <span data-ttu-id="e2c76-129">请在安装过程中监视 **格式** 确认消息。</span><span class="sxs-lookup"><span data-stu-id="e2c76-129">Watch for the **Format** confirmation message during setup.</span></span> <span data-ttu-id="e2c76-130">其他打开的应用程序可能会隐藏该消息，但请务必选择 Format 选项。</span><span class="sxs-lookup"><span data-stu-id="e2c76-130">The message could be hidden by another open application, but it’s important to select the Format option.</span></span> <span data-ttu-id="e2c76-131">如果驱动器的格式不正确，则 boot 将会失败。</span><span class="sxs-lookup"><span data-stu-id="e2c76-131">If the drive isn't properly formatted, boot will fail.</span></span>
9. <span data-ttu-id="e2c76-132">你的 **SD 卡已就绪** 的消息随即出现。</span><span class="sxs-lookup"><span data-stu-id="e2c76-132">The message **Your SD card is ready** appears.</span></span>

     ![SD 卡就绪消息](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. <span data-ttu-id="e2c76-134">最小化此页。</span><span class="sxs-lookup"><span data-stu-id="e2c76-134">Minimize this page.</span></span>  <span data-ttu-id="e2c76-135">稍后你将返回到它。</span><span class="sxs-lookup"><span data-stu-id="e2c76-135">You'll come back to it later.</span></span>

### <a name="create-a-provisioning-package-for-intune-enrollment"></a><span data-ttu-id="e2c76-136">为 Intune 注册创建预配包</span><span class="sxs-lookup"><span data-stu-id="e2c76-136">Create a provisioning package for Intune enrollment</span></span>

1. <span data-ttu-id="e2c76-137">按照 [安装 Windows 配置设计器](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)中的步骤安装 Windows 配置设计应用。</span><span class="sxs-lookup"><span data-stu-id="e2c76-137">Install the Windows Configuration Design app by following the steps in [Install Windows Configuration Designer](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).</span></span>

2. <span data-ttu-id="e2c76-138">打开 **Windows 映像和配置设计器**。</span><span class="sxs-lookup"><span data-stu-id="e2c76-138">Open the **Windows Imaging and Configuration Designer**.</span></span>
3. <span data-ttu-id="e2c76-139">选择 " **预配桌面设备** " 以创建项目。</span><span class="sxs-lookup"><span data-stu-id="e2c76-139">Choose **Provision desktop devices** to create a project.</span></span>

     ![选择设置桌面服务](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. <span data-ttu-id="e2c76-141">根据需要输入 **项目详细信息** 。</span><span class="sxs-lookup"><span data-stu-id="e2c76-141">Enter the **Project Details** as desired.</span></span> <span data-ttu-id="e2c76-142">然后选择“完成”。</span><span class="sxs-lookup"><span data-stu-id="e2c76-142">Then select **Finish**.</span></span>
5. <span data-ttu-id="e2c76-143">请在 " **帐户管理** " 页上，选择 " **注册 Azure AD**。</span><span class="sxs-lookup"><span data-stu-id="e2c76-143">Go to the **Account Management** page and select **Enroll in Azure AD**.</span></span>
     > [!NOTE]
     > <span data-ttu-id="e2c76-144"> (ADK) Microsoft Store 或 Windows 评估和部署工具包中安装应用程序。</span><span class="sxs-lookup"><span data-stu-id="e2c76-144">Installing the app from either the Microsoft Store or the Windows Assessment and Deployment Kit (ADK) is fine.</span></span>

     ![选择注册 Azure AD](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. <span data-ttu-id="e2c76-146">在 " **批量令牌到期**" 旁边，输入 "批量令牌到期日期"。</span><span class="sxs-lookup"><span data-stu-id="e2c76-146">Next to **Bulk Token Expiry**, enter a bulk token expiry date.</span></span>
7. <span data-ttu-id="e2c76-147">选择 " **获取批量令牌**"。</span><span class="sxs-lookup"><span data-stu-id="e2c76-147">Select **Get Bulk Token**.</span></span> <span data-ttu-id="e2c76-148">此时将显示一个登录消息，用于连接到 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="e2c76-148">A sign-in message appears for connecting to Azure AD.</span></span>

     ![Azure AD 登录页](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. <span data-ttu-id="e2c76-150">输入租户用户名 (例如， john@mycompany.onmicrosoft.com) 和密码。</span><span class="sxs-lookup"><span data-stu-id="e2c76-150">Enter your tenant username (for example, john@mycompany.onmicrosoft.com) and your password.</span></span>
9. <span data-ttu-id="e2c76-151">同意允许 Windows 配置设计应用访问你的 Azure AD 信息。</span><span class="sxs-lookup"><span data-stu-id="e2c76-151">Agree to allow the Windows Configuration Design app to access your Azure AD information.</span></span>
10. <span data-ttu-id="e2c76-152">页面上的消息显示已成功获取批量 Azure AD 令牌。</span><span class="sxs-lookup"><span data-stu-id="e2c76-152">A message on the page shows that the Bulk Azure AD token was fetched successfully.</span></span>

     ![批量令牌成功消息](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. <span data-ttu-id="e2c76-154">选择 " **切换到高级编辑器**"，然后选择 *"是"*。</span><span class="sxs-lookup"><span data-stu-id="e2c76-154">Select **Switch to advanced editor**, and then select *Yes*.</span></span>

     ![切换到 "高级编辑器确认" 页](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. <span data-ttu-id="e2c76-156">在 " **所选自定义**" 下，保留 **帐户** 设置，但删除所有其他设置：</span><span class="sxs-lookup"><span data-stu-id="e2c76-156">Under **Selected customizations**, Leave the **Account** settings, but remove all other settings:</span></span>
13. <span data-ttu-id="e2c76-157">选择 " **OOBE**"，然后选择 " **删除**"。</span><span class="sxs-lookup"><span data-stu-id="e2c76-157">Select **OOBE**, and then select **Remove**.</span></span>
14. <span data-ttu-id="e2c76-158">如果 **SharedPC** 已列出，请选择它，然后选择 " **删除**"。</span><span class="sxs-lookup"><span data-stu-id="e2c76-158">If **SharedPC** is listed, select it, and then select **Remove**.</span></span>

     ![删除自定义项](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. <span data-ttu-id="e2c76-160">选择 " **导出**"，然后选择 " **设置包**"。</span><span class="sxs-lookup"><span data-stu-id="e2c76-160">Select **Export**, and then choose **Provisioning package**.</span></span>

     ![选择预配包](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. <span data-ttu-id="e2c76-162">在下一页上，接受默认设置，然后选择 " **下一步**"。</span><span class="sxs-lookup"><span data-stu-id="e2c76-162">On the next page, accept the default settings and select **Next**.</span></span>
17. <span data-ttu-id="e2c76-163">同样，在下一页上，接受默认设置，然后选择 "下一步"。</span><span class="sxs-lookup"><span data-stu-id="e2c76-163">Again, on the next page, accept the default settings and select Next.</span></span>
18. <span data-ttu-id="e2c76-164">更改 **设置包** 目标或保留默认路径，然后选择 " **下一步**"。</span><span class="sxs-lookup"><span data-stu-id="e2c76-164">Change the **Provisioning Package** destination or leave the default path, and then select **Next**.</span></span>
19. <span data-ttu-id="e2c76-165">选择“生成”  。</span><span class="sxs-lookup"><span data-stu-id="e2c76-165">Select **Build**.</span></span>
20. <span data-ttu-id="e2c76-166">选择 " **输出位置** " 链接，以便您可以在 ppkg 文件准备就绪时找到该文件。</span><span class="sxs-lookup"><span data-stu-id="e2c76-166">Select the **Output Location** link so that you can locate the .ppkg file when it's ready.</span></span>

     ![输出位置链接](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. <span data-ttu-id="e2c76-168">选择“完成”  。</span><span class="sxs-lookup"><span data-stu-id="e2c76-168">Select **Finish**.</span></span>
22. <span data-ttu-id="e2c76-169">请在 "文件资源管理器" 中，将预配包复制到 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="e2c76-169">Go to File Explorer and copy the provisioning package to your IoT Core device.</span></span> <span data-ttu-id="e2c76-170">将其保存到**c:\windows\provisioning\packages**文件夹中**MainOS**驱动器下的 microSD 卡。</span><span class="sxs-lookup"><span data-stu-id="e2c76-170">Save it to the microSD card under the **MainOS** drive in the **c:\windows\provisioning\packages** folder.</span></span>  <span data-ttu-id="e2c76-171">你将必须授予将文件保存到此文件夹的权限。</span><span class="sxs-lookup"><span data-stu-id="e2c76-171">You'll have to grant permissions to save the file in this folder.</span></span>

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a><span data-ttu-id="e2c76-172">在 Intune 中预配和注册 IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="e2c76-172">Provision and enroll the IoT Core device in Intune</span></span>

1. <span data-ttu-id="e2c76-173">将 microSD 卡插入 IoT 核心设备。</span><span class="sxs-lookup"><span data-stu-id="e2c76-173">Insert the microSD card into your IoT Core device.</span></span>
2. <span data-ttu-id="e2c76-174">打开 IoT Core 设备，并留出时间启动并显示标准屏幕。</span><span class="sxs-lookup"><span data-stu-id="e2c76-174">Turn on your IoT Core device and allow time for it to start up and display the standard screen.</span></span>
3. <span data-ttu-id="e2c76-175">返回到 Azure 门户中的 Microsoft Intune 控制台。</span><span class="sxs-lookup"><span data-stu-id="e2c76-175">Return to the Microsoft Intune console in the Azure portal.</span></span> <span data-ttu-id="e2c76-176">设备应显示在设备列表中。</span><span class="sxs-lookup"><span data-stu-id="e2c76-176">Your device should appear in the list of devices.</span></span>
     > [!NOTE]
     > <span data-ttu-id="e2c76-177">注册可能需要15分钟或更长时间才能完成。</span><span class="sxs-lookup"><span data-stu-id="e2c76-177">Enrollment could take 15 minutes or more to complete.</span></span>

     ![Intune 设备列表](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a><span data-ttu-id="e2c76-179">后续步骤</span><span class="sxs-lookup"><span data-stu-id="e2c76-179">Next steps</span></span>

- <span data-ttu-id="e2c76-180">[请参阅 Intune 中的设备详细信息](https://docs.microsoft.com/intune/device-inventory)。</span><span class="sxs-lookup"><span data-stu-id="e2c76-180">[See device details in Intune](https://docs.microsoft.com/intune/device-inventory).</span></span>
- <span data-ttu-id="e2c76-181">[同步设备以通过 Intune 获取最新的策略和操作](https://docs.microsoft.com/intune/device-sync)。</span><span class="sxs-lookup"><span data-stu-id="e2c76-181">[Sync the device to get the latest policies and actions with Intune](https://docs.microsoft.com/intune/device-sync).</span></span>
- <span data-ttu-id="e2c76-182">[用 Intune 远程重启设备](https://docs.microsoft.com/intune/device-restart)。</span><span class="sxs-lookup"><span data-stu-id="e2c76-182">[Remotely restart the device with Intune](https://docs.microsoft.com/intune/device-restart).</span></span>
