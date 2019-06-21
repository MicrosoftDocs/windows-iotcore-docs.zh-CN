---
title: 注册在 Intune 中的 Windows IoT Core 设备
author: msmimart
ms.author: mimart
ms.date: 05/08/2018
ms.topic: article
description: 了解有关如何使用 Microsoft Intune 设备管理和 Windows IoT 管理设备。
keywords: windows iot，Azure IoT 中，Intune 设备管理，设备管理
ms.openlocfilehash: 6a82eab36882e6e2cac830e711b2bba6d4fc95bb
ms.sourcegitcommit: 58f66754eecff826756b686b202c8e21d658bb9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/20/2019
ms.locfileid: "67277810"
---
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a><span data-ttu-id="bddca-104">在 Microsoft Intune 中注册 Windows IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="bddca-104">Enrolling Windows IoT Core devices in Microsoft Intune</span></span>

<span data-ttu-id="bddca-105">你的公司可以管理 IoT Core 设备以及所有其他受管理设备。</span><span class="sxs-lookup"><span data-stu-id="bddca-105">Your company can manage IoT Core devices alongside all of your other managed devices.</span></span> <span data-ttu-id="bddca-106">这为您提供了管理 IoT 核心版、 IoT 企业版和其他使用 Intune 在 Windows 设备的一致方法。</span><span class="sxs-lookup"><span data-stu-id="bddca-106">This gives you a consistent way to manage IoT Core, IoT Enterprise, and other Windows devices using Intune.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a><span data-ttu-id="bddca-107">如何在 Intune 中注册 IoT Core 设备？</span><span class="sxs-lookup"><span data-stu-id="bddca-107">How do I enroll an IoT Core device into Intune?</span></span>

<span data-ttu-id="bddca-108">Intune 注册的 IoT Core 设备通过使用 Windows IoT Core 仪表板准备设备，，然后使用 Windows 配置设计器来创建预配包。</span><span class="sxs-lookup"><span data-stu-id="bddca-108">Intune enrollment of an IoT Core device is accomplished by using the Windows IoT Core Dashboard to prepare the device, and then using Windows Configuration Designer to create a provisioning package.</span></span>

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a><span data-ttu-id="bddca-109">在 Azure AD 中更改 Intune MDM 用户作用域</span><span class="sxs-lookup"><span data-stu-id="bddca-109">Change the Intune MDM user scope in Azure AD</span></span>

