---
title: Dragonboard 引脚映射
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解 Dragonboard 的引脚映射功能，包括 GPIO、串行 UART、I2C 总线和 SPI 总线。
keywords: windows iot， Dragonboard， 引脚映射， GPIO
ms.openlocfilehash: a5644e05d4743a2d61f7144b266b500d2e841163
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229624"
---
# <a name="dragonboard-pin-mappings"></a>Dragonboard 引脚映射

![Dragonboard 引脚标头](../../media/PinMappingsDB/DB_Pinout.png)

Dragonboard 的硬件接口通过板上的 40 引脚标头公开。 功能包括：

* **11x** - GPIO 引脚
* **2x** - 串行 UART
* **1x** - SPI 总线
* **2x** - I2C 总线
* **1x** - 5V 电源引脚
* **1x** - 1.8V 电源引脚
* **4x** - 地引脚

请注意，Dragonboard 在所有 IO 引脚上使用 1.8V 逻辑级别。 

## <a name="gpio-pins"></a>GPIO 引脚

让我们看看此设备上提供的 GPIO。

### <a name="gpio-pin-table"></a>GPIO 引脚表

可通过 API 访问以下 GPIO 引脚：

> | GPIO# | 标头引脚         |
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


例如，以下代码将 **GPIO 35** 作为输出打开，在引脚上写出数字 **"1"：**
         
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

* 输出在 GPIO 24 上不起作用。 输入正常。
* 引脚在启动时配置为 InputPullDown，但在首次打开时 (将更改为) 浮点输入
* 引脚在关闭时不会恢复为默认状态
* 在多个引脚上启用中断时，可能会看到虚假中断


## <a name="serial-uart"></a>串行 UART

Dragonboard **UART0** 和 UART1 上提供两个 **串行 UARTS**

**UART0** 具有标准 **UART0 TX** 和 **UART0 RX** 行，以及流控制信号 **UART0 CTS** 和 **UART0 RTS。**

* 引脚 5 - **UART0 TX**
* 引脚 7 - **UART0 RX**
* 引脚 3 - **UART0 CTS**
* 引脚 9 - **UART0 RTS**


**UART1** 仅包括 **UART1 TX 和** **UART1 RX** 行。

* 引脚 11 - **UART1 TX**
* 引脚 13 - **UART1 RX**

以下示例初始化 **UART1** 并执行写入，然后执行读取：

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
> Visual Studio 2017 在清单设计器中 (appxmanifest 文件的可视化编辑器中) 影响串行通信功能。  如果 appxmanifest 添加了串行通信功能，则使用设计器修改 appxmanifest 将损坏 appxmanifest (设备 xml 子级将丢失) 。  可以通过右键单击 appxmanifest，然后从上下文菜单中选择"查看代码"，手动编辑 appxmanifest 来解决此问题。

必须将以下功能添加到 UWP 项目中 **的 Package.appxmanifest** 文件，以运行串行 UART 代码：

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

让我们看看此设备上可用的 I2C 总线。

### <a name="i2c-pins"></a>I2C 引脚

使用两行 **SDA** 和 **SCL** 在引脚标头上公开 **I2C0**

* 引脚 17 - **I2C0 SDA**
* 引脚 15 - **I2C0 SCL**

使用两行 **SDA** 和 **SCL** 在引脚标头上公开 **I2C1**

* 引脚 21 - **I2C1 SDA**
* 引脚 19 - **I2C1 SCL**

### <a name="i2c-sample"></a>I2C 示例

以下示例初始化 **I2C0，** 并将数据写入地址为 的 I2C **0x40：**

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

让我们看看此设备上提供的 SPI 总线。

### <a name="spi-pins"></a>SPI 引脚

DB 上提供了一个 SPI 控制器 **SPI0**

* 引脚 10 - **SPI0 MISO**
* 引脚 14 - **SPI0 MOSI**
* 引脚 8 - **SPI0 SCLK**
* 引脚 12 - **SPI0 CS0**

### <a name="spi-issues"></a>SPI 问题

SPI 时钟固定在 4.8mhz。 将忽略请求的 SPI 时钟。 


### <a name="spi-sample"></a>SPI 示例

下面显示了如何在总线 **SPI0** 上执行 SPI 写入的示例：

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
