---
title: Raspberry Pi 2 & 3 引脚映射
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解 Raspberry Pi 2 和 3 的引脚映射功能。
keywords: windows iot， Rasperry Pi 2， Raspberry Pi 3， 引脚映射， GPIO
ms.openlocfilehash: 6abad2dbebf192c377e17ce840d7a728011d259d
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229594"
---
# <a name="raspberry-pi-2--3-pin-mappings"></a>Raspberry Pi 2 & 3 引脚映射

![Raspberry Pi 2 & 3 引脚标头](../../media/PinMappingsRPI/RP2_Pinout.png)

Raspberry Pi 2 和 Raspberry Pi 3 的硬件接口通过板上的 40 引脚标头 **J8** 公开。 功能包括：

* **24x** - GPIO 引脚
* **1x** - RPi3 (UART 仅包含微型 UART) 
* **2x** - SPI 总线
* **1x** - I2C 总线
* **2x** - 5V 电源引脚
* **2x** - 3.3V 电源引脚
* **8x** - 地引脚

## <a name="gpio-pins"></a>GPIO 引脚

让我们看看此设备上提供的 GPIO。

### <a name="gpio-pin-overview"></a>GPIO 引脚概述

可通过 API 访问以下 GPIO 引脚：

> | GPIO# | 打开电源拉取 | 备用函数 | 标头引脚         |
> |-------|---------------|---------------------|--------------------|
> | 2     | PullUp        | I2C1 SDA            | 3                  |
> | 3     | PullUp        | I2C1 SCL            | 5                  |
> | 4     | PullUp        |                     | 7                  |
> | 5     | PullUp        |                     | 29                 |
> | 6     | PullUp        |                     | 31                 |
> | 7     | PullUp        | SPI0 CS1            | 26                 |
> | 8     | PullUp        | SPI0 CS0            | 24                 |
> | 9     | PullDown      | SPI0 MISO           | 21                 |
> | 10    | PullDown      | SPI0 MOSI           | 19                 |
> | 11    | PullDown      | SPI0 SCLK           | 23                 |
> | 12    | PullDown      |                     | 32                 |
> | 13    | PullDown      |                     | 33                 |
> | 16    | PullDown      | SPI1 CS0            | 36                 |
> | 17    | PullDown      |                     | 11                 |
> | 18    | PullDown      |                     | 12                 |
> | 19    | PullDown      | SPI1 MISO           | 35                 |
> | 20    | PullDown      | SPI1 MOSI           | 38                 |
> | 21    | PullDown      | SPI1 SCLK           | 40                 |
> | 22    | PullDown      |                     | 15                 |
> | 23    | PullDown      |                     | 16                 |
> | 24    | PullDown      |                     | 18                 |
> | 25    | PullDown      |                     | 22                 |
> | 26    | PullDown      |                     | 37                 |
> | 27    | PullDown      |                     | 13                 |
> | 35*   | PullUp        |                     | 红色电源 LED      |
> | 47*   | PullUp        |                     | 绿色活动 LED |

\* = Raspberry Pi 2 ONLY。 GPIO 35 & 47 在 Raspberry Pi 3 上不可用。

### <a name="gpio-sample"></a>GPIO 示例

例如，以下代码将 **GPIO 5** 作为输出打开，在引脚上写出数字 **"1"：**

```csharp
using Windows.Devices.Gpio;

public void GPIO()
{
    // Get the default GPIO controller on the system
    GpioController gpio = GpioController.GetDefault();
    if (gpio == null)
        return; // GPIO not available on this system

    // Open GPIO 5
    using (GpioPin pin = gpio.OpenPin(5))
    {
        // Latch HIGH value first. This ensures a default value when the pin is set as output
        pin.Write(GpioPinValue.High);

        // Set the IO direction as output
        pin.SetDriveMode(GpioPinDriveMode.Output);

    } // Close pin - will revert to its power-on state
}
```

打开引脚时，它将位于其打开状态，可能包括拉取器。 若要断开拉取器并获取高抗抗性输入，将驱动器模式设置为 GpioPinDriveMode.Input：
```
    pin.SetDriveMode(GpioPinDriveMode.Input);
```
当引脚关闭时，它将还原为其打开状态。

### <a name="pin-muxing"></a>固定多路复用

某些 GPIO 引脚可以执行多个功能。 默认情况下，引脚配置为 GPIO 输入。 通过调用 或 打开备用函数时，该函数所需的引脚 `I2cDevice.FromIdAsync()` `SpiDevice.FromIdAsync()` ("muxed") 切换到正确的函数。 通过调用 或 关闭设备 `I2cDevice.Dispose()` 时 `SpiDevice.Dispose()` ，引脚将恢复为默认功能。 如果尝试同时对两个不同的函数使用 pin，则当你尝试打开冲突函数时，将引发异常。 例如，

```csharp
var controller = GpioController.GetDefault();
var gpio2 = controller.OpenPin(2);      // open GPIO2, shared with I2C1 SDA

var dis = await DeviceInformation.FindAllAsync(I2cDevice.GetDeviceSelector());
var i2cDevice = await I2cDevice.FromIdAsync(dis[0].Id, new I2cConnectionSettings(0x55)); // exception thrown because GPIO2 is open

gpio2.Dispose(); // close GPIO2
var i2cDevice = await I2cDevice.FromIdAsync(dis[0].Id, new I2cConnectionSettings(0x55)); // succeeds because gpio2 is now available

var gpio2 = controller.OpenPin(2); // throws exception because GPIO2 is in use as SDA1

i2cDevice.Dispose(); // release I2C device
var gpio2 = controller.OpenPin(2); // succeeds now that GPIO2 is available
```

