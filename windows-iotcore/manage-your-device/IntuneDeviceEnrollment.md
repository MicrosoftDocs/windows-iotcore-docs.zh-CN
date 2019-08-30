---
title: 在 Intune 中注册 Windows IoT Core 设备
author: msmimart
ms.author: mimart
ms.date: 05/08/2018
ms.topic: article
description: 了解如何使用 Microsoft Intune 设备管理和 Windows IoT 来管理设备。
keywords: windows iot, Azure IoT, Intune 设备管理, 设备管理
ms.openlocfilehash: 6a82eab36882e6e2cac830e711b2bba6d4fc95bb
ms.sourcegitcommit: 58f66754eecff826756b686b202c8e21d658bb9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/20/2019
ms.locfileid: "67277810"
---
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a>在 Microsoft Intune 中注册 Windows IoT Core 设备

你的公司可以管理 IoT 核心设备以及其他所有托管设备。 这为你提供了使用 Intune 管理 IoT Core、IoT Enterprise 和其他 Windows 设备的一致方式。

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a>如何实现将 IoT Core 设备注册到 Intune？

通过使用 Windows IoT 核心仪表板准备设备, 然后使用 Windows 配置设计器创建预配包, 可以完成 IoT 核心设备的 Intune 注册。

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a>在 Azure AD 中更改 Intune MDM 用户范围

1. 登录到[Azure 门户](https://portal.azure.com), 然后选择 " **Azure Active Directory**"。
2. 选择 "**移动性 (MDM 和 MAM)** "。

     ![选择移动性和 Microsoft Intune](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)

3. 选择**Microsoft Intune**。 在 "**配置 Microsoft Intune** " 页上的 " **MDM 用户范围**" 旁边, 选择 "**全部**"。 这将允许在加入 Azure AD 后, 在 Intune 中注册 IoT Core 设备用户。

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a>为 IoT 核心设备创建安装 SD 卡

1. 将 microSD 卡插入到电脑上的读卡器中。
     > [!NOTE]
     > 在此过程中, 将会设置 microSD 卡的格式, 因此卡上的所有数据都将被删除。
2. 请参阅 " [Windows IoT 核心" 仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)以下载并安装仪表板。
3. 安装仪表板后, 将其打开, 然后选择 "**设置新设备**"。

     ![Windows IoT 核心版仪表板](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. 键入**设备名称**。
5. 输入新的管理员密码。
6. 如果要为设备启用 Wi-fi, 请选中 " **Wi-fi 网络连接**" 复选框。 如果设备仅使用以太网网络连接, 则跳过此。

     ![IoT 面板上的 "wi-fi" 复选框](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. 选中 "**我接受软件许可条款**" 复选框, 然后选择 "**下载并安装**"。
8. 出现确认消息时, 请选择用于**格式化**SD 卡的选项。
     > [!NOTE]
     > 请在安装过程中监视**格式**确认消息。 其他打开的应用程序可能会隐藏该消息, 但请务必选择 Format 选项。 如果驱动器的格式不正确, 则 boot 将会失败。
9. 你的**SD 卡已就绪**的消息随即出现。

     ![SD 卡就绪消息](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. 最小化此页。  稍后你将返回到它。

### <a name="create-a-provisioning-package-for-intune-enrollment"></a>为 Intune 注册创建预配包

1. 按照[安装 Windows 配置设计器](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)中的步骤安装 Windows 配置设计应用。

2. 打开**Windows 映像和配置设计器**。
3. 选择 "**预配桌面设备**" 以创建项目。

     ![选择设置桌面服务](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. 根据需要输入**项目详细信息**。 然后选择 "**完成**"。
5. 请在 "**帐户管理**" 页上, 选择 "**注册 Azure AD**。
     > [!NOTE]
     > 可以从 Microsoft Store 或 Windows 评估和部署工具包 (ADK) 安装应用程序。

     ![选择注册 Azure AD](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. 在 "**批量令牌到期**" 旁边, 输入 "批量令牌到期日期"。
7. 选择 "**获取批量令牌**"。 此时将显示一个登录消息, 用于连接到 Azure AD。

     ![Azure AD 登录页](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. 输入租户用户名 (例如john@mycompany.onmicrosoft.com) 和密码。
9. 同意允许 Windows 配置设计应用访问你的 Azure AD 信息。
10. 页面上的消息显示已成功获取批量 AAD 令牌。

     ![批量令牌成功消息](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. 选择 "**切换到高级编辑器**", 然后选择 *"是"* 。

     ![切换到 "高级编辑器确认" 页](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. 在 "**所选自定义**" 下, 保留**帐户**设置, 但删除所有其他设置:
13. 选择 " **OOBE**", 然后选择 "**删除**"。
14. 如果**SharedPC**已列出, 请选择它, 然后选择 "**删除**"。

     ![删除自定义项](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. 选择 "**导出**", 然后选择 "**设置包**"。

     ![选择预配包](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. 在下一页上, 接受默认设置, 然后选择 "**下一步**"。
17. 同样, 在下一页上, 接受默认设置, 然后选择 "下一步"。
18. 更改**设置包**目标或保留默认路径, 然后选择 "**下一步**"。
19. 选择 "**生成**"。
20. 选择 "**输出位置**" 链接, 以便您可以在 ppkg 文件准备就绪时找到该文件。

     ![输出位置链接](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. 选择 "**完成**"。
22. 请在 "文件资源管理器" 中, 将预配包复制到 IoT Core 设备。 将其保存到**c:\windows\provisioning\packages**文件夹中**MainOS**驱动器下的 microSD 卡。  你将必须授予将文件保存到此文件夹的权限。

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a>在 Intune 中预配和注册 IoT Core 设备

1. 将 microSD 卡插入 IoT 核心设备。
2. 打开 IoT Core 设备, 并留出时间启动并显示标准屏幕。
3. 返回到 Azure 门户中的 Microsoft Intune 控制台。 设备应显示在设备列表中。
     > [!NOTE]
     > 注册可能需要15分钟或更长时间才能完成。

     ![Intune 设备列表](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a>后续步骤

- [请参阅 Intune 中的设备详细信息](https://docs.microsoft.com/intune/device-inventory)。
- [同步设备以通过 Intune 获取最新的策略和操作](https://docs.microsoft.com/intune/device-sync)。
- [用 Intune 远程重启设备](https://docs.microsoft.com/intune/device-restart)。
