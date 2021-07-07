---
title: 在 IoT Core 设备上安装应用
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 IoT 核心映像Windows 设备门户安装应用。
keywords: windows iot， 应用安装， Windows 设备门户， 设备
ms.openlocfilehash: ac0aed3e7f6f1eb630a0fda106133645fd01a1e1
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229874"
---
# <a name="install-your-app-on-an-iot-core-device"></a>在 IoT Core 设备上安装应用
可以使用下面列出的两种方法之一安装应用。

> [!NOTE]
> 使用应用程序安装Windows 设备门户仅适用于开发人员方案。
> 请为生产方案创建预配包或将Windows IoT 核心映像。

## <a name="using-windows-device-portal"></a>使用 Windows 设备门户

> [!NOTE]
> 需要 .appx 或 .appxbundle 才能Windows 设备门户。 从 SDK 和工具版本 17763 开始，如果应用项目的最低目标版本> 为 17763 或更大，则工具将创建 [.msix 或 .msixbundle](https://developercommunity.visualstudio.com/content/problem/391934/makeappx-now-creates-msix-files-instead-of-appx.html)。
> 若要创建 .appx 或 .appxbundle，将最低版本设置为低于 17763 的版本，或直接makeappx.exe [运行](https://docs.microsoft.com/windows/desktop/appxpkg/make-appx-package--makeappx-exe-#command-line-syntax)。 还可以将 .msix 重命名为 .appx，或将 .msixbundle 重命名为 .appxbundle。

对于此方法，需要确保已连接到 Internet。 如果无法访问 Internet，则还可以在设备和不包含用于访问开放 Internet 的路径的客户端计算机之间建立对等以太网连接。 但是，使用后一种方法将安装应用，但如果应用已进行存储签名，将无法启动。

若要在设备上安装应用程序，请执行以下步骤：

1. 打开[Windows 设备门户](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal)IoT 设备的信息。

2. 在" **应用"** 菜单中，通过选择应用文件并单击"安装"来 **安装应用**。

3. 单击" **选择文件"**

4. 选择 .appx 文件，然后单击"打开 **"**

5. 选中 **"允许我选择框架包"**

6. 点击“下一步” 

7. 对于 .appx **的 Dependencies** 文件夹中的每个项，重复步骤 7.1 和 7.2

    7.1 单击" **选择文件"**

    7.2 选择依赖项 .appx，然后单击"打开 **"**

8. 添加所有依赖项后，单击"安装 **"**

9. 等待安装完成，然后单击"完成 **"**

 ![安装应用](../media/AppInstaller/install-app.gif)

10. 应用程序现在将在设备上的应用程序列表中可见。
 ![安装应用](../media/AppInstaller/install-app.gif)


## <a name="using-provisioning-package-from-wcd"></a>使用 WCD 中的预配包
可以使用应用创建预配包，在设备上安装预配包。 此方法即使在没有 Internet 连接的设备上也有效，是安装应用商店许可证文件的首选方法。 例如，这样可以实现工厂方案：设备未连接到 Internet，但主应用是商店签名的 UWP 应用。

> [!NOTE]
> "包系列名称 (PFN) 位于"应用管理"Windows 开发人员中心应用标识>**中**

1. 打开[Windows 配置设计器 (WICD) ](https://docs.microsoft.com/windows/configuration/provisioning-packages/provisioning-install-icd)

2. 选择 **"高级预配"，** 输入项目名称和说明

3. 选择Windows 10 IoT 核心版设置"，并跳过预配包导入

4. 在左侧，展开"运行时"设置 **然后单击"** 通用 **应用安装>用户上下文应用"**

5. 输入应用的包系列名称，然后单击"添加 **"**

6. 在新添加的 PFN 下
    - 添加 Appx 及其依赖项
    - 将 DeploymentOptions 设置为"强制目标应用程序关闭"

7. 对于应用商店签名的应用，需要指定许可证。 在 UserContextAppLicense 下，
    - 在许可证 XML (中添加 LicenseProductID) 
    - 将许可证 xml 扩展更改为 *.ms-windows-store-license*。
    - 选择左侧的"许可证产品 ID"，并浏览许可证文件以分配 LicenseInstall 字段

8. 对于未存储签名的应用，需要在"证书""证书""根证书"下 **> app.cer 文件** 

9. 导出包

10. 使用 [SSH](../connect-your-device/SSH.md)或 [PowerShell](../connect-your-device/powershell.md)将导出的 .ppkg 文件复制到 IoT 设备上 _C：\Windows\Provisioning\Packages，_ 然后) 重启。 设备重新启动时，将处理预配包并安装应用。


## <a name="add-the-app-to-the-windows-iot-core-imageffu"></a>将应用添加到 ioT 核心Windows映像 (.ffu) 
可以将应用添加为 IoT 核心Windows的一部分。
这是 OEM 在设备上安装应用的首选方法。

了解如何将 [应用添加到映像和](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board) 示例 [应用包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp)。
