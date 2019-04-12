---
title: 在 IoT Core 设备上安装您的应用程序
author: parameshbabu
ms.author: pabab
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Windows Device Portal 将应用安装或作为一部分 IoT core 映像。
keywords: windows iot，应用程序安装，Windows Device Portal 设备
ms.openlocfilehash: 6e188eaef6551548c6c71ac50859516d4cbe7e9c
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510801"
---
# <a name="install-your-app-on-an-iot-core-device"></a>在 IoT Core 设备上安装您的应用程序
你可以安装应用程序使用下面列出了两种方法之一。

> [!NOTE]
> 使用 Windows Device Portal 方法仅适用于开发人员方案。 其他两种方法适用于生产方案。

## <a name="using-windows-device-portal"></a>使用 Windows Device Portal

对于此方法，需要确保已连接到 internet。 如果还没有 internet 访问权限，还可以在设备和不包括路径访问开放 internet 的客户端计算机之间的对等以太网连接。 但是，看后一种方式将安装应用，将无法启动，如果应用是应用商店签名。

若要安装在设备上的应用程序请执行以下步骤：

1. 打开[Windows Device Portal](https://docs.microsoft.com/windows/iot-core/manage-your-device/deviceportal) IoT 设备。

2. 在中*应用*菜单中，通过上传应用包安装您的应用程序。
 ![安装应用](../media/AppInstaller/install-app.gif)

3. 将应用部署。

4. 该应用程序现在将你的设备上的应用程序列表中可见。
 ![应用列表](../media/AppInstaller/AppList.png)


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


## <a name="add-to-the-iot-core-imageffu"></a>将添加到 IoT core image(.ffu)   
您可以添加该应用程序本身 IoT Core 映像的一部分。 这是 oem 广泛使用的机制。 

请参阅如何[将应用添加到你的映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)和一个[示例应用包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp)。
