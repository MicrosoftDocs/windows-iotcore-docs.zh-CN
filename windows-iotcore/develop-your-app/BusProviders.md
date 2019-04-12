---
title: 总线提供程序
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 了解有关不同的提供程序可通过 Windows 10 IoT 核心版的信息。
keywords: windows iot、 提供程序、 UWP、 Gpio、 Spi 总线提供程序
ms.openlocfilehash: 63e62e649aa6f54576e47419fe0be86ae5e5f096
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510833"
---
# <a name="bus-providers"></a><span data-ttu-id="cf2bf-104">总线提供程序</span><span class="sxs-lookup"><span data-stu-id="cf2bf-104">Bus Providers</span></span>

<span data-ttu-id="cf2bf-105">从 Windows 10 开始，Windows 已提供相应的框中 UWP Api 提供对 Gpio，Spi，直接访问或 I2c 总线位于 soc.上这使能够非常轻松地访问这个硬件从高级别 API。</span><span class="sxs-lookup"><span data-stu-id="cf2bf-105">Starting with Windows 10, Windows has had in-box UWP APIs that provide direct access to Gpio, Spi, or I2c busses located on-soc. This gives very easy access to this hardware from a high level API.</span></span> <span data-ttu-id="cf2bf-106">但是，有很多时候时设备制造者想要使用 soc 关闭控制器将访问总线。</span><span class="sxs-lookup"><span data-stu-id="cf2bf-106">However, there are many times when a device maker wants to use an off-soc controller to access a bus.</span></span> <span data-ttu-id="cf2bf-107">它可以是简单的成本低廉的芯片，添加 16 GPIO 插针或丰富的完整 MCU （如 Arduino) 不仅添加 Gpio、 SPI 和 I2C pin，但还支持 PWM 和 ADC。</span><span class="sxs-lookup"><span data-stu-id="cf2bf-107">It can be as simple as a cheap chip that adds 16 GPIO pins, or as rich as a full MCU (like an Arduino) that not only adds Gpio, SPI, and I2C pins, but also supports PWM and ADC.</span></span> <span data-ttu-id="cf2bf-108">通过"总线提供程序"模型中，我们使开发人员能够访问这些关闭 soc 总线，使用该桥的内置 Api，使用用户模式提供程序无缝连接。</span><span class="sxs-lookup"><span data-stu-id="cf2bf-108">With the "Bus Provider" model, we give developers the ability to access these off-soc busses using the in-box APIs, using a user-mode provider that bridges the gap.</span></span> 

<span data-ttu-id="cf2bf-109">有人生成提供程序到 UWP 类库，然后任何开发人员想要与硬件只需包括的组件，并介绍内置 Api 实现一组接口。</span><span class="sxs-lookup"><span data-stu-id="cf2bf-109">Someone building a provider implements a set of interfaces into a UWP class library and then any developer who wants to talk to that hardware simply includes the component and tells the in-box APIs about it.</span></span> <span data-ttu-id="cf2bf-110">如果您看一下从示例代码[远程 Arduino 提供程序](https://github.com/ms-iot/BusProviders/tree/develop/Arduino)可以看到配置提供程序是多么容易，以及一次将设置为该应用的默认提供程序，客户端应用中的代码的其余部分是否与所需的代码访问在 soc 总线。</span><span class="sxs-lookup"><span data-stu-id="cf2bf-110">If you look at the sample code from the [Remote Arduino provider](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) you can see how easy it is to configure the provider and, once set as the default provider for that app, the rest of the code in the client app is identical to the code required to access an on-soc bus.</span></span>  

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

## <a name="available-providers"></a><span data-ttu-id="cf2bf-111">可用的提供程序</span><span class="sxs-lookup"><span data-stu-id="cf2bf-111">Available Providers</span></span>

<span data-ttu-id="cf2bf-112">目前有大量的提供商上可用[总线提供程序](https://github.com/ms-iot/BusProviders)github 存储库。</span><span class="sxs-lookup"><span data-stu-id="cf2bf-112">We currently have a number of providers available on the [Bus Providers](https://github.com/ms-iot/BusProviders) github repo.</span></span> <span data-ttu-id="cf2bf-113">除了提供程序的代码，每个提供程序还具有一个演示如何在客户端将使用该提供程序的示例 VS 解决方案。</span><span class="sxs-lookup"><span data-stu-id="cf2bf-113">In addition to the code for the provider, each provider has a sample VS solution that demonstrates how a client would use that provider.</span></span> 

* <span data-ttu-id="cf2bf-114">ADC \*\* Ads1x15 \*\* Mcp3008 \*\* Remote Arduino</span><span class="sxs-lookup"><span data-stu-id="cf2bf-114">ADC \*\* Ads1x15 \*\* Mcp3008 \*\* Remote Arduino</span></span>
* <span data-ttu-id="cf2bf-115">PWM \* \* PCA9685 \* \* 使用 Gpio 模拟 \* \* 远程 Arduino</span><span class="sxs-lookup"><span data-stu-id="cf2bf-115">PWM \*\* PCA9685 \*\* Simulated with Gpio \*\* Remote Arduino</span></span>
* <span data-ttu-id="cf2bf-116">Gpio, SPI, I2c \*\* Remote Arduino</span><span class="sxs-lookup"><span data-stu-id="cf2bf-116">Gpio, SPI, I2c \*\* Remote Arduino</span></span>

<span data-ttu-id="cf2bf-117">除了向你的真实硬件的提供程序，我们已构建[模拟的提供程序](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider)，将其行为就好像它是 inifitely 支持提供商，并旨在让您编写和调试你的应用程序且不会首先将其部署到的工作设备。</span><span class="sxs-lookup"><span data-stu-id="cf2bf-117">In addition to the providers that give you access to real hardware, we have built a [Simulated Provider](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) that will act as if it was an inifitely capable provider and is designed to let you write and debug your applications without having to first deploy them to a working device.</span></span> <span data-ttu-id="cf2bf-118">对于更丰富的体验，你可以自定义它来模拟实际硬件。</span><span class="sxs-lookup"><span data-stu-id="cf2bf-118">For a richer experience, you can customize it to simulate your actual hardware.</span></span> <span data-ttu-id="cf2bf-119">例如： 当您将其发送的温度读数具有指定的从属节点地址的设备上的命令时，更新 I2c 提供程序返回返回结果"75"。</span><span class="sxs-lookup"><span data-stu-id="cf2bf-119">For example: updating the I2c provider to return back the result "75" when you send it the command for a temperature reading on a device with the designated slave address.</span></span> 
