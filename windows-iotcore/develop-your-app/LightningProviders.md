---
title: Lightning 提供程序
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 了解有关如何使用 Microosft 闪电提供程序库的详细信息。
keywords: windows iot, 闪电提供商, 闪电性能测试, 总线
ms.openlocfilehash: 50cbf4f9940538da1570cebb6cc142e7fbe06588
ms.sourcegitcommit: fcc0c6add468040e2f676893b44b260e3ddc3c52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/16/2019
ms.locfileid: "65779387"
---
# <a name="working-with-lightning-providers"></a><span data-ttu-id="7b02a-104">使用闪电提供程序</span><span class="sxs-lookup"><span data-stu-id="7b02a-104">Working with lightning providers</span></span>
<span data-ttu-id="7b02a-105">Microsoft DMAP 库包含一组提供程序, 用于通过闪电直内存映射驱动程序 () 与板控制器总线上的进行交互。</span><span class="sxs-lookup"><span data-stu-id="7b02a-105">The Microsoft.IoT.Lightning.Providers library contains a set of providers to interface with the on board controller buses through the Lightning direct memory mapped driver (DMAP).</span></span>


## <a name="about-the-direct-memory-mapped-driver-dmap"></a><span data-ttu-id="7b02a-106">关于直接内存映射驱动程序 (DMAP)</span><span class="sxs-lookup"><span data-stu-id="7b02a-106">About the direct memory mapped driver (DMAP)</span></span>

<span data-ttu-id="7b02a-107">DMAP 驱动程序是一个开发中的驱动程序, 它提供对默认收件箱驱动程序的 GPIO 性能改进。</span><span class="sxs-lookup"><span data-stu-id="7b02a-107">The DMAP driver is an in-development driver that provides GPIO performance improvements over the default inbox driver.</span></span> <span data-ttu-id="7b02a-108">若要了解有关这些性能改进的详细信息, 请访问[闪电性能测试](../develop-your-app/LightningPerformance.md)页。</span><span class="sxs-lookup"><span data-stu-id="7b02a-108">To learn more about these performance improvements visit the [Lightning Performance Testing](../develop-your-app/LightningPerformance.md) page.</span></span>

<span data-ttu-id="7b02a-109">尽管 DMAP 驱动程序通过收件箱驱动程序提供 GPIO 性能改进, 但控制器命令通过每个控制器的用户模式内存映射地址发送到 DMAP 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="7b02a-109">While DMAP driver offer GPIO performance improvements over the Inbox driver, controller commands are sent to the DMAP driver through user-mode memory mapped addresses for each of the controllers.</span></span> <span data-ttu-id="7b02a-110">仅使用闪电提供程序 Api 或 Microsoft 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="7b02a-110">An app that only uses the Lightning provider APIs or Microsoft.IoT.Lightning.Providers.</span></span> <span data-ttu-id="7b02a-111">但是, 恶意应用程序能够直接写入该内存并导致硬件/安全问题。</span><span class="sxs-lookup"><span data-stu-id="7b02a-111">However, a malicious app would be able to write directly to that memory and cause hardware/security issues.</span></span> <span data-ttu-id="7b02a-112">在仅具有受信任应用的计算机上, DMAP 通常可以安全使用。</span><span class="sxs-lookup"><span data-stu-id="7b02a-112">On a machine with only trusted apps, the DMAP is generally safe to use.</span></span>   

## <a name="obtaining-the-library"></a><span data-ttu-id="7b02a-113">获取库</span><span class="sxs-lookup"><span data-stu-id="7b02a-113">Obtaining the library</span></span>

