---
title: 管理 Windows IoT Core 设备
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 了解管理 Windows 10 IoT Core 设备的不同方法。
keywords: windows iot, 设备管理, windows iot, Azure DM, Azure 集线器, Azure IoT
ms.openlocfilehash: dbcc6858ee32ce9eb8b33c3d1831a6581a8fa3c7
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60170852"
---
# <a name="managing-windows-iot-core-devices"></a>管理 Windows IoT Core 设备

可以使用支持基于证书的注册或使用 Azure IoT 中心的设备管理的传统 OMA DM MDM 服务器来管理 Windows 10 IoT Core 设备。  

 _[在此处](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)详细了解 MDM 和 Windows 10。_  

对于使用 OMA DM 服务器管理的设备, 适用于 Windows 10 IoT Core 的 MDM 策略与其他 Windows 10 版本中支持的策略一致。 若要详细了解 IoT Core 设备上的策略以及可管理的内容, 请参阅[此处](https://aka.ms/csplist)的 Windows 10 配置服务提供程序参考。 Windows 10 中的 MDM 支持基于开放移动联盟 (OMA) 设备管理 (DM) 协议1.2.1 规范。

## <a name="how-do-i-enroll-an-iot-core-device-into-a-mdm"></a>如何实现将 IoT Core 设备注册到 MDM？
___
使用预配包完成 IoT 核心设备的 MDM 注册。 可以使用 Windows 映像配置和设计器 (WICD) 创建预配包。 让我们尝试将设备注册到 MDM。

### <a name="creating-a-provisioning-package"></a>创建预配包

#### <a name="microsoft-system-center-configuration-manager-standalone-or-sccmintune-hybrid"></a>Microsoft System Center Configuration Manager (独立或 SCCM + Intune 混合)

1. 打开 Configuration Manager 管理控制台 (ConfigMgr 控制台)

2. 导航到 "_资产和符合性" > 符合性设置 > 公司资源访问 > 证书配置文件_
   ![证书配置文件](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)

3. 单击 "**创建证书配置文件**"

4. 提供配置文件的名称和描述
   - 名称：ConfigMgr 示例受信任的根证书
     - 证书配置文件的类型:受信任的 CA 证书  
     ![可信证书](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard.png)

5. 单击“下一步”。

6. 导入证书文件。

7. 选择 "**计算机证书存储区-** **目标存储**的根目录"。

8. 单击“下一步”。

9. 对于支持的平台![支持平台, 选择 "全选"](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)

10. 单击 "**摘要"、"下一步", 然后单击 "关闭**" 退出向导。

11. 右键单击刚创建的配置文件, 然后单击 "**导出**"。

12. 单击 "**浏览**", 找到应导出 ppkg 文件的位置, 然后单击 "**保存**"。

13. 单击 "**导出**", 然后单击 **"确定"** 退出向导。

#### <a name="other-mdm-servers"></a>其他 MDM 服务器

1. 下载并安装[Windows 评估和部署工具包 (WINDOWS ADK)](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit)。

2. 打开 Windows 映像和配置设计器 (WICD)。
   ![Windows 映像和配置设计器](../media/ManagingDevices/WICD-Start-Page.png)

3. 选择**高级设置**

4. 设置包的名称。

5. 选择 Windows 10 IoT Core 的通用设置。

6. 跳过 "导入包" 步骤。
   ![WICD--](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
   WICD-![-新项目-WICD--新建-项目-Import![](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
   ](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)

7. 导航到 "工作区-> 注册"。

8. UPN 字段中输入你想要注册设备下的帐户 (即trmck@contoso.co)，单击 **添加** 。

   ![已填充工作区注册](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Filled.png)

9. 对于 AuthPolicy, 请选择 "基于用户名的身份验证 (本地)" 或 "基于证书的身份验证"。

10. 输入 MDM 服务器的发现服务 URL。

> [!NOTE]
> 注册服务 URL 和策略服务 URL 是可选的。

11. 输入密码  
    - 本地要注册的帐户的密码  
    - 证书证书的指纹
    
    ![实心 OnPremise](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Details-Filled-Premise.png)  

12. 在 WICD 窗口的顶部, 单击 "**导出 > 预配包**"。

13. 提供包的名称和版本, 然后单击 "**下一步**"。 

> [!NOTE]
> 务必递增版本号, 以确保执行更新的包。

14. 在 "**安全详细信息" 页**上单击 "**下一步**"。

15. 选择要在本地计算机上导出包的位置, 并单击 "**下一步**"。

16. 单击 "**生成**", 然后单击 "**完成**" 退出向导。

### <a name="installing-the-provisioning-package"></a>安装预配包

可通过几种方法将预配包部署到 IoT 设备。 可以通过将包复制到设备, 或在映像过程中将包添加到映像来部署包。

#### <a name="copying-package-to-device"></a>将包复制到设备

获取从 SCCM 或 WICD 导出的预配包, 并将 ppkg 文件复制到`C:\Windows\Provisioning\Packages` IoT 设备上的目录。 设备重新启动时, 将执行包, 并且设备将启动注册过程。

#### <a name="adding-package-to-image"></a>将包添加到映像

请参阅[向映像添加预配包](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image)。 首次启动时, 设备将执行包并启动注册过程。
