---
title: 总线提供程序
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解通过以下方法提供的不同Windows 10 IoT 核心版。
keywords: windows iot， 提供程序， 总线提供程序， UWP， Gpio， Spi
ms.openlocfilehash: 637fee11da2b91647d01c627491d3088a2816767
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229063"
---
# <a name="usermode-access-to-gpio-i2c-and-spi"></a><span data-ttu-id="19a9f-104">用户对 GPIO、I2C 和 SPI 的访问权限</span><span class="sxs-lookup"><span data-stu-id="19a9f-104">Usermode access to GPIO, I2C, and SPI</span></span>

<span data-ttu-id="19a9f-105">Windows 10 包含的新 API 可用于直接通过用户模式访问 GPIO、I2C、SPI 和 UART。</span><span class="sxs-lookup"><span data-stu-id="19a9f-105">Windows 10 contains new APIs for accessing GPIO, I2C, SPI, and UART directly from usermode.</span></span> <span data-ttu-id="19a9f-106">开发板（如 Raspberry Pi 2）将公开这些连接的子集，这些连接支持用户使用自定义电路扩展基本计算模块来处理特定应用程序。</span><span class="sxs-lookup"><span data-stu-id="19a9f-106">Development boards like Raspberry Pi 2 expose a subset of these connections which enable users to extend a base compute module with custom circuitry to address a particular application.</span></span> <span data-ttu-id="19a9f-107">这些低级别总线通常与其他关键载入功能共享，仅一部分 GPIO 引脚和总线在标头上公开。</span><span class="sxs-lookup"><span data-stu-id="19a9f-107">These low-level buses are usually shared with other critical onboard functions, with only a subset of GPIO pins and buses exposed on headers.</span></span> <span data-ttu-id="19a9f-108">若要保持系统稳定性，必须通过用户模式应用程序指定可供安全修改的引脚和总线。</span><span class="sxs-lookup"><span data-stu-id="19a9f-108">To preserve system stability, it is necessary to specify which pins and buses are safe for modification by usermode applications.</span></span>

<span data-ttu-id="19a9f-109">用户通过现有 和 框架Windows上对低级别总线 `GpioClx` `SpbCx` 的访问。</span><span class="sxs-lookup"><span data-stu-id="19a9f-109">Usermode access to low-level buses on Windows is plumbed through the existing `GpioClx` and `SpbCx` frameworks.</span></span> <span data-ttu-id="19a9f-110">名为 RhProxy 的新驱动程序（Windows IoT Core 和 Windows Enterprise）向 `GpioClx` `SpbCx` usermode 公开和资源。</span><span class="sxs-lookup"><span data-stu-id="19a9f-110">A new driver called RhProxy, available on Windows IoT Core and Windows Enterprise, exposes `GpioClx` and `SpbCx` resources to usermode.</span></span> <span data-ttu-id="19a9f-111">若要启用这些 API，必须在 ACPI 表（内含应向用户模式公开的每个 GPIO 和 SPB 资源）中声明用于 RhProxy 的设备节点。</span><span class="sxs-lookup"><span data-stu-id="19a9f-111">To enable the APIs, a device node for rhproxy must be declared in your ACPI tables with each of the GPIO and SPB resources that should be exposed to usermode.</span></span>

<span data-ttu-id="19a9f-112">有关通过 RhProxy 访问 UserMode 的其他深入文档，可在此处 [找到](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access)。</span><span class="sxs-lookup"><span data-stu-id="19a9f-112">Additional in-depth documentation on UserMode access via RhProxy can be found [here](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access).</span></span>

## <a name="bus-providers"></a><span data-ttu-id="19a9f-113">总线提供程序</span><span class="sxs-lookup"><span data-stu-id="19a9f-113">Bus Providers</span></span>

