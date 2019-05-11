---
title: 总线提供程序
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 了解有关不同的提供程序可通过 Windows 10 IoT 核心版的信息。
keywords: windows iot、 提供程序、 UWP、 Gpio、 Spi 总线提供程序
ms.openlocfilehash: 7e2a3bf45317cd11ca558db6f1b6845e0e0f7a67
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533283"
---
# <a name="usermode-access-to-gpio-i2c-and-spi"></a><span data-ttu-id="98322-104">用户模式访问 GPIO、 I2C 和 SPI</span><span class="sxs-lookup"><span data-stu-id="98322-104">Usermode access to GPIO, I2C and SPI</span></span>

<span data-ttu-id="98322-105">Windows 10 包含的新 API 可用于直接通过用户模式访问 GPIO、I2C、SPI 和 UART。</span><span class="sxs-lookup"><span data-stu-id="98322-105">Windows 10 contains new APIs for accessing GPIO, I2C, SPI, and UART directly from usermode.</span></span> <span data-ttu-id="98322-106">开发板（如 Raspberry Pi 2）将公开这些连接的子集，这些连接支持用户使用自定义电路扩展基本计算模块来处理特定应用程序。</span><span class="sxs-lookup"><span data-stu-id="98322-106">Development boards like Raspberry Pi 2 expose a subset of these connections which enable users to extend a base compute module with custom circuitry to address a particular application.</span></span> <span data-ttu-id="98322-107">通常，只需使用 GPIO 引脚的一个子集和标头上公开的总线，即可与其他关键板载功能共享这些低级别总线。</span><span class="sxs-lookup"><span data-stu-id="98322-107">These low level buses are usually shared with other critical onboard functions, with only a subset of GPIO pins and buses exposed on headers.</span></span> <span data-ttu-id="98322-108">若要保持系统稳定性，必须通过用户模式应用程序指定可供安全修改的引脚和总线。</span><span class="sxs-lookup"><span data-stu-id="98322-108">To preserve system stability, it is necessary to specify which pins and buses are safe for modification by usermode applications.</span></span>

<span data-ttu-id="98322-109">Windows 上低级别总线的用户模式访问通过现有 `GpioClx` 和 `SpbCx` 框架实现。</span><span class="sxs-lookup"><span data-stu-id="98322-109">Usermode access to low level buses on Windows is plumbed through the existing `GpioClx` and `SpbCx` frameworks.</span></span> <span data-ttu-id="98322-110">新的驱动程序调用 RhProxy，可在 Windows IoT Core 和 Windows 企业版上公开`GpioClx`和`SpbCx`的资源添加到用户模式。</span><span class="sxs-lookup"><span data-stu-id="98322-110">A new driver called RhProxy, available on Windows IoT Core and Windows Enterprise, exposes `GpioClx` and `SpbCx` resources to usermode.</span></span> <span data-ttu-id="98322-111">若要启用这些 API，必须在 ACPI 表（内含应向用户模式公开的每个 GPIO 和 SPB 资源）中声明用于 RhProxy 的设备节点。</span><span class="sxs-lookup"><span data-stu-id="98322-111">To enable the APIs, a device node for rhproxy must be declared in your ACPI tables with each of the GPIO and SPB resources that should be exposed to usermode.</span></span>

<span data-ttu-id="98322-112">可找到有关通过 RhProxy 用户模式访问的其他深入文档[此处](https://docs.microsoft.com/en-us/windows/uwp/devices-sensors/enable-usermode-access)。</span><span class="sxs-lookup"><span data-stu-id="98322-112">Additional in-depth documentation on UserMode access via RhProxy can be found [here](https://docs.microsoft.com/en-us/windows/uwp/devices-sensors/enable-usermode-access).</span></span>

## <a name="bus-providers"></a><span data-ttu-id="98322-113">总线提供程序</span><span class="sxs-lookup"><span data-stu-id="98322-113">Bus Providers</span></span>

<span data-ttu-id="98322-114">从 Windows 10 开始，Windows 已提供相应的框中 UWP Api 提供对 Gpio，Spi，直接访问或 I2c 总线位于 soc.上这使能够非常轻松地访问这个硬件从高级别 API。</span><span class="sxs-lookup"><span data-stu-id="98322-114">Starting with Windows 10, Windows has had in-box UWP APIs that provide direct access to Gpio, Spi, or I2c busses located on-soc. This gives very easy access to this hardware from a high level API.</span></span> <span data-ttu-id="98322-115">但是，有很多时候时设备制造者想要使用 soc 关闭控制器将访问总线。</span><span class="sxs-lookup"><span data-stu-id="98322-115">However, there are many times when a device maker wants to use an off-soc controller to access a bus.</span></span> <span data-ttu-id="98322-116">它可以是简单的成本低廉的芯片，添加 16 GPIO 插针或丰富的完整 MCU （如 Arduino) 不仅添加 Gpio、 SPI 和 I2C pin，但还支持 PWM 和 ADC。</span><span class="sxs-lookup"><span data-stu-id="98322-116">It can be as simple as a cheap chip that adds 16 GPIO pins, or as rich as a full MCU (like an Arduino) that not only adds Gpio, SPI, and I2C pins, but also supports PWM and ADC.</span></span> <span data-ttu-id="98322-117">通过"总线提供程序"模型中，我们使开发人员能够访问这些关闭 soc 总线，使用该桥的内置 Api，使用用户模式提供程序无缝连接。</span><span class="sxs-lookup"><span data-stu-id="98322-117">With the "Bus Provider" model, we give developers the ability to access these off-soc busses using the in-box APIs, using a user-mode provider that bridges the gap.</span></span>

