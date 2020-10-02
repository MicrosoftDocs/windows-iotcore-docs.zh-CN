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
# <a name="working-with-lightning-providers"></a><span data-ttu-id="56b49-104">使用闪电提供程序</span><span class="sxs-lookup"><span data-stu-id="56b49-104">Working with lightning providers</span></span>
<span data-ttu-id="56b49-105">DMAP 库包含一组提供程序，这些提供程序用于通过闪电直内存映射驱动 (程序在) 上通过闪电形控制器总线连接。</span><span class="sxs-lookup"><span data-stu-id="56b49-105">The Microsoft.IoT.Lightning.Providers library contains a set of providers to interface with the on board controller buses through the Lightning direct memory mapped driver (DMAP).</span></span>


## <a name="about-the-direct-memory-mapped-driver-dmap"></a><span data-ttu-id="56b49-106">关于直接内存映射驱动程序 (DMAP) </span><span class="sxs-lookup"><span data-stu-id="56b49-106">About the direct memory mapped driver (DMAP)</span></span>

<span data-ttu-id="56b49-107">DMAP 驱动程序是一个开发中的驱动程序，它提供对默认收件箱驱动程序的 GPIO 性能改进。</span><span class="sxs-lookup"><span data-stu-id="56b49-107">The DMAP driver is an in-development driver that provides GPIO performance improvements over the default inbox driver.</span></span> <span data-ttu-id="56b49-108">若要了解有关这些性能改进的详细信息，请访问 [闪电性能测试](../develop-your-app/LightningPerformance.md) 页。</span><span class="sxs-lookup"><span data-stu-id="56b49-108">To learn more about these performance improvements visit the [Lightning Performance Testing](../develop-your-app/LightningPerformance.md) page.</span></span>

<span data-ttu-id="56b49-109">尽管 DMAP 驱动程序通过收件箱驱动程序提供 GPIO 性能改进，但控制器命令通过每个控制器的用户模式内存映射地址发送到 DMAP 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="56b49-109">While DMAP driver offer GPIO performance improvements over the Inbox driver, controller commands are sent to the DMAP driver through user-mode memory mapped addresses for each of the controllers.</span></span> <span data-ttu-id="56b49-110">仅使用闪电提供程序 Api 或 Microsoft 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="56b49-110">An app that only uses the Lightning provider APIs or Microsoft.IoT.Lightning.Providers.</span></span> <span data-ttu-id="56b49-111">但是，恶意应用程序能够直接写入该内存并导致硬件/安全问题。</span><span class="sxs-lookup"><span data-stu-id="56b49-111">However, a malicious app would be able to write directly to that memory and cause hardware/security issues.</span></span> <span data-ttu-id="56b49-112">在仅具有受信任应用的计算机上，DMAP 通常可以安全使用。</span><span class="sxs-lookup"><span data-stu-id="56b49-112">On a machine with only trusted apps, the DMAP is generally safe to use.</span></span>   

## <a name="obtaining-the-library"></a><span data-ttu-id="56b49-113">获取库</span><span class="sxs-lookup"><span data-stu-id="56b49-113">Obtaining the library</span></span>

