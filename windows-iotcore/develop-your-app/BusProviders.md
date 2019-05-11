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
# <a name="usermode-access-to-gpio-i2c-and-spi"></a>用户模式访问 GPIO、 I2C 和 SPI

Windows 10 包含的新 API 可用于直接通过用户模式访问 GPIO、I2C、SPI 和 UART。 开发板（如 Raspberry Pi 2）将公开这些连接的子集，这些连接支持用户使用自定义电路扩展基本计算模块来处理特定应用程序。 通常，只需使用 GPIO 引脚的一个子集和标头上公开的总线，即可与其他关键板载功能共享这些低级别总线。 若要保持系统稳定性，必须通过用户模式应用程序指定可供安全修改的引脚和总线。

Windows 上低级别总线的用户模式访问通过现有 `GpioClx` 和 `SpbCx` 框架实现。 新的驱动程序调用 RhProxy，可在 Windows IoT Core 和 Windows 企业版上公开`GpioClx`和`SpbCx`的资源添加到用户模式。 若要启用这些 API，必须在 ACPI 表（内含应向用户模式公开的每个 GPIO 和 SPB 资源）中声明用于 RhProxy 的设备节点。

可找到有关通过 RhProxy 用户模式访问的其他深入文档[此处](https://docs.microsoft.com/en-us/windows/uwp/devices-sensors/enable-usermode-access)。

## <a name="bus-providers"></a>总线提供程序

从 Windows 10 开始，Windows 已提供相应的框中 UWP Api 提供对 Gpio，Spi，直接访问或 I2c 总线位于 soc.上这使能够非常轻松地访问这个硬件从高级别 API。 但是，有很多时候时设备制造者想要使用 soc 关闭控制器将访问总线。 它可以是简单的成本低廉的芯片，添加 16 GPIO 插针或丰富的完整 MCU （如 Arduino) 不仅添加 Gpio、 SPI 和 I2C pin，但还支持 PWM 和 ADC。 通过"总线提供程序"模型中，我们使开发人员能够访问这些关闭 soc 总线，使用该桥的内置 Api，使用用户模式提供程序无缝连接。

有人生成提供程序到 UWP 类库，然后任何开发人员想要与硬件只需包括的组件，并介绍内置 Api 实现一组接口。 如果您看一下从示例代码[远程 Arduino 提供程序](https://github.com/ms-iot/BusProviders/tree/develop/Arduino)可以看到配置提供程序是多么容易，以及一次将设置为该应用的默认提供程序，客户端应用中的代码的其余部分是否与所需的代码访问在 soc 总线。


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

## <a name="available-providers"></a>可用的提供程序

目前有大量的提供商上可用[总线提供程序](https://github.com/ms-iot/BusProviders)github 存储库。 除了提供程序的代码，每个提供程序还具有一个演示如何在客户端将使用该提供程序的示例 VS 解决方案。 

- **ADC**
  - Ads1x15
  - Mcp3008
  - 远程 Arduino

- **PWM**
  - PCA9685
  - 模拟与 Gpio
  - 远程 Arduino
  
- **Gpio, SPI, I2C**
  - 远程 Arduino

除了向你的真实硬件的提供程序，我们已构建[模拟的提供程序](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider)，将其行为就好像它是 inifitely 支持提供商，并旨在让您编写和调试你的应用程序且不会首先将其部署到的工作设备。 对于更丰富的体验，你可以自定义它来模拟实际硬件。 例如： 当您将其发送的温度读数具有指定的从属节点地址的设备上的命令时，更新 I2c 提供程序返回返回结果"75"。

## <a name="additional-resources"></a>其他资源

其他总线工具、 示例代码，以及构建和 I2C，SPI，GPIO 上测试，可以找到 MinComm/UART[此处](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools)。

