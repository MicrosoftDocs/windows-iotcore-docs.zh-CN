---
title: 管理Windows IoT 核心设备
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解管理设备Windows 10 IoT 核心版方法，例如使用支持基于证书注册的传统 OMA DM MDM 服务器。
keywords: windows iot， 设备管理， windows iot， Azure DM， Azure 中心， Azure IoT
ms.openlocfilehash: bb8ac34bbb7f759faef2d4b72e1315bd3f28d071
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113228733"
---
# <a name="managing-windows-iot-core-devices"></a>管理Windows IoT 核心设备

Windows 10 IoT 核心版使用支持基于证书的注册的传统 OMA DM MDM 服务器，或者使用 Azure IoT 中心的设备管理设备管理。  

 _在此处详细了解 MDM 和 [Windows 10。](https://msdn.microsoft.com/library/windows/hardware/dn914769(v=vs.85).aspx)_  

对于使用 OMA DM 服务器管理的设备，WINDOWS 10 IOT 核心版的 MDM 策略与其他版本版本支持的策略Windows 10。 若要详细了解策略以及可在 IoT 核心设备上管理哪些内容，请参阅此处的配置服务提供程序Windows 10[参考](https://aka.ms/csplist)。 WINDOWS 10 中的 MDM 支持基于开放移动 (OMA) 设备管理 (DM) 协议 1.2.1 规范。

## <a name="how-do-i-enroll-an-iot-core-device-into-a-mdm"></a>如何实现将 IoT Core 设备注册到 MDM？
___
IoT Core 设备的 MDM 注册是使用预配包完成的。 预配包可以使用 WICD Windows映像配置和设计器 (创建) 。 让我们尝试将设备注册到 MDM。

### <a name="creating-a-provisioning-package"></a>创建预配包

#### <a name="microsoft-system-center-configuration-manager-standalone-or-sccmintune-hybrid"></a>Microsoft System Center Configuration Manager (独立版或 SCCM+Intune 混合) 

1. 打开 配置服务器 Management Console (ConfigMgr 控制台) 

2. 导航到 _"资产和符合性>合规性设置 >"公司资源访问>证书配置文件_ 
    ![ "](../media/ManagingDevices/ConfigMgr-Certificate-Profiles.PNG)

3. 单击 **"创建证书配置文件"**

4. 提供配置文件的名称和说明
   - 名称：ConfigMgr 示例受信任的根证书
     - 证书配置文件类型：受信任的 CA 证书  
     ![受信任的认证](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard.png)

5. 单击“下一步”  。

6. 导入证书文件。

7. 选择 **"计算机证书存储 - 目标** 存储 **的根"。**

8. 单击“下一步”  。

9. 为 **支持的平台支持** 的平台选择" ![ 全选"](../media/ManagingDevices/ConfigMgr-Certificate-Profiles-Wizard-Supported-Platforms.png)

10. 单击 **"摘要"、"下一步"和"关闭** "退出向导。

11. 右键单击刚刚创建的配置文件，然后单击"导出 **"。**

12. 单击 **"** 浏览"，找到 .ppkg 文件应导出的位置，然后单击"保存 **"。**

13. 单击 **"导出** "， **然后单击"** 确定"退出向导。

#### <a name="other-mdm-servers"></a>其他 MDM 服务器

1. 下载并安装[Windows ADK (Windows评估和部署) 。 ](https://developer.microsoft.com/windows/hardware/windows-assessment-deployment-kit)

2. 打开 WINDOWS 映像和配置设计器 (WICD) 。
   ![Windows 映像和配置设计器](../media/ManagingDevices/WICD-Start-Page.png)

3. 选择 **"高级预配"**

4. 设置包的名称。

5. 选择常用设置Windows 10 IoT 核心版。

6. 跳过"导入包"步骤。
   ![WICD-New-Project-Details ](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Details.PNG) 
    ![ WICD-New-Project-Editions ](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Editions.PNG) 
    ![ WICD-New-Project-Import](../media/ManagingDevices/WICD-Advanced-Provisioning-New-Project-Import.PNG)

7. 导航到"工作区 ->注册&quot;。

8. 在&quot;UPN&quot;字段中，输入要注册设备的帐户， (，然后单击 trmck@contoso.co **") "。**

   ![工作区注册已填充](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Filled.png)

9. 对于 AuthPolicy，请选择"基于用户名密码的身份验证 (OnPremises) 或基于证书的身份验证。

10. 输入 MDM 服务器的发现服务 URL。

> [!NOTE]
> 注册服务 URL 和策略服务 URL 是可选的。

11. 对于"机密"，请输入  
    - OnPremises：要注册的帐户的密码  
    - 证书：证书的指纹
    
    ![填充的 OnPremise](../media/ManagingDevices/WICD-Workplace-Enrollments-UPN-Details-Filled-Premise.png)  

12. 在 WICD 窗口顶部，单击 **"导出>预配包"。**

13. 提供包的名称和版本，然后单击"下一 **步"。** 

> [!NOTE]
> 请务必递增版本号，以确保执行更新的包。

14. 单击 **安全** 详细信息 **页上的"下一步"。**

15. 选择要在本地计算机上导出包的位置，然后单击"下一步 **"。**

16. 单击 **"生成** "， **然后单击"完成** "退出向导。

### <a name="installing-the-provisioning-package"></a>安装预配包

可通过多种方式将预配包部署到 IoT 设备。 通过将包复制到设备或在映像过程中将包添加到映像，可以部署包。

#### <a name="copying-package-to-device"></a>将包复制到设备

使用从 SCCM 或 WICD 导出的预配包，将 .ppkg 文件复制到 `C:\Windows\Provisioning\Packages` IoT 设备的目录中。 重新启动设备后，将执行包，设备将启动注册过程。

#### <a name="adding-package-to-image"></a>将包添加到映像

请参阅 [将预配包添加到映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image)。 首次启动时，设备将执行包并启动注册过程。
