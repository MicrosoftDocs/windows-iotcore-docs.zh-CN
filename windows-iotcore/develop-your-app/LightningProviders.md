---
title: Lightning 提供程序
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解有关如何使用 Microsoft 闪电提供程序库的详细信息。
keywords: windows iot，闪电提供商，闪电性能测试，总线
ms.openlocfilehash: 1ad7acd8d40bcedd4b0a2ef21af3e866e36ed790
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656293"
---
# <a name="working-with-lightning-providers"></a>使用闪电提供程序
DMAP 库包含一组提供程序，这些提供程序用于通过闪电直内存映射驱动 (程序在) 上通过闪电形控制器总线连接。


## <a name="about-the-direct-memory-mapped-driver-dmap"></a>关于直接内存映射驱动程序 (DMAP) 

DMAP 驱动程序是一个开发中的驱动程序，它提供对默认收件箱驱动程序的 GPIO 性能改进。 若要了解有关这些性能改进的详细信息，请访问 [闪电性能测试](../develop-your-app/LightningPerformance.md) 页。

尽管 DMAP 驱动程序通过收件箱驱动程序提供 GPIO 性能改进，但控制器命令通过每个控制器的用户模式内存映射地址发送到 DMAP 驱动程序。 仅使用闪电提供程序 Api 或 Microsoft 的应用程序。 但是，恶意应用程序能够直接写入该内存并导致硬件/安全问题。 在仅具有受信任应用的计算机上，DMAP 通常可以安全使用。   

## <a name="obtaining-the-library"></a>获取库

