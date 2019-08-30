---
title: 总线提供程序
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 了解通过 Windows 10 IoT Core 提供的不同提供商。
keywords: windows iot, 提供程序, 总线提供程序, UWP, Gpio, Spi
ms.openlocfilehash: 7e2a3bf45317cd11ca558db6f1b6845e0e0f7a67
ms.sourcegitcommit: 77b86eee2bba3844e87f9d3dbef816761ddf0dd9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/11/2019
ms.locfileid: "65533283"
---
# <a name="usermode-access-to-gpio-i2c-and-spi"></a>Usermode 访问 GPIO、I2C 和 SPI

Windows 10 包含的新 API 可用于直接通过用户模式访问 GPIO、I2C、SPI 和 UART。 开发板（如 Raspberry Pi 2）将公开这些连接的子集，这些连接支持用户使用自定义电路扩展基本计算模块来处理特定应用程序。 通常，只需使用 GPIO 引脚的一个子集和标头上公开的总线，即可与其他关键板载功能共享这些低级别总线。 若要保持系统稳定性，必须通过用户模式应用程序指定可供安全修改的引脚和总线。

Windows 上低级别总线的用户模式访问通过现有 `GpioClx` 和 `SpbCx` 框架实现。 Windows IoT Core 和 windows Enterprise 上提供了名为 RhProxy 的新驱动程序`GpioClx` , `SpbCx`它向 usermode 公开了资源。 若要启用这些 API，必须在 ACPI 表（内含应向用户模式公开的每个 GPIO 和 SPB 资源）中声明用于 RhProxy 的设备节点。

可在[此处](https://docs.microsoft.com/en-us/windows/uwp/devices-sensors/enable-usermode-access)找到有关通过 RhProxy 访问 UserMode 的其他深入文档。

## <a name="bus-providers"></a>总线提供程序

从 Windows 10 开始, Windows 提供了内置的 UWP Api, 可提供对位于 soc 上的 Gpio、Spi 或 I2c 总线的直接访问。这可以从高级别 API 轻松访问此硬件。 但是, 在许多情况下, 设备制造商希望使用脱离 soc 控制器来访问总线。 它可以像是一个低价芯片一样简单, 也可以像添加16个 GPIO pin 一样简单, 也可以像是一个完整的 MCU (如 Arduino), 它不仅能添加 Gpio、SPI 和 I2C pin, 而且还支持 PWM 和 ADC。 使用 "总线提供程序" 模型, 开发人员可以使用内置的 Api, 使用桥梁的用户模式提供程序来访问这些脱离 soc 总线。

构建提供程序的用户在 UWP 类库中实现了一组接口, 然后需要与该硬件通信的任何开发人员都只包含该组件, 并告诉内置 Api。 如果你查看来自[远程 Arduino 提供程序](https://github.com/ms-iot/BusProviders/tree/develop/Arduino)的示例代码, 你可以看到配置提供程序的过程是多么简单, 并且一旦设置为该应用程序的默认提供程序, 客户端应用程序中的其余代码就会与访问 on soc 总线所需的代码完全相同。


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

## <a name="available-providers"></a>可用提供程序

目前,[总线提供](https://github.com/ms-iot/BusProviders)商 github 存储库中提供了许多提供程序。 除了提供程序的代码以外, 每个提供程序都有一个示例 VS 解决方案, 该解决方案演示了客户端如何使用该提供程序。 

- **ADC**
  - Ads1x15
  - Mcp3008
  - 远程 Arduino

- **PWM**
  - PCA9685
  - 模拟 with Gpio
  - 远程 Arduino
  
- **Gpio、SPI、I2C**
  - 远程 Arduino

除了提供对实际硬件的访问权的提供程序外, 我们还构建了[模拟的提供程序, 该提供程序](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider)将充当支持 inifitely 的提供程序, 并可让你编写和调试应用程序, 而无需先将其部署到正在运行的设备。 为了获得更丰富的体验, 你可以对其进行自定义以模拟你的实际硬件。 例如: 在向其发送指定的从属地址的设备上, 更新 I2c 提供程序以返回结果 "75"。

## <a name="additional-resources"></a>其他资源

可在[此处](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools)找到 I2C、SPI、GPIO、MINCOMM/UART 的其他总线工具、示例代码和生成和测试。

