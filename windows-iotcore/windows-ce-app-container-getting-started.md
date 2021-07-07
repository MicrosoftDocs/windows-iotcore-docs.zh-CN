---
title: Windows CE 应用容器入门
ms.date: 08/25/2020
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows CE 应用容器迁移入门指南
keywords: Windows 10 IoT 核心版，Windows CE，应用程序迁移，cepal
ms.openlocfilehash: 6e1fb421df4ecb26099a08c489c4c6eeca0a392e
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113230414"
---
# <a name="getting-started-with-windows-ce-app-container"></a>Windows CE 应用容器入门

Windows CE 应用容器是一种技术，允许大多数 CE 应用程序在 Windows 10 IoT 核心版之上运行。

此解决方案分为两个阶段。 第一阶段使用适用于 x86 或 ARM32 体系结构的 BSP 创建 Windows CE 2013 映像。 然后，在第二阶段中，此映像包含在一个 Windows 10 IoT 核心版映像中，该映像利用 x64 或 ARM32 BSP 来实现将安装解决方案的特定设备硬件。

![CE 应用容器体系结构](.//media/WindowsCEAppContainer/image1.png)

有关此体系结构的详细信息，请查看以下视频：[现代化 Windows CE 设备](https://channel9.msdn.com/Shows/Internet-of-Things-Show/Modernizing-Windows-CE-Devices)。

## <a name="prerequisites"></a>先决条件
Windows CE 应用容器软件需要[从6月2020或更高版本) 的 Windows Compact 2013 (内部版本号 6294](https://support.microsoft.com/help/4566035/update-for-windows-embedded-compact-2013)的更新版本，以及[x64 和 ARM32 的更新 Windows 10 IoT 核心版包 (8 月2020更新或更高版本) ](https://support.microsoft.com/help/4565349/windows-10-update-kb4565349)。 若要获取 Windows 10 IoT 核心版的最新包，请联系你的 Microsoft 分发服务器。

> [!NOTE]
> 你必须具有有效的 [IoT Core Services](https://docs.microsoft.com/windows-hardware/manufacture/iot/iotcoreservicesoverview) 订阅才能分发采用 CE 应用容器技术的设备。

此外，你将需要以下各项：

- [Microsoft Visual Studio 2013 Professional 或 Visual Studio 2015 Professional](<https://visualstudio.microsoft.com/vs/>)。 这些版本是应用程序生成器和平台生成器工具所必需的。

- [适用于 Windows Embedded Compact 2013 的应用程序生成器](<https://www.microsoft.com/download/details.aspx?id=38819>)

- 适用于 Windows Compact 2013 的平台生成器

- 工作 IoT 核心 BSP

- [Windows IoT 制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/set-up-your-pc-to-customize-iot-core)中引用的工具
- 请记得安装已更新的组件来代替本指南中所述的组件 (Windows 10 ADK 和 Windows 10 ADK PE 加载项、IoT Core ADK 外接程序、Windows 10 IoT 核心版仪表板) 


## <a name="configuring-building-and-packaging-ce-for-the-windows-ce-app-container"></a>为 Windows CE 应用容器配置、构建和打包 CE

[用于创建 Windows 嵌入 Compact 2013 映像的过程](https://docs.microsoft.com/previous-versions/windows/embedded/jj200349(v=winembedded.80))没有明显更新。 生成映像的一般过程如下：

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

为 CE 应用容器创建 OS 设计时，请选择 "Windows CE 应用容器： x86" 或 "Windows CE 应用容器： ARMv7" (ARM32) ，具体取决于基于 IoT 内核的设备的底层硬件。

例如，如果目标 IoT 核心设备使用 Intel 硬件，你将选择 "Windows CE 应用容器： x86" 选项。 或者，如果 IoT 核心硬件使用 NXP MX6，将选择 "Windows CE 应用容器： ARMv7" 选项。

![选择 CE 应用容器 BSP](./media/WindowsCEAppContainer/image2.png)

完成此操作后，你将能够配置选项和子项目，就像通常为 Windows 嵌入的压缩映像执行的操作一样。 这些配置将内置到 CE 容器，你将部署到 Windows 10 IoT 核心版映像。

## <a name="building-the-windows-10-iot-core-image"></a>构建 Windows 10 IoT 核心版映像

> [!NOTE]
> 作为[Windows 10 IoT 核心版制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)一部分的实验室中更详细地介绍了此过程。 以下部分仅提供在 IoT Core 映像生成过程的某些阶段执行的其他操作。 在继续操作之前，强烈建议先熟悉 Windows 10 IoT 核心版制造指南。

### <a name="process-overview"></a>过程概述

与构建 Windows 嵌入精简映像的过程不同，Windows 10 IoT 核心版分离还集成了固件的创建、板支持包、映像定义和应用程序包含。 通过利用这些组件的不同技术，你可以将所需的工作划分为不同团队或组织中的个人所需的工作。

创建映像的基本步骤如下：

1. [创建工作区](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

2. [ (BSP) 导入相应的 IoT 核心板支持包 ](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

3. 导入先前创建的 CE 应用容器

4. [创建产品定义](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

5. [向产品添加功能和应用程序](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)

6. [ (FFU 创建完整的闪存更新) ](https://docs.microsoft.com/windows-hardware/manufacture/iot/deploy-your-app-with-a-standard-board)

7. [将 FFU 部署到设备并测试](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)

8. [完成零售 FFU 并为其签名](https://docs.microsoft.com/windows-hardware/manufacture/iot/build-retail-image)

[Windows 10 IoT 核心版制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)中提供了每个步骤的详细指南。 尽管其中一些步骤类似于使用平台生成器 (PB) 创建设备映像的过程，但有必要更深入地探讨一些区域。

#### <a name="step-1---create-a-workspace"></a>步骤 1-创建工作区

请查看 IoT 核心制造指南中的文档 " [创建基本图像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)"，了解如何创建工作区。

#### <a name="step-2---import-the-appropriate-iot-core-board-support-package-bsp"></a>步骤 2-导入适当的 IoT 核心板支持包 (BSP) 

查看 IoT 核心制造指南中的文档 " [创建基本映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)"，以获取有关板的支持。

#### <a name="step-3---importing-the-windows-ce-app-container"></a>步骤 3-导入 Windows CE 应用容器

Windows CE 应用容器使用 PB 创建，并使用[IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-IoTCEPAL.md#Import-IoTCEPAL)命令导入到 IoT 核心工作区。 此命令会将 CE 单层发布目录中所需的内容复制到 IoT ADK 工作区。 如果多次调用，则会在工作区中的目录下备份以前的状态 `Source-\$Arch\CEPAL.OLD` 。

#### <a name="step-4---create-your-product-definition"></a>步骤 4-创建产品定义

请查看 IoT 核心制造指南中的文档， [创建基本映像](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)，创建产品定义。


#### <a name="step-5---adding-ce-app-container-to-a-product"></a>步骤 5-将 CE 应用容器添加到产品

将 CE 应用容器定义导入到工作区后，需要确保运行 [IoTCEPAL](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTCEPAL.md#Add-IoTCEPAL) 命令，该命令会将对 CE 应用容器包的引用添加到相关产品 OEMInput.xml 文件 (测试和零售) 。

下一步是使用 [IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Add-IoTProductFeature.md#Add-IoTProductFeature) 命令将 IOT \_ CEPAL 功能添加到 OEMInput.xml。 这会将 (Windows CE 应用容器的 Windows 主机支持添加 Windows CE 的前端 UWP 应用 + 支持驱动程序) 到我们的产品定义，并在默认应用组中包含 CE 应用容器。 我们将在后面的部分中讨论启动配置。

#### <a name="step-6---build-your-cab-files"></a>步骤 6-生成 CAB 文件

这是在创建 FFU 的过程中的一个重要步骤，并且应在每次更改配置、添加/更改应用程序或驱动程序时执行。 将使用 [IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md#New-IoTCabPackage) 和 "All" 选项。 你还可以根据需要构建单一功能，但通常应在生成 FFU 的步骤之前重新生成所有包。

#### <a name="step-7---deploying-your-ffu-to-your-device"></a>步骤 7-将 FFU 部署到设备

构建映像后，可以将其部署到设备。 这可以通过使用[DISM](https://docs.microsoft.com/windows-hardware/manufacture/desktop/what-is-dism)通过特定于设备的部署过程或通过使用[Windows 10 IoT 核心版仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)从命令行完成。 [Windows 10 IoT 核心版制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-a-basic-image)中提供了更多详细信息。

##### <a name="deploying-the-windows-ce-app-container-to-a-device-when-using-an-existing-ffu"></a>使用现有 FFU 将 Windows CE 应用容器部署到设备

CE Cab 是 IoT Core 上的可部署包。 如果存在现有的 IoT 核心映像，可以使用命令将这些 Cab 部署到设备 `APPLYUPDATE` 。 首先将 Cab 复制到设备，然后通过暂存并提交 Cab `APPLYUPDATE` 。 请注意，更新此方法会使包版本控制更为强大，因此，如果要将包的更新版本部署到设备，则这些版本的版本号必须更高。  (在 IoT ADK 环境) 中查看 Set-IoTCabVersion 命令。 有关此方面的详细信息，请参阅 [创建和安装包](https://docs.microsoft.com/enus/windows-hardware/manufacture/iot/create-install-package.)

#### <a name="step-8---building-a-retail-image"></a>步骤 8-构建零售映像

使用正确的签名映像是保护和更新设备的重要部分。 对于 Windows 10 IoT 核心版，此外观显示为测试签名版本和已签名零售版本之间的差异。 绝不应公开部署测试已签名映像。 测试签名映像只应用于调试目的，在创建最终零售签名映像之前，应更正任何错误或配置更改。

> [!NOTE]
> 除了计算机上安装的开发和部署工具外，还需要以下内容来启用零售签名：
>
> - 零售代码签名证书
> - 交叉签名证书

### <a name="properly-signing-and-including-your-applications"></a>正确签名和包括应用程序

如果你有一个或多个要包含在 Windows 10 IoT 核心版零售映像中的自定义应用程序，则需要验证这些应用程序在零售映像中包含它们时是否已正确签名。

## <a name="additional-information"></a>其他信息

### <a name="adding-new-applications-to-an-existing-image"></a>将新应用程序添加到现有映像

若要将新应用程序添加到现有 OS 设计，可以将项目作为子项目添加到 OS 设计 Project，也可以创建常规部署 CAB 包，以在初始设备设置过程中将其部署到设备。

### <a name="packaging-best-practices"></a>打包最佳做法

应始终确保包尽可能精细，以减少更新时间。

由于包是最小的更新单元，因此请确保每个包尽可能小。 在 Platform Builder 中生成时，生成的包根据内存部分和模块/文件类型根据 bib 文件自动进行分隔。

- 对于在平台生成器中构建并通过 OSDesign.bib 打包的自定义资产，请考虑将自定义资产添加到 BIB (中的单独内存部分，而不是在 NK) 中，以便自定义代码的更新可以独立于 CE OS 的更新提供。

- 对于通过 IoT ADK 打包命令添加的自定义资产：请确保创建的包尽可能小。

### <a name="adding-other-things-to-the-platform-builder-package"></a>将其他内容添加到 Platform Builder 包

通常，建议不要修改平台生成器生成的包，以在系统映像中包括其他组件。 请改为按照Windows 10 IoT 核心版[指南操作](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)。 但是，如果必须将文件添加到平台生成器创建的包中，请按照现有过程操作。 将内容添加到 PB 生成的包时，请考虑以下事项：

- 包的最大大小为 (400 MB) 超过此大小将阻止更新。

- 更新在包粒度上发生。 如果需要更新包中的单个资产，则包的所有资产将同时更新。 若要减小更新大小，可将内容隔离到单独的包中，以最大程度地减小总体更新大小。

### <a name="adding-additional-files-through-platform-builder"></a>通过平台生成器添加其他文件

上面详述的打包过程由生成 CE BIN 文件的相同输入驱动。 因此，如果在 OSDesign.bib 中引用文件，并且注册表项添加到 OSDesign.reg，则该过程将在生成的 CAB 文件中包括 `MAKEIMG` 这些文件。 在此过程期间 `MAKEIMG` ，现在将：

1. `ROMIMAGE`将在平面发布目录和 FRD (内) 一个名为 的目录，用于为 `CEPAL\_PKG` CEPAL Windows CE安装目录结构。

2. `ROMIMAGE` 根据 CE BIB 文件清点放入 `CEPAL\_PKG` 的所有 CE 文件。

3. `ROMIMAGE` 将为每个内存WM.XML多个文件。 这样做是为了以更精细的方式推送更新，因为更新的最小单位是包。

4. `ROMIMAGE` 将创建引用所有已创建的包的 。

创建的所有包都将使用固定前缀 进行命名，在 `“%OEM\_NAME%.WindowsCE.\*”` `%OEM\_NAME%` 调用 [New-IoTCabPackage](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/New-IoTCabPackage.md)时，将在 IoT 核心创建过程中填充该前缀。 名称空间内的包名称派生自 BIB 文件的内存部分 (例如 NK) 后跟模块/文件 (BIB 文件也由 BIB 文件) 。

#### <a name="communicating-between-windows-embedded-compact-2013-and-windows-10-iot-core-applications"></a>Windows Embedded Compact 2013 与 Windows 10 IoT 核心版 应用程序之间的通信

在 CE 容器中运行的应用程序之间进行通信的建议方法是使用本地环回。 可以在此文档中详细了解 [本地环回。](https://docs.microsoft.com/windows/iot-core/develop-your-app/loopback)

### <a name="automatically-starting-the-ce-app-container-application"></a>自动启动 CE 应用容器应用程序

若要自动启动 CE 容器应用程序，可以创建一个预配[包，将](https://docs.microsoft.com/windows-hardware/manufacture/iot/add-a-provisioning-package-to-an-image)启动应用程序设置为"Microsoft" 。Windows。IoT.CEPAL.DkMonUWP \_ cw5n1h2txyewy！应用"，并且此预配包包含在映像中。 还需要使用 [Remove-IoTProductFeature](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Remove-IoTProductFeature.md) 命令删除默认启动应用程序，并从 IoT 核心产品定义中删除 IOT \_ BERTHA 功能 ID。

### <a name="available-configuration-settings-for-the-windows-ce-app-container"></a>可用的配置设置Windows CE 应用容器

#### <a name="registry-based-configuration-in-ce"></a>CE 中基于注册表的配置

##### <a name="non-executable-stack-by-default"></a>默认为非可执行堆栈

默认情况下Windows CE 应用容器禁用可执行堆栈页以提高安全性。 但是，某些旧版应用程序可能依赖于此行为来正常运行。 若要启用可执行堆栈，在 CE 映像中设置以下注册表值 (建议在 Platform Builder 映像中转到 OSDesign.reg) 

```AsciiDoc
KeyPath = HKEY\_LOCAL\_MACHINE\CEPAL
ValueName = MemoryOptions Type = REG\_DWORD
Value = 1
```

##### <a name="16-bit-565-override-for-gwes"></a>GWES 的 16 位 565 重写

如果 Windows CE 应用容器 配置为 32 位显示器，则 GWES 完成 16 位到 32 位 RGB 的转换，前提是 16 位 RGB 像素数据采用 RGB555 格式。 如果位图资源位于 16 位 565 中，并且无法转换为这些资源中的 RGB555，则可以通过注册表项更改 GWES 的默认转换行为。 创建以下注册表项：

```AsciiDoc
HKEY\_LOCAL\_MACHINE\SYSTEM\GDI\16bpp565RGBPalette.
```

#### <a name="registry-based-configuration-in-host-iot-core"></a>主机和 IoT Core (中基于注册表) 

##### <a name="configuring-serial-ports-for-the-windows-ce-app-container"></a>为端口配置串行Windows CE 应用容器

主机串行端口需要映射到 CE 环境中。 此映射存在于 IoT 核心的注册表中，需要由映像创建者配置。

在 `HKEY\_CURRENT\_USER\Software\Microsoft\Windows NT\CurrentVersion\CEPAL\Devices\Serial` 下，存在配置条目，以使用以下架构将来宾 COM 端口映射到主机 COM 端口。

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

如果在启动 CE 时上述注册表路径不存在，将基于系统上发现的串行设备写入默认配置。

#### <a name="file-based-configuration-in-host"></a>主机中的基于文件的配置

CE 容器可以使用主机 上的本地文件进行配置 `C:\WindowsCE\CEEnvConfig.json` 。 下面是此配置文件的示例：

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
| GUI           | 使用 UI 启动 CE 应用容器 (默认值 true)                                                                      |
| 宽度         | CE 应用容器的宽度显示 (默认为 1024)                                                                    |
| 高度        | CE 应用容器的高度 (默认为 768)                                                                    |
| FillScreen    |                                                                                                                        |
| ColorDepth    | 将每个像素的默认位数设置为 (默认 32)                                                                                |
| RefreshRate   | 每秒重绘显示次数                                                                       |
| noAslrSupport | 禁用 CE 应用容器中的地址空间布局随机化 (默认值 true)                                      |
| OEMConfigApp  | OEM 提供的应用的包系列名称，应启动该应用进行配置。                                  |
| OEMConfigFile | 包含 OEMConfigApp 和 CE 应用容器之间共享的其他配置选项的文件的路径 |

CE 应用容器仅提供一个网络接口供使用。 如果主机系统中存在多个 NIC，则必须在主机注册表中选择一个接口，以确保所选 NIC 具有确定性。

##### <a name="oemconfigfile"></a>OEMConfigFile

OEMConfigFile 在 中指定 `C:\WindowsCE\CEEnvConfig.json` 。 确保 UWP 应用程序可以读取此文件。 下面是一个示例：

```xml
{
   “FactoryReset”: false, “PlatformBuilderDebugMode”: false,
   “NetInterface”: “Some Network Profile Id”
}
```

选项：

| 密钥                      | 说明                                                                              |
|--------------------------|------------------------------------------------------------------------------------------|
| FactoryReset             | 由配置应用用来指示 CE 应用容器转储持久状态。          |
| PlatformBuilderDebugMode | 用于启动具有 KITL 支持的 CE 应用容器，以便使用平台生成器进行调试。 |
| NetInterface             | 根据配置文件名称为 CE 选择网络接口。                                 |


## <a name="references"></a>参考

- [获取自定义数据所需的Windows 10 IoT 核心版](https://docs.microsoft.com/windows-hardware/manufacture/iot/set-up-your-pc-to-customize-iot-core)
- [BSP 支持 IoT 核心 (包) ](https://docs.microsoft.com/windows-hardware/manufacture/iot/bsphardware)
- [IoT 核心制造指南](https://docs.microsoft.com/windows-hardware/manufacture/iot/iot-core-manufacturing-guide)
- [Windows 10 IoT 核心版仪表板](https://docs.microsoft.com/windows/iot-core/connect-your-device/iotdashboard)
- [创建和安装包](https://docs.microsoft.com/windows-hardware/manufacture/iot/create-install-package)
