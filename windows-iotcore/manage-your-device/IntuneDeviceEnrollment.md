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
# <a name="enrolling-windows-iot-core-devices-in-microsoft-intune"></a>在 Microsoft Intune 中注册 Windows IoT Core 设备

你的公司可以管理 IoT Core 设备以及所有其他受管理设备。 这为您提供了管理 IoT 核心版、 IoT 企业版和其他使用 Intune 在 Windows 设备的一致方法。

## <a name="how-do-i-enroll-an-iot-core-device-into-intune"></a>如何在 Intune 中注册 IoT Core 设备？

Intune 注册的 IoT Core 设备通过使用 Windows IoT Core 仪表板准备设备，，然后使用 Windows 配置设计器来创建预配包。

### <a name="change-the-intune-mdm-user-scope-in-azure-ad"></a>在 Azure AD 中更改 Intune MDM 用户作用域

1. 登录到[Azure 门户](https://portal.azure.com)，然后选择**Azure Active Directory**。
2. 选择**移动性 （MDM 和 MAM）** 。

     ![选择移动性和 Microsoft Intune](../media/IntuneDeviceEnrollment/iot-ap-mobility-intune.png)

3. 选择**Microsoft Intune**。 上**配置 Microsoft Intune**页上下, 一步**MDM 用户作用域**，选择**所有**。 这将允许 IoT Core 设备用户加入 Azure AD 后在 Intune 中注册。

### <a name="create-a-setup-sd-card-for-the-iot-core-device"></a>创建 IoT Core 设备安装程序 SD 卡

1. 将 microSD 卡插入读卡器在您的 PC 上。
     > [!NOTE]
     > 在此过程中，将格式化 microSD 卡，以便在卡上的任何数据将被删除。
2. 转到[Windows IoT Core 仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)下载并安装仪表板。
3. 在仪表板安装后，将其打开，并选择**设置新设备**。

     ![Windows IoT 核心版仪表板](../media/IntuneDeviceEnrollment/IoT-dashboard-my-devices.png)

4. 键入一个**设备名称**。
5. 输入新管理员密码。
6. 如果你想要为设备启用的 Wi-fi，请选择**Wi-fi 网络连接**复选框。 如果设备将使用仅限以太网网络连接，跳过此。

     ![Wi-fi IoT 仪表板上的复选框](../media/IntuneDeviceEnrollment/IoT-dashboard-wifi-connection.png)

7. 选择**我接受软件许可条款**复选框，然后选择**下载并安装**。
8. 出现确认消息时，选择选项**格式**SD 卡。
     > [!NOTE]
     > 观看有关**格式**在安装过程的确认消息。 该消息可能会隐藏另一个打开的应用程序，但务必要选择的格式选项。 如果驱动器不正确的格式，将无法启动。
9. 消息**Your SD 卡已准备好**出现。

     ![SD 卡准备消息](../media/IntuneDeviceEnrollment/IoT-dashboard-sd-card-ready.png)

10. 最小化此页。  你将稍后返回到它。

### <a name="create-a-provisioning-package-for-intune-enrollment"></a>创建用于 Intune 注册的预配包

1. 安装 Windows 配置设计应用程序中的步骤[安装 Windows 配置设计器](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)。

2. 打开**Windows 映像和配置设计器**。
3. 选择**桌面设备预配**创建项目。

     ![选择预配桌面服务](../media/IntuneDeviceEnrollment/iot-wcd-provision-desktop-devices.png)

4. 输入**项目详细信息**根据需要。 然后选择**完成**。
5. 转到**帐户管理**页，然后选择**在 Azure AD 中的注册**。
     > [!NOTE]
     > 从 Microsoft Store 或 Windows 评估和部署工具包 (ADK) 安装应用程序是没问题。

     ![选择在 Azure AD 中注册](../media/IntuneDeviceEnrollment/iot-wcd-enroll-in-azure-ad.png)

6. 下一步**批量令牌到期**，输入批量令牌到期日期。
7. 选择**获取批量令牌**。 连接到 Azure AD 会显示在登录消息。

     ![Azure AD 登录页](../media/IntuneDeviceEnrollment/iot-wcd-sign-in.png)

8. 输入你的租户用户名 (例如， john@mycompany.onmicrosoft.com) 和你的密码。
9. 同意允许 Windows 配置设计应用程序访问 Azure AD 信息。
10. 上的一条消息显示已成功提取了大容量 AAD 令牌。

     ![大容量令牌成功消息](../media/IntuneDeviceEnrollment/iot-wcd-bulk-token-successful.png)

11. 选择**切换到高级编辑器**，然后选择*是*。

     ![切换到高级的编辑器确认页](../media/IntuneDeviceEnrollment/iot-wcd-switch-to-advanced-editor.png)

12. 下**选择自定义项**，将保留**帐户**设置，但删除所有其他设置：
13. 选择**OOBE**，然后选择**删除**。
14. 如果**SharedPC**是列出，请选择它，并选择**删除**。

     ![删除自定义项](../media/IntuneDeviceEnrollment/iot-wcd-select-customizations.png)

15. 选择**导出**，然后选择**预配包**。

     ![选择预配包](../media/IntuneDeviceEnrollment/iot-wcd-export-provisioning-package.png)

16. 在下一页上，接受默认设置，然后选择**下一步**。
17. 同样，在下一页上，接受默认设置，然后选择下一步。
18. 更改**预配包**目标或保留默认路径，并选择**下一步**。
19. 选择**生成**。
20. 选择**输出位置**链接，以便准备就绪时，可以查找.ppkg 文件。

     ![输出位置链接](../media/IntuneDeviceEnrollment/iot-wcd-all-done.png)

21. 选择**完成**。
22. 转到文件资源管理器，并将预配包复制到你的 IoT Core 设备。 将其保存到 microSD 卡下**MainOS**推动**c:\windows\provisioning\packages**文件夹。  您必须授予此文件夹中将该文件的权限。

### <a name="provision-and-enroll-the-iot-core-device-in-intune"></a>预配并注册 Intune 中的 IoT Core 设备

1. 将 microSD 卡插入 IoT Core 设备。
2. 打开 IoT Core 设备并留出时间让它启动并显示标准的屏幕。
3. 返回到 Azure 门户中的 Microsoft Intune 控制台。 你的设备应显示在设备列表中。
     > [!NOTE]
     > 注册可能需要 15 分钟或更久。

     ![Intune 的设备列表](../media/IntuneDeviceEnrollment/iot-ap-devices-after-enrollment.png)

## <a name="next-steps"></a>后续步骤

- [在 Intune 中的设备详细信息请参阅](https://docs.microsoft.com/intune/device-inventory)。
- [同步设备以获取最新的策略和操作与 Intune](https://docs.microsoft.com/intune/device-sync)。
- [远程重启设备与 Intune](https://docs.microsoft.com/intune/device-restart)。
