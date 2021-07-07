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
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a>在 Windows 中注册 IoT 核心Microsoft Intune

你的公司可以连同所有其他托管设备一起管理 IoT Core 设备。 这为你提供了一种使用 Intune 管理 IoT 核心、IoT Enterprise和其他Windows设备的方法。

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a>如何实现将 IoT Core 设备注册到 Intune？

使用 Windows IoT 核心仪表板准备设备，然后使用 Windows 配置设计器创建预配包，完成 IoT Core 设备的 Intune 注册。

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a>更改 Intune MDM 用户范围Azure AD

1. 登录到 [Azure 门户](https://portal.azure.com)，然后选择“Azure Active Directory”。
2. 选择“移动性 (MDM 和 MAM)”  。

     ![选择"移动性和Microsoft Intune](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)

3. 选择“Microsoft Intune”。 在"**配置Microsoft Intune"** 页上 **的"MDM 用户范围"旁边**，选择"全部 **"。** 这样，IoT Core 设备用户可以在加入设备后在 Intune Azure AD。

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a>为 IoT Core 设备创建安装 SD 卡

1. 将 microSD 卡插入电脑上的卡读卡器。
     > [!NOTE]
     > microSD 卡将在此过程中格式化，因此卡上的任何数据都将被删除。
2. 转到[Windows IoT 核心仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)下载并安装仪表板。
3. 安装仪表板后，打开它，然后选择 **"设置新设备"。**

     ![WindowsIoT 核心仪表板](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. 键入设备 **名称**。
5. 输入新的管理员密码。
6. 如果要为设备启用Wi-Fi，请选中 **"Wi-Fi 网络连接"** 复选框。 如果设备将仅使用以太网网络连接，请跳过此操作。

     ![Wi-Fi IoT 仪表板上的"设置"复选框](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. 选中"**我接受软件许可条款**"复选框，然后选择"**下载并安装"。**
8. 出现确认消息时，选择"设置 SD 卡格式"选项。 
     > [!NOTE]
     > 在安装过程中 **监视"格式** "确认消息。 该消息可能由另一个打开的应用程序隐藏，但选择"格式"选项很重要。 如果驱动器的格式不正确，启动将失败。
9. 将显示 **"SD 卡已准备就绪"** 消息。

     ![SD 卡就绪消息](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. 最小化此页。  稍后我们将返回到这里。

### <a name="create-a-provisioning-package-for-intune-enrollment"></a>为 Intune 注册创建预配包

1. 按照Windows配置设计器 中的步骤安装[Windows 配置设计应用](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)。

2. 打开 Windows **映像和配置设计器**。
3. 选择 **"预配桌面设备** "以创建项目。

     ![选择"预配桌面服务"](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. 输入Project **详细信息**"。 然后选择“完成”。
5. 转到"帐户 **管理"页**，然后选择"**在 Azure AD"。**
     > [!NOTE]
     > 从 ADK Microsoft Store或 Windows 评估和部署工具包 (应用) 正常。

     ![选择"在 Azure AD](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. 在" **批量令牌过期"旁边**，输入批量令牌到期日期。
7. 选择 **"获取批量令牌"。** 将出现一条登录消息，用于连接到 Azure AD。

     ![Azure AD 登录页](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. 输入租户用户名 (例如，) john@mycompany.onmicrosoft.com 密码。
9. 同意允许 Windows Configuration Design 应用访问Azure AD信息。
10. 页面上的消息显示已成功提取批量Azure AD令牌。

     ![批量令牌成功消息](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. 选择 **"切换到高级编辑器"，** 然后选择"*是"。*

     ![切换到高级编辑器确认页](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. 在 **"所选自定义项"** 下，保留 **"帐户设置** "，但删除所有其他设置：
13. 选择 **"OOBE"，** 然后选择"删除 **"。**
14. 如果 **列出了 SharedPC，** 请选择它，然后选择"删除 **"。**

     ![删除自定义项](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. 选择 **"导出**"，然后选择 **"预配包"。**

     ![选择预配包](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. 下一页上，接受默认设置，然后选择"下一 **步"。**
17. 同样，在下一页上接受默认设置，然后选择"下一步"。
18. 更改预配 **包目标** 或保留默认路径，然后选择"下一 **步"。**
19. 选择“生成”  。
20. 选择 **"输出位置** "链接，以便可以在 .ppkg 文件准备就绪时找到该文件。

     ![输出位置链接](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. 选择“完成”。
22. 转到文件资源管理器，将预配包复制到 IoT Core 设备。 将其保存到 **c：\windows\provisioning\packages** 文件夹中 **MainOS** 驱动器下的 microSD 卡。  必须授予权限才能将文件保存到此文件夹中。

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a>在 Intune 中预配和注册 IoT Core 设备

1. 将 microSD 卡插入 IoT Core 设备。
2. 打开 IoT Core 设备，并留出时间让设备启动并显示标准屏幕。
3. 返回到Microsoft Intune控制台Azure 门户。 设备应显示在设备列表中。
     > [!NOTE]
     > 注册可能需要 15 分钟或 15 分钟以上才能完成。

     ![Intune 设备列表](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a>后续步骤

- [请参阅 Intune 中的设备详细信息](https://docs.microsoft.com/intune/device-inventory)。
- [使用 Intune 同步设备，获取最新的策略和操作](https://docs.microsoft.com/intune/device-sync)。
- [使用 Intune 远程重启设备](https://docs.microsoft.com/intune/device-restart)。
