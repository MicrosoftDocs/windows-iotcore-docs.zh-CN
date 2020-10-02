---
title: 总线提供程序
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解通过 Windows 10 IoT Core 提供的不同提供商。
keywords: windows iot，提供程序，总线提供程序，UWP，Gpio，Spi
ms.openlocfilehash: c7c335bb791e487b1ef7808e0a7104ba9dbb91f3
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656403"
---
# <a name="usermode-access-to-gpio-i2c-and-spi"></a><span data-ttu-id="ac327-104">Usermode 访问 GPIO、I2C 和 SPI</span><span class="sxs-lookup"><span data-stu-id="ac327-104">Usermode access to GPIO, I2C, and SPI</span></span>

<span data-ttu-id="ac327-105">Windows 10 包含的新 API 可用于直接通过用户模式访问 GPIO、I2C、SPI 和 UART。</span><span class="sxs-lookup"><span data-stu-id="ac327-105">Windows 10 contains new APIs for accessing GPIO, I2C, SPI, and UART directly from usermode.</span></span> <span data-ttu-id="ac327-106">开发板（如 Raspberry Pi 2）将公开这些连接的子集，这些连接支持用户使用自定义电路扩展基本计算模块来处理特定应用程序。</span><span class="sxs-lookup"><span data-stu-id="ac327-106">Development boards like Raspberry Pi 2 expose a subset of these connections which enable users to extend a base compute module with custom circuitry to address a particular application.</span></span> <span data-ttu-id="ac327-107">通常，这些低级别的总线与其他关键板载函数共享，仅包含在标头中公开的 GPIO pin 和总线子集。</span><span class="sxs-lookup"><span data-stu-id="ac327-107">These low-level buses are usually shared with other critical onboard functions, with only a subset of GPIO pins and buses exposed on headers.</span></span> <span data-ttu-id="ac327-108">若要保持系统稳定性，必须通过用户模式应用程序指定可供安全修改的引脚和总线。</span><span class="sxs-lookup"><span data-stu-id="ac327-108">To preserve system stability, it is necessary to specify which pins and buses are safe for modification by usermode applications.</span></span>

<span data-ttu-id="ac327-109">Usermode 在 Windows 上访问低级别总线的权限通过现有和框架进行了检测 `GpioClx` `SpbCx` 。</span><span class="sxs-lookup"><span data-stu-id="ac327-109">Usermode access to low-level buses on Windows is plumbed through the existing `GpioClx` and `SpbCx` frameworks.</span></span> <span data-ttu-id="ac327-110">Windows IoT Core 和 Windows Enterprise 上提供了名为 RhProxy 的新驱动程序， `GpioClx` 它 `SpbCx` 向 usermode 公开了资源。</span><span class="sxs-lookup"><span data-stu-id="ac327-110">A new driver called RhProxy, available on Windows IoT Core and Windows Enterprise, exposes `GpioClx` and `SpbCx` resources to usermode.</span></span> <span data-ttu-id="ac327-111">若要启用这些 API，必须在 ACPI 表（内含应向用户模式公开的每个 GPIO 和 SPB 资源）中声明用于 RhProxy 的设备节点。</span><span class="sxs-lookup"><span data-stu-id="ac327-111">To enable the APIs, a device node for rhproxy must be declared in your ACPI tables with each of the GPIO and SPB resources that should be exposed to usermode.</span></span>

<span data-ttu-id="ac327-112">可在 [此处](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access)找到有关通过 RhProxy 访问 UserMode 的其他深入文档。</span><span class="sxs-lookup"><span data-stu-id="ac327-112">Additional in-depth documentation on UserMode access via RhProxy can be found [here](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access).</span></span>

## <a name="bus-providers"></a><span data-ttu-id="ac327-113">总线提供程序</span><span class="sxs-lookup"><span data-stu-id="ac327-113">Bus Providers</span></span>

<span data-ttu-id="ac327-114">从 Windows 10 开始，Windows 提供了内置的 UWP Api，可提供对位于 soc 上的 Gpio、Spi 或 I2c 总线的直接访问。这样就可以从高级别 API 轻松访问此硬件。</span><span class="sxs-lookup"><span data-stu-id="ac327-114">Starting with Windows 10, Windows has had in-box UWP APIs that provide direct access to Gpio, Spi, or I2c busses located on-soc. This gives very easy access to this hardware from a high-level API.</span></span> <span data-ttu-id="ac327-115">但是，在许多情况下，设备制造商希望使用脱离 soc 控制器来访问总线。</span><span class="sxs-lookup"><span data-stu-id="ac327-115">However, there are many times when a device maker wants to use an off-soc controller to access a bus.</span></span> <span data-ttu-id="ac327-116">它可以像一个低价芯片一样简单，也可以像添加16个 GPIO pin 一样简单，也可以像 Arduino 一样 (丰富，如) ，不仅可以添加 Gpio、SPI 和 I2C pin，还支持 PWM 和 ADC。</span><span class="sxs-lookup"><span data-stu-id="ac327-116">It can be as simple as a cheap chip that adds 16 GPIO pins, or as rich as a full MCU (like an Arduino) that not only adds Gpio, SPI, and I2C pins, but also supports PWM and ADC.</span></span> <span data-ttu-id="ac327-117">使用 "总线提供程序" 模型，开发人员可以使用内置的 Api，使用桥梁的用户模式提供程序来访问这些脱离 soc 总线。</span><span class="sxs-lookup"><span data-stu-id="ac327-117">With the "Bus Provider" model, we give developers the ability to access these off-soc busses using the in-box APIs, using a user-mode provider that bridges the gap.</span></span>

