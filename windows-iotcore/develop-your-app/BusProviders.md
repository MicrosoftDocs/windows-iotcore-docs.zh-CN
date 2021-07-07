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
# <a name="usermode-access-to-gpio-i2c-and-spi"></a>用户对 GPIO、I2C 和 SPI 的访问权限

Windows 10 包含的新 API 可用于直接通过用户模式访问 GPIO、I2C、SPI 和 UART。 开发板（如 Raspberry Pi 2）将公开这些连接的子集，这些连接支持用户使用自定义电路扩展基本计算模块来处理特定应用程序。 这些低级别总线通常与其他关键载入功能共享，仅一部分 GPIO 引脚和总线在标头上公开。 若要保持系统稳定性，必须通过用户模式应用程序指定可供安全修改的引脚和总线。

用户通过现有 和 框架Windows上对低级别总线 `GpioClx` `SpbCx` 的访问。 名为 RhProxy 的新驱动程序（Windows IoT Core 和 Windows Enterprise）向 `GpioClx` `SpbCx` usermode 公开和资源。 若要启用这些 API，必须在 ACPI 表（内含应向用户模式公开的每个 GPIO 和 SPB 资源）中声明用于 RhProxy 的设备节点。

有关通过 RhProxy 访问 UserMode 的其他深入文档，可在此处 [找到](https://docs.microsoft.com/windows/uwp/devices-sensors/enable-usermode-access)。

## <a name="bus-providers"></a>总线提供程序

从 Windows 10 开始，Windows已具有提供对位于 soc 上的 Gpio、Spi 或 I2c 总线的直接访问的开箱式 UWP API。这样，通过高级 API 可以轻松访问此硬件。 但是，许多时候，设备制造商想要使用 soc 控制器来访问总线。 它可以像添加 16 个 GPIO 引脚的便宜芯片一样简单，也可以像 Arduino () 一样丰富（如 Arduino) 不仅添加 Gpio、SPI 和 I2C 引脚，还支持 PWM 和 ADC）。 借助"总线提供程序"模型，我们使开发人员能够使用可弥补差距的用户模式提供程序，使用箱内 API 访问这些非总线总线。

构建提供程序的人将一组接口实现到 UWP 类库中，然后任何想要与硬件对话的开发人员只需包含组件，并告知其 API。 如果查看远程 [Arduino](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) 提供程序中的示例代码，可以看到配置提供程序是多么容易，并且一旦设置为该应用的默认提供程序，客户端应用中的其余代码与访问 on-soc 总线所需的代码相同。


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

目前，我们在总线提供程序 github 存储库中 [提供了许多](https://github.com/ms-iot/BusProviders) 提供程序。 除了提供程序的代码之外，每个提供程序还有一个示例 VS 解决方案，用于演示客户端如何使用该提供程序。

- **ADC**
  - Ads1x15
  - Mcp3008
  - 远程 Arduino

- **PWM**
  - PCA9685
  - 使用 Gpio 模拟
  - 远程 Arduino

- **Gpio、SPI、I2C**
  - 远程 Arduino

除了提供对真实硬件的访问权限的提供商之外，我们还构建了模拟提供程序，该[](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider)提供程序将充当无限功能提供程序，旨在让你编写和调试应用程序，而无需先将它们部署到工作设备。 若要获得更丰富的体验，可以对其进行自定义以模拟实际硬件。 例如：更新 I2c 提供程序，以在向 I2c 提供程序发送温度读数命令时返回结果"75"，以在具有指定辅助地址的设备上读取温度。

## <a name="additional-resources"></a>其他资源

有关 I2C、SPI、GPIO、MinComm/UART 的其他总线工具、示例代码以及生成和测试，可在此处 [找到](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools)。

请参阅[Windows Runtime (WinRT) API，](https://docs.microsoft.com/uwp/api)下面将了解如何利用[Win32 应用程序中的 API。](https://blogs.windows.com/windowsdeveloper/2017/01/25/calling-windows-10-apis-desktop-application/)   
