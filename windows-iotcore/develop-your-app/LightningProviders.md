---
title: 快如闪电提供程序
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 了解有关如何使用要获得有关 Microosft 闪电提供程序库的详细信息。
keywords: windows iot、 快如闪电提供程序、 快如闪电性能测试、 总线
ms.openlocfilehash: 8f290bf741f64e07b7b048287128e1ae42ef6b9e
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510949"
---
# <a name="working-with-lightning-providers"></a>使用闪电提供程序
Microsoft.IoT.Lightning.Providers 库包含一组通过闪电般的控制器总线提供程序以便与在看板进行交互的直接内存映射驱动程序 (DMAP)。


## <a name="about-the-direct-memory-mapped-driver-dmap"></a>有关直接内存映射驱动程序 (DMAP)

DMAP 驱动程序是通过默认收件箱驱动程序提供 GPIO 性能改进的开发中驱动程序。 若要了解有关这些性能改进的详细信息，请访问[闪电性能测试](../develop-your-app/LightningPerformance.md)页。

DMAP 驱动程序产品/服务 GPIO 性能改进通过收件箱驱动程序，而控制器命令发送到通过用户模式内存映射地址 DMAP 驱动程序的每个控制器。 仅使用闪电般的提供程序 Api 或 Microsoft.IoT.Lightning.Providers 的应用。 但是，恶意应用程序可以直接写入内存并会导致硬件/安全问题。 在具有受信任的应用的计算机，DMAP 是通常可以安全地使用。   

## <a name="obtaining-the-library"></a>获取库