<span data-ttu-id="ac327-118">构建提供程序的用户在 UWP 类库中实现了一组接口，然后需要与该硬件通信的任何开发人员都只包含该组件，并告诉内置 Api。</span><span class="sxs-lookup"><span data-stu-id="ac327-118">Someone building a provider implements a set of interfaces into a UWP class library and then any developer who wants to talk to that hardware simply includes the component and tells the in-box APIs about it.</span></span> <span data-ttu-id="ac327-119">如果你查看来自 [远程 Arduino 提供程序](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) 的示例代码，你可以看到配置提供程序的过程是多么简单，并且一旦设置为该应用程序的默认提供程序，客户端应用程序中的其余代码就会与访问 on soc 总线所需的代码完全相同。</span><span class="sxs-lookup"><span data-stu-id="ac327-119">If you look at the sample code from the [Remote Arduino provider](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) you can see how easy it is to configure the provider and, once set as the default provider for that app, the rest of the code in the client app is identical to the code required to access an on-soc bus.</span></span>


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

## <a name="available-providers"></a><span data-ttu-id="ac327-120">可用提供程序</span><span class="sxs-lookup"><span data-stu-id="ac327-120">Available Providers</span></span>

<span data-ttu-id="ac327-121">目前， [总线提供](https://github.com/ms-iot/BusProviders) 商 github 存储库中提供了许多提供程序。</span><span class="sxs-lookup"><span data-stu-id="ac327-121">We currently have a number of providers available on the [Bus Providers](https://github.com/ms-iot/BusProviders) github repo.</span></span> <span data-ttu-id="ac327-122">除了提供程序的代码以外，每个提供程序都有一个示例 VS 解决方案，该解决方案演示了客户端如何使用该提供程序。</span><span class="sxs-lookup"><span data-stu-id="ac327-122">In addition to the code for the provider, each provider has a sample VS solution that demonstrates how a client would use that provider.</span></span> 

- <span data-ttu-id="ac327-123">**ADC**</span><span class="sxs-lookup"><span data-stu-id="ac327-123">**ADC**</span></span>
  - <span data-ttu-id="ac327-124">Ads1x15</span><span class="sxs-lookup"><span data-stu-id="ac327-124">Ads1x15</span></span>
  - <span data-ttu-id="ac327-125">Mcp3008</span><span class="sxs-lookup"><span data-stu-id="ac327-125">Mcp3008</span></span>
  - <span data-ttu-id="ac327-126">远程 Arduino</span><span class="sxs-lookup"><span data-stu-id="ac327-126">Remote Arduino</span></span>

- <span data-ttu-id="ac327-127">**PWM**</span><span class="sxs-lookup"><span data-stu-id="ac327-127">**PWM**</span></span>
  - <span data-ttu-id="ac327-128">PCA9685</span><span class="sxs-lookup"><span data-stu-id="ac327-128">PCA9685</span></span>
  - <span data-ttu-id="ac327-129">模拟 with Gpio</span><span class="sxs-lookup"><span data-stu-id="ac327-129">Simulated with Gpio</span></span>
  - <span data-ttu-id="ac327-130">远程 Arduino</span><span class="sxs-lookup"><span data-stu-id="ac327-130">Remote Arduino</span></span>
  
- <span data-ttu-id="ac327-131">**Gpio、SPI、I2C**</span><span class="sxs-lookup"><span data-stu-id="ac327-131">**Gpio, SPI, I2C**</span></span>
  - <span data-ttu-id="ac327-132">远程 Arduino</span><span class="sxs-lookup"><span data-stu-id="ac327-132">Remote Arduino</span></span>

<span data-ttu-id="ac327-133">除了提供对实际硬件的访问权的提供程序外，我们还构建了 [模拟的提供程序，该提供程序](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) 将充当一种不受支持的提供程序，旨在使你能够编写和调试应用程序，而无需首先将它们部署到工作设备。</span><span class="sxs-lookup"><span data-stu-id="ac327-133">In addition to the providers that give you access to real hardware, we have built a [Simulated Provider](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) that will act as if it was an infinitely capable provider and is designed to let you write and debug your applications without having to first deploy them to a working device.</span></span> <span data-ttu-id="ac327-134">为了获得更丰富的体验，你可以对其进行自定义以模拟你的实际硬件。</span><span class="sxs-lookup"><span data-stu-id="ac327-134">For a richer experience, you can customize it to simulate your actual hardware.</span></span> <span data-ttu-id="ac327-135">例如：在向其发送指定辅助地址的设备上，更新 I2c 提供程序以返回结果 "75"。</span><span class="sxs-lookup"><span data-stu-id="ac327-135">For example: updating the I2c provider to return back the result "75" when you send it the command for a temperature reading on a device with the designated secondary address.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ac327-136">其他资源</span><span class="sxs-lookup"><span data-stu-id="ac327-136">Additional Resources</span></span>

<span data-ttu-id="ac327-137">可在 [此处](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools)找到 I2C、SPI、GPIO、MINCOMM/UART 的其他总线工具、示例代码和生成和测试。</span><span class="sxs-lookup"><span data-stu-id="ac327-137">Additional bus tools, sample codes, and building and testing on I2C, SPI, GPIO, MinComm/UART can be found [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools).</span></span>

