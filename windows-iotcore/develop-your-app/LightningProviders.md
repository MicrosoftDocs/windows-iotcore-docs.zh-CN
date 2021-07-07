---
title: Lightning 提供程序
author: msalehmsft
ms.author: msaleh
ms.date: 11/12/2020
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 详细了解如何使用 Microsoft 闪电提供程序库。
keywords: windows iot， 闪电提供程序， 闪电性能测试， 总线
ms.openlocfilehash: 1fea55dd6a9fd45dc2396feed4973bc470ba0f7d
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229834"
---
# <a name="working-with-lightning-providers"></a>使用闪电提供程序
> [!NOTE]
> 此页仅供旧用途使用。

Microsoft.IoT.Lightning.Providers 库包含一组提供程序，这些提供程序通过"闪电"直接内存映射驱动程序与板载控制器总线 (DMAP) 。


## <a name="about-the-direct-memory-mapped-driver-dmap"></a>关于直接内存映射驱动程序 (DMAP) 

DMAP 驱动程序是开发中的驱动程序，提供比默认收件箱驱动程序更高性能的 GPIO。 若要详细了解这些性能改进，请访问 [闪电性能测试](../develop-your-app/LightningPerformance.md) 页。

虽然 DMAP 驱动程序比收件箱驱动程序提供 GPIO 性能改进，但控制器命令通过每个控制器的用户模式内存映射地址发送到 DMAP 驱动程序。 仅使用闪电提供程序 API 或 Microsoft.IoT.Lightning.Providers 的应用。 但是，恶意应用能够直接写入该内存，并引发硬件/安全问题。 在仅包含受信任的应用的计算机上，DMAP 通常是安全的。   

## <a name="obtaining-the-library"></a>获取库

