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
# <a name="working-with-lightning-providers"></a><span data-ttu-id="75b55-104">使用闪电提供程序</span><span class="sxs-lookup"><span data-stu-id="75b55-104">Working with lightning providers</span></span>
<span data-ttu-id="75b55-105">Microsoft.IoT.Lightning.Providers 库包含一组通过闪电般的控制器总线提供程序以便与在看板进行交互的直接内存映射驱动程序 (DMAP)。</span><span class="sxs-lookup"><span data-stu-id="75b55-105">The Microsoft.IoT.Lightning.Providers library contains a set of providers to interface with the on board controller buses through the Lightning direct memory mapped driver (DMAP).</span></span>


## <a name="about-the-direct-memory-mapped-driver-dmap"></a><span data-ttu-id="75b55-106">有关直接内存映射驱动程序 (DMAP)</span><span class="sxs-lookup"><span data-stu-id="75b55-106">About the direct memory mapped driver (DMAP)</span></span>

<span data-ttu-id="75b55-107">DMAP 驱动程序是通过默认收件箱驱动程序提供 GPIO 性能改进的开发中驱动程序。</span><span class="sxs-lookup"><span data-stu-id="75b55-107">The DMAP driver is an in-development driver that provides GPIO performance improvements over the default inbox driver.</span></span> <span data-ttu-id="75b55-108">若要了解有关这些性能改进的详细信息，请访问[闪电性能测试](../develop-your-app/LightningPerformance.md)页。</span><span class="sxs-lookup"><span data-stu-id="75b55-108">To learn more about these performance improvements visit the [Lightning Performance Testing](../develop-your-app/LightningPerformance.md) page.</span></span>

<span data-ttu-id="75b55-109">DMAP 驱动程序产品/服务 GPIO 性能改进通过收件箱驱动程序，而控制器命令发送到通过用户模式内存映射地址 DMAP 驱动程序的每个控制器。</span><span class="sxs-lookup"><span data-stu-id="75b55-109">While DMAP driver offer GPIO performance improvements over the Inbox driver, controller commands are sent to the DMAP driver through user-mode memory mapped addresses for each of the controllers.</span></span> <span data-ttu-id="75b55-110">仅使用闪电般的提供程序 Api 或 Microsoft.IoT.Lightning.Providers 的应用。</span><span class="sxs-lookup"><span data-stu-id="75b55-110">An app that only uses the Lightning provider APIs or Microsoft.IoT.Lightning.Providers.</span></span> <span data-ttu-id="75b55-111">但是，恶意应用程序可以直接写入内存并会导致硬件/安全问题。</span><span class="sxs-lookup"><span data-stu-id="75b55-111">However, a malicious app would be able to write directly to that memory and cause hardware/security issues.</span></span> <span data-ttu-id="75b55-112">在具有受信任的应用的计算机，DMAP 是通常可以安全地使用。</span><span class="sxs-lookup"><span data-stu-id="75b55-112">On a machine with only trusted apps, the DMAP is generally safe to use.</span></span>   

## <a name="obtaining-the-library"></a><span data-ttu-id="75b55-113">获取库</span><span class="sxs-lookup"><span data-stu-id="75b55-113">Obtaining the library</span></span>

