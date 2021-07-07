---
title: 在 Intune Windows IoT 核心设备
author: msmimart
ms.author: mimart
ms.date: 05/08/2018
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 IoT Microsoft Intune 设备管理 Windows设备。
keywords: windows iot、Azure IoT、Intune 设备管理、设备管理
ms.openlocfilehash: 6f62981d9eebff493eeccdc65b75d9cf67522a07
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229494"
---
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a><span data-ttu-id="fdd9b-104">在 Windows 中注册 IoT 核心Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="fdd9b-104">Enrolling Windows IoT Core devices in Microsoft Intune</span></span>

<span data-ttu-id="fdd9b-105">你的公司可以连同所有其他托管设备一起管理 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-105">Your company can manage IoT Core devices alongside all of your other managed devices.</span></span> <span data-ttu-id="fdd9b-106">这为你提供了一种使用 Intune 管理 IoT 核心、IoT Enterprise和其他Windows设备的方法。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-106">This gives you a consistent way to manage IoT Core, IoT Enterprise, and other Windows devices using Intune.</span></span>

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a><span data-ttu-id="fdd9b-107">如何实现将 IoT Core 设备注册到 Intune？</span><span class="sxs-lookup"><span data-stu-id="fdd9b-107">How do I enroll an IoT Core device into Intune?</span></span>

<span data-ttu-id="fdd9b-108">使用 Windows IoT 核心仪表板准备设备，然后使用 Windows 配置设计器创建预配包，完成 IoT Core 设备的 Intune 注册。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-108">Intune enrollment of an IoT Core device is accomplished by using the Windows IoT Core Dashboard to prepare the device, and then using Windows Configuration Designer to create a provisioning package.</span></span>

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a><span data-ttu-id="fdd9b-109">更改 Intune MDM 用户范围Azure AD</span><span class="sxs-lookup"><span data-stu-id="fdd9b-109">Change the Intune MDM user scope in Azure AD</span></span>