库提供的一部分[闪电 SDK Nuget 包](https://www.nuget.org/packages/Microsoft.IoT.Lightning)上可用的源代码[闪电般 ms-iot 的 GitHub 存储库](https://github.com/ms-iot/lightning/)。

此外上, 提供有示例演示如何使用不同的提供程序[ms-iot/BusProviders 的 GitHub 存储库](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)。

## <a name="adding-the-library-to-your-application"></a>将库添加到你的应用程序

### <a name="option-1-starting-from-an-existing-sample"></a>选项 1：从现有示例开始
开始编码使用闪电提供程序的快速方法是开始中的示例之一[ms-iot/BusProviders 的 GitHub 存储库](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)。

每个示例引用闪电 SDK 并正确配置为使用闪电提供程序库。

**请注意**，若要运行示例，需要使用 Windows 设备的 Web 门户启用 DMAP 驱动程序。 请参阅[闪电设置指南](LightningSetup.md)有关如何启用它的详细信息。

### <a name="option-2-referencing-the-library"></a>选项 2：引用库

此外，它很简单添加所需的闪电形提供程序 Nuget 引用，并支持添加到新的或现有应用程序。 按以下步骤操作：

1. 在应用程序中，右键单击项目，然后单击"管理 NuGet 包..."菜单项![UWP 项目](../media/LightningProviders/manage-nuget-project.png)

2. NuGet 包管理器将打开。 在浏览选项卡，搜索"闪电 SDK"，并确保选中"包括预发行版"复选框。

3. 选择最新版本，然后单击"安装"以将快如闪电 SDK 添加到你的项目。 
![NuGet 包管理器](../media/LightningProviders/nuget-package-manager.png)

4. 按照屏幕上的说明根据需要。 安装完成后，对闪电 SDK 的引用将添加到项目中。

![快如闪电 SDK 参考](../media/LightningProviders/lightning-sdk-added-to-solution.png)

5. 将以下代码添加到清单文件，Package.appxmanifest。

``` XML
<iot:Capability Name="lowLevelDevices" />
<DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>
```

* 首先是使应用程序可以访问自定义设备的功能。
* 其次是适用于该 Lightning 接口的设备 GUID ID

两种功能都必须添加到 `<Capabilities>` 节点下的项目的 AppX 清单。 此外，请务必根据需要添加到应用清单中的所需命名空间。

![AppX 清单功能](../media/LightningProviders/package-manifest-updates.png)

## <a name="updating-your-code-to-use-the-lightning-providers"></a>更新代码以使用闪电提供程序

### <a name="checking-for-the-lightning-dmap-driver"></a>检查 Lightning (DMAP) 驱动程序

若要检查是否已启用 Lightning，应使用 `LightningProvider.IsLightningEnabled` 属性。 通常，最好在使用 Lightning 提供程序 API 之前验证 Lightning 驱动程序是否已启用。 

``` C#
if (Microsoft.IoT.Lightning.Providers.LightningProvider.IsLightningEnabled)
{
    // Do something with the Lightning providers
}
```

### <a name="general-usage-pattern"></a>一般使用模式

使用提供程序的最简单方法是在应用内部将 Lightning 提供程序设置为默认提供程序。 

将以下代码如果闪电提供程序不可用，设置`Microsoft.IoT.Lightning.Providers.LightningProvider`作为默认提供程序。 否则，在没有显式设置任何默认提供程序时，各种总线将退回到默认提供程序。
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

为所需总线配备了控制器后，你可以像往常一样使用它。 

### <a name="using-lightning-for-individual-buses"></a>将 Lightning 用于个别总线

如果你需要使用不同的默认提供程序，以下部分将介绍如何将 Lightning 提供程序用于个别总线。 

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
使用 Microsoft.IoT.Lightning.Providers; 使用 Windows.Devices; 使用 Windows.Devices.Spi;

``` C#
if (LightningProvider.IsLightningEnabled)
{
    SpiController controller =  (await SpiController.GetControllersAsync(LightningSpiProvider.GetSpiProvider()))[0];
    SpiDevice SpiDisplay = controller.GetDevice(spiConnectionSettings);
}
```

## <a name="lightning-provider-samples"></a>Lightning 提供程序示例

以下示例演示了如何使用 Lightning 提供程序以及受支持的总线类型：

* [带有 Lightning 提供程序的 Blinky (UI)](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) 演示了前台应用程序中带有 Lightning 提供程序的 GPIO

* [带有 Lightning 提供程序的 BlinkyHeadless](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) 演示了无外设应用程序中带有 Lightning 提供程序的 GPIO

* [带有 Lightning 提供程序的 SPIDisplay](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) 演示了使用 API 控制使用带有 Lightning 提供程序的 SPI 的设备
 
* [带有 Lightning 提供程序的 WeatherStation](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) 演示了与使用带有 Lightning 提供程序的 I2C 的设备进行交互

## <a name="build-requirements"></a>生成要求



### <a name="windows-sdk-update"></a>Windows SDK 更新

生成和使用库所需的 Windows SDK 为 10.0.10586.0 或更高版本（可以从[此处](https://dev.windows.com/en-US/downloads/windows-10-sdk)下载）。

有关设置的所有内容的详细信息，请参阅[我们入门指南。](https://developer.microsoft.com/en-us/windows/iot/getstarted)。

### <a name="nuget-package-dependencies"></a>Nuget 包依赖关系

Lightning 提供程序库依赖于 [Microsoft.IoT.Lightning Nuget 包](https://www.nuget.org/packages/Microsoft.IoT.Lightning)，该包反过来又依赖于 [Arduino SDK Nuget 包](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino)。 这两个 Nuget 包在库项目中引用，并且可以从 Nuget.org 中获取。

如果需要，每个包的源代码也可用于 [Lightning](https://github.com/ms-iot/lightning) 和 [Arduino SDK](https://github.com/ms-iot/arduino-sdk) 存储库中的 GitHub 上。

Microsoft.IoT.Lightning Nuget 目前仍是预发行版，因此当更新的版本可用时，应从 Nuget.org 进行更新。

为了能够安装预发行版（当前版本）的 Microsoft.IoT.Lightning Nuget 包以及接收 Lightning 程序包的预发行更新，请务必在 Nuget 包管理器中设置“包含预发行版”。

1. 右键单击项目中的“引用”
1. 单击“管理 Nuget 包...”
1. 选择 Lightning Nuget 的程序包源
1. 单击“包含预发行版”。
1. 单击“安装”以将 Nuget 包安装到你的项目中

![程序包管理器配置](../media/LightningProviders/Nuget_PackageManager.png)

## <a name="runtime-requirements"></a>运行时要求

### <a name="windows-iot-core-fall-update-required"></a>需要 Windows IoT 核心版秋季更新
目前仅 Windows IoT 核心版的秋季更新版本中包含 Lightning 提供程序支持。
你可以从我们的[下载页](https://developer.microsoft.com/windows/iot/Downloads)下载 Windows 10 IoT 核心版映像。 单击你的设备类型的“下载 Insider Preview”。

### <a name="direct-memory-mapped-driver-must-be-enabled"></a>必须启用直接内存映射的驱动程序
 
Lightning 提供程序库中的 API 需要在目标设备上启用 Lightning 直接内存映射的驱动程序。 Raspberry Pi 2/3 和 MinnowBoard Max 让驱动程序可用，但默认情况下不启用。

可以使用 Windows Devices Web Portal 启用驱动程序。 有关如何启用 Lightning 驱动程序的详细信息，请参阅 [Lightning 设置指南](LightningSetup.md)。

![设备页面](../media/LightningProviders/dmap4.png)

此外可以使用 DmapUtil 命令启用驱动程序：

DmapUtil:若要启用或禁用使用情况的 DMAP 直接内存映射器驱动程序的实用程序： dmaputil.exe 状态 | 启用 | 禁用状态 [-v] 打印 dmap 当前是否已启用。 传递的详细的配置信息-v 标志。
启用在下一步启动启用 dmap。
禁用在下一步启动禁用 dmap。