## <a name="serial-uart"></a>串行 UART

RPi2/3 上提供了一个串行 **UART：UART0**

* 引脚 8 - **UART0 TX**
* 引脚 10 - **UART0 RX**

下面的示例初始化 **UART0** 并执行写入，然后执行读取：


```csharp
using Windows.Storage.Streams;
using Windows.Devices.Enumeration;
using Windows.Devices.SerialCommunication;

public async void Serial()
{
    string aqs = SerialDevice.GetDeviceSelector("UART0");                   /* Find the selector string for the serial device   */
    var dis = await DeviceInformation.FindAllAsync(aqs);                    /* Find the serial device with our selector string  */
    SerialDevice SerialPort = await SerialDevice.FromIdAsync(dis[0].Id);    /* Create an serial device with our selected device */

    /* Configure serial settings */
    SerialPort.WriteTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.ReadTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.BaudRate = 9600;                                             /* mini UART: only standard baudrates */
    SerialPort.Parity = SerialParity.None;                                  /* mini UART: no parities */  
    SerialPort.StopBits = SerialStopBitCount.One;                           /* mini UART: 1 stop bit */
    SerialPort.DataBits = 8;

    /* Write a string out over serial */
    string txBuffer = "Hello Serial";
    DataWriter dataWriter = new DataWriter();
    dataWriter.WriteString(txBuffer);
    uint bytesWritten = await SerialPort.OutputStream.WriteAsync(dataWriter.DetachBuffer());

    /* Read data in from the serial port */
    const uint maxReadLength = 1024;
    DataReader dataReader = new DataReader(SerialPort.InputStream);
    uint bytesToRead = await dataReader.LoadAsync(maxReadLength);
    string rxBuffer = dataReader.ReadString(bytesToRead);
}
```

请注意，必须将以下功能添加到 UWP 项目中 **的 Package.appxmanifest** 文件，以运行串行 UART 代码：

Visual Studio 2017 在清单设计器中 (appxmanifest 文件的可视化编辑器中) 影响串行通信功能。  如果 appxmanifest 添加了串行通信功能，则使用设计器修改 appxmanifest 将损坏 appxmanifest (设备 xml 子级将丢失) 。  可以通过手动编辑 appxmanifest 来解决此问题，方法是右键单击 appxmanifest，然后从上下文菜单中选择"查看代码"。

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a>I2C 总线

让我们看看此设备上提供的 I2C 总线。

### <a name="i2c-overview"></a>I2C 概述

在引脚标头上公开了一个 **I2C 控制器 I2C1，** 包含两行 **SDA 和** **SCL**。 此总线&#x2126;板中已安装 1.8K 个内部拉取开关。

> | 信号名称 | 标头引脚编号 | Gpio 编号 |
> |-------------|-------------------|-------------|
> | Sda         | 3                 | 2           |
> | SCL         | 5                 | 3           |

以下示例初始化 **I2C1，** 将数据写入地址为 的 I2C **0x40：**

```csharp
using Windows.Devices.Enumeration;
using Windows.Devices.I2c;

public async void I2C()
{
    // 0x40 is the I2C device address
    var settings = new I2cConnectionSettings(0x40);
    // FastMode = 400KHz
    settings.BusSpeed = I2cBusSpeed.FastMode;

    // Create an I2cDevice with the specified I2C settings
    var controller = await I2cController.GetDefaultAsync();

    using (I2cDevice device = controller.GetDevice(settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```

## <a name="spi-bus"></a>SPI 总线

RPi2/3 上提供两个 SPI 总线控制器。

### <a name="spi0"></a>SPI0

> | 信号名称 | 标头引脚编号 | Gpio 编号 |
> |-------------|-------------------|-------------|
> | MOSI        | 19                | 10          |
> | 酱        | 21                | 9           |
> | SCLK        | 23                | 11          |
> | CS0         | 24                | 8           |
> | CS1         | 26                | 7           |

### <a name="spi1"></a>SPI1

> | 信号名称 | 标头引脚编号 | Gpio 编号 |
> |-------------|-------------------|-------------|
> | MOSI        | 38                | 20          |
> | 酱        | 35                | 19          |
> | SCLK        | 40                | 21          |
> | CS0         | 36                | 16          |


### <a name="spi-sample"></a>SPI 示例

下面显示了如何使用芯片选择 0 在总线 **SPI0** 上执行 SPI 写入的示例：

```csharp
using Windows.Devices.Enumeration;
using Windows.Devices.Spi;

public async void SPI()
{
    // Use chip select line CS0
    var settings = new SpiConnectionSettings(0);
    // Set clock to 10MHz
    settings.ClockFrequency = 10000000;

    // Get a selector string that will return our wanted SPI controller
    string aqs = SpiDevice.GetDeviceSelector("SPI0");

    // Find the SPI bus controller devices with our selector string
    var dis = await DeviceInformation.FindAllAsync(aqs);

    // Create an SpiDevice with our selected bus controller and Spi settings
    using (SpiDevice device = await SpiDevice.FromIdAsync(dis[0].Id, settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```