<span data-ttu-id="75b55-114">库提供的一部分[闪电 SDK Nuget 包](https://www.nuget.org/packages/Microsoft.IoT.Lightning)上可用的源代码[闪电般 ms-iot 的 GitHub 存储库](https://github.com/ms-iot/lightning/)。</span><span class="sxs-lookup"><span data-stu-id="75b55-114">The library is provided as part of the [Lightning SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning) with source code available on [GitHub ms-iot/Lightning repository](https://github.com/ms-iot/lightning/).</span></span>

<span data-ttu-id="75b55-115">此外上, 提供有示例演示如何使用不同的提供程序[ms-iot/BusProviders 的 GitHub 存储库](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)。</span><span class="sxs-lookup"><span data-stu-id="75b55-115">Additonally, samples showing how to use the different providers are available on [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

## <a name="adding-the-library-to-your-application"></a><span data-ttu-id="75b55-116">将库添加到你的应用程序</span><span class="sxs-lookup"><span data-stu-id="75b55-116">Adding the library to your application</span></span>

### <a name="option-1-starting-from-an-existing-sample"></a><span data-ttu-id="75b55-117">选项 1：从现有示例开始</span><span class="sxs-lookup"><span data-stu-id="75b55-117">Option 1: Starting from an existing sample</span></span>
<span data-ttu-id="75b55-118">开始编码使用闪电提供程序的快速方法是开始中的示例之一[ms-iot/BusProviders 的 GitHub 存储库](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)。</span><span class="sxs-lookup"><span data-stu-id="75b55-118">A quick way to start coding using the Lightning providers is to start with one of the samples in the [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

<span data-ttu-id="75b55-119">每个示例引用闪电 SDK 并正确配置为使用闪电提供程序库。</span><span class="sxs-lookup"><span data-stu-id="75b55-119">Each of the samples references the Lightning SDK and is configured properly to use the Lightning providers library.</span></span>

<span data-ttu-id="75b55-120">**请注意**，若要运行示例，需要使用 Windows 设备的 Web 门户启用 DMAP 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="75b55-120">**Note**, To run the samples, the DMAP driver need to be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="75b55-121">请参阅[闪电设置指南](LightningSetup.md)有关如何启用它的详细信息。</span><span class="sxs-lookup"><span data-stu-id="75b55-121">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable it.</span></span>

### <a name="option-2-referencing-the-library"></a><span data-ttu-id="75b55-122">选项 2：引用库</span><span class="sxs-lookup"><span data-stu-id="75b55-122">Option 2: Referencing the library</span></span>

<span data-ttu-id="75b55-123">此外，它很简单添加所需的闪电形提供程序 Nuget 引用，并支持添加到新的或现有应用程序。</span><span class="sxs-lookup"><span data-stu-id="75b55-123">Additionally, it's straightforward to add the required Lightning providers Nuget reference and support to a new or existing application.</span></span> <span data-ttu-id="75b55-124">按以下步骤操作：</span><span class="sxs-lookup"><span data-stu-id="75b55-124">Follow the steps below:</span></span>

1. <span data-ttu-id="75b55-125">在应用程序中，右键单击项目，然后单击"管理 NuGet 包..."菜单项![UWP 项目</span><span class="sxs-lookup"><span data-stu-id="75b55-125">In your application, right click the project and click the "Manage NuGet Packages..." menu item ![UWP Project</span></span>](../media/LightningProviders/manage-nuget-project.png)

2. <span data-ttu-id="75b55-126">NuGet 包管理器将打开。</span><span class="sxs-lookup"><span data-stu-id="75b55-126">The NuGet Package Manager will open.</span></span> <span data-ttu-id="75b55-127">在浏览选项卡，搜索"闪电 SDK"，并确保选中"包括预发行版"复选框。</span><span class="sxs-lookup"><span data-stu-id="75b55-127">In the Browse tab, search for the "Lightning SDK", making sure to check the "Include prerelease" checkbox.</span></span>

3. <span data-ttu-id="75b55-128">选择最新版本，然后单击"安装"以将快如闪电 SDK 添加到你的项目。</span><span class="sxs-lookup"><span data-stu-id="75b55-128">Select the latest version, and click "Install" to add the Lightning SDK to your project.</span></span> 
![NuGet 包管理器](../media/LightningProviders/nuget-package-manager.png)

4. <span data-ttu-id="75b55-130">按照屏幕上的说明根据需要。</span><span class="sxs-lookup"><span data-stu-id="75b55-130">Follow any on-screen instructions if needed.</span></span> <span data-ttu-id="75b55-131">安装完成后，对闪电 SDK 的引用将添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="75b55-131">When installation is complete, a reference to the Lightning SDK will be added to your project.</span></span>

![快如闪电 SDK 参考](../media/LightningProviders/lightning-sdk-added-to-solution.png)

5. <span data-ttu-id="75b55-133">将以下代码添加到清单文件，Package.appxmanifest。</span><span class="sxs-lookup"><span data-stu-id="75b55-133">Add the code below to your manifest file, Package.appxmanifest.</span></span>

``` XML
<iot:Capability Name="lowLevelDevices" />
<DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>
```

* <span data-ttu-id="75b55-134">首先是使应用程序可以访问自定义设备的功能。</span><span class="sxs-lookup"><span data-stu-id="75b55-134">The first is a capability that will enable the application to access custom devices.</span></span>
* <span data-ttu-id="75b55-135">其次是适用于该 Lightning 接口的设备 GUID ID</span><span class="sxs-lookup"><span data-stu-id="75b55-135">The second is the device guid id for the Lightning interface</span></span>

<span data-ttu-id="75b55-136">两种功能都必须添加到 `<Capabilities>` 节点下的项目的 AppX 清单。</span><span class="sxs-lookup"><span data-stu-id="75b55-136">Both capabilities must be added to the AppX manifest of your project under the `<Capabilities>` node.</span></span> <span data-ttu-id="75b55-137">此外，请务必根据需要添加到应用清单中的所需命名空间。</span><span class="sxs-lookup"><span data-stu-id="75b55-137">Also, make sure to add the required namespaces to your manifest if needed.</span></span>

![AppX 清单功能](../media/LightningProviders/package-manifest-updates.png)

## <a name="updating-your-code-to-use-the-lightning-providers"></a><span data-ttu-id="75b55-139">更新代码以使用闪电提供程序</span><span class="sxs-lookup"><span data-stu-id="75b55-139">Updating your code to use the Lightning providers</span></span>

### <a name="checking-for-the-lightning-dmap-driver"></a><span data-ttu-id="75b55-140">检查 Lightning (DMAP) 驱动程序</span><span class="sxs-lookup"><span data-stu-id="75b55-140">Checking for the Lightning (DMAP) driver</span></span>

<span data-ttu-id="75b55-141">若要检查是否已启用 Lightning，应使用 `LightningProvider.IsLightningEnabled` 属性。</span><span class="sxs-lookup"><span data-stu-id="75b55-141">To check if Lightning is enabled, the `LightningProvider.IsLightningEnabled` property should be used.</span></span> <span data-ttu-id="75b55-142">通常，最好在使用 Lightning 提供程序 API 之前验证 Lightning 驱动程序是否已启用。</span><span class="sxs-lookup"><span data-stu-id="75b55-142">In general, it is always a good practice to verify if the Lightning driver is enabled before using the Lightning provider APIs.</span></span> 

``` C#
if (Microsoft.IoT.Lightning.Providers.LightningProvider.IsLightningEnabled)
{
    // Do something with the Lightning providers
}
```

### <a name="general-usage-pattern"></a><span data-ttu-id="75b55-143">一般使用模式</span><span class="sxs-lookup"><span data-stu-id="75b55-143">General usage pattern</span></span>

<span data-ttu-id="75b55-144">使用提供程序的最简单方法是在应用内部将 Lightning 提供程序设置为默认提供程序。</span><span class="sxs-lookup"><span data-stu-id="75b55-144">The simplest way to use the providers is to set the Lightning Provider as the default inside your app.</span></span> 

<span data-ttu-id="75b55-145">将以下代码如果闪电提供程序不可用，设置`Microsoft.IoT.Lightning.Providers.LightningProvider`作为默认提供程序。</span><span class="sxs-lookup"><span data-stu-id="75b55-145">The code below will, if the Lightning Provider is available, set `Microsoft.IoT.Lightning.Providers.LightningProvider` as the default provider.</span></span> <span data-ttu-id="75b55-146">否则，在没有显式设置任何默认提供程序时，各种总线将退回到默认提供程序。</span><span class="sxs-lookup"><span data-stu-id="75b55-146">Otherwise, when no default provider is explicitly set, the various busses will fall back to the default one.</span></span>
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

<span data-ttu-id="75b55-147">为所需总线配备了控制器后，你可以像往常一样使用它。</span><span class="sxs-lookup"><span data-stu-id="75b55-147">After you have a controller for the desired bus, you can use it as you normally would.</span></span> 

### <a name="using-lightning-for-individual-buses"></a><span data-ttu-id="75b55-148">将 Lightning 用于个别总线</span><span class="sxs-lookup"><span data-stu-id="75b55-148">Using Lightning for individual buses</span></span>

<span data-ttu-id="75b55-149">如果你需要使用不同的默认提供程序，以下部分将介绍如何将 Lightning 提供程序用于个别总线。</span><span class="sxs-lookup"><span data-stu-id="75b55-149">If you want to use a different default provider, the sections below show how you can use the Lightning providers for individual busses.</span></span> 

#### <a name="for-gpio-bus-controller"></a><span data-ttu-id="75b55-150">对于 GPIO 总线控制器：</span><span class="sxs-lookup"><span data-stu-id="75b55-150">For GPIO bus controller:</span></span>

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

#### <a name="for-i2c-bus-controller"></a><span data-ttu-id="75b55-151">对于 I2C 总线控制器：</span><span class="sxs-lookup"><span data-stu-id="75b55-151">For I2C bus controller:</span></span>

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

#### <a name="for-spi-bus-controller"></a><span data-ttu-id="75b55-152">对于 SPI 总线控制器：</span><span class="sxs-lookup"><span data-stu-id="75b55-152">For SPI bus controller:</span></span>
<span data-ttu-id="75b55-153">使用 Microsoft.IoT.Lightning.Providers; 使用 Windows.Devices; 使用 Windows.Devices.Spi;</span><span class="sxs-lookup"><span data-stu-id="75b55-153">using Microsoft.IoT.Lightning.Providers; using Windows.Devices; using Windows.Devices.Spi;</span></span>

``` C#
if (LightningProvider.IsLightningEnabled)
{
    SpiController controller =  (await SpiController.GetControllersAsync(LightningSpiProvider.GetSpiProvider()))[0];
    SpiDevice SpiDisplay = controller.GetDevice(spiConnectionSettings);
}
```

## <a name="lightning-provider-samples"></a><span data-ttu-id="75b55-154">Lightning 提供程序示例</span><span class="sxs-lookup"><span data-stu-id="75b55-154">Lightning Provider Samples</span></span>

<span data-ttu-id="75b55-155">以下示例演示了如何使用 Lightning 提供程序以及受支持的总线类型：</span><span class="sxs-lookup"><span data-stu-id="75b55-155">The following samples demonstrate using the Lightning providers with supported bus types:</span></span>

* <span data-ttu-id="75b55-156">[带有 Lightning 提供程序的 Blinky (UI)](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) 演示了前台应用程序中带有 Lightning 提供程序的 GPIO</span><span class="sxs-lookup"><span data-stu-id="75b55-156">[Blinky (UI) with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) demonstrates GPIO with Lightning Provider in a foreground application</span></span>

* <span data-ttu-id="75b55-157">[带有 Lightning 提供程序的 BlinkyHeadless](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) 演示了无外设应用程序中带有 Lightning 提供程序的 GPIO</span><span class="sxs-lookup"><span data-stu-id="75b55-157">[BlinkyHeadless with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) demonstrates GPIO with Lightning Provider in a headless application</span></span>

* <span data-ttu-id="75b55-158">[带有 Lightning 提供程序的 SPIDisplay](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) 演示了使用 API 控制使用带有 Lightning 提供程序的 SPI 的设备</span><span class="sxs-lookup"><span data-stu-id="75b55-158">[SPIDisplay with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) demonstrates the usage of the API to control a device using SPI with Lightning Provider</span></span>
 
* <span data-ttu-id="75b55-159">[带有 Lightning 提供程序的 WeatherStation](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) 演示了与使用带有 Lightning 提供程序的 I2C 的设备进行交互</span><span class="sxs-lookup"><span data-stu-id="75b55-159">[WeatherStation with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) demonstrates interacting with a device using I2C with Lightning Provider</span></span>

## <a name="build-requirements"></a><span data-ttu-id="75b55-160">生成要求</span><span class="sxs-lookup"><span data-stu-id="75b55-160">Build Requirements</span></span>



### <a name="windows-sdk-update"></a><span data-ttu-id="75b55-161">Windows SDK 更新</span><span class="sxs-lookup"><span data-stu-id="75b55-161">Windows SDK Update</span></span>

<span data-ttu-id="75b55-162">生成和使用库所需的 Windows SDK 为 10.0.10586.0 或更高版本（可以从[此处](https://dev.windows.com/en-US/downloads/windows-10-sdk)下载）。</span><span class="sxs-lookup"><span data-stu-id="75b55-162">Windows SDK required for building and using the library is 10.0.10586.0 or higher which can be downloaded from [here](https://dev.windows.com/en-US/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="75b55-163">有关设置的所有内容的详细信息，请参阅[我们入门指南。](https://developer.microsoft.com/en-us/windows/iot/getstarted)。</span><span class="sxs-lookup"><span data-stu-id="75b55-163">For more information on setting everything up, refer to [our get started guide.](https://developer.microsoft.com/en-us/windows/iot/getstarted).</span></span>

### <a name="nuget-package-dependencies"></a><span data-ttu-id="75b55-164">Nuget 包依赖关系</span><span class="sxs-lookup"><span data-stu-id="75b55-164">Nuget Package Dependencies</span></span>

<span data-ttu-id="75b55-165">Lightning 提供程序库依赖于 [Microsoft.IoT.Lightning Nuget 包](https://www.nuget.org/packages/Microsoft.IoT.Lightning)，该包反过来又依赖于 [Arduino SDK Nuget 包](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino)。</span><span class="sxs-lookup"><span data-stu-id="75b55-165">The Lightning Provider library depends on the [Microsoft.IoT.Lightning Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning), which in turn depends on the [Arduino SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino).</span></span> <span data-ttu-id="75b55-166">这两个 Nuget 包在库项目中引用，并且可以从 Nuget.org 中获取。</span><span class="sxs-lookup"><span data-stu-id="75b55-166">Both Nuget packages are referenced in the library projects, and are available from Nuget.org.</span></span>

<span data-ttu-id="75b55-167">如果需要，每个包的源代码也可用于 [Lightning](https://github.com/ms-iot/lightning) 和 [Arduino SDK](https://github.com/ms-iot/arduino-sdk) 存储库中的 GitHub 上。</span><span class="sxs-lookup"><span data-stu-id="75b55-167">If needed, source code for each is also available on GitHub at the [Lightning](https://github.com/ms-iot/lightning) and [Arduino SDK](https://github.com/ms-iot/arduino-sdk) repositories.</span></span>

<span data-ttu-id="75b55-168">Microsoft.IoT.Lightning Nuget 目前仍是预发行版，因此当更新的版本可用时，应从 Nuget.org 进行更新。</span><span class="sxs-lookup"><span data-stu-id="75b55-168">Currently, Microsoft.IoT.Lightning Nuget is still pre-release, so should be updated from Nuget.org, when newer versions are available.</span></span>

<span data-ttu-id="75b55-169">为了能够安装预发行版（当前版本）的 Microsoft.IoT.Lightning Nuget 包以及接收 Lightning 程序包的预发行更新，请务必在 Nuget 包管理器中设置“包含预发行版”。</span><span class="sxs-lookup"><span data-stu-id="75b55-169">In order to install prerelease (current) version of Microsoft.IoT.Lightning Nuget package as well as receive prerelease updates to the Lightning package, make sure to set the "Include prerelease" option in the Nuget Package Manager.</span></span>

1. <span data-ttu-id="75b55-170">右键单击项目中的“引用”</span><span class="sxs-lookup"><span data-stu-id="75b55-170">Right click References in your project</span></span>
1. <span data-ttu-id="75b55-171">单击“管理 Nuget 包...”</span><span class="sxs-lookup"><span data-stu-id="75b55-171">Click "Manage Nuget Packages..."</span></span>
1. <span data-ttu-id="75b55-172">选择 Lightning Nuget 的程序包源</span><span class="sxs-lookup"><span data-stu-id="75b55-172">Select package sources for Lightning nuget</span></span>
1. <span data-ttu-id="75b55-173">单击“包含预发行版”。</span><span class="sxs-lookup"><span data-stu-id="75b55-173">Click "Include prerelease".</span></span>
1. <span data-ttu-id="75b55-174">单击“安装”以将 Nuget 包安装到你的项目中</span><span class="sxs-lookup"><span data-stu-id="75b55-174">Click "Install" to install the nuget package to your project</span></span>

![程序包管理器配置](../media/LightningProviders/Nuget_PackageManager.png)

## <a name="runtime-requirements"></a><span data-ttu-id="75b55-176">运行时要求</span><span class="sxs-lookup"><span data-stu-id="75b55-176">Runtime Requirements</span></span>

### <a name="windows-iot-core-fall-update-required"></a><span data-ttu-id="75b55-177">需要 Windows IoT 核心版秋季更新</span><span class="sxs-lookup"><span data-stu-id="75b55-177">Windows IoT Core Fall Update required</span></span>
<span data-ttu-id="75b55-178">目前仅 Windows IoT 核心版的秋季更新版本中包含 Lightning 提供程序支持。</span><span class="sxs-lookup"><span data-stu-id="75b55-178">Lightning providers support is currently included in the Fall Update builds for Windows IoT Core.</span></span>
<span data-ttu-id="75b55-179">你可以从我们的[下载页](https://developer.microsoft.com/windows/iot/Downloads)下载 Windows 10 IoT 核心版映像。</span><span class="sxs-lookup"><span data-stu-id="75b55-179">You can download a Windows 10 IoT Core image from our [downloads page](https://developer.microsoft.com/windows/iot/Downloads).</span></span> <span data-ttu-id="75b55-180">单击你的设备类型的“下载 Insider Preview”。</span><span class="sxs-lookup"><span data-stu-id="75b55-180">Click on "Download Insider Preview" for your device type.</span></span>

### <a name="direct-memory-mapped-driver-must-be-enabled"></a><span data-ttu-id="75b55-181">必须启用直接内存映射的驱动程序</span><span class="sxs-lookup"><span data-stu-id="75b55-181">Direct Memory Mapped driver must be enabled</span></span>
 
<span data-ttu-id="75b55-182">Lightning 提供程序库中的 API 需要在目标设备上启用 Lightning 直接内存映射的驱动程序。</span><span class="sxs-lookup"><span data-stu-id="75b55-182">The APIs in the Lightning Provider library require the Lightning Direct Memory Mapped driver to be enabled on the target device.</span></span> <span data-ttu-id="75b55-183">Raspberry Pi 2/3 和 MinnowBoard Max 让驱动程序可用，但默认情况下不启用。</span><span class="sxs-lookup"><span data-stu-id="75b55-183">Both Raspberry Pi 2/3 and MinnowBoard Max have the driver available, but not enabled by default.</span></span>

<span data-ttu-id="75b55-184">可以使用 Windows Devices Web Portal 启用驱动程序。</span><span class="sxs-lookup"><span data-stu-id="75b55-184">The driver can be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="75b55-185">有关如何启用 Lightning 驱动程序的详细信息，请参阅 [Lightning 设置指南](LightningSetup.md)。</span><span class="sxs-lookup"><span data-stu-id="75b55-185">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable the Lightning driver.</span></span>

![设备页面](../media/LightningProviders/dmap4.png)

<span data-ttu-id="75b55-187">此外可以使用 DmapUtil 命令启用驱动程序：</span><span class="sxs-lookup"><span data-stu-id="75b55-187">The driver can also be enabled with the DmapUtil command:</span></span>

<span data-ttu-id="75b55-188">DmapUtil:若要启用或禁用使用情况的 DMAP 直接内存映射器驱动程序的实用程序： dmaputil.exe 状态 | 启用 | 禁用状态 [-v] 打印 dmap 当前是否已启用。</span><span class="sxs-lookup"><span data-stu-id="75b55-188">DmapUtil: Utility to turn the DMAP direct memory mapper driver on or off Usage: dmaputil.exe status|enable|disable status [-v]   Print out whether dmap is currently enabled.</span></span> <span data-ttu-id="75b55-189">传递的详细的配置信息-v 标志。</span><span class="sxs-lookup"><span data-stu-id="75b55-189">Pass the -v flag for detailed configuration information.</span></span>
<span data-ttu-id="75b55-190">启用在下一步启动启用 dmap。</span><span class="sxs-lookup"><span data-stu-id="75b55-190">enable        Enable dmap on next boot.</span></span>
<span data-ttu-id="75b55-191">禁用在下一步启动禁用 dmap。</span><span class="sxs-lookup"><span data-stu-id="75b55-191">disable       Disable dmap on next boot.</span></span>
