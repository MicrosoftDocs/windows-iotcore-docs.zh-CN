---
title: 与 Windows CE 应用容器入门
ms.date: 08/25/2020
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows CE 应用容器迁移入门指南
keywords: Windows 10 IoT Core，Windows CE，应用程序迁移，cepal
ms.openlocfilehash: 9ce7f9316641e07c349bbe5c142c2a8c9c716f2f
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91657233"
---
# <a name="getting-started-with-windows-ce-app-container"></a>与 Windows CE 应用容器入门

Windows CE 应用容器是一种技术，允许大多数 CE 应用程序运行在 Windows 10 IoT Core 的顶层。

此解决方案分为两个阶段。 第一阶段使用适用于 x86 或 ARM32 体系结构的 BSP 创建 Windows CE 2013 映像。 然后，在第二阶段中，此映像包含在 Windows 10 IoT Core 映像中，该映像利用 x64 或 ARM32 BSP 来实现将安装解决方案的特定设备硬件。

![CE 应用容器体系结构](.//media/WindowsCEAppContainer/image1.png)

有关此体系结构的详细信息，请查看以下视频： [现代化 Windows CE 设备](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Modernizing-Windows-CE-Devices)。

## <a name="prerequisites"></a>必备条件
Windows CE 应用容器软件需要 2013 [年 6) 2020 月版的 Windows Compact (版本 6294 ](https://support.microsoft.com/help/4566035/update-for-windows-embedded-compact-2013) 的更新版本，以及适用于 [x64 和 ARM32 的更新的 Windows 10 IoT 核心包 (8 月2020更新或更高) 版本 ](https://support.microsoft.com/help/4565349/windows-10-update-kb4565349)。 若要获取适用于 Windows 10 IoT Core 的最新包，请联系你的 Microsoft 分发服务器。

> [!NOTE]
> 你必须具有有效的 [IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) 订阅才能分发采用 CE 应用容器技术的设备。

此外，你将需要以下各项：

- [Microsoft Visual Studio 2013 专业版或 Visual Studio 2015 professional](<https://visualstudio.microsoft.com/vs/>)。 这些版本是应用程序生成器和平台生成器工具所必需的。

- [适用于 Windows Embedded Compact 2013 的应用程序生成器](<https://www.microsoft.com/download/details.aspx?id=38819>)

- 适用于 Windows Compact 2013 的平台生成器

- 工作 IoT 核心 BSP

- [Windows IoT 制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/set-up-your-pc-to-customize-iot-core)中引用的工具
- 请记住，安装已更新的组件来代替本指南中所述的组件 (Windows 10 ADK 和 Windows 10 ADK PE 加载项、IoT Core ADK 外接程序、Windows 10 IoT 核心仪表板) 


## <a name="configuring-building-and-packaging-ce-for-the-windows-ce-app-container"></a>为 Windows CE 应用容器配置、构建和打包 CE

[用于创建 Windows Embedded Compact 2013 映像的过程](https://docs.microsoft.com/previous-versions/windows/embedded/jj200349(v=winembedded.80))没有明显更新。 生成映像的一般过程如下：

1. 在平台生成器中创建 OS 设计项目

2. 选择 "平台生成器" 支持包 (BSP) 

3. 选择适当的设计模板

4. 配置设计模板提供的选项

5. 选择性地将子项目添加到设计项目

6. 生成映像

主要更改是为 CE 映像选择正确的 BSP 和其他注意事项。 本指南假定你已熟悉构建 Windows CE 系统映像的过程，但在 "已更改" 部分有必要更深入地查看。

步骤2是以前的 OS 设计项目过程的唯一一部分，该过程是在使用 CE 应用容器时更改的，请参阅下面的详细信息。

### <a name="step-2---platform-builder-bsp-selection"></a>步骤 2-平台生成器 BSP 选择

为了支持 Windows CE 应用容器，已将面向 x86 和 ARM 体系结构的新 BSP 添加到了平台生成器中。

为 CE 应用容器创建 OS 设计时，请选择 "Windows CE App Container： x86" 或 "Windows CE App Container： ARMv7" (ARM32) ，具体取决于基于 IoT 内核的设备的底层硬件。

例如，如果目标 IoT 核心设备使用 Intel 硬件，你将选择 "Windows CE 应用容器： x86" 选项。 或者，如果 IoT 核心硬件使用 NXP MX6，将选择 "Windows CE App Container： ARMv7" 选项。

![选择 CE 应用容器 BSP](./media/WindowsCEAppContainer/image2.png)

完成此操作后，你将能够配置选项和子项目，就像通常为 Windows Embedded Compact 映像执行的操作一样。 这些配置将内置到 CE 容器，你将部署到 Windows 10 IoT Core 映像。

## <a name="building-the-windows-10-iot-core-image"></a>构建 Windows 10 IoT Core 映像

> [!NOTE]
> 作为 [Windows 10 IoT 核心制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)一部分的实验室中更详细地介绍了此过程。 以下部分仅提供在 IoT Core 映像生成过程的某些阶段执行的其他操作。 在继续操作之前，强烈建议先熟悉 Windows 10 IoT 核心制造指南。

### <a name="process-overview"></a>过程概述

与构建 Windows Embedded Compact 映像的过程不同，Windows 10 IoT Core 分离还集成了固件的创建、板支持包、映像定义和应用程序包含。 通过利用这些组件的不同技术，你可以将所需的工作划分为不同团队或组织中的个人所需的工作。

创建映像的基本步骤如下：

1. [创建工作区](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

2. [ (BSP) 导入相应的 IoT 核心板支持包 ](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

3. 导入先前创建的 CE 应用容器

4. [创建产品定义](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

5. [向产品添加功能和应用程序](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)

6. [ (FFU 创建完整的闪存更新) ](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)

7. [将 FFU 部署到设备并测试](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

8. [完成零售 FFU 并为其签名](https://docs.microsoft.com/windows-hardware/manufacture/iot/build-retail-image)

在 [Windows 10 IoT 核心制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)中，每个步骤都有详细指南。 尽管其中一些步骤类似于使用平台生成器 (PB) 创建设备映像的过程，但有必要更深入地探讨一些区域。

#### <a name="step-1---create-a-workspace"></a>步骤 1-创建工作区

请查看 IoT 核心制造指南中的文档 " [创建基本图像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)"，了解如何创建工作区。

#### <a name="step-2---import-the-appropriate-iot-core-board-support-package-bsp"></a>步骤 2-导入适当的 IoT 核心板支持包 (BSP) 

查看 IoT 核心制造指南中的文档 " [创建基本映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)"，以获取有关板的支持。

#### <a name="step-3---importing-the-windows-ce-app-container"></a>步骤 3-导入 Windows CE 应用容器

Windows CE 应用容器使用上图所述的 PB 创建，并使用 [IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-IoTCEPAL.md#Import-IoTCEPAL) 命令导入到 IoT 核心工作区。 此命令会将 CE 单层发布目录中所需的内容复制到 IoT ADK 工作区。 如果多次调用，则会在工作区中的目录下备份以前的状态 `Source-\$Arch\CEPAL.OLD` 。

#### <a name="step-4---create-your-product-definition"></a>步骤 4-创建产品定义

请查看 IoT 核心制造指南中的文档， [创建基本映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)，创建产品定义。


#### <a name="step-5---adding-ce-app-container-to-a-product"></a>步骤 5-将 CE 应用容器添加到产品

将 CE 应用容器定义导入到工作区后，需要确保运行 [IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTCEPAL.md#Add-IoTCEPAL) 命令，该命令会将对 CE 应用容器包的引用添加到相关产品 OEMInput.xml 文件 (测试和零售) 。

下一步是使用 [IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTProductFeature.md#Add-IoTProductFeature) 命令将 IOT \_ CEPAL 功能添加到 OEMInput.xml。 这会将 Windows CE 应用容器的 Windows 主机支持添加 (Windows CE 的前端 UWP 应用 + 支持驱动程序) 到我们的产品定义，并在默认应用组中包含 CE 应用容器。 我们将在后面的部分中讨论启动配置。

#### <a name="step-6---build-your-cab-files"></a>步骤 6-生成 CAB 文件

这是在创建 FFU 的过程中的一个重要步骤，并且应在每次更改配置、添加/更改应用程序或驱动程序时执行。 将使用 [IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md#New-IoTCabPackage) 和 "All" 选项。 你还可以根据需要构建单一功能，但通常应在生成 FFU 的步骤之前重新生成所有包。

#### <a name="step-7---deploying-your-ffu-to-your-device"></a>步骤 7-将 FFU 部署到设备

构建映像后，可以将其部署到设备。 这可以通过使用 [DISM](https://docs.microsoft.com/windows-hardware/manufacture/desktop/what-is-dism)的命令行通过特定于设备的部署过程或通过使用 [Windows 10 IoT 核心仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)来完成。 有关更多详细信息，请访问 [Windows 10 IoT 核心制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)。

##### <a name="deploying-the-windows-ce-app-container-to-a-device-when-using-an-existing-ffu"></a>使用现有 FFU 将 Windows CE 应用容器部署到设备

CE Cab 是 IoT Core 上的可部署包。 如果存在现有的 IoT 核心映像，可以使用命令将这些 Cab 部署到设备 `APPLYUPDATE` 。 首先将 Cab 复制到设备，然后通过暂存并提交 Cab `APPLYUPDATE` 。 请注意，更新此方法会使包版本控制更为强大，因此，如果要将包的更新版本部署到设备，则这些版本的版本号必须更高。  (参阅 IoT ADK 环境) 中的 IoTCabVersion 命令。 有关此方面的详细信息，请参阅 [创建和安装包](https://docs.microsoft.com/enus/windows-hardware/manufacture/iot/create-install-package.)

#### <a name="step-8---building-a-retail-image"></a>步骤 8-构建零售映像

使用正确的签名映像是保护和更新设备的重要部分。 对于 Windows 10 IoT Core，此外观显示为测试签名版本和零售签名版本之间的差异。 绝不应公开部署测试已签名映像。 测试签名映像只应用于调试目的，在创建最终零售签名映像之前，应更正任何错误或配置更改。

> [!NOTE]
> 除了计算机上安装的开发和部署工具外，还需要以下内容来启用零售签名：
>
> - 零售代码签名证书
> - 交叉签名证书

### <a name="properly-signing-and-including-your-applications"></a>正确签名和包括应用程序

如果你有一个或多个你想要包含在 Windows 10 IoT 核心零售映像中的自定义应用程序，则需要验证这些应用程序是否已在零售映像中包含它们时进行了正确签名。

## <a name="additional-information"></a>其他信息

### <a name="adding-new-applications-to-an-existing-image"></a>将新应用程序添加到现有映像

若要将新应用程序添加到现有的操作系统设计中，可以将该项目作为子项目添加到 OS 设计项目，也可以创建常规部署 CAB 包，将这些包部署到作为初始设备设置的一部分的设备上。

### <a name="packaging-best-practices"></a>打包最佳实践

应始终确保包尽可能细化，以减少更新时间。

由于包是更新的最小单位，因此请确保每个包尽可能小。 在平台生成器中生成时，根据选手文件自动将生成的包与内存部分和模块/文件类型分隔开来。

- 对于在平台生成器中构建并通过 OSDesign 进行打包的自定义资产，请考虑将自定义资产添加到选手 (不在 NK) 中的单独内存部分，以便自定义代码更新与 CE OS 的更新不同。

- 对于通过 IoT ADK 打包命令添加的自定义资产：请确保创建的包尽可能小。

### <a name="adding-other-things-to-the-platform-builder-package"></a>向平台生成器包添加其他项

通常，建议不要修改平台生成器生成的生成的包，以将其他组件包括到系统映像中。 而应按照 [Windows 10 IoT Core 制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)进行操作。 但是，如果必须将文件添加到平台生成器创建的包中，请按照现有过程进行操作。 向 PB 生成的包添加内容时，请考虑以下事项：

- 包的最大大小 (大约 400 MB) ，超过此大小将阻止更新。

- 更新会在包粒度进行。 如果需要更新包中的单个资产，则该程序包的所有资产将同时更新。 若要减少更新的大小，请将内容隔离到单独的包中，以最大程度地减少总体更新大小。

### <a name="adding-additional-files-through-platform-builder"></a>通过平台生成器添加其他文件

上面详述的打包过程由与构建 CE 箱文件相同的输入驱动。 因此，如果在 OSDesign 中引用了文件，则会将选手中的注册表项添加到 OSDesign 中， `MAKEIMG` 进程将在生成的 CAB 文件中包含这些文件。 在此过程中， `MAKEIMG` 将立即执行以下操作：

1. `ROMIMAGE` 将在平面发布目录中创建一个名为的目录 `CEPAL\_PKG` (FRD) ，该目录将 Windows CE 的目录结构暂存用于 CEPAL。

2. `ROMIMAGE` 列出基于 CE 选手文件放入的所有 CE 文件的清单 `CEPAL\_PKG` 。

3. `ROMIMAGE` 将为每个内存部分创建多个 WM.XML 文件。 这样做的目的是为了使更新以更精细的方式推送，因为更新的最小单位是包。

4. `ROMIMAGE` 将创建引用所有已创建的包的。

所有创建的包都将使用固定的前缀命名 `“%OEM\_NAME%.WindowsCE.\*”` ，其中， `%OEM\_NAME%` 将在调用 [IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md)时在 IoT Core 创建过程中填充。 命名空间中的包名称是从选手文件的内存部分派生的 (例如，NK) 后跟模块/文件 (也由选手文件) 决定。

#### <a name="communicating-between-windows-embedded-compact-2013-and-windows-10-iot-core-applications"></a>Windows Embedded Compact 2013 和 Windows 10 IoT Core 应用程序之间的通信

在 CE 容器中运行的应用程序之间进行通信的建议方法是使用本地环回。 有关详细信息，请参阅 [本文档中的本地环回。](https://docs.microsoft.com/windows/iot-core/develop-your-app/loopback)

### <a name="automatically-starting-the-ce-app-container-application"></a>自动启动 CE 应用容器应用程序

若要自动启动 CE 容器应用程序，可以创建一个设置 [包](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image) ，将启动应用程序设置为 "CEPAL. DkMonUWP \_ cw5n1h2txyewy！应用 "，并将其包含在映像中。 还需要使用 [IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Remove-IoTProductFeature.md) 命令删除默认启动应用程序，并 \_ 从 iot 核心产品定义中删除 IOT BERTHA 功能 ID。

### <a name="available-configuration-settings-for-the-windows-ce-app-container"></a>Windows CE 应用容器的可用配置设置

#### <a name="registry-based-configuration-in-ce"></a>CE 中基于注册表的配置

##### <a name="non-executable-stack-by-default"></a>默认情况下，不可执行的堆栈

默认情况下，Windows CE 应用容器已禁用可执行堆栈页，以提高安全性。 但是，某些旧版应用程序可能依赖于此行为才能正常运行。 若要启用可执行堆栈，请在 CE 映像中设置以下注册表值 (建议在平台生成器中将其放入 OSDesign) 

```AsciiDoc
KeyPath = HKEY\_LOCAL\_MACHINE\CEPAL
ValueName = MemoryOptions Type = REG\_DWORD
Value = 1
```

##### <a name="16-bit-565-override-for-gwes"></a>16位565替代 GWES

如果 Windows CE 应用容器配置了32位显示，则 GWES 完成了16位到32位的 RGB 转换，假设16位 RGB 像素数据采用 RGB555 格式。 如果位图资源采用16位565，并且无法转换为 RGB555 的这些资源，则可以通过注册表项更改 GWES 的默认转换行为。 创建以下注册表项：

```AsciiDoc
HKEY\_LOCAL\_MACHINE\SYSTEM\GDI\16bpp565RGBPalette.
```

#### <a name="registry-based-configuration-in-host-iot-core"></a>Host 中基于注册表的配置 (IoT 核心) 

##### <a name="configuring-serial-ports-for-the-windows-ce-app-container"></a>为 Windows CE 应用容器配置串行端口

需要将主机串行端口映射到 CE 环境。 此映射存在于 IoT 核心的注册表中，需要由映像创建者进行配置。

在 `HKEY\_CURRENT\_USER\Software\Microsoft\Windows NT\CurrentVersion\CEPAL\Devices\Serial` 中，存在使用以下架构将来宾 COM 端口映射到主机 COM 端口的配置条目。

```AsciiDoc
KeyPath = HKEY\_CURRENT\_USER\Software\Microsoft\Windows NT\CurrentVersion\CEPAL\Devices\Serial\0

ValueName = Guest Type = REG\_SZ Value = COM1

ValueName = Host

Type = REG\_SZ

Value = \\?\Some\DeviceInterface\Path

KeyPath= HKEY\_CURRENT\_USER\Software\Microsoft\Windows NT\CurrentVersion\CEPAL\Devices\Serial\1

ValueName = Guest Type = REG\_SZ Value = COM2

ValueName= Host Type = REG\_SZ

Value = \\?\Some\Other\DeviceInterface\Path
```

如果上面的注册表路径在启动 CE 时不存在，则将根据系统上发现的串行设备来写入默认配置。

#### <a name="file-based-configuration-in-host"></a>主机中基于文件的配置

可以使用主机上的本地文件配置 CE 容器 `C:\WindowsCE\CEEnvConfig.json` 。 下面是此配置文件的示例：

```xml
{
 "OEMOptions" :
    {
     "GUI" : true,
     "Width" : 1024,
     "Height" : 768, "FillScreen" : true, "ColorDepth" : 32,
     "RefreshRate" : 30, "noAslrSupport" : true, "OemConfigApp" : "",
     "OemConfigFile" : ""
    },
 "CEPALDevOptions" :
    {
     "VsDebugMode" : true, "FastDebugBoot" : false
    }
 }
 ```

#### <a name="oemoptions"></a>OEMOptions

| 密钥           | 说明                                                                                                            |
|---------------|------------------------------------------------------------------------------------------------------------------------|
| GUI           | 启动带有 UI (默认为 true) 的 CE 应用容器                                                                     |
| 宽度         | CE 应用容器的宽度显示 (默认 1024)                                                                    |
| 高度        | CE 应用容器的高度显示 (默认 768)                                                                    |
| FillScreen    |                                                                                                                        |
| ColorDepth    | 设置默认的每像素 (默认位数 32)                                                                                |
| RefreshRate   | 每秒重绘显示的次数                                                                       |
| noAslrSupport | 在 CE 应用容器中禁用地址空间布局随机化 (默认值为 true)                                      |
| OEMConfigApp  | 应为配置启动的 OEM 提供的应用的包系列名称。                                  |
| OEMConfigFile | 文件的路径，该文件包含 OEMConfigApp 与 CE 应用容器之间共享的其他配置选项 |

CE 应用容器只会使一个网络接口可供使用。 如果主机系统中有多个 Nic，则必须在主机注册表中选择一个接口，以确保所选 NIC 是确定性的。

##### <a name="oemconfigfile"></a>OEMConfigFile

OEMConfigFile 在中指定 `C:\WindowsCE\CEEnvConfig.json` 。 请确保此文件可由 UWP 应用程序读取。 下面是一个示例：

```xml
{
   “FactoryReset”: false, “PlatformBuilderDebugMode”: false,
   “NetInterface”: “Some Network Profile Id”
}
```

选项：

| 密钥                      | 说明                                                                              |
|--------------------------|------------------------------------------------------------------------------------------|
| FactoryReset             | 由 config 应用用来指示 CE 应用容器转储持久状态。          |
| PlatformBuilderDebugMode | 用于使用支持使用平台生成器进行调试的 KITL 支持启动 CE 应用程序容器。 |
| NetInterface             | 基于配置文件名称为 CE 选择一个网络接口。                                 |


## <a name="references"></a>参考

- [获取自定义 Windows 10 IoT Core 所需的工具](https://docs.microsoft.com/windows-hardware/manufacture/iot/set-up-your-pc-to-customize-iot-core)
- [IoT 核心板支持的包 (BSP) ](https://docs.microsoft.com/windows-hardware/manufacture/iot/bsphardware)
- [IoT 核心制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)
- [Windows 10 IoT 核心版仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)
- [创建和安装包](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-install-package)