1. <span data-ttu-id="bddca-110">登录到[Azure 门户](https://portal.azure.com)，然后选择**Azure Active Directory**。</span><span class="sxs-lookup"><span data-stu-id="bddca-110">Sign in to the [Azure portal](https://portal.azure.com), and then select **Azure Active Directory**.</span></span>
2. <span data-ttu-id="bddca-111">选择**移动性 （MDM 和 MAM）** 。</span><span class="sxs-lookup"><span data-stu-id="bddca-111">Select **Mobility (MDM and MAM)**.</span></span>

     ![选择移动性和 Microsoft Intune](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)

3. <span data-ttu-id="bddca-113">选择**Microsoft Intune**。</span><span class="sxs-lookup"><span data-stu-id="bddca-113">Select **Microsoft Intune**.</span></span> <span data-ttu-id="bddca-114">上**配置 Microsoft Intune**页上下, 一步**MDM 用户作用域**，选择**所有**。</span><span class="sxs-lookup"><span data-stu-id="bddca-114">On the **Configure Microsoft Intune** page, next to **MDM user scope**, select **All**.</span></span> <span data-ttu-id="bddca-115">这将允许 IoT Core 设备用户加入 Azure AD 后在 Intune 中注册。</span><span class="sxs-lookup"><span data-stu-id="bddca-115">This will allow your IoT Core device user to be enrolled in Intune after joining Azure AD.</span></span>

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a><span data-ttu-id="bddca-116">创建 IoT Core 设备安装程序 SD 卡</span><span class="sxs-lookup"><span data-stu-id="bddca-116">Create a setup SD card for the IoT Core device</span></span>

1. <span data-ttu-id="bddca-117">将 microSD 卡插入读卡器在您的 PC 上。</span><span class="sxs-lookup"><span data-stu-id="bddca-117">Insert a microSD card into the card reader on your PC.</span></span>
     > [!NOTE]
     > <span data-ttu-id="bddca-118">在此过程中，将格式化 microSD 卡，以便在卡上的任何数据将被删除。</span><span class="sxs-lookup"><span data-stu-id="bddca-118">The microSD card will be formatted during this process, so any data on the card will be deleted.</span></span>
2. <span data-ttu-id="bddca-119">转到[Windows IoT Core 仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)下载并安装仪表板。</span><span class="sxs-lookup"><span data-stu-id="bddca-119">Go to [Windows IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) to download and install the dashboard.</span></span>
3. <span data-ttu-id="bddca-120">在仪表板安装后，将其打开，并选择**设置新设备**。</span><span class="sxs-lookup"><span data-stu-id="bddca-120">After the dashboard installs, open it and select **Set up a new device**.</span></span>

     ![Windows IoT 核心版仪表板](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. <span data-ttu-id="bddca-122">键入一个**设备名称**。</span><span class="sxs-lookup"><span data-stu-id="bddca-122">Type a **Device name**.</span></span>
5. <span data-ttu-id="bddca-123">输入新管理员密码。</span><span class="sxs-lookup"><span data-stu-id="bddca-123">Enter a new administrator password.</span></span>
6. <span data-ttu-id="bddca-124">如果你想要为设备启用的 Wi-fi，请选择**Wi-fi 网络连接**复选框。</span><span class="sxs-lookup"><span data-stu-id="bddca-124">If you want to enable Wi-Fi for the device, select the **Wi-Fi Network Connection** checkbox.</span></span> <span data-ttu-id="bddca-125">如果设备将使用仅限以太网网络连接，跳过此。</span><span class="sxs-lookup"><span data-stu-id="bddca-125">Skip this if the device will use an ethernet network connection only.</span></span>

     ![Wi-fi IoT 仪表板上的复选框](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. <span data-ttu-id="bddca-127">选择**我接受软件许可条款**复选框，然后选择**下载并安装**。</span><span class="sxs-lookup"><span data-stu-id="bddca-127">Select the **I accept the software license terms** checkbox, and then select **Download and Install**.</span></span>
8. <span data-ttu-id="bddca-128">出现确认消息时，选择选项**格式**SD 卡。</span><span class="sxs-lookup"><span data-stu-id="bddca-128">When the confirmation message appears, select the option to **Format** the SD Card.</span></span>
     > [!NOTE]
     > <span data-ttu-id="bddca-129">观看有关**格式**在安装过程的确认消息。</span><span class="sxs-lookup"><span data-stu-id="bddca-129">Watch for the **Format** confirmation message during setup.</span></span> <span data-ttu-id="bddca-130">该消息可能会隐藏另一个打开的应用程序，但务必要选择的格式选项。</span><span class="sxs-lookup"><span data-stu-id="bddca-130">The message could be hidden by another open application, but it’s important to select the Format option.</span></span> <span data-ttu-id="bddca-131">如果驱动器不正确的格式，将无法启动。</span><span class="sxs-lookup"><span data-stu-id="bddca-131">If the drive isn't properly formatted, boot will fail.</span></span>
9. <span data-ttu-id="bddca-132">消息**Your SD 卡已准备好**出现。</span><span class="sxs-lookup"><span data-stu-id="bddca-132">The message **Your SD card is ready** appears.</span></span>

     ![SD 卡准备消息](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. <span data-ttu-id="bddca-134">最小化此页。</span><span class="sxs-lookup"><span data-stu-id="bddca-134">Minimize this page.</span></span>  <span data-ttu-id="bddca-135">你将稍后返回到它。</span><span class="sxs-lookup"><span data-stu-id="bddca-135">You'll come back to it later.</span></span>

### <a name="create-a-provisioning-package-for-intune-enrollment"></a><span data-ttu-id="bddca-136">创建用于 Intune 注册的预配包</span><span class="sxs-lookup"><span data-stu-id="bddca-136">Create a provisioning package for Intune enrollment</span></span>

1. <span data-ttu-id="bddca-137">安装 Windows 配置设计应用程序中的步骤[安装 Windows 配置设计器](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)。</span><span class="sxs-lookup"><span data-stu-id="bddca-137">Install the Windows Configuration Design app by following the steps in [Install Windows Configuration Designer](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).</span></span>

2. <span data-ttu-id="bddca-138">打开**Windows 映像和配置设计器**。</span><span class="sxs-lookup"><span data-stu-id="bddca-138">Open the **Windows Imaging and Configuration Designer**.</span></span>
3. <span data-ttu-id="bddca-139">选择**桌面设备预配**创建项目。</span><span class="sxs-lookup"><span data-stu-id="bddca-139">Choose **Provision desktop devices** to create a project.</span></span>

     ![选择预配桌面服务](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. <span data-ttu-id="bddca-141">输入**项目详细信息**根据需要。</span><span class="sxs-lookup"><span data-stu-id="bddca-141">Enter the **Project Details** as desired.</span></span> <span data-ttu-id="bddca-142">然后选择**完成**。</span><span class="sxs-lookup"><span data-stu-id="bddca-142">Then select **Finish**.</span></span>
5. <span data-ttu-id="bddca-143">转到**帐户管理**页，然后选择**在 Azure AD 中的注册**。</span><span class="sxs-lookup"><span data-stu-id="bddca-143">Go to the **Account Management** page and select **Enroll in Azure AD**.</span></span>
     > [!NOTE]
     > <span data-ttu-id="bddca-144">从 Microsoft Store 或 Windows 评估和部署工具包 (ADK) 安装应用程序是没问题。</span><span class="sxs-lookup"><span data-stu-id="bddca-144">Installing the app from either the Microsoft Store or the Windows Assessment and Deployment Kit (ADK) is fine.</span></span>

     ![选择在 Azure AD 中注册](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. <span data-ttu-id="bddca-146">下一步**批量令牌到期**，输入批量令牌到期日期。</span><span class="sxs-lookup"><span data-stu-id="bddca-146">Next to **Bulk Token Expiry**, enter a bulk token expiry date.</span></span>
7. <span data-ttu-id="bddca-147">选择**获取批量令牌**。</span><span class="sxs-lookup"><span data-stu-id="bddca-147">Select **Get Bulk Token**.</span></span> <span data-ttu-id="bddca-148">连接到 Azure AD 会显示在登录消息。</span><span class="sxs-lookup"><span data-stu-id="bddca-148">A sign-in message appears for connecting to Azure AD.</span></span>

     ![Azure AD 登录页](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. <span data-ttu-id="bddca-150">输入你的租户用户名 (例如， john@mycompany.onmicrosoft.com) 和你的密码。</span><span class="sxs-lookup"><span data-stu-id="bddca-150">Enter your tenant username (for example, john@mycompany.onmicrosoft.com) and your password.</span></span>
9. <span data-ttu-id="bddca-151">同意允许 Windows 配置设计应用程序访问 Azure AD 信息。</span><span class="sxs-lookup"><span data-stu-id="bddca-151">Agree to allow the Windows Configuration Design app to access your Azure AD information.</span></span>
10. <span data-ttu-id="bddca-152">上的一条消息显示已成功提取了大容量 AAD 令牌。</span><span class="sxs-lookup"><span data-stu-id="bddca-152">A message on the page shows that the Bulk AAD token was fetched successfully.</span></span>

     ![大容量令牌成功消息](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. <span data-ttu-id="bddca-154">选择**切换到高级编辑器**，然后选择*是*。</span><span class="sxs-lookup"><span data-stu-id="bddca-154">Select **Switch to advanced editor**, and then select *Yes*.</span></span>

     ![切换到高级的编辑器确认页](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. <span data-ttu-id="bddca-156">下**选择自定义项**，将保留**帐户**设置，但删除所有其他设置：</span><span class="sxs-lookup"><span data-stu-id="bddca-156">Under **Selected customizations**, Leave the **Account** settings, but remove all other settings:</span></span>
13. <span data-ttu-id="bddca-157">选择**OOBE**，然后选择**删除**。</span><span class="sxs-lookup"><span data-stu-id="bddca-157">Select **OOBE**, and then select **Remove**.</span></span>
14. <span data-ttu-id="bddca-158">如果**SharedPC**是列出，请选择它，并选择**删除**。</span><span class="sxs-lookup"><span data-stu-id="bddca-158">If **SharedPC** is listed, select it, and then select **Remove**.</span></span>

     ![删除自定义项](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. <span data-ttu-id="bddca-160">选择**导出**，然后选择**预配包**。</span><span class="sxs-lookup"><span data-stu-id="bddca-160">Select **Export**, and then choose **Provisioning package**.</span></span>

     ![选择预配包](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. <span data-ttu-id="bddca-162">在下一页上，接受默认设置，然后选择**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bddca-162">On the next page, accept the default settings and select **Next**.</span></span>
17. <span data-ttu-id="bddca-163">同样，在下一页上，接受默认设置，然后选择下一步。</span><span class="sxs-lookup"><span data-stu-id="bddca-163">Again, on the next page, accept the default settings and select Next.</span></span>
18. <span data-ttu-id="bddca-164">更改**预配包**目标或保留默认路径，并选择**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bddca-164">Change the **Provisioning Package** destination or leave the default path, and then select **Next**.</span></span>
19. <span data-ttu-id="bddca-165">选择**生成**。</span><span class="sxs-lookup"><span data-stu-id="bddca-165">Select **Build**.</span></span>
20. <span data-ttu-id="bddca-166">选择**输出位置**链接，以便准备就绪时，可以查找.ppkg 文件。</span><span class="sxs-lookup"><span data-stu-id="bddca-166">Select the **Output Location** link so that you can locate the .ppkg file when it's ready.</span></span>

     ![输出位置链接](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. <span data-ttu-id="bddca-168">选择**完成**。</span><span class="sxs-lookup"><span data-stu-id="bddca-168">Select **Finish**.</span></span>
22. <span data-ttu-id="bddca-169">转到文件资源管理器，并将预配包复制到你的 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="bddca-169">Go to File Explorer and copy the provisioning package to your IoT Core device.</span></span> <span data-ttu-id="bddca-170">将其保存到 microSD 卡下**MainOS**推动**c:\windows\provisioning\packages**文件夹。</span><span class="sxs-lookup"><span data-stu-id="bddca-170">Save it to the microSD card under the **MainOS** drive in the **c:\windows\provisioning\packages** folder.</span></span>  <span data-ttu-id="bddca-171">您必须授予此文件夹中将该文件的权限。</span><span class="sxs-lookup"><span data-stu-id="bddca-171">You'll have to grant permissions to save the file in this folder.</span></span>

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a><span data-ttu-id="bddca-172">预配并注册 Intune 中的 IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="bddca-172">Provision and enroll the IoT Core device in Intune</span></span>

1. <span data-ttu-id="bddca-173">将 microSD 卡插入 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="bddca-173">Insert the microSD card into your IoT Core device.</span></span>
2. <span data-ttu-id="bddca-174">打开 IoT Core 设备并留出时间让它启动并显示标准的屏幕。</span><span class="sxs-lookup"><span data-stu-id="bddca-174">Turn on your IoT Core device and allow time for it to start up and display the standard screen.</span></span>
3. <span data-ttu-id="bddca-175">返回到 Azure 门户中的 Microsoft Intune 控制台。</span><span class="sxs-lookup"><span data-stu-id="bddca-175">Return to the Microsoft Intune console in the Azure portal.</span></span> <span data-ttu-id="bddca-176">你的设备应显示在设备列表中。</span><span class="sxs-lookup"><span data-stu-id="bddca-176">Your device should appear in the list of devices.</span></span>
     > [!NOTE]
     > <span data-ttu-id="bddca-177">注册可能需要 15 分钟或更久。</span><span class="sxs-lookup"><span data-stu-id="bddca-177">Enrollment could take 15 minutes or more to complete.</span></span>

     ![Intune 的设备列表](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a><span data-ttu-id="bddca-179">后续步骤</span><span class="sxs-lookup"><span data-stu-id="bddca-179">Next steps</span></span>

- <span data-ttu-id="bddca-180">[在 Intune 中的设备详细信息请参阅](https://docs.microsoft.com/intune/device-inventory)。</span><span class="sxs-lookup"><span data-stu-id="bddca-180">[See device details in Intune](https://docs.microsoft.com/intune/device-inventory).</span></span>
- <span data-ttu-id="bddca-181">[同步设备以获取最新的策略和操作与 Intune](https://docs.microsoft.com/intune/device-sync)。</span><span class="sxs-lookup"><span data-stu-id="bddca-181">[Sync the device to get the latest policies and actions with Intune](https://docs.microsoft.com/intune/device-sync).</span></span>
- <span data-ttu-id="bddca-182">[远程重启设备与 Intune](https://docs.microsoft.com/intune/device-restart)。</span><span class="sxs-lookup"><span data-stu-id="bddca-182">[Remotely restart the device with Intune](https://docs.microsoft.com/intune/device-restart).</span></span>