1. <span data-ttu-id="fdd9b-110">登录到 [Azure 门户](https://portal.azure.com)，然后选择“Azure Active Directory”。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-110">Sign in to the [Azure portal](https://portal.azure.com), and then select **Azure Active Directory**.</span></span>
2. <span data-ttu-id="fdd9b-111">选择“移动性 (MDM 和 MAM)”  。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-111">Select **Mobility (MDM and MAM)**.</span></span>

     ![选择"移动性和Microsoft Intune](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)

3. <span data-ttu-id="fdd9b-113">选择“Microsoft Intune”。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-113">Select **Microsoft Intune**.</span></span> <span data-ttu-id="fdd9b-114">在"**配置Microsoft Intune"** 页上 **的"MDM 用户范围"旁边**，选择"全部 **"。**</span><span class="sxs-lookup"><span data-stu-id="fdd9b-114">On the **Configure Microsoft Intune** page, next to **MDM user scope**, select **All**.</span></span> <span data-ttu-id="fdd9b-115">这样，IoT Core 设备用户可以在加入设备后在 Intune Azure AD。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-115">This will allow your IoT Core device user to be enrolled in Intune after joining Azure AD.</span></span>

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a><span data-ttu-id="fdd9b-116">为 IoT Core 设备创建安装 SD 卡</span><span class="sxs-lookup"><span data-stu-id="fdd9b-116">Create a setup SD card for the IoT Core device</span></span>

1. <span data-ttu-id="fdd9b-117">将 microSD 卡插入电脑上的卡读卡器。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-117">Insert a microSD card into the card reader on your PC.</span></span>
     > [!NOTE]
     > <span data-ttu-id="fdd9b-118">microSD 卡将在此过程中格式化，因此卡上的任何数据都将被删除。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-118">The microSD card will be formatted during this process, so any data on the card will be deleted.</span></span>
2. <span data-ttu-id="fdd9b-119">转到[Windows IoT 核心仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)下载并安装仪表板。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-119">Go to [Windows IoT Core Dashboard](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard) to download and install the dashboard.</span></span>
3. <span data-ttu-id="fdd9b-120">安装仪表板后，打开它，然后选择 **"设置新设备"。**</span><span class="sxs-lookup"><span data-stu-id="fdd9b-120">After the dashboard installs, open it and select **Set up a new device**.</span></span>

     ![WindowsIoT 核心仪表板](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. <span data-ttu-id="fdd9b-122">键入设备 **名称**。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-122">Type a **Device name**.</span></span>
5. <span data-ttu-id="fdd9b-123">输入新的管理员密码。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-123">Enter a new administrator password.</span></span>
6. <span data-ttu-id="fdd9b-124">如果要为设备启用Wi-Fi，请选中 **"Wi-Fi 网络连接"** 复选框。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-124">If you want to enable Wi-Fi for the device, select the **Wi-Fi Network Connection** checkbox.</span></span> <span data-ttu-id="fdd9b-125">如果设备将仅使用以太网网络连接，请跳过此操作。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-125">Skip this if the device will use an ethernet network connection only.</span></span>

     ![Wi-Fi IoT 仪表板上的"设置"复选框](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. <span data-ttu-id="fdd9b-127">选中"**我接受软件许可条款**"复选框，然后选择"**下载并安装"。**</span><span class="sxs-lookup"><span data-stu-id="fdd9b-127">Select the **I accept the software license terms** checkbox, and then select **Download and Install**.</span></span>
8. <span data-ttu-id="fdd9b-128">出现确认消息时，选择"设置 SD 卡格式"选项。 </span><span class="sxs-lookup"><span data-stu-id="fdd9b-128">When the confirmation message appears, select the option to **Format** the SD Card.</span></span>
     > [!NOTE]
     > <span data-ttu-id="fdd9b-129">在安装过程中 **监视"格式** "确认消息。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-129">Watch for the **Format** confirmation message during setup.</span></span> <span data-ttu-id="fdd9b-130">该消息可能由另一个打开的应用程序隐藏，但选择"格式"选项很重要。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-130">The message could be hidden by another open application, but it’s important to select the Format option.</span></span> <span data-ttu-id="fdd9b-131">如果驱动器的格式不正确，启动将失败。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-131">If the drive isn't properly formatted, boot will fail.</span></span>
9. <span data-ttu-id="fdd9b-132">将显示 **"SD 卡已准备就绪"** 消息。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-132">The message **Your SD card is ready** appears.</span></span>

     ![SD 卡就绪消息](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. <span data-ttu-id="fdd9b-134">最小化此页。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-134">Minimize this page.</span></span>  <span data-ttu-id="fdd9b-135">稍后我们将返回到这里。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-135">You'll come back to it later.</span></span>

### <a name="create-a-provisioning-package-for-intune-enrollment"></a><span data-ttu-id="fdd9b-136">为 Intune 注册创建预配包</span><span class="sxs-lookup"><span data-stu-id="fdd9b-136">Create a provisioning package for Intune enrollment</span></span>

1. <span data-ttu-id="fdd9b-137">按照Windows配置设计器 中的步骤安装[Windows 配置设计应用](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-137">Install the Windows Configuration Design app by following the steps in [Install Windows Configuration Designer](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd).</span></span>

2. <span data-ttu-id="fdd9b-138">打开 Windows **映像和配置设计器**。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-138">Open the **Windows Imaging and Configuration Designer**.</span></span>
3. <span data-ttu-id="fdd9b-139">选择 **"预配桌面设备** "以创建项目。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-139">Choose **Provision desktop devices** to create a project.</span></span>

     ![选择"预配桌面服务"](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. <span data-ttu-id="fdd9b-141">输入Project **详细信息**"。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-141">Enter the **Project Details** as desired.</span></span> <span data-ttu-id="fdd9b-142">然后选择“完成”。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-142">Then select **Finish**.</span></span>
5. <span data-ttu-id="fdd9b-143">转到"帐户 **管理"页**，然后选择"**在 Azure AD"。**</span><span class="sxs-lookup"><span data-stu-id="fdd9b-143">Go to the **Account Management** page and select **Enroll in Azure AD**.</span></span>
     > [!NOTE]
     > <span data-ttu-id="fdd9b-144">从 ADK Microsoft Store或 Windows 评估和部署工具包 (应用) 正常。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-144">Installing the app from either the Microsoft Store or the Windows Assessment and Deployment Kit (ADK) is fine.</span></span>

     ![选择"在 Azure AD](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. <span data-ttu-id="fdd9b-146">在" **批量令牌过期"旁边**，输入批量令牌到期日期。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-146">Next to **Bulk Token Expiry**, enter a bulk token expiry date.</span></span>
7. <span data-ttu-id="fdd9b-147">选择 **"获取批量令牌"。**</span><span class="sxs-lookup"><span data-stu-id="fdd9b-147">Select **Get Bulk Token**.</span></span> <span data-ttu-id="fdd9b-148">将出现一条登录消息，用于连接到 Azure AD。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-148">A sign-in message appears for connecting to Azure AD.</span></span>

     ![Azure AD 登录页](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. <span data-ttu-id="fdd9b-150">输入租户用户名 (例如，) john@mycompany.onmicrosoft.com 密码。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-150">Enter your tenant username (for example, john@mycompany.onmicrosoft.com) and your password.</span></span>
9. <span data-ttu-id="fdd9b-151">同意允许 Windows Configuration Design 应用访问Azure AD信息。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-151">Agree to allow the Windows Configuration Design app to access your Azure AD information.</span></span>
10. <span data-ttu-id="fdd9b-152">页面上的消息显示已成功提取批量Azure AD令牌。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-152">A message on the page shows that the Bulk Azure AD token was fetched successfully.</span></span>

     ![批量令牌成功消息](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. <span data-ttu-id="fdd9b-154">选择 **"切换到高级编辑器"，** 然后选择"*是"。*</span><span class="sxs-lookup"><span data-stu-id="fdd9b-154">Select **Switch to advanced editor**, and then select *Yes*.</span></span>

     ![切换到高级编辑器确认页](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. <span data-ttu-id="fdd9b-156">在 **"所选自定义项"** 下，保留 **"帐户设置** "，但删除所有其他设置：</span><span class="sxs-lookup"><span data-stu-id="fdd9b-156">Under **Selected customizations**, Leave the **Account** settings, but remove all other settings:</span></span>
13. <span data-ttu-id="fdd9b-157">选择 **"OOBE"，** 然后选择"删除 **"。**</span><span class="sxs-lookup"><span data-stu-id="fdd9b-157">Select **OOBE**, and then select **Remove**.</span></span>
14. <span data-ttu-id="fdd9b-158">如果 **列出了 SharedPC，** 请选择它，然后选择"删除 **"。**</span><span class="sxs-lookup"><span data-stu-id="fdd9b-158">If **SharedPC** is listed, select it, and then select **Remove**.</span></span>

     ![删除自定义项](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. <span data-ttu-id="fdd9b-160">选择 **"导出**"，然后选择 **"预配包"。**</span><span class="sxs-lookup"><span data-stu-id="fdd9b-160">Select **Export**, and then choose **Provisioning package**.</span></span>

     ![选择预配包](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. <span data-ttu-id="fdd9b-162">下一页上，接受默认设置，然后选择"下一 **步"。**</span><span class="sxs-lookup"><span data-stu-id="fdd9b-162">On the next page, accept the default settings and select **Next**.</span></span>
17. <span data-ttu-id="fdd9b-163">同样，在下一页上接受默认设置，然后选择"下一步"。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-163">Again, on the next page, accept the default settings and select Next.</span></span>
18. <span data-ttu-id="fdd9b-164">更改预配 **包目标** 或保留默认路径，然后选择"下一 **步"。**</span><span class="sxs-lookup"><span data-stu-id="fdd9b-164">Change the **Provisioning Package** destination or leave the default path, and then select **Next**.</span></span>
19. <span data-ttu-id="fdd9b-165">选择“生成”  。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-165">Select **Build**.</span></span>
20. <span data-ttu-id="fdd9b-166">选择 **"输出位置** "链接，以便可以在 .ppkg 文件准备就绪时找到该文件。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-166">Select the **Output Location** link so that you can locate the .ppkg file when it's ready.</span></span>

     ![输出位置链接](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. <span data-ttu-id="fdd9b-168">选择“完成”。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-168">Select **Finish**.</span></span>
22. <span data-ttu-id="fdd9b-169">转到文件资源管理器，将预配包复制到 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-169">Go to File Explorer and copy the provisioning package to your IoT Core device.</span></span> <span data-ttu-id="fdd9b-170">将其保存到 **c：\windows\provisioning\packages** 文件夹中 **MainOS** 驱动器下的 microSD 卡。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-170">Save it to the microSD card under the **MainOS** drive in the **c:\windows\provisioning\packages** folder.</span></span>  <span data-ttu-id="fdd9b-171">必须授予权限才能将文件保存到此文件夹中。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-171">You'll have to grant permissions to save the file in this folder.</span></span>

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a><span data-ttu-id="fdd9b-172">在 Intune 中预配和注册 IoT Core 设备</span><span class="sxs-lookup"><span data-stu-id="fdd9b-172">Provision and enroll the IoT Core device in Intune</span></span>

1. <span data-ttu-id="fdd9b-173">将 microSD 卡插入 IoT Core 设备。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-173">Insert the microSD card into your IoT Core device.</span></span>
2. <span data-ttu-id="fdd9b-174">打开 IoT Core 设备，并留出时间让设备启动并显示标准屏幕。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-174">Turn on your IoT Core device and allow time for it to start up and display the standard screen.</span></span>
3. <span data-ttu-id="fdd9b-175">返回到Microsoft Intune控制台Azure 门户。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-175">Return to the Microsoft Intune console in the Azure portal.</span></span> <span data-ttu-id="fdd9b-176">设备应显示在设备列表中。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-176">Your device should appear in the list of devices.</span></span>
     > [!NOTE]
     > <span data-ttu-id="fdd9b-177">注册可能需要 15 分钟或 15 分钟以上才能完成。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-177">Enrollment could take 15 minutes or more to complete.</span></span>

     ![Intune 设备列表](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a><span data-ttu-id="fdd9b-179">后续步骤</span><span class="sxs-lookup"><span data-stu-id="fdd9b-179">Next steps</span></span>

- <span data-ttu-id="fdd9b-180">[请参阅 Intune 中的设备详细信息](https://docs.microsoft.com/intune/device-inventory)。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-180">[See device details in Intune](https://docs.microsoft.com/intune/device-inventory).</span></span>
- <span data-ttu-id="fdd9b-181">[使用 Intune 同步设备，获取最新的策略和操作](https://docs.microsoft.com/intune/device-sync)。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-181">[Sync the device to get the latest policies and actions with Intune](https://docs.microsoft.com/intune/device-sync).</span></span>
- <span data-ttu-id="fdd9b-182">[使用 Intune 远程重启设备](https://docs.microsoft.com/intune/device-restart)。</span><span class="sxs-lookup"><span data-stu-id="fdd9b-182">[Remotely restart the device with Intune](https://docs.microsoft.com/intune/device-restart).</span></span>