<span data-ttu-id="56b49-114">使用[GitHub ms-iot/闪电存储库](https://github.com/ms-iot/lightning/)中提供源代码的[闪电 SDK NuGet 包](https://www.nuget.org/packages/Microsoft.IoT.Lightning)中提供了库。</span><span class="sxs-lookup"><span data-stu-id="56b49-114">The library is provided as part of the [Lightning SDK NuGet package](https://www.nuget.org/packages/Microsoft.IoT.Lightning) with source code available on [GitHub ms-iot/Lightning repository](https://github.com/ms-iot/lightning/).</span></span>

<span data-ttu-id="56b49-115">此外，还提供了有关如何使用不同的提供程序的示例，请访问 [GitHub ms-iot/BusProviders 存储库](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)。</span><span class="sxs-lookup"><span data-stu-id="56b49-115">Additionally, samples showing how to use the different providers are available on [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

## <a name="adding-the-library-to-your-application"></a><span data-ttu-id="56b49-116">向应用程序添加库</span><span class="sxs-lookup"><span data-stu-id="56b49-116">Adding the library to your application</span></span>

### <a name="option-1-starting-from-an-existing-sample"></a><span data-ttu-id="56b49-117">选项1：从现有示例开始</span><span class="sxs-lookup"><span data-stu-id="56b49-117">Option 1: Starting from an existing sample</span></span>
<span data-ttu-id="56b49-118">使用闪电提供程序进行编码的一种快速方法是从 [GitHub ms-iot/BusProviders 存储库](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)中的一个示例开始。</span><span class="sxs-lookup"><span data-stu-id="56b49-118">A quick way to start coding using the Lightning providers is to start with one of the samples in the [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

<span data-ttu-id="56b49-119">每个示例都引用了闪电 SDK，并正确配置为使用闪电提供程序库。</span><span class="sxs-lookup"><span data-stu-id="56b49-119">Each of the samples references the Lightning SDK and is configured properly to use the Lightning providers library.</span></span>

<span data-ttu-id="56b49-120">**请注意**，若要运行这些示例，需要使用 Windows 设备 Web 门户启用 DMAP 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="56b49-120">**Note**, To run the samples, the DMAP driver need to be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="56b49-121">有关如何启用它的详细信息，请参阅 [闪电安装指南](LightningSetup.md) 。</span><span class="sxs-lookup"><span data-stu-id="56b49-121">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable it.</span></span>

### <a name="option-2-referencing-the-library"></a><span data-ttu-id="56b49-122">选项2：引用库</span><span class="sxs-lookup"><span data-stu-id="56b49-122">Option 2: Referencing the library</span></span>

<span data-ttu-id="56b49-123">此外，将所需的闪电提供程序 NuGet 引用和支持添加到新的或现有的应用程序也很简单。</span><span class="sxs-lookup"><span data-stu-id="56b49-123">Additionally, it's straightforward to add the required Lightning providers NuGet reference and support to a new or existing application.</span></span> <span data-ttu-id="56b49-124">请遵循以下步骤进行配置：</span><span class="sxs-lookup"><span data-stu-id="56b49-124">Follow the steps below:</span></span>

1. <span data-ttu-id="56b49-125">在应用程序中，右键单击项目，然后单击 "管理 NuGet 包 ..."菜单项</span><span class="sxs-lookup"><span data-stu-id="56b49-125">In your application, right-click the project and click the "Manage NuGet Packages..." menu item</span></span>  
![UWP 项目](../media/LightningProviders/manage-nuget-project.png)

2. <span data-ttu-id="56b49-127">NuGet 包管理器将打开。</span><span class="sxs-lookup"><span data-stu-id="56b49-127">The NuGet Package Manager will open.</span></span> <span data-ttu-id="56b49-128">在 "浏览" 选项卡中，搜索 "闪电 SDK"，确保选中 "包括预发行版" 复选框。</span><span class="sxs-lookup"><span data-stu-id="56b49-128">In the Browse tab, search for the "Lightning SDK", making sure to check the "Include prerelease" checkbox.</span></span>

3. <span data-ttu-id="56b49-129">选择最新版本，然后单击 "安装" 以将闪电 SDK 添加到你的项目。</span><span class="sxs-lookup"><span data-stu-id="56b49-129">Select the latest version, and click "Install" to add the Lightning SDK to your project.</span></span> 
<span data-ttu-id="56b49-130">![NuGet 包管理器](../media/LightningProviders/nuget-package-manager.png)</span><span class="sxs-lookup"><span data-stu-id="56b49-130">![NuGet Package Manager](../media/LightningProviders/nuget-package-manager.png)</span></span>

4. <span data-ttu-id="56b49-131">如果需要，请按照屏幕上的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="56b49-131">Follow any on-screen instructions if needed.</span></span> <span data-ttu-id="56b49-132">安装完成后，将向你的项目添加对闪电 SDK 的引用。</span><span class="sxs-lookup"><span data-stu-id="56b49-132">When installation is complete, a reference to the Lightning SDK will be added to your project.</span></span>

![闪电 SDK 参考](../media/LightningProviders/lightning-sdk-added-to-solution.png)

5. <span data-ttu-id="56b49-134">将下面的代码添加到清单文件 appxmanifest.xml。</span><span class="sxs-lookup"><span data-stu-id="56b49-134">Add the code below to your manifest file, Package.appxmanifest.</span></span>

``` XML
<iot:Capability Name="lowLevelDevices" />
<DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>
```

* <span data-ttu-id="56b49-135">第一种功能将使应用程序能够访问自定义设备。</span><span class="sxs-lookup"><span data-stu-id="56b49-135">The first is a capability that will enable the application to access custom devices.</span></span>
* <span data-ttu-id="56b49-136">第二个是闪电接口的设备 guid ID</span><span class="sxs-lookup"><span data-stu-id="56b49-136">The second is the device guid ID for the Lightning interface</span></span>

<span data-ttu-id="56b49-137">必须将这两项功能添加到项目的 AppX 清单中 `<Capabilities>` 。</span><span class="sxs-lookup"><span data-stu-id="56b49-137">Both capabilities must be added to the AppX manifest of your project under the `<Capabilities>` node.</span></span> <span data-ttu-id="56b49-138">此外，如果需要，请确保将所需的命名空间添加到清单中。</span><span class="sxs-lookup"><span data-stu-id="56b49-138">Also, make sure to add the required namespaces to your manifest if needed.</span></span>

![AppX 清单 Capabailities](../media/LightningProviders/package-manifest-updates.png)

## <a name="updating-your-code-to-use-the-lightning-providers"></a><span data-ttu-id="56b49-140">更新代码以使用闪电提供程序</span><span class="sxs-lookup"><span data-stu-id="56b49-140">Updating your code to use the Lightning providers</span></span>

### <a name="checking-for-the-lightning-dmap-driver"></a><span data-ttu-id="56b49-141">检查闪电 (DMAP) 驱动程序</span><span class="sxs-lookup"><span data-stu-id="56b49-141">Checking for the Lightning (DMAP) driver</span></span>

<span data-ttu-id="56b49-142">若要检查是否启用了闪电， `LightningProvider.IsLightningEnabled` 应使用属性。</span><span class="sxs-lookup"><span data-stu-id="56b49-142">To check if Lightning is enabled, the `LightningProvider.IsLightningEnabled` property should be used.</span></span> <span data-ttu-id="56b49-143">通常，在使用闪电提供程序 Api 之前，验证是否启用了闪电驱动程序是一种很好的做法。</span><span class="sxs-lookup"><span data-stu-id="56b49-143">In general, it is always a good practice to verify if the Lightning driver is enabled before using the Lightning provider APIs.</span></span> 

``` C#
if (Microsoft.IoT.Lightning.Providers.LightningProvider.IsLightningEnabled)
{
    // Do something with the Lightning providers
}
```

### <a name="general-usage-pattern"></a><span data-ttu-id="56b49-144">常规用法模式</span><span class="sxs-lookup"><span data-stu-id="56b49-144">General usage pattern</span></span>

<span data-ttu-id="56b49-145">使用提供程序的最简单方法是将闪电提供程序设置为应用程序中的默认提供程序。</span><span class="sxs-lookup"><span data-stu-id="56b49-145">The simplest way to use the providers is to set the Lightning Provider as the default inside your app.</span></span> 

<span data-ttu-id="56b49-146">如果闪电提供商可用，以下代码将设置 `Microsoft.IoT.Lightning.Providers.LightningProvider` 为默认提供程序。</span><span class="sxs-lookup"><span data-stu-id="56b49-146">The code below will, if the Lightning Provider is available, set `Microsoft.IoT.Lightning.Providers.LightningProvider` as the default provider.</span></span> <span data-ttu-id="56b49-147">否则，如果未显式设置默认提供程序，则不同的总线会退回到默认提供程序。</span><span class="sxs-lookup"><span data-stu-id="56b49-147">Otherwise, when no default provider is explicitly set, the various busses will fall back to the default one.</span></span>
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

<span data-ttu-id="56b49-148">获得所需总线的控制器后，可以像平常一样使用它。</span><span class="sxs-lookup"><span data-stu-id="56b49-148">After you have a controller for the desired bus, you can use it as you normally would.</span></span> 

### <a name="using-lightning-for-individual-buses"></a><span data-ttu-id="56b49-149">为单个总线使用闪电</span><span class="sxs-lookup"><span data-stu-id="56b49-149">Using Lightning for individual buses</span></span>

<span data-ttu-id="56b49-150">如果要使用其他默认提供程序，以下部分说明了如何为单个总线使用闪电提供程序。</span><span class="sxs-lookup"><span data-stu-id="56b49-150">If you want to use a different default provider, the sections below show how you can use the Lightning providers for individual busses.</span></span> 

#### <a name="for-gpio-bus-controller"></a><span data-ttu-id="56b49-151">对于 GPIO 总线控制器：</span><span class="sxs-lookup"><span data-stu-id="56b49-151">For GPIO bus controller:</span></span>

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

#### <a name="for-i2c-bus-controller"></a><span data-ttu-id="56b49-152">对于 I2C 总线控制器：</span><span class="sxs-lookup"><span data-stu-id="56b49-152">For I2C bus controller:</span></span>

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

#### <a name="for-spi-bus-controller"></a><span data-ttu-id="56b49-153">对于 SPI 总线控制器：</span><span class="sxs-lookup"><span data-stu-id="56b49-153">For SPI bus controller:</span></span>
<span data-ttu-id="56b49-154">使用 Microsoft IoT。使用 Windows 设备;使用 Windows. Spi;</span><span class="sxs-lookup"><span data-stu-id="56b49-154">using Microsoft.IoT.Lightning.Providers; using Windows.Devices; using Windows.Devices.Spi;</span></span>

``` C#
if (LightningProvider.IsLightningEnabled)
{
    SpiController controller =  (await SpiController.GetControllersAsync(LightningSpiProvider.GetSpiProvider()))[0];
    SpiDevice SpiDisplay = controller.GetDevice(spiConnectionSettings);
}
```

## <a name="lightning-provider-samples"></a><span data-ttu-id="56b49-155">闪电提供商示例</span><span class="sxs-lookup"><span data-stu-id="56b49-155">Lightning Provider Samples</span></span>

<span data-ttu-id="56b49-156">以下示例演示如何将闪电提供程序与支持的总线类型一起使用：</span><span class="sxs-lookup"><span data-stu-id="56b49-156">The following samples demonstrate using the Lightning providers with supported bus types:</span></span>

* <span data-ttu-id="56b49-157">[使用闪电提供商) 的 Blinky (UI](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) 说明了在前台应用程序中使用闪电提供程序的 GPIO</span><span class="sxs-lookup"><span data-stu-id="56b49-157">[Blinky (UI) with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) demonstrates GPIO with Lightning Provider in a foreground application</span></span>

* <span data-ttu-id="56b49-158">[使用闪电提供](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) 程序的 BlinkyHeadless 演示如何在无外设应用程序中使用闪电提供程序</span><span class="sxs-lookup"><span data-stu-id="56b49-158">[BlinkyHeadless with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) demonstrates GPIO with Lightning Provider in a headless application</span></span>

* <span data-ttu-id="56b49-159">使用[闪电提供程序的 SPIDisplay](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay)演示了如何使用 API 来控制使用 SPI 和闪电提供程序的设备</span><span class="sxs-lookup"><span data-stu-id="56b49-159">[SPIDisplay with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) demonstrates the usage of the API to control a device using SPI with Lightning Provider</span></span>
 
* <span data-ttu-id="56b49-160">使用[闪电提供程序的 WeatherStation](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation)演示如何使用带有闪电的 I2C 提供程序与设备交互</span><span class="sxs-lookup"><span data-stu-id="56b49-160">[WeatherStation with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) demonstrates interacting with a device using I2C with Lightning Provider</span></span>

## <a name="build-requirements"></a><span data-ttu-id="56b49-161">生成要求</span><span class="sxs-lookup"><span data-stu-id="56b49-161">Build Requirements</span></span>



### <a name="windows-sdk-update"></a><span data-ttu-id="56b49-162">Windows SDK 更新</span><span class="sxs-lookup"><span data-stu-id="56b49-162">Windows SDK Update</span></span>

<span data-ttu-id="56b49-163">生成和使用库所需的 Windows SDK 10.0.10586.0 或更高版本，可从 [此处](https://dev.windows.com/en-US/downloads/windows-10-sdk)下载。</span><span class="sxs-lookup"><span data-stu-id="56b49-163">Windows SDK required for building and using the library is 10.0.10586.0 or higher, which can be downloaded from [here](https://dev.windows.com/en-US/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="56b49-164">有关设置所有内容的详细信息，请参阅[入门指南。](https://developer.microsoft.com/en-us/windows/iot/getstarted)</span><span class="sxs-lookup"><span data-stu-id="56b49-164">For more information on setting up everything, refer to [our get started guide.](https://developer.microsoft.com/en-us/windows/iot/getstarted).</span></span>

### <a name="nuget-package-dependencies"></a><span data-ttu-id="56b49-165">NuGet 包依赖项</span><span class="sxs-lookup"><span data-stu-id="56b49-165">NuGet Package Dependencies</span></span>

<span data-ttu-id="56b49-166">闪电提供程序库依赖于[ARDUINO SDK nuget](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino)[包，而](https://www.nuget.org/packages/Microsoft.IoT.Lightning)后者又依赖于 "</span><span class="sxs-lookup"><span data-stu-id="56b49-166">The Lightning Provider library depends on the [Microsoft.IoT.Lightning NuGet package](https://www.nuget.org/packages/Microsoft.IoT.Lightning), which in turn depends on the [Arduino SDK NuGet package](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino).</span></span> <span data-ttu-id="56b49-167">这两个 NuGet 包都在库项目中进行引用，可从 Nuget.org 中获取。</span><span class="sxs-lookup"><span data-stu-id="56b49-167">Both NuGet packages are referenced in the library projects, and are available from Nuget.org.</span></span>

<span data-ttu-id="56b49-168">如果需要，还可以在 GitHub 上的 [闪电](https://github.com/ms-iot/lightning) 和 [Arduino SDK](https://github.com/ms-iot/arduino-sdk) 存储库中使用每个的源代码。</span><span class="sxs-lookup"><span data-stu-id="56b49-168">If needed, source code for each is also available on GitHub at the [Lightning](https://github.com/ms-iot/lightning) and [Arduino SDK](https://github.com/ms-iot/arduino-sdk) repositories.</span></span>

<span data-ttu-id="56b49-169">目前，在更新版本可用时，Microsoft IoT NuGet 仍处于预发布版本，应从 Nuget.org 更新。</span><span class="sxs-lookup"><span data-stu-id="56b49-169">Currently, Microsoft.IoT.Lightning NuGet is still pre-release, so should be updated from Nuget.org, when newer versions are available.</span></span>

<span data-ttu-id="56b49-170">若要安装 (当前) 版本的 Microsoft IoT NuGet 包，并接收对闪电包的预发布更新，请确保在 NuGet 包管理器中设置 "包括预发行版" 选项。</span><span class="sxs-lookup"><span data-stu-id="56b49-170">In order to install prerelease (current) version of Microsoft.IoT.Lightning NuGet package as well as receive prerelease updates to the Lightning package, make sure to set the "Include prerelease" option in the NuGet Package Manager.</span></span>

1. <span data-ttu-id="56b49-171">右键单击项目中的 "引用"</span><span class="sxs-lookup"><span data-stu-id="56b49-171">Right-click References in your project</span></span>
1. <span data-ttu-id="56b49-172">单击 "管理 NuGet 包 ..."</span><span class="sxs-lookup"><span data-stu-id="56b49-172">Click "Manage NuGet Packages..."</span></span>
1. <span data-ttu-id="56b49-173">为闪电 NuGet 选择包源</span><span class="sxs-lookup"><span data-stu-id="56b49-173">Select package sources for Lightning NuGet</span></span>
1. <span data-ttu-id="56b49-174">单击 "包括预发行版"。</span><span class="sxs-lookup"><span data-stu-id="56b49-174">Click "Include prerelease".</span></span>
1. <span data-ttu-id="56b49-175">单击 "安装" 以将 NuGet 包安装到项目中</span><span class="sxs-lookup"><span data-stu-id="56b49-175">Click "Install" to install the NuGet package to your project</span></span>

![程序包管理器配置](../media/LightningProviders/Nuget_PackageManager.png)

## <a name="runtime-requirements"></a><span data-ttu-id="56b49-177">运行时要求</span><span class="sxs-lookup"><span data-stu-id="56b49-177">Runtime Requirements</span></span>

### <a name="windows-iot-core-fall-update-required"></a><span data-ttu-id="56b49-178">需要 Windows IoT 核心秋季更新</span><span class="sxs-lookup"><span data-stu-id="56b49-178">Windows IoT Core Fall Update required</span></span>
<span data-ttu-id="56b49-179">闪电提供商支持目前包含在 Windows IoT Core 的秋季更新版本中。</span><span class="sxs-lookup"><span data-stu-id="56b49-179">Lightning providers support is currently included in the Fall Update builds for Windows IoT Core.</span></span>
<span data-ttu-id="56b49-180">可以从 [下载页面](https://developer.microsoft.com/windows/iot/Downloads)下载 Windows 10 IoT Core 映像。</span><span class="sxs-lookup"><span data-stu-id="56b49-180">You can download a Windows 10 IoT Core image from our [downloads page](https://developer.microsoft.com/windows/iot/Downloads).</span></span> <span data-ttu-id="56b49-181">对于设备类型，请单击 "下载内幕预览版"。</span><span class="sxs-lookup"><span data-stu-id="56b49-181">Click on "Download Insider Preview" for your device type.</span></span>

### <a name="direct-memory-mapped-driver-must-be-enabled"></a><span data-ttu-id="56b49-182">必须启用直接内存映射驱动程序</span><span class="sxs-lookup"><span data-stu-id="56b49-182">Direct Memory Mapped driver must be enabled</span></span>
 
<span data-ttu-id="56b49-183">闪电提供程序库中的 Api 需要在目标设备上启用闪电直接内存映射驱动程序。</span><span class="sxs-lookup"><span data-stu-id="56b49-183">The APIs in the Lightning Provider library require the Lightning Direct Memory Mapped driver to be enabled on the target device.</span></span> <span data-ttu-id="56b49-184">Raspberry Pi 2/3 和 MinnowBoard Max 都有可用的驱动程序，但默认情况下未启用。</span><span class="sxs-lookup"><span data-stu-id="56b49-184">Both Raspberry Pi 2/3 and MinnowBoard Max have the driver available, but not enabled by default.</span></span>

<span data-ttu-id="56b49-185">可以使用 Windows 设备 Web 门户启用该驱动程序。</span><span class="sxs-lookup"><span data-stu-id="56b49-185">The driver can be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="56b49-186">有关如何启用闪电驱动程序的详细信息，请参阅 [闪电安装指南](LightningSetup.md) 。</span><span class="sxs-lookup"><span data-stu-id="56b49-186">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable the Lightning driver.</span></span>

![设备页](../media/LightningProviders/dmap4.png)

<span data-ttu-id="56b49-188">还可以通过 DmapUtil 命令启用该驱动程序：</span><span class="sxs-lookup"><span data-stu-id="56b49-188">The driver can also be enabled with the DmapUtil command:</span></span>

<span data-ttu-id="56b49-189">DmapUtil：用于打开或关闭 DMAP 直接内存映射器驱动程序的实用工具： dmaputil.exe 状态 | 启用 | 禁用状态 [-v] 输出当前是否已启用 DMAP。</span><span class="sxs-lookup"><span data-stu-id="56b49-189">DmapUtil: Utility to turn the DMAP direct memory mapper driver on or off Usage: dmaputil.exe status|enable|disable status [-v]   Print out whether dmap is currently enabled.</span></span> <span data-ttu-id="56b49-190">传递-v 标志以获取详细的配置信息。</span><span class="sxs-lookup"><span data-stu-id="56b49-190">Pass the -v flag for detailed configuration information.</span></span>
<span data-ttu-id="56b49-191">启用 "在下一次启动时启用 dmap"。</span><span class="sxs-lookup"><span data-stu-id="56b49-191">enable        Enable dmap on next boot.</span></span>
<span data-ttu-id="56b49-192">禁用 "在下一次启动时禁用 dmap"。</span><span class="sxs-lookup"><span data-stu-id="56b49-192">disable       Disable dmap on next boot.</span></span>