<span data-ttu-id="7b02a-114">使用[GitHub ms-iot/闪电存储库](https://github.com/ms-iot/lightning/)中提供源代码的[闪电 SDK Nuget 包](https://www.nuget.org/packages/Microsoft.IoT.Lightning)中提供了库。</span><span class="sxs-lookup"><span data-stu-id="7b02a-114">The library is provided as part of the [Lightning SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning) with source code available on [GitHub ms-iot/Lightning repository](https://github.com/ms-iot/lightning/).</span></span>

<span data-ttu-id="7b02a-115">另外中提供了有关如何使用不同的提供程序的示例, 请访问[GitHub ms-iot/BusProviders 存储库](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)。</span><span class="sxs-lookup"><span data-stu-id="7b02a-115">Additonally, samples showing how to use the different providers are available on [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

## <a name="adding-the-library-to-your-application"></a><span data-ttu-id="7b02a-116">向应用程序添加库</span><span class="sxs-lookup"><span data-stu-id="7b02a-116">Adding the library to your application</span></span>

### <a name="option-1-starting-from-an-existing-sample"></a><span data-ttu-id="7b02a-117">选项 1：从现有示例开始</span><span class="sxs-lookup"><span data-stu-id="7b02a-117">Option 1: Starting from an existing sample</span></span>
<span data-ttu-id="7b02a-118">使用闪电提供程序进行编码的一种快速方法是从[GitHub ms-iot/BusProviders 存储库](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers)中的一个示例开始。</span><span class="sxs-lookup"><span data-stu-id="7b02a-118">A quick way to start coding using the Lightning providers is to start with one of the samples in the [GitHub ms-iot/BusProviders repository](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers).</span></span>

<span data-ttu-id="7b02a-119">每个示例都引用了闪电 SDK, 并正确配置为使用闪电提供程序库。</span><span class="sxs-lookup"><span data-stu-id="7b02a-119">Each of the samples references the Lightning SDK and is configured properly to use the Lightning providers library.</span></span>

<span data-ttu-id="7b02a-120">**请注意**, 若要运行这些示例, 需要使用 Windows 设备 Web 门户启用 DMAP 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="7b02a-120">**Note**, To run the samples, the DMAP driver need to be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="7b02a-121">有关如何启用它的详细信息, 请参阅[闪电安装指南](LightningSetup.md)。</span><span class="sxs-lookup"><span data-stu-id="7b02a-121">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable it.</span></span>

### <a name="option-2-referencing-the-library"></a><span data-ttu-id="7b02a-122">选项 2：引用库</span><span class="sxs-lookup"><span data-stu-id="7b02a-122">Option 2: Referencing the library</span></span>

<span data-ttu-id="7b02a-123">此外, 将所需的闪电提供程序 Nuget 引用和支持添加到新的或现有的应用程序也很简单。</span><span class="sxs-lookup"><span data-stu-id="7b02a-123">Additionally, it's straightforward to add the required Lightning providers Nuget reference and support to a new or existing application.</span></span> <span data-ttu-id="7b02a-124">按以下步骤操作：</span><span class="sxs-lookup"><span data-stu-id="7b02a-124">Follow the steps below:</span></span>

1. <span data-ttu-id="7b02a-125">在应用程序中, 右键单击项目, 然后单击 "管理 NuGet 包 ..."菜单项</span><span class="sxs-lookup"><span data-stu-id="7b02a-125">In your application, right click the project and click the "Manage NuGet Packages..." menu item</span></span>  
![UWP 项目](../media/LightningProviders/manage-nuget-project.png)

2. <span data-ttu-id="7b02a-127">NuGet 包管理器将打开。</span><span class="sxs-lookup"><span data-stu-id="7b02a-127">The NuGet Package Manager will open.</span></span> <span data-ttu-id="7b02a-128">在 "浏览" 选项卡中, 搜索 "闪电 SDK", 确保选中 "包括预发行版" 复选框。</span><span class="sxs-lookup"><span data-stu-id="7b02a-128">In the Browse tab, search for the "Lightning SDK", making sure to check the "Include prerelease" checkbox.</span></span>

3. <span data-ttu-id="7b02a-129">选择最新版本, 然后单击 "安装" 以将闪电 SDK 添加到你的项目。</span><span class="sxs-lookup"><span data-stu-id="7b02a-129">Select the latest version, and click "Install" to add the Lightning SDK to your project.</span></span> 
<span data-ttu-id="7b02a-130">![NuGet 包管理器](../media/LightningProviders/nuget-package-manager.png)</span><span class="sxs-lookup"><span data-stu-id="7b02a-130">![NuGet Package Manager](../media/LightningProviders/nuget-package-manager.png)</span></span>

4. <span data-ttu-id="7b02a-131">如果需要, 请按照屏幕上的说明进行操作。</span><span class="sxs-lookup"><span data-stu-id="7b02a-131">Follow any on-screen instructions if needed.</span></span> <span data-ttu-id="7b02a-132">安装完成后, 将向你的项目添加对闪电 SDK 的引用。</span><span class="sxs-lookup"><span data-stu-id="7b02a-132">When installation is complete, a reference to the Lightning SDK will be added to your project.</span></span>

![闪电 SDK 参考](../media/LightningProviders/lightning-sdk-added-to-solution.png)

5. <span data-ttu-id="7b02a-134">将下面的代码添加到清单文件 appxmanifest.xml。</span><span class="sxs-lookup"><span data-stu-id="7b02a-134">Add the code below to your manifest file, Package.appxmanifest.</span></span>

``` XML
<iot:Capability Name="lowLevelDevices" />
<DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>
```

* <span data-ttu-id="7b02a-135">首先是使应用程序可以访问自定义设备的功能。</span><span class="sxs-lookup"><span data-stu-id="7b02a-135">The first is a capability that will enable the application to access custom devices.</span></span>
* <span data-ttu-id="7b02a-136">其次是适用于该 Lightning 接口的设备 GUID ID</span><span class="sxs-lookup"><span data-stu-id="7b02a-136">The second is the device guid id for the Lightning interface</span></span>

<span data-ttu-id="7b02a-137">两种功能都必须添加到 `<Capabilities>` 节点下的项目的 AppX 清单。</span><span class="sxs-lookup"><span data-stu-id="7b02a-137">Both capabilities must be added to the AppX manifest of your project under the `<Capabilities>` node.</span></span> <span data-ttu-id="7b02a-138">此外, 如果需要, 请确保将所需的命名空间添加到清单中。</span><span class="sxs-lookup"><span data-stu-id="7b02a-138">Also, make sure to add the required namespaces to your manifest if needed.</span></span>

![AppX 清单功能](../media/LightningProviders/package-manifest-updates.png)

## <a name="updating-your-code-to-use-the-lightning-providers"></a><span data-ttu-id="7b02a-140">更新代码以使用闪电提供程序</span><span class="sxs-lookup"><span data-stu-id="7b02a-140">Updating your code to use the Lightning providers</span></span>

### <a name="checking-for-the-lightning-dmap-driver"></a><span data-ttu-id="7b02a-141">检查 Lightning (DMAP) 驱动程序</span><span class="sxs-lookup"><span data-stu-id="7b02a-141">Checking for the Lightning (DMAP) driver</span></span>

<span data-ttu-id="7b02a-142">若要检查是否已启用 Lightning，应使用 `LightningProvider.IsLightningEnabled` 属性。</span><span class="sxs-lookup"><span data-stu-id="7b02a-142">To check if Lightning is enabled, the `LightningProvider.IsLightningEnabled` property should be used.</span></span> <span data-ttu-id="7b02a-143">通常，最好在使用 Lightning 提供程序 API 之前验证 Lightning 驱动程序是否已启用。</span><span class="sxs-lookup"><span data-stu-id="7b02a-143">In general, it is always a good practice to verify if the Lightning driver is enabled before using the Lightning provider APIs.</span></span> 

``` C#
if (Microsoft.IoT.Lightning.Providers.LightningProvider.IsLightningEnabled)
{
    // Do something with the Lightning providers
}
```

### <a name="general-usage-pattern"></a><span data-ttu-id="7b02a-144">一般使用模式</span><span class="sxs-lookup"><span data-stu-id="7b02a-144">General usage pattern</span></span>

<span data-ttu-id="7b02a-145">使用提供程序的最简单方法是在应用内部将 Lightning 提供程序设置为默认提供程序。</span><span class="sxs-lookup"><span data-stu-id="7b02a-145">The simplest way to use the providers is to set the Lightning Provider as the default inside your app.</span></span> 

<span data-ttu-id="7b02a-146">如果闪电提供商可用, 以下代码将设置`Microsoft.IoT.Lightning.Providers.LightningProvider`为默认提供程序。</span><span class="sxs-lookup"><span data-stu-id="7b02a-146">The code below will, if the Lightning Provider is available, set `Microsoft.IoT.Lightning.Providers.LightningProvider` as the default provider.</span></span> <span data-ttu-id="7b02a-147">否则，在没有显式设置任何默认提供程序时，各种总线将退回到默认提供程序。</span><span class="sxs-lookup"><span data-stu-id="7b02a-147">Otherwise, when no default provider is explicitly set, the various busses will fall back to the default one.</span></span>
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

<span data-ttu-id="7b02a-148">为所需总线配备了控制器后，你可以像往常一样使用它。</span><span class="sxs-lookup"><span data-stu-id="7b02a-148">After you have a controller for the desired bus, you can use it as you normally would.</span></span> 

### <a name="using-lightning-for-individual-buses"></a><span data-ttu-id="7b02a-149">将 Lightning 用于个别总线</span><span class="sxs-lookup"><span data-stu-id="7b02a-149">Using Lightning for individual buses</span></span>

<span data-ttu-id="7b02a-150">如果你需要使用不同的默认提供程序，以下部分将介绍如何将 Lightning 提供程序用于个别总线。</span><span class="sxs-lookup"><span data-stu-id="7b02a-150">If you want to use a different default provider, the sections below show how you can use the Lightning providers for individual busses.</span></span> 

#### <a name="for-gpio-bus-controller"></a><span data-ttu-id="7b02a-151">对于 GPIO 总线控制器：</span><span class="sxs-lookup"><span data-stu-id="7b02a-151">For GPIO bus controller:</span></span>

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

#### <a name="for-i2c-bus-controller"></a><span data-ttu-id="7b02a-152">对于 I2C 总线控制器：</span><span class="sxs-lookup"><span data-stu-id="7b02a-152">For I2C bus controller:</span></span>

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

#### <a name="for-spi-bus-controller"></a><span data-ttu-id="7b02a-153">对于 SPI 总线控制器：</span><span class="sxs-lookup"><span data-stu-id="7b02a-153">For SPI bus controller:</span></span>
<span data-ttu-id="7b02a-154">使用 Microsoft.IoT.Lightning.Providers; 使用 Windows.Devices; 使用 Windows.Devices.Spi;</span><span class="sxs-lookup"><span data-stu-id="7b02a-154">using Microsoft.IoT.Lightning.Providers; using Windows.Devices; using Windows.Devices.Spi;</span></span>

``` C#
if (LightningProvider.IsLightningEnabled)
{
    SpiController controller =  (await SpiController.GetControllersAsync(LightningSpiProvider.GetSpiProvider()))[0];
    SpiDevice SpiDisplay = controller.GetDevice(spiConnectionSettings);
}
```

## <a name="lightning-provider-samples"></a><span data-ttu-id="7b02a-155">Lightning 提供程序示例</span><span class="sxs-lookup"><span data-stu-id="7b02a-155">Lightning Provider Samples</span></span>

<span data-ttu-id="7b02a-156">以下示例演示了如何使用 Lightning 提供程序以及受支持的总线类型：</span><span class="sxs-lookup"><span data-stu-id="7b02a-156">The following samples demonstrate using the Lightning providers with supported bus types:</span></span>

* <span data-ttu-id="7b02a-157">[带有 Lightning 提供程序的 Blinky (UI)](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) 演示了前台应用程序中带有 Lightning 提供程序的 GPIO</span><span class="sxs-lookup"><span data-stu-id="7b02a-157">[Blinky (UI) with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky) demonstrates GPIO with Lightning Provider in a foreground application</span></span>

* <span data-ttu-id="7b02a-158">[带有 Lightning 提供程序的 BlinkyHeadless](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) 演示了无外设应用程序中带有 Lightning 提供程序的 GPIO</span><span class="sxs-lookup"><span data-stu-id="7b02a-158">[BlinkyHeadless with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/Blinky/Background) demonstrates GPIO with Lightning Provider in a headless application</span></span>

* <span data-ttu-id="7b02a-159">[带有 Lightning 提供程序的 SPIDisplay](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) 演示了使用 API 控制使用带有 Lightning 提供程序的 SPI 的设备</span><span class="sxs-lookup"><span data-stu-id="7b02a-159">[SPIDisplay with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/SPIDisplay) demonstrates the usage of the API to control a device using SPI with Lightning Provider</span></span>
 
* <span data-ttu-id="7b02a-160">[带有 Lightning 提供程序的 WeatherStation](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) 演示了与使用带有 Lightning 提供程序的 I2C 的设备进行交互</span><span class="sxs-lookup"><span data-stu-id="7b02a-160">[WeatherStation with Lightning Provider](https://github.com/ms-iot/BusProviders/tree/develop/Microsoft.IoT.Lightning.Providers/WeatherStation) demonstrates interacting with a device using I2C with Lightning Provider</span></span>

## <a name="build-requirements"></a><span data-ttu-id="7b02a-161">生成要求</span><span class="sxs-lookup"><span data-stu-id="7b02a-161">Build Requirements</span></span>



### <a name="windows-sdk-update"></a><span data-ttu-id="7b02a-162">Windows SDK 更新</span><span class="sxs-lookup"><span data-stu-id="7b02a-162">Windows SDK Update</span></span>

<span data-ttu-id="7b02a-163">生成和使用库所需的 Windows SDK 为 10.0.10586.0 或更高版本（可以从[此处](https://dev.windows.com/en-US/downloads/windows-10-sdk)下载）。</span><span class="sxs-lookup"><span data-stu-id="7b02a-163">Windows SDK required for building and using the library is 10.0.10586.0 or higher which can be downloaded from [here](https://dev.windows.com/en-US/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="7b02a-164">有关设置所有内容的详细信息, 请参阅[入门指南。](https://developer.microsoft.com/en-us/windows/iot/getstarted)</span><span class="sxs-lookup"><span data-stu-id="7b02a-164">For more information on setting everything up, refer to [our get started guide.](https://developer.microsoft.com/en-us/windows/iot/getstarted).</span></span>

### <a name="nuget-package-dependencies"></a><span data-ttu-id="7b02a-165">Nuget 包依赖关系</span><span class="sxs-lookup"><span data-stu-id="7b02a-165">Nuget Package Dependencies</span></span>

<span data-ttu-id="7b02a-166">Lightning 提供程序库依赖于 [Microsoft.IoT.Lightning Nuget 包](https://www.nuget.org/packages/Microsoft.IoT.Lightning)，该包反过来又依赖于 [Arduino SDK Nuget 包](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino)。</span><span class="sxs-lookup"><span data-stu-id="7b02a-166">The Lightning Provider library depends on the [Microsoft.IoT.Lightning Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning), which in turn depends on the [Arduino SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.SDKFromArduino).</span></span> <span data-ttu-id="7b02a-167">这两个 Nuget 包在库项目中引用，并且可以从 Nuget.org 中获取。</span><span class="sxs-lookup"><span data-stu-id="7b02a-167">Both Nuget packages are referenced in the library projects, and are available from Nuget.org.</span></span>

<span data-ttu-id="7b02a-168">如果需要，每个包的源代码也可用于 [Lightning](https://github.com/ms-iot/lightning) 和 [Arduino SDK](https://github.com/ms-iot/arduino-sdk) 存储库中的 GitHub 上。</span><span class="sxs-lookup"><span data-stu-id="7b02a-168">If needed, source code for each is also available on GitHub at the [Lightning](https://github.com/ms-iot/lightning) and [Arduino SDK](https://github.com/ms-iot/arduino-sdk) repositories.</span></span>

<span data-ttu-id="7b02a-169">Microsoft.IoT.Lightning Nuget 目前仍是预发行版，因此当更新的版本可用时，应从 Nuget.org 进行更新。</span><span class="sxs-lookup"><span data-stu-id="7b02a-169">Currently, Microsoft.IoT.Lightning Nuget is still pre-release, so should be updated from Nuget.org, when newer versions are available.</span></span>

<span data-ttu-id="7b02a-170">为了能够安装预发行版（当前版本）的 Microsoft.IoT.Lightning Nuget 包以及接收 Lightning 程序包的预发行更新，请务必在 Nuget 包管理器中设置“包含预发行版”。</span><span class="sxs-lookup"><span data-stu-id="7b02a-170">In order to install prerelease (current) version of Microsoft.IoT.Lightning Nuget package as well as receive prerelease updates to the Lightning package, make sure to set the "Include prerelease" option in the Nuget Package Manager.</span></span>

1. <span data-ttu-id="7b02a-171">右键单击项目中的“引用”</span><span class="sxs-lookup"><span data-stu-id="7b02a-171">Right click References in your project</span></span>
1. <span data-ttu-id="7b02a-172">单击“管理 Nuget 包...”</span><span class="sxs-lookup"><span data-stu-id="7b02a-172">Click "Manage Nuget Packages..."</span></span>
1. <span data-ttu-id="7b02a-173">选择 Lightning Nuget 的程序包源</span><span class="sxs-lookup"><span data-stu-id="7b02a-173">Select package sources for Lightning nuget</span></span>
1. <span data-ttu-id="7b02a-174">单击“包含预发行版”。</span><span class="sxs-lookup"><span data-stu-id="7b02a-174">Click "Include prerelease".</span></span>
1. <span data-ttu-id="7b02a-175">单击“安装”以将 Nuget 包安装到你的项目中</span><span class="sxs-lookup"><span data-stu-id="7b02a-175">Click "Install" to install the nuget package to your project</span></span>

![程序包管理器配置](../media/LightningProviders/Nuget_PackageManager.png)

## <a name="runtime-requirements"></a><span data-ttu-id="7b02a-177">运行时要求</span><span class="sxs-lookup"><span data-stu-id="7b02a-177">Runtime Requirements</span></span>

### <a name="windows-iot-core-fall-update-required"></a><span data-ttu-id="7b02a-178">需要 Windows IoT 核心版秋季更新</span><span class="sxs-lookup"><span data-stu-id="7b02a-178">Windows IoT Core Fall Update required</span></span>
<span data-ttu-id="7b02a-179">目前仅 Windows IoT 核心版的秋季更新版本中包含 Lightning 提供程序支持。</span><span class="sxs-lookup"><span data-stu-id="7b02a-179">Lightning providers support is currently included in the Fall Update builds for Windows IoT Core.</span></span>
<span data-ttu-id="7b02a-180">你可以从我们的[下载页](https://developer.microsoft.com/windows/iot/Downloads)下载 Windows 10 IoT 核心版映像。</span><span class="sxs-lookup"><span data-stu-id="7b02a-180">You can download a Windows 10 IoT Core image from our [downloads page](https://developer.microsoft.com/windows/iot/Downloads).</span></span> <span data-ttu-id="7b02a-181">单击你的设备类型的“下载 Insider Preview”。</span><span class="sxs-lookup"><span data-stu-id="7b02a-181">Click on "Download Insider Preview" for your device type.</span></span>

### <a name="direct-memory-mapped-driver-must-be-enabled"></a><span data-ttu-id="7b02a-182">必须启用直接内存映射的驱动程序</span><span class="sxs-lookup"><span data-stu-id="7b02a-182">Direct Memory Mapped driver must be enabled</span></span>
 
<span data-ttu-id="7b02a-183">Lightning 提供程序库中的 API 需要在目标设备上启用 Lightning 直接内存映射的驱动程序。</span><span class="sxs-lookup"><span data-stu-id="7b02a-183">The APIs in the Lightning Provider library require the Lightning Direct Memory Mapped driver to be enabled on the target device.</span></span> <span data-ttu-id="7b02a-184">Raspberry Pi 2/3 和 MinnowBoard Max 都有可用的驱动程序, 但默认情况下未启用。</span><span class="sxs-lookup"><span data-stu-id="7b02a-184">Both Raspberry Pi 2/3 and MinnowBoard Max have the driver available, but not enabled by default.</span></span>

<span data-ttu-id="7b02a-185">可以使用 Windows Devices Web Portal 启用驱动程序。</span><span class="sxs-lookup"><span data-stu-id="7b02a-185">The driver can be enabled using the Windows Devices Web Portal.</span></span> <span data-ttu-id="7b02a-186">有关如何启用 Lightning 驱动程序的详细信息，请参阅 [Lightning 设置指南](LightningSetup.md)。</span><span class="sxs-lookup"><span data-stu-id="7b02a-186">Refer to the [Lightning Setup Guide](LightningSetup.md) for detailed information on how to enable the Lightning driver.</span></span>

![设备页面](../media/LightningProviders/dmap4.png)

<span data-ttu-id="7b02a-188">还可以通过 DmapUtil 命令启用该驱动程序:</span><span class="sxs-lookup"><span data-stu-id="7b02a-188">The driver can also be enabled with the DmapUtil command:</span></span>

<span data-ttu-id="7b02a-189">DmapUtil:用于打开或关闭 DMAP 直接内存映射器驱动程序的实用工具: dmaputil 状态 | 启用 | 禁用状态 [-v] 打印输出当前是否已启用 DMAP。</span><span class="sxs-lookup"><span data-stu-id="7b02a-189">DmapUtil: Utility to turn the DMAP direct memory mapper driver on or off Usage: dmaputil.exe status|enable|disable status [-v]   Print out whether dmap is currently enabled.</span></span> <span data-ttu-id="7b02a-190">传递-v 标志以获取详细的配置信息。</span><span class="sxs-lookup"><span data-stu-id="7b02a-190">Pass the -v flag for detailed configuration information.</span></span>
<span data-ttu-id="7b02a-191">启用 "在下一次启动时启用 dmap"。</span><span class="sxs-lookup"><span data-stu-id="7b02a-191">enable        Enable dmap on next boot.</span></span>
<span data-ttu-id="7b02a-192">禁用 "在下一次启动时禁用 dmap"。</span><span class="sxs-lookup"><span data-stu-id="7b02a-192">disable       Disable dmap on next boot.</span></span>
