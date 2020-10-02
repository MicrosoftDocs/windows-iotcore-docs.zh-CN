---
title: Dragonboard Pin 映射
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解 Dragonboard 的 pin 映射功能，包括 GPIO、串行 UART、I2C 总线和 SPI 总线。
keywords: windows iot，Dragonboard，pin 映射，GPIO
ms.openlocfilehash: 3d0f164dd1d61ee52897864c28f0d7116e0c4a34
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655753"
---
# <a name="dragonboard-pin-mappings"></a>Dragonboard Pin 映射

![Dragonboard 针标头](../../media/PinMappingsDB/DB_Pinout.png)

Dragonboard 的硬件接口通过板上的40针标头公开。 功能包括：

* **11x** -GPIO 引脚
* **2x** -串行 UARTs
* **1x** -SPI 总线
* **2x** -I2C 总线
* **1x** -5v 电源
* **1x** -1.8 v 电源固定
* **4x**

请注意，Dragonboard 在所有 IO 引脚上使用 1.8 V 逻辑级别。 

## <a name="gpio-pins"></a>GPIO Pin

让我们看看此设备上的 GPIO 可用。

### <a name="gpio-pin-table"></a>GPIO 固定表

以下 GPIO pin 可通过 Api 访问：

> | GPIO# | 标头 Pin         |
> |-------|--------------------|
> | 36    | 23                 |
> | 12    | 24                 |
> | 13    | 25                 |
> | 69    | 26                 |
> | 115   | 27                 |
> | 24    | 29                 |
> | 25    | 30                 |
> | 35    | 31                 |
> | 34    | 32                 |
> | 28    | 33                 |
> | 33    | 34                 |
> | 21    | 用户 LED 1         | 
> | 120   | 用户 LED 2         |         


例如，以下代码将 **GPIO 35** 打开为输出，并在 pin 上写入数字 "**1**"：
         
```C#
using Windows.Devices.Gpio;
         
public void GPIO()
{
    GpioController Controller = GpioController.GetDefault(); /* Get the default GPIO controller on the system */

    GpioPin Pin = Controller.OpenPin(35);       /* Open GPIO 35                      */
    Pin.SetDriveMode(GpioPinDriveMode.Output);  /* Set the IO direction as output   */
    Pin.Write(GpioPinValue.High);               /* Output a digital '1'             */
}
```

### <a name="gpio-issues"></a>GPIO 问题

* 输出在 GPIO 24 上不起作用。 输入工作正常。
* 在启动时，pin 配置为 InputPullDown，但在首次打开时，将更改为 "输入 (" 浮动) 
* Pin 在关闭时不会恢复为其默认状态
* 如果对多个 pin 启用了中断，可能会出现虚假中断


## <a name="serial-uart"></a>串行 UART

Dragonboard **UART0**和**UART1**上提供了两个串行 UARTS

**UART0** 具有标准的 **UART0 TX** 和 **UART0 RX** 线路，以及流控制信号 **UART0 CTS** 和 **UART0 RTS**。

* Pin 5- **UART0 TX**
* 引脚 7- **UART0 RX**
* Pin 3- **UART0 CTS**
* Pin 9- **UART0 RTS**


**UART1** 仅包括 **UART1 TX** 和 **UART1 RX** 行。

* Pin 11- **UART1 TX**
* Pin 13- **UART1 RX**

下面的示例初始化 **UART1** 并执行写操作，后跟读取：

```C#
using Windows.Storage.Streams;
using Windows.Devices.Enumeration;
using Windows.Devices.SerialCommunication;

public async void Serial()
{
    string aqs = SerialDevice.GetDeviceSelector("UART1");                   /* Find the selector string for the serial device   */
    var dis = await DeviceInformation.FindAllAsync(aqs);                    /* Find the serial device with our selector string  */
    SerialDevice SerialPort = await SerialDevice.FromIdAsync(dis[0].Id);    /* Create an serial device with our selected device */

    /* Configure serial settings */
    SerialPort.WriteTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.ReadTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.BaudRate = 9600;
    SerialPort.Parity = SerialParity.None;         
    SerialPort.StopBits = SerialStopBitCount.One;
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
> [!NOTE]
> Visual Studio 2017 在清单设计器中有一个已知 bug， (用于 appxmanifest.xml 文件的可视化编辑器) 会影响 serialcommunication 功能。  如果你的 appxmanifest.xml 添加 serialcommunication 功能，则通过设计器修改 appxmanifest.xml 将损坏 appxmanifest.xml (设备 xml 子级将丢失) 。  若要解决此问题，请右键单击 appxmanifest.xml，然后从上下文菜单中选择 "查看代码"，手动编辑 appxmanifest.xml。

必须将以下功能添加到 UWP 项目中的 **appxmanifest.xml** 文件，才能运行串行 UART 代码：

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

### <a name="i2c-pins"></a>I2C 引脚

**I2C0** 在 pin 标头上公开，并带有两行 **SDA** 和 **SCL**

* Pin 17- **I2C0 SDA**
* 固定 15- **I2C0 SCL**

**I2C1** 在 pin 标头上公开，并带有两行 **SDA** 和 **SCL**

* Pin 21- **I2C1 SDA**
* 固定 19- **I2C1 SCL**

### <a name="i2c-sample"></a>I2C 示例

下面的示例使用 address **0x40**初始化**I2C0**并将数据写入 I2C 设备：

```C#
using Windows.Devices.Enumeration;
using Windows.Devices.I2c;

public async void I2C()
{
    // 0x40 is the I2C device address
    var settings = new I2cConnectionSettings(0x40);
    // FastMode = 400KHz
    settings.BusSpeed = I2cBusSpeed.FastMode;

    // Get a selector string that will return our wanted I2C controller
    string aqs = I2cDevice.GetDeviceSelector("I2C0");
    
    // Find the I2C bus controller devices with our selector string
    var dis = await DeviceInformation.FindAllAsync(aqs);

    // Create an I2cDevice with our selected bus controller and I2C settings 
    using (I2cDevice device = await I2cDevice.FromIdAsync(dis[0].Id, settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```


## <a name="spi-bus"></a>SPI 总线

让我们看看此设备上可用的 SPI 总线。

### <a name="spi-pins"></a>SPI Pin

数据库上有一个 SPI 控制器 **SPI0** 可用

* Pin 10- **SPI0 MISO**
* Pin 14- **SPI0 MOSI**
* Pin 8- **SPI0 SCLK**
* Pin 12- **SPI0 CS0**

### <a name="spi-issues"></a>SPI 问题

SPI 时钟固定在 4.8 mhz。 请求的 SPI 时钟将被忽略。 


### <a name="spi-sample"></a>SPI 示例

下面显示了有关如何在总线上执行 SPI 写入的示例 **SPI0** ：

```C#
using Windows.Devices.Enumeration;
using Windows.Devices.Spi;

public async void SPI()
{
    // Use chip select line CS0
    var settings = new SpiConnectionSettings(0);

    // Create an SpiDevice with the specified Spi settings
    var controller = await SpiController.GetDefaultAsync();

    using (SpiDevice device = controller.GetDevice(settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```