<span data-ttu-id="98322-118">有人生成提供程序到 UWP 类库，然后任何开发人员想要与硬件只需包括的组件，并介绍内置 Api 实现一组接口。</span><span class="sxs-lookup"><span data-stu-id="98322-118">Someone building a provider implements a set of interfaces into a UWP class library and then any developer who wants to talk to that hardware simply includes the component and tells the in-box APIs about it.</span></span> <span data-ttu-id="98322-119">如果您看一下从示例代码[远程 Arduino 提供程序](https://github.com/ms-iot/BusProviders/tree/develop/Arduino)可以看到配置提供程序是多么容易，以及一次将设置为该应用的默认提供程序，客户端应用中的代码的其余部分是否与所需的代码访问在 soc 总线。</span><span class="sxs-lookup"><span data-stu-id="98322-119">If you look at the sample code from the [Remote Arduino provider](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) you can see how easy it is to configure the provider and, once set as the default provider for that app, the rest of the code in the client app is identical to the code required to access an on-soc bus.</span></span>


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

## <a name="available-providers"></a><span data-ttu-id="98322-120">可用的提供程序</span><span class="sxs-lookup"><span data-stu-id="98322-120">Available Providers</span></span>

<span data-ttu-id="98322-121">目前有大量的提供商上可用[总线提供程序](https://github.com/ms-iot/BusProviders)github 存储库。</span><span class="sxs-lookup"><span data-stu-id="98322-121">We currently have a number of providers available on the [Bus Providers](https://github.com/ms-iot/BusProviders) github repo.</span></span> <span data-ttu-id="98322-122">除了提供程序的代码，每个提供程序还具有一个演示如何在客户端将使用该提供程序的示例 VS 解决方案。</span><span class="sxs-lookup"><span data-stu-id="98322-122">In addition to the code for the provider, each provider has a sample VS solution that demonstrates how a client would use that provider.</span></span> 

- <span data-ttu-id="98322-123">**ADC**</span><span class="sxs-lookup"><span data-stu-id="98322-123">**ADC**</span></span>
  - <span data-ttu-id="98322-124">Ads1x15</span><span class="sxs-lookup"><span data-stu-id="98322-124">Ads1x15</span></span>
  - <span data-ttu-id="98322-125">Mcp3008</span><span class="sxs-lookup"><span data-stu-id="98322-125">Mcp3008</span></span>
  - <span data-ttu-id="98322-126">远程 Arduino</span><span class="sxs-lookup"><span data-stu-id="98322-126">Remote Arduino</span></span>

- <span data-ttu-id="98322-127">**PWM**</span><span class="sxs-lookup"><span data-stu-id="98322-127">**PWM**</span></span>
  - <span data-ttu-id="98322-128">PCA9685</span><span class="sxs-lookup"><span data-stu-id="98322-128">PCA9685</span></span>
  - <span data-ttu-id="98322-129">模拟与 Gpio</span><span class="sxs-lookup"><span data-stu-id="98322-129">Simulated with Gpio</span></span>
  - <span data-ttu-id="98322-130">远程 Arduino</span><span class="sxs-lookup"><span data-stu-id="98322-130">Remote Arduino</span></span>
  
- <span data-ttu-id="98322-131">**Gpio, SPI, I2C**</span><span class="sxs-lookup"><span data-stu-id="98322-131">**Gpio, SPI, I2C**</span></span>
  - <span data-ttu-id="98322-132">远程 Arduino</span><span class="sxs-lookup"><span data-stu-id="98322-132">Remote Arduino</span></span>

<span data-ttu-id="98322-133">除了向你的真实硬件的提供程序，我们已构建[模拟的提供程序](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider)，将其行为就好像它是 inifitely 支持提供商，并旨在让您编写和调试你的应用程序且不会首先将其部署到的工作设备。</span><span class="sxs-lookup"><span data-stu-id="98322-133">In addition to the providers that give you access to real hardware, we have built a [Simulated Provider](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) that will act as if it was an inifitely capable provider and is designed to let you write and debug your applications without having to first deploy them to a working device.</span></span> <span data-ttu-id="98322-134">对于更丰富的体验，你可以自定义它来模拟实际硬件。</span><span class="sxs-lookup"><span data-stu-id="98322-134">For a richer experience, you can customize it to simulate your actual hardware.</span></span> <span data-ttu-id="98322-135">例如： 当您将其发送的温度读数具有指定的从属节点地址的设备上的命令时，更新 I2c 提供程序返回返回结果"75"。</span><span class="sxs-lookup"><span data-stu-id="98322-135">For example: updating the I2c provider to return back the result "75" when you send it the command for a temperature reading on a device with the designated slave address.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="98322-136">其他资源</span><span class="sxs-lookup"><span data-stu-id="98322-136">Additional Resources</span></span>

<span data-ttu-id="98322-137">其他总线工具、 示例代码，以及构建和 I2C，SPI，GPIO 上测试，可以找到 MinComm/UART[此处](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools)。</span><span class="sxs-lookup"><span data-stu-id="98322-137">Additional bus tools, sample codes, and building and testing on I2C, SPI, GPIO, MinComm/UART can be found [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools).</span></span>

