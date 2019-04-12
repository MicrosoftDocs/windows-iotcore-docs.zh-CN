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
# <a name="managing-windows-iot-core-devices"></a>管理 Windows IoT Core 设备

Windows 10 IoT Core 设备可以使用支持基于证书注册的传统 OMA DM MDM 服务器或使用 Azure IoT 中心设备管理进行管理。  

 _详细了解 MDM 和 Windows 10[此处](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)。_  

使用 OMA DM 服务器管理的设备的 Windows 10 IoT Core 的 MDM 策略与在其他版本的 Windows 10 中受支持的策略保持一致。 若要了解更多的策略以及为什么可以管理在 IoT Core 设备上，请参阅适用于 Windows 10 配置服务提供程序参考[此处](https://aka.ms/csplist)。 Windows 10 中的 MDM 支持基于开放移动联盟 (OMA) 设备管理 (DM) 协议 1.2.1 规范。

## <a name="how-do-i-enroll-an-iot-core-device-into-a-mdm"></a>如何到 MDM 注册 IoT Core 设备？
___
MDM 注册的 IoT Core 设备被通过预配包。 可以使用 Windows 映像配置和设计器 (WICD) 创建预配包。 让我们尝试设备注册到 mdm。

### <a name="creating-a-provisioning-package"></a>创建预配包

#### <a name="microsoft-system-center-configuration-manager-standalone-or-sccmintune-hybrid"></a>Microsoft System Center Configuration Manager （独立或 SCCM + Intune 混合版）

1. 打开 Configuration Manager 管理控制台 （ConfigMgr 控制台）

2. 导航到_资产和符合性 > 符合性设置 > 公司资源访问 > 的证书配置文件_
   ![的证书配置文件](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)

3. 单击**创建证书配置文件**

4. 提供名称和配置文件说明
   - 名称：ConfigMgr 示例受信任的根证书
     - 证书配置文件的类型：受信任的 CA 证书  
     ![受信任的证书](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard.png)

5. 单击“下一步” 。

6. 导入的证书文件。

7. 选择**计算机证书存储区-根**有关**目标存储区**。

8. 单击“下一步” 。

9. 选择**全**支持的平台为![受支持的平台](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)

10. 单击**摘要、 下一步，并关闭**以退出向导。

11. 右键单击刚创建的配置文件，然后单击**导出**。

12. 单击**浏览**，找到的位置，其中.ppkg 文件应导出，然后单击**保存**。

13. 单击**导出**然后单击**确定**以退出向导。

#### <a name="other-mdm-servers"></a>其他 MDM 服务器

1. 下载并安装[Windows 评估和部署工具包 (Windows ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit)。

2. 打开 Windows 映像和配置设计器 (WICD)。
   ![Windows 映像和配置设计器](../media/ManagingDevices/WICD-Start-Page.png)

3. 选择**高级预配**

4. 设置包的名称。

5. 选择设置普遍适用于 Windows 10 IoT Core。

6. 跳过导入包步骤。
   ![WICD-New-Project-Details](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
   ![WICD-New-Project-Editions](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
   ![WICD-New-Project-Import](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)

7. 导航到工作区-> 注册。

8. UPN 字段中输入你想要注册设备下的帐户 (即trmck@contoso.co)，单击**添加**。

   ![填充工作区注册](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Filled.png)

9. AuthPolicy 之间进行选择的用户名密码基于身份验证 （本地） 或基于证书的身份验证。

10. 输入 MDM 服务器的发现服务 URL。

> [!NOTE]
> 注册服务 URL 和策略服务 URL 是可选的。

11. 有关机密的 enter 键  
    - 本地：要注册与帐户的密码  
    - 证书：证书的指纹
    
    ![填充的 OnPremise](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Details-Filled-Premise.png)  

12. 单击 WICD 窗口顶部**导出 > 预配包**。

13. 为包提供名称和版本，然后单击**下一步**。 

> [!NOTE]
> 请确保递增版本号，以确保在执行更新的包。

14. 单击**下一步**上**安全详细信息页**。

15. 选择包将在本地计算机上单击要导出的位置**下一步**。

16. 单击**构建**，然后**完成**以退出向导。

### <a name="installing-the-provisioning-package"></a>安装预配包

有几种方法在其中预配包可部署到 IoT 设备。 就可以通过将包复制到设备或映像创建过程中将包添加到映像部署的包。

#### <a name="copying-package-to-device"></a>将包复制到设备

获取已从 SCCM 或 WICD 导出预配程序包并复制到.ppkg 文件`C:\Windows\Provisioning\Packages`IoT 设备目录。 在设备的重新启动时执行包，设备会开始注册过程。

#### <a name="adding-package-to-image"></a>将包添加到映像

请参阅[向映像添加预配包](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image)。 首次启动时设备将执行包并启动注册流程。
