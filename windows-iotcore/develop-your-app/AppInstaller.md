---
title: 在 IoT Core 设备上安装您的应用程序
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Windows Device Portal 将应用安装或作为一部分 IoT core 映像。
keywords: windows iot，应用程序安装，Windows Device Portal 设备
ms.openlocfilehash: 23df6bec04395eb31f066eb3befc84a4ff4bbe56
ms.sourcegitcommit: 5a103405cbc5c61101139aff6aaa709bd4ef9582
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694153"
---
# <a name="install-your-app-on-an-iot-core-device"></a>在 IoT Core 设备上安装您的应用程序
你可以安装应用程序使用下面列出了两种方法之一。

> [!NOTE]
> 通过 Windows Device Portal 安装应用程序仅适用于开发人员方案。
> 请创建预配包，或将应用添加到 Windows IoT Core 映像对于生产方案。

## <a name="using-windows-device-portal"></a>使用 Windows Device Portal

> [!NOTE]
> 需要 Windows Device Portal.appx 或.appxbundle。 如果所需的最低目标版本的应用程序项目版本的 SDK 和工具 17763 开始 > 17763 或更高版本工具将创建[.msix 或.msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html)。
> 若要创建的最低版本为版本低于 17763 的.appx 或.appxbundle 集或[直接运行 makeappx.exe](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax)。 它还可以重命名为.appx 或.appxbundle 的.msixbundle.msix。

对于此方法，需要确保已连接到 internet。 如果还没有 internet 访问权限，还可以在设备和不包括路径访问开放 internet 的客户端计算机之间的对等以太网连接。 但是，看后一种方式将安装应用，将无法启动，如果应用是应用商店签名。

若要安装在设备上的应用程序请执行以下步骤：

1. 打开[Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) IoT 设备。

2. 在中**应用程序**菜单中，选择你的应用程序文件并单击安装您的应用程序**安装**。

3. 单击**选择文件**

4. 选择您的.appx 文件，然后单击**打开**

5. 检查**允许我选择 framework 包**

6. 单击“下一步” 

7. 中每一项**依赖项**文件夹为.appx 重复步骤 7.1 和 7.2

    7.1 单击**选择文件**

    7.2 选择 depenency.appx，然后单击**打开**

8. 在所有依赖项添加单击时**安装**

9. 等待安装完成，然后单击**完成**

 ![安装应用](../media/AppInstaller/install-app.gif)

10. 该应用程序现在将你的设备上的应用程序列表中可见。
 ![安装应用](../media/AppInstaller/install-app.gif)


## <a name="using-provisioning-package-from-wcd"></a>使用从 WCD 预配包
可以使用应用创建预配包，并在设备上安装预配包。 此方法甚至没有 internet 连接的设备上运行，并且是用于安装应用商店的许可证文件的首选的方法。 例如，这样，在设备未连接到 internet 但主应用程序已签名应用商店的 UWP 应用的工厂方案。

> [!NOTE]
> 包系列名称 (PFN) 可以位于下在 Windows 开发人员中心**应用管理 > 应用程序标识**

1. 打开[Windows 配置设计器 (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)

2. 选择**高级预配**，输入项目名称和描述

3. 为项目设置中选择 Windows 10 IoT 核心版和跳过预配包导入

4. 在左侧依次展开**运行时设置**，然后单击**通用应用安装 > 用户上下文应用**

5. 输入包系列名称的应用程序并单击**添加**

6. 在新添加的 PFN
    - 添加 Appx 和其依赖项
    - 设置为"强制目标应用程序关闭"DeploymentOptions

7. 对于存储已签名的应用，需要指定许可证。 下 UserContextAppLicense，
    - 添加 LicenseProductID （可用作 LicenseID 许可证 XML 文件中）
    - 将许可证 xml 扩展名更改为 *.ms windows 应用商店许可*。
    - 选择您的左侧上的许可证产品 ID 并浏览您的许可证文件来分配 LicenseInstall 字段

8. 对于非应用商店已签名应用程序，您需要添加下的 app.cer 文件**证书 > RootCertificates** 

9. 导出包

10. 将导出的.ppkg 文件复制到_C:\Windows\Provisioning\Packages_ IoT 设备使用[SSH](../connect-your-device/SSH.md)或[Powershell](../connect-your-device/powershell.md)) 并重新启动。 当设备重新启动时，处理预配包和安装应用。


## <a name="add-the-app-to-the-windows-iot-core-imageffu"></a>将应用添加到 Windows IoT Core image(.ffu)
您可以添加该应用程序 Windows IoT Core 映像本身的一部分。
这是 Oem 可以在其设备上安装应用的首选的方法。

请参阅如何[将应用添加到你的映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)和一个[示例应用包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp)。
