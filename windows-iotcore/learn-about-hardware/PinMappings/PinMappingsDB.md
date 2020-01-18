---
title: DragonBoard 引脚映射
ms.date: 08/28/2017
ms.topic: article
description: 了解 Dragonboard 的 pin 映射功能。
keywords: windows iot，Dragonboard，pin 映射，GPIO
ms.openlocfilehash: f0a811c05b371d9f7a85c1f86b0f69de4d750487
ms.sourcegitcommit: 0fa10fafb13788496674d13e0ae810a6d93e3483
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/17/2020
ms.locfileid: "76258551"
---
# <a name="dragonboard-pin-mappings"></a>DragonBoard 引脚映射

![Dragonboard 针标头](../../media/PinMappingsDB/DB_Pinout.png)

Dragonboard 的硬件接口通过开发板上的 40 排针公开。 功能包括：

* **11x** - GPIO 引脚
* **2x** - 串行 UART
* **1x** - SPI 总线
* **2x** - I2C 总线
* **1x** - 5V 电源引脚
* **1x** - 1.8V 电源引脚
* **4x** - 接地引脚

请注意，Dragonboard 在所有 IO 引脚上使用 1.8 V 逻辑级别。 

## <a name="gpio-pins"></a>GPIO Pin

让我们看看此设备上的 GPIO 可用。

### <a name="gpio-pin-table"></a>GPIO 固定表

以下 GPIO 引脚可通过 API 访问：

> | GPIO# | 排针         |
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


例如，以下代码将**GPIO 35**打开为输出，并在 pin 上写入数字 "**1**"：
         
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
* 引脚会在启动时配置为 InputPullDown，但在首次打开时将更改为 Input (floating)
* 关闭时，引脚不会还原为默认状态
* 当多个引脚上启用了中断时，可能会看到假中断


## <a name="serial-uart"></a>串行 UART

Dragonboard 上提供了两个串行 UART：**UART0** 和 **UART1**

**UART0** 具有标准 **UART0 TX** 和 **UART0 RX** 线以及流控制信号 **UART0 CTS** 和 **UART0 RTS**。

* Pin 5- **UART0 TX**
* 引脚 7- **UART0 RX**
* Pin 3- **UART0 CTS**
* Pin 9- **UART0 RTS**


**UART1** 仅包含 **UART1 TX** 和 **UART1 RX** 线。

* Pin 11- **UART1 TX**
* Pin 13- **UART1 RX**

以下示例初始化 **UART1** 并依次执行写入和读取操作：

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
> Visual Studio 2017 在清单设计器（appxmanifest.xml 文件的可视化编辑器）中有一个已知 bug，该 bug 会影响 serialcommunication 功能。  如果 appxmanifest.xml 添加 serialcommunication 功能，则在设计器中修改 appxmanifest.xml 将损坏 appxmanifest.xml （设备 xml 子级将丢失）。  若要解决此问题，请右键单击 appxmanifest.xml，然后从上下文菜单中选择 "查看代码"，手动编辑 appxmanifest.xml。

必须将以下功能添加到 UWP 项目中的**appxmanifest.xml**文件，才能运行串行 UART 代码：

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

在排针上公开的 **I2C0**，带有 **SDA** 和 **SCL** 两条线

* 引脚 17 - **I2C0 SDA**
* 引脚 15 - **I2C0 SCL**

在排针上公开的 **I2C1**，带有 **SDA** 和 **SCL** 两条线

* 引脚 21 - **I2C1 SDA**
* 引脚 19 - **I2C1 SCL**

### <a name="i2c-sample"></a>I2C 示例

以下示例将初始化 **I2C0** 并将数据写入地址为 **0x40** 的 I2C 设备：

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

DB 上提供一个 SPI 控制器 **SPI0**

* Pin 10- **SPI0 MISO**
* Pin 14- **SPI0 MOSI**
* 引脚 8 - **SPI0 SCLK**
* 引脚 12 - **SPI0 CS0**

### <a name="spi-issues"></a>SPI 问题

SPI 时钟固定在 4.8mhz。 请求的 SPI 时钟将被忽略。 


### <a name="spi-sample"></a>SPI 示例

有关如何在总线 **SPI0** 上执行 SPI 写入的示例如下所示：

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
