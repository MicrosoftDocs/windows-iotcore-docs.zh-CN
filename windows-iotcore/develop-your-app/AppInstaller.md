---
title: 在 IoT Core 设备上安装应用
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Windows 设备门户或 IoT core 映像的一部分来安装应用。
keywords: windows iot, 应用安装, Windows 设备门户, 设备
ms.openlocfilehash: 23df6bec04395eb31f066eb3befc84a4ff4bbe56
ms.sourcegitcommit: 5a103405cbc5c61101139aff6aaa709bd4ef9582
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694153"
---
# <a name="install-your-app-on-an-iot-core-device"></a>在 IoT Core 设备上安装应用
可以使用下面列出的两种方法之一来安装应用。

> [!NOTE]
> 使用 Windows 设备门户安装应用仅适用于开发人员方案。
> 请创建一个预配包, 或将应用添加到用于生产方案的 Windows IoT Core 映像。

## <a name="using-windows-device-portal"></a>使用 Windows 设备门户

> [!NOTE]
> 需要将 .appx 或 .appxbundle 用于 Windows 设备门户。 从 SDK 和工具版本17763开始, 如果应用项目的最低目标版本 > 为17763或更高版本, 则工具将创建[.msix 或 .msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html)。
> 若要创建 .appx 或 .appxbundle, 请将最低版本设置为低于17763的版本, 或[直接运行 makeappx.exe](https://docs.microsoft.com/en-us/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax)。 也可以将 .msix 重命名为 .appx, 或将 .msixbundle 重命名为 .appxbundle。

对于此方法, 需要确保已连接到 internet。 如果你无权访问 internet, 则还可以在设备和客户端计算机之间建立对等以太网连接, 但不包括访问开放 internet 的路径。 但是, 如果不想这样做, 则会安装应用程序, 但如果应用程序已进行了存储签名, 则无法启动。

若要在设备上安装应用程序, 请执行以下操作:

1. 打开 IoT 设备的[Windows 设备门户](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)。

2. 在 "**应用**" 菜单中, 选择应用文件, 然后单击 "**安装**" 来安装应用。

3. 单击 "**选择文件**"

4. 选择 .appx 文件并单击 "**打开**"

5. 选中 "**允许我选择框架包**"

6. 单击“下一步”

7. 对于 .appx 的 "**依赖项**" 文件夹中的每个项, 重复步骤7.1 和7。2

    7.1 单击 "**选择文件**"

    7.2 选择 depenency 并单击 "**打开**"

8. 添加所有依赖项后, 请单击 "**安装**"

9. 等待安装完成, 然后单击 "**完成**"

 ![安装应用](../media/AppInstaller/install-app.gif)

10. 现在, 应用程序将显示在设备上的应用程序列表中。
 ![安装应用](../media/AppInstaller/install-app.gif)


## <a name="using-provisioning-package-from-wcd"></a>使用 WCD 中的预配包
你可以使用应用创建预配包, 并在设备上安装预配包。 即使是在没有连接 internet 的设备上, 也可以使用此方法, 这是安装存储许可证文件的首选方法。 例如, 这可以启用工厂方案, 其中设备未连接到 internet, 但主应用是应用商店签名的 UWP 应用。

> [!NOTE]
> 包系列名称 (PFN) 可在 Windows 开发人员中心中的 "应用管理" 下找到 **> 应用标识**

1. 打开[Windows 配置设计器 (WICD)](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)

2. 选择 "**高级设置**", 输入项目名称和说明

3. 为项目设置选择 Windows 10 IoT Core, 并跳过预配包导入

4. 在左侧展开 "**运行时设置**", 然后单击 "**通用应用安装 > 用户上下文应用**

5. 输入应用的包系列名称, 并单击 "**添加**"

6. 在新添加的 PFN 下
    - 添加 Appx 及其依赖项
    - 将 d 设置为 "强制关闭目标应用程序"

7. 对于应用商店签名应用, 需要指定许可证。 在 UserContextAppLicense 下,
    - 添加 LicenseProductID (可用于许可证 XML 文件中的 LicenseID)
    - 将许可证 xml 扩展更改为 " *ms-windows-应用商店-许可证*"。
    - 选择左侧的许可证产品 ID, 并浏览许可证文件以分配 LicenseInstall 字段

8. 对于非应用商店签名应用, 需要在 "**证书 > RootCertificates** " 下添加 app.config 文件。 

9. 导出包

10. 使用[SSH](../connect-your-device/SSH.md)或[Powershell](../connect-your-device/powershell.md)将导出的 Ppkg 文件复制到 IoT 设备上的_C:\Windows\Provisioning\Packages_ , 然后重新启动。 当设备重新启动时, 将处理预配包, 并安装应用程序。


## <a name="add-the-app-to-the-windows-iot-core-imageffu"></a>将应用添加到 Windows IoT Core 映像 (. ffu)
你可以将该应用添加为 Windows IoT Core 映像自身的一部分。
这是 Oem 在其设备上安装应用程序的首选方法。

请参阅如何[将应用添加到映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)和[示例应用程序包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp)。