该库作为[Lightning SDK](https://www.nuget.org/packages/Microsoft.IoT.Lightning)包的一NuGet提供，源代码可在[ms-iot/Lightning GitHub上获得](https://github.com/ms-iot/lightning/)。

此外[，ms-iot/BusProviders](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)存储库上提供了GitHub提供程序的示例。

## <a name="adding-the-library-to-your-application"></a>将库添加到应用程序

### <a name="option-1-starting-from-an-existing-sample"></a>选项 1：从现有示例开始
开始使用闪电提供程序进行编码的一种快速方法就是从[ms-iot/BusProviders](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)GitHub中的示例之一开始。

每个示例都引用了 Lightning SDK，并正确配置为使用闪电提供程序库。

**请注意**，若要运行示例，需使用"设备"Web 门户Windows启用 DMAP 驱动程序。 请参阅 [闪电设置指南](LightningSetup.md) ，详细了解如何启用它。

### <a name="option-2-referencing-the-library"></a>选项 2：引用库

此外，将所需的闪电提供程序添加到新的NuGet应用程序的引用和支持非常简单。 请遵循以下步骤进行配置：

1. 在应用程序中，右键单击项目，然后单击"管理NuGet包..."菜单项  
![UWP 项目](../media/LightningProviders/manage-nuget-project.png)

2. 该NuGet 程序包管理器将打开。 在"浏览"选项卡中，搜索"闪电 SDK"，确保选中"包括预发布"复选框。

3. 选择最新版本，然后单击"安装"，将 Lightning SDK 添加到项目。
![NuGet 包管理器](../media/LightningProviders/nuget-package-manager.png)

4. 如果需要，请按照任何屏幕上的说明进行操作。 安装完成后，对 Lightning SDK 的引用将添加到项目中。

![闪电 SDK 参考](../media/LightningProviders/lightning-sdk-added-to-solution.png)

5. 将以下代码添加到清单文件 Package.appxmanifest。

``` XML
<iot:Capability Name="lowLevelDevices" />
<DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>
```

* 第一种是使应用程序能够访问自定义设备的功能。
* 第二个是闪电接口的设备 GUID ID

这两项功能都必须添加到 节点下项目的 AppX `<Capabilities>` 清单中。 此外，如果需要，请确保将所需的命名空间添加到清单。

![AppX 清单功能](../media/LightningProviders/package-manifest-updates.png)

## <a name="updating-your-code-to-use-the-lightning-providers"></a>更新代码以使用闪电提供程序

### <a name="checking-for-the-lightning-dmap-driver"></a>检查闪电 (DMAP) 驱动程序

若要检查是否启用了 Lightning， `LightningProvider.IsLightningEnabled` 应使用 属性。 通常，在使用闪电提供程序 API 之前，验证是否启用了闪电驱动程序始终是一个不错的做法。

``` C#
if (Microsoft.IoT.Lightning.Providers.LightningProvider.IsLightningEnabled)
{
    // Do something with the Lightning providers
}
```

### <a name="general-usage-pattern"></a>常规使用模式

使用提供程序的最简单方法就是将"闪电提供程序"设置为应用中的默认值。

如果闪电提供程序可用，以下代码将设置为 `Microsoft.IoT.Lightning.Providers.LightningProvider` 默认提供程序。 否则，如果没有显式设置默认提供程序，则各种总线将回退到默认提供程序。
``` C#
using Microsoft.IoT.Lightning.Providers;
using Windows.Devices;
if (LightningProvider.IsLightningEnabled)
{
    LowLevelDevicesController.DefaultProvider = LightningProvider.GetAggregateProvider();
}

gpioController = await GpioController.GetDefaultAsync();
i2cController = await I2cController.GetDefaultAsync();
spiController = await SpiController.GetDefaultAsync();
```

获得所需总线的控制器后，可以像平时一样使用它。

### <a name="using-lightning-for-individual-buses"></a>对单个总线使用闪电

如果要使用不同的默认提供程序，以下部分将展示如何对单个总线使用闪电提供程序。

#### <a name="for-gpio-bus-controller"></a>对于 GPIO 总线控制器：

``` C#
using Microsoft.IoT.Lightning.Providers;
using Windows.Devices;
using Windows.Devices.Gpio;

if (LightningProvider.IsLightningEnabled)
{
    GpioController gpioController = (await GpioController.GetControllersAsync(LightningGpioProvider.GetGpioProvider()))[0];
    GpioPin pin = gpioController.OpenPin(LED_PIN, GpioSharingMode.Exclusive);
}
```

#### <a name="for-i2c-bus-controller"></a>对于 I2C 总线控制器：

``` C#
using Microsoft.IoT.Lightning.Providers;
using Windows.Devices;
using Windows.Devices.I2c;

if (LightningProvider.IsLightningEnabled)
{
    I2cController controller =  (await I2cController.GetControllersAsync(LightningI2cProvider.GetI2cProvider()))[0];
    I2cDevice sensor = controller.GetDevice(new I2cConnectionSettings(0x40));
}
```

#### <a name="for-spi-bus-controller"></a>对于 SPI 总线控制器：
使用 Microsoft.IoT.Lightning.Providers;使用 Windows。设备;使用 Windows。Devices.Spi;

``` C#
if (LightningProvider.IsLightningEnabled)
{
    SpiController controller =  (await SpiController.GetControllersAsync(LightningSpiProvider.GetSpiProvider()))[0];
    SpiDevice SpiDisplay = controller.GetDevice(spiConnectionSettings);
}
```

## <a name="lightning-provider-samples"></a>闪电提供程序示例

以下示例演示如何将闪电提供程序与支持的总线类型一起使用：

* [Blinky (UI) 和闪电提供程序](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) 演示了在前台应用程序中使用闪电提供程序的 GPIO

* [带闪电提供程序的 BlinkyHeadless](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) 演示无头应用程序中具有闪电提供程序的 GPIO

* [带闪电提供程序的 SPIDisplay](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) 演示了使用 API 通过 SPI 和闪电提供程序控制设备的用法

* [具有闪电提供程序的 WeatherStation](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) 演示如何使用 I2C 与闪电提供程序与设备交互

## <a name="build-requirements"></a>生成要求



### <a name="windows-sdk-update"></a>WindowsSDK 更新

Windows生成和使用库所需的 SDK 为 10.0.10586.0 或更高版本，可从此处[下载](https://dev.windows.com/en-US/downloads/windows-10-sdk)。

有关设置所有内容的信息，请参阅 [入门指南](https://developer.microsoft.com/en-us/windows/iot/getstarted)。。

### <a name="nuget-package-dependencies"></a>NuGet包依赖项

闪电提供程序库依赖于[Microsoft.IoT.Lightning NuGet](https://www.nuget.org/packages/Microsoft.IoT.Lightning)包 ，而该包又依赖于[Arduino SDK NuGet包](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino)。 库NuGet引用这两个包，并且可从 Nuget.org。

如果需要，每个的源代码也可在GitHub[和](https://github.com/ms-iot/lightning) [Arduino SDK](https://github.com/ms-iot/arduino-sdk)存储库上获得。

目前，Microsoft.IoT.Lightning NuGet仍处于预发布状态，因此，当有新版本可用时，Nuget.org 更新 Microsoft.IoT.Lightning。

若要安装 Microsoft.IoT.Lightning NuGet 包的当前 () 版本以及接收对 Lightning 包的预发行更新，请确保在 NuGet 程序包管理器 中设置"包括预发行"选项。

1. 右键单击项目中的"引用"
1. 单击"管理NuGet包..."
1. 选择"闪电"包NuGet
1. 单击"包括预发行"。
1. 单击"安装"，将NuGet包安装到项目中

![程序包管理器配置](../media/LightningProviders/Nuget_PackageManager.png)

## <a name="runtime-requirements"></a>运行时要求

### <a name="windows-iot-core-fall-update-required"></a>Windows需要 IoT 核心 Fall 更新
适用于 IoT Core 的 Fall Update 内部版本当前包含闪电Windows支持。
可以从下载[Windows 10 IoT 核心版下载映像](https://developer.microsoft.com/windows/iot/Downloads)。 单击设备类型的"下载预览体验成员"。

### <a name="direct-memory-mapped-driver-must-be-enabled"></a>必须启用直接内存映射驱动程序

闪电提供程序库中的 API 要求在目标设备上启用"闪电直接内存映射"驱动程序。 Raspberry Pi 2/3 和 MinnowBoard Max 都提供驱动程序，但默认未启用。

可以使用设备 Web 门户Windows驱动程序。 请参阅 [闪电设置指南](LightningSetup.md) ，详细了解如何启用闪电驱动程序。

!["设备"页](../media/LightningProviders/dmap4.png)

还可使用 DmapUtil 命令启用驱动程序：

DmapUtil：用于打开或关闭 DMAP 直接内存映射器驱动程序的实用工具使用情况：dmaputil.exe status|enable|disable status [-v] 打印出当前是否启用 dmap。 传递 -v 标志，了解详细的配置信息。
启用"下次启动时启用 dmap"。
禁用 下次启动时禁用 dmap。