使用[GitHub ms-iot/闪电存储库](https://github.com/ms-iot/lightning/)中提供源代码的[闪电 SDK NuGet 包](https://www.nuget.org/packages/Microsoft.IoT.Lightning)中提供了库。

此外，还提供了有关如何使用不同的提供程序的示例，请访问 [GitHub ms-iot/BusProviders 存储库](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)。

## <a name="adding-the-library-to-your-application"></a>向应用程序添加库

### <a name="option-1-starting-from-an-existing-sample"></a>选项1：从现有示例开始
使用闪电提供程序进行编码的一种快速方法是从 [GitHub ms-iot/BusProviders 存储库](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)中的一个示例开始。

每个示例都引用了闪电 SDK，并正确配置为使用闪电提供程序库。

**请注意**，若要运行这些示例，需要使用 Windows 设备 Web 门户启用 DMAP 驱动程序。 有关如何启用它的详细信息，请参阅 [闪电安装指南](LightningSetup.md) 。

### <a name="option-2-referencing-the-library"></a>选项2：引用库

此外，将所需的闪电提供程序 NuGet 引用和支持添加到新的或现有的应用程序也很简单。 请遵循以下步骤进行配置：

1. 在应用程序中，右键单击项目，然后单击 "管理 NuGet 包 ..."菜单项  
![UWP 项目](../media/LightningProviders/manage-nuget-project.png)

2. NuGet 包管理器将打开。 在 "浏览" 选项卡中，搜索 "闪电 SDK"，确保选中 "包括预发行版" 复选框。

3. 选择最新版本，然后单击 "安装" 以将闪电 SDK 添加到你的项目。 
![NuGet 包管理器](../media/LightningProviders/nuget-package-manager.png)

4. 如果需要，请按照屏幕上的说明进行操作。 安装完成后，将向你的项目添加对闪电 SDK 的引用。

![闪电 SDK 参考](../media/LightningProviders/lightning-sdk-added-to-solution.png)

5. 将下面的代码添加到清单文件 appxmanifest.xml。

``` XML
<iot:Capability Name="lowLevelDevices" />
<DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>
```

* 第一种功能将使应用程序能够访问自定义设备。
* 第二个是闪电接口的设备 guid ID

必须将这两项功能添加到项目的 AppX 清单中 `<Capabilities>` 。 此外，如果需要，请确保将所需的命名空间添加到清单中。

![AppX 清单 Capabailities](../media/LightningProviders/package-manifest-updates.png)

## <a name="updating-your-code-to-use-the-lightning-providers"></a>更新代码以使用闪电提供程序

### <a name="checking-for-the-lightning-dmap-driver"></a>检查闪电 (DMAP) 驱动程序

若要检查是否启用了闪电， `LightningProvider.IsLightningEnabled` 应使用属性。 通常，在使用闪电提供程序 Api 之前，验证是否启用了闪电驱动程序是一种很好的做法。 

``` C#
if (Microsoft.IoT.Lightning.Providers.LightningProvider.IsLightningEnabled)
{
    // Do something with the Lightning providers
}
```

### <a name="general-usage-pattern"></a>常规用法模式

使用提供程序的最简单方法是将闪电提供程序设置为应用程序中的默认提供程序。 

如果闪电提供商可用，以下代码将设置 `Microsoft.IoT.Lightning.Providers.LightningProvider` 为默认提供程序。 否则，如果未显式设置默认提供程序，则不同的总线会退回到默认提供程序。
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

获得所需总线的控制器后，可以像平常一样使用它。 

### <a name="using-lightning-for-individual-buses"></a>为单个总线使用闪电

如果要使用其他默认提供程序，以下部分说明了如何为单个总线使用闪电提供程序。 

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
使用 Microsoft IoT。使用 Windows 设备;使用 Windows. Spi;

``` C#
if (LightningProvider.IsLightningEnabled)
{
    SpiController controller =  (await SpiController.GetControllersAsync(LightningSpiProvider.GetSpiProvider()))[0];
    SpiDevice SpiDisplay = controller.GetDevice(spiConnectionSettings);
}
```

## <a name="lightning-provider-samples"></a>闪电提供商示例

以下示例演示如何将闪电提供程序与支持的总线类型一起使用：

* [使用闪电提供商) 的 Blinky (UI](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) 说明了在前台应用程序中使用闪电提供程序的 GPIO

* [使用闪电提供](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) 程序的 BlinkyHeadless 演示如何在无外设应用程序中使用闪电提供程序

* 使用[闪电提供程序的 SPIDisplay](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay)演示了如何使用 API 来控制使用 SPI 和闪电提供程序的设备
 
* 使用[闪电提供程序的 WeatherStation](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation)演示如何使用带有闪电的 I2C 提供程序与设备交互

## <a name="build-requirements"></a>生成要求



### <a name="windows-sdk-update"></a>Windows SDK 更新

生成和使用库所需的 Windows SDK 10.0.10586.0 或更高版本，可从 [此处](https://dev.windows.com/en-US/downloads/windows-10-sdk)下载。

有关设置所有内容的详细信息，请参阅[入门指南。](https://developer.microsoft.com/en-us/windows/iot/getstarted)

### <a name="nuget-package-dependencies"></a>NuGet 包依赖项

闪电提供程序库依赖于[ARDUINO SDK nuget](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino)[包，而](https://www.nuget.org/packages/Microsoft.IoT.Lightning)后者又依赖于 " 这两个 NuGet 包都在库项目中进行引用，可从 Nuget.org 中获取。

如果需要，还可以在 GitHub 上的 [闪电](https://github.com/ms-iot/lightning) 和 [Arduino SDK](https://github.com/ms-iot/arduino-sdk) 存储库中使用每个的源代码。

目前，在更新版本可用时，Microsoft IoT NuGet 仍处于预发布版本，应从 Nuget.org 更新。

若要安装 (当前) 版本的 Microsoft IoT NuGet 包，并接收对闪电包的预发布更新，请确保在 NuGet 包管理器中设置 "包括预发行版" 选项。

1. 右键单击项目中的 "引用"
1. 单击 "管理 NuGet 包 ..."
1. 为闪电 NuGet 选择包源
1. 单击 "包括预发行版"。
1. 单击 "安装" 以将 NuGet 包安装到项目中

![程序包管理器配置](../media/LightningProviders/Nuget_PackageManager.png)

## <a name="runtime-requirements"></a>运行时要求

### <a name="windows-iot-core-fall-update-required"></a>需要 Windows IoT 核心秋季更新
闪电提供商支持目前包含在 Windows IoT Core 的秋季更新版本中。
可以从 [下载页面](https://developer.microsoft.com/windows/iot/Downloads)下载 Windows 10 IoT Core 映像。 对于设备类型，请单击 "下载内幕预览版"。

### <a name="direct-memory-mapped-driver-must-be-enabled"></a>必须启用直接内存映射驱动程序
 
闪电提供程序库中的 Api 需要在目标设备上启用闪电直接内存映射驱动程序。 Raspberry Pi 2/3 和 MinnowBoard Max 都有可用的驱动程序，但默认情况下未启用。

可以使用 Windows 设备 Web 门户启用该驱动程序。 有关如何启用闪电驱动程序的详细信息，请参阅 [闪电安装指南](LightningSetup.md) 。

![设备页](../media/LightningProviders/dmap4.png)

还可以通过 DmapUtil 命令启用该驱动程序：

DmapUtil：用于打开或关闭 DMAP 直接内存映射器驱动程序的实用工具： dmaputil.exe 状态 | 启用 | 禁用状态 [-v] 输出当前是否已启用 DMAP。 传递-v 标志以获取详细的配置信息。
启用 "在下一次启动时启用 dmap"。
禁用 "在下一次启动时禁用 dmap"。
