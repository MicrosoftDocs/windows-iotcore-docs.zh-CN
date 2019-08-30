---
title: Raspberry Pi 2 和 3 引脚映射
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解 Raspberry Pi 2 和3的 pin 映射功能。
keywords: windows iot, Rasperry Pi 2, Raspberry Pi 3, 固定映射, GPIO
ms.openlocfilehash: 86e641bdcc6b4895161c6509ca7529b0dd55fad9
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167509"
---
# <a name="raspberry-pi-2--3-pin-mappings"></a>Raspberry Pi 2 和 3 引脚映射

![Raspberry Pi 2 & 3 针标题](../../media/PinMappingsRPI/RP2_Pinout.png)

Raspberry Pi 2 和 Raspberry Pi 3 的硬件接口通过开发板上的 40 排针 **J8** 公开。 功能包括：

* **24x** -GPIO 引脚
* **1x** -串行 UARTs (RPi3 仅包含微型 UART)
* **2x** -SPI 总线
* **1x** - I2C 总线
* **2x** - 5V 电源引脚
* **2x** - 3.3V 电源引脚
* **8x** - 接地引脚

## <a name="gpio-pins"></a>GPIO Pin

让我们看看此设备上的 GPIO 可用。

### <a name="gpio-pin-overview"></a>GPIO Pin 概述

以下 GPIO 引脚可通过 API 访问：

> | GPIO# | 通电拉 | 备用函数 | 排针         |
> |-------|---------------|---------------------|--------------------|
> | 2     | 上拉        | I2C1 SDA            | 3                  |
> | 3     | 上拉        | I2C1 SCL            | 5                  |
> | 4     | 上拉        |                     | 7                  |
> | 5     | 上拉        |                     | 29                 |
> | 6     | 上拉        |                     | 31                 |
> | 7     | 上拉        | SPI0 CS1            | 26                 |
> | 8     | 上拉        | SPI0 CS0            | 24                 |
> | 9     | 下拉      | SPI0 MISO           | 21                 |
> | 10    | 下拉      | SPI0 MOSI           | 19                 |
> | 11    | 下拉      | SPI0 SCLK           | 23                 |
> | 12    | 下拉      |                     | 32                 |
> | 13    | 下拉      |                     | 33                 |
> | 16    | 下拉      | SPI1 CS0            | 36                 |
> | 17    | 下拉      |                     | 11                 |
> | 18    | 下拉      |                     | 12                 |
> | 19    | 下拉      | SPI1 MISO           | 35                 |
> | 20    | 下拉      | SPI1 MOSI           | 38                 |
> | 21    | 下拉      | SPI1 SCLK           | 40                 |
> | 22    | 下拉      |                     | 15                 |
> | 23    | 下拉      |                     | 16                 |
> | 24    | 下拉      |                     | 18                 |
> | 25    | 下拉      |                     | 22                 |
> | 26    | 下拉      |                     | 37                 |
> | 27    | 下拉      |                     | 13                 |
> | 35*   | 上拉        |                     | 红色电源 LED      |
> | 47*   | 上拉        |                     | 绿色活动 LED |

\*= Raspberry Pi 2。 Raspberry Pi 3 上未提供 GPIO 35 和 47。

### <a name="gpio-sample"></a>GPIO 示例

例如，以下代码将 **GPIO 5** 作为输出打开，并在该引脚上写入数字“**1**”：

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

打开 pin 时, 它将处于其开机状态, 其中可能包括拉取电阻器。 若要断开拉电阻的连接并获取高阻抗输入，请将驱动程序模式设置为 GpioPinDriveMode.Input：

    pin.SetDriveMode(GpioPinDriveMode.Input);

当关闭引脚时，它将还原到其通电状态。

### <a name="pin-muxing"></a>固定 Muxing

某些 GPIO pin 可以执行多个功能。 默认情况下, pin 配置为 GPIO 输入。 当通过调用`I2cDevice.FromIdAsync()`或`SpiDevice.FromIdAsync()`打开替代函数时, 该函数所需的 pin 会自动切换 ("muxed") 到正确的函数。 当通过调用`I2cDevice.Dispose()`或`SpiDevice.Dispose()`关闭设备时, pin 会恢复为其默认功能。 如果尝试同时对两个不同的函数使用 pin, 则在尝试打开冲突的函数时会引发异常。 例如，

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

RPi2/3 上有一个串行 UART：**UART0**

* Pin 8- **UART0 TX**
* 引脚 10- **UART0 RX**

以下示例初始化 **UART0** 并依次执行写入和读取操作：


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

请注意，必须将以下功能添加到 UWP 项目中的 **Package.appxmanifest** 文件，才能运行串行 UART 代码：

Visual Studio 2017 在清单设计器 (appxmanifest.xml 文件的可视化编辑器) 中有一个已知 bug, 该 bug 会影响 serialcommunication 功能。  如果 appxmanifest.xml 添加 serialcommunication 功能, 则在设计器中修改 appxmanifest.xml 将损坏 appxmanifest.xml (设备 xml 子级将丢失)。  若要解决此问题, 请右键单击 appxmanifest.xml, 然后从上下文菜单中选择 "查看代码", 手动编辑 appxmanifest.xml。

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

排针上公开了一个 I2C 控制器 **I2C1**，带有 **SDA** 和 **SCL** 两条线。 用于此总线的 1.8K&#x2126; 内部上拉电阻已安装在开发板上。

> | 信号名称 | 标头 Pin 号 | Gpio 编号 |
> |-------------|-------------------|-------------|
> | SDA         | 3                 | 2           |
> | SCL         | 5                 | 3           |

下面的示例将初始化 **I2C1** 并将数据写入地址为 **0x40** 的 I2C 设备：

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

RPi2/3 提供了两个 SPI 总线控制器。

### <a name="spi0"></a>SPI0

> | 信号名称 | 标头 Pin 号 | Gpio 编号 |
> |-------------|-------------------|-------------|
> | MOSI        | 19                | 10          |
> | MISO        | 21                | 9           |
> | SCLK        | 23                | 11          |
> | CS0         | 24                | 8           |
> | CS1         | 26                | 7           |

### <a name="spi1"></a>SPI1

> | 信号名称 | 标头 Pin 号 | Gpio 编号 |
> |-------------|-------------------|-------------|
> | MOSI        | 38                | 20          |
> | MISO        | 35                | 19          |
> | SCLK        | 40                | 21          |
> | CS0         | 36                | 16          |


### <a name="spi-sample"></a>SPI 示例

下面显示了一个示例, 说明如何使用芯片**SPI0**在总线上执行 SPI 写入操作:

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