<span data-ttu-id="19a9f-114">从 Windows 10 开始，Windows已具有提供对位于 soc 上的 Gpio、Spi 或 I2c 总线的直接访问的开箱式 UWP API。这样，通过高级 API 可以轻松访问此硬件。</span><span class="sxs-lookup"><span data-stu-id="19a9f-114">Starting with Windows 10, Windows has had in-box UWP APIs that provide direct access to Gpio, Spi, or I2c busses located on-soc. This gives very easy access to this hardware from a high-level API.</span></span> <span data-ttu-id="19a9f-115">但是，许多时候，设备制造商想要使用 soc 控制器来访问总线。</span><span class="sxs-lookup"><span data-stu-id="19a9f-115">However, there are many times when a device maker wants to use an off-soc controller to access a bus.</span></span> <span data-ttu-id="19a9f-116">它可以像添加 16 个 GPIO 引脚的便宜芯片一样简单，也可以像 Arduino () 一样丰富（如 Arduino) 不仅添加 Gpio、SPI 和 I2C 引脚，还支持 PWM 和 ADC）。</span><span class="sxs-lookup"><span data-stu-id="19a9f-116">It can be as simple as a cheap chip that adds 16 GPIO pins, or as rich as a full MCU (like an Arduino) that not only adds Gpio, SPI, and I2C pins, but also supports PWM and ADC.</span></span> <span data-ttu-id="19a9f-117">借助"总线提供程序"模型，我们使开发人员能够使用可弥补差距的用户模式提供程序，使用箱内 API 访问这些非总线总线。</span><span class="sxs-lookup"><span data-stu-id="19a9f-117">With the "Bus Provider" model, we give developers the ability to access these off-soc busses using the in-box APIs, using a user-mode provider that bridges the gap.</span></span>

<span data-ttu-id="19a9f-118">构建提供程序的人将一组接口实现到 UWP 类库中，然后任何想要与硬件对话的开发人员只需包含组件，并告知其 API。</span><span class="sxs-lookup"><span data-stu-id="19a9f-118">Someone building a provider implements a set of interfaces into a UWP class library and then any developer who wants to talk to that hardware simply includes the component and tells the in-box APIs about it.</span></span> <span data-ttu-id="19a9f-119">如果查看远程 [Arduino](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) 提供程序中的示例代码，可以看到配置提供程序是多么容易，并且一旦设置为该应用的默认提供程序，客户端应用中的其余代码与访问 on-soc 总线所需的代码相同。</span><span class="sxs-lookup"><span data-stu-id="19a9f-119">If you look at the sample code from the [Remote Arduino provider](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) you can see how easy it is to configure the provider and, once set as the default provider for that app, the rest of the code in the client app is identical to the code required to access an on-soc bus.</span></span>


```
ArduinoProviders.ArduinoProvider.Configuration =
    new ArduinoProviders.ArduinoConnectionConfiguration("VID_2341", "PID_0043", 57600);
Windows.Devices.LowLevelDevicesController.DefaultProvider =  new ArduinoProviders.ArduinoProvider();

gpioController = await GpioController.GetDefaultAsync();
i2cController = await I2cController.GetDefaultAsync();
adcController = await AdcController.GetDefaultAsync();
pwmController = await PwmController.GetDefaultAsync();

GpioPin pin = gpioController.OpenPin(LED_PIN, GpioSharingMode.Exclusive);`
```

## <a name="available-providers"></a><span data-ttu-id="19a9f-120">可用提供程序</span><span class="sxs-lookup"><span data-stu-id="19a9f-120">Available Providers</span></span>

<span data-ttu-id="19a9f-121">目前，我们在总线提供程序 github 存储库中 [提供了许多](https://github.com/ms-iot/BusProviders) 提供程序。</span><span class="sxs-lookup"><span data-stu-id="19a9f-121">We currently have a number of providers available on the [Bus Providers](https://github.com/ms-iot/BusProviders) github repo.</span></span> <span data-ttu-id="19a9f-122">除了提供程序的代码之外，每个提供程序还有一个示例 VS 解决方案，用于演示客户端如何使用该提供程序。</span><span class="sxs-lookup"><span data-stu-id="19a9f-122">In addition to the code for the provider, each provider has a sample VS solution that demonstrates how a client would use that provider.</span></span>

- <span data-ttu-id="19a9f-123">**ADC**</span><span class="sxs-lookup"><span data-stu-id="19a9f-123">**ADC**</span></span>
  - <span data-ttu-id="19a9f-124">Ads1x15</span><span class="sxs-lookup"><span data-stu-id="19a9f-124">Ads1x15</span></span>
  - <span data-ttu-id="19a9f-125">Mcp3008</span><span class="sxs-lookup"><span data-stu-id="19a9f-125">Mcp3008</span></span>
  - <span data-ttu-id="19a9f-126">远程 Arduino</span><span class="sxs-lookup"><span data-stu-id="19a9f-126">Remote Arduino</span></span>

- <span data-ttu-id="19a9f-127">**PWM**</span><span class="sxs-lookup"><span data-stu-id="19a9f-127">**PWM**</span></span>
  - <span data-ttu-id="19a9f-128">PCA9685</span><span class="sxs-lookup"><span data-stu-id="19a9f-128">PCA9685</span></span>
  - <span data-ttu-id="19a9f-129">使用 Gpio 模拟</span><span class="sxs-lookup"><span data-stu-id="19a9f-129">Simulated with Gpio</span></span>
  - <span data-ttu-id="19a9f-130">远程 Arduino</span><span class="sxs-lookup"><span data-stu-id="19a9f-130">Remote Arduino</span></span>

- <span data-ttu-id="19a9f-131">**Gpio、SPI、I2C**</span><span class="sxs-lookup"><span data-stu-id="19a9f-131">**Gpio, SPI, I2C**</span></span>
  - <span data-ttu-id="19a9f-132">远程 Arduino</span><span class="sxs-lookup"><span data-stu-id="19a9f-132">Remote Arduino</span></span>

<span data-ttu-id="19a9f-133">除了提供对真实硬件的访问权限的提供商之外，我们还构建了模拟提供程序，该[](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider)提供程序将充当无限功能提供程序，旨在让你编写和调试应用程序，而无需先将它们部署到工作设备。</span><span class="sxs-lookup"><span data-stu-id="19a9f-133">In addition to the providers that give you access to real hardware, we have built a [Simulated Provider](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) that will act as if it was an infinitely capable provider and is designed to let you write and debug your applications without having to first deploy them to a working device.</span></span> <span data-ttu-id="19a9f-134">若要获得更丰富的体验，可以对其进行自定义以模拟实际硬件。</span><span class="sxs-lookup"><span data-stu-id="19a9f-134">For a richer experience, you can customize it to simulate your actual hardware.</span></span> <span data-ttu-id="19a9f-135">例如：更新 I2c 提供程序，以在向 I2c 提供程序发送温度读数命令时返回结果"75"，以在具有指定辅助地址的设备上读取温度。</span><span class="sxs-lookup"><span data-stu-id="19a9f-135">For example: updating the I2c provider to return back the result "75" when you send it the command for a temperature reading on a device with the designated secondary address.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="19a9f-136">其他资源</span><span class="sxs-lookup"><span data-stu-id="19a9f-136">Additional Resources</span></span>

<span data-ttu-id="19a9f-137">有关 I2C、SPI、GPIO、MinComm/UART 的其他总线工具、示例代码以及生成和测试，可在此处 [找到](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools)。</span><span class="sxs-lookup"><span data-stu-id="19a9f-137">Additional bus tools, sample codes, and building and testing on I2C, SPI, GPIO, MinComm/UART can be found [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools).</span></span>

<span data-ttu-id="19a9f-138">请参阅[Windows Runtime (WinRT) API，](https://docs.microsoft.com/uwp/api)下面将了解如何利用[Win32 应用程序中的 API。](https://blogs.windows.com/windowsdeveloper/2017/01/25/calling-windows-10-apis-desktop-application/)</span><span class="sxs-lookup"><span data-stu-id="19a9f-138">Please reference [Windows Runtime (WinRT) APIs](https://docs.microsoft.com/uwp/api) and here's how to leverage the APIs from [Win32 applications](https://blogs.windows.com/windowsdeveloper/2017/01/25/calling-windows-10-apis-desktop-application/).</span></span>   
