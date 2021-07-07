---
title: Minnowboard 最大引脚映射
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解 Minnowboard Max 的引脚映射功能。 获取有关串行 UART、I2C 总线和 SPI 总线的信息。 阅读 GPIO 代码示例。
keywords: windows iot、Minnowboard Max、引脚映射、GPIO
ms.openlocfilehash: ade7f026ac4b21401e47f09c01c8474be110999a
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113228843"
---
# <a name="minnowboard-max-pin-mappings"></a>MinnowBoard 最大引脚映射

> [!NOTE] 
> 若要将此引脚映射与较新版本的 Minnowboard 进行比较，请访问此处 [的文档](https://minnowboard.org/minnowboard-turbot/documentation)。

## <a name="overview"></a>概述

![MinnowBoard 最大引脚标头](../../media/PinMappingsMBM/MBM_Pinout.png)

MinnowBoard Max 的硬件接口通过板上的 26 引脚标头 **JP1** 公开。 功能包括：

* **10x** - GPIO 引脚
* **2x** - 串行 UART
* **1x** - SPI 总线
* **1x** - I2C 总线
* **1x** - 5V 电源引脚
* **1x** - 3.3V 电源引脚
* **2x** - 地引脚

MinnowBoard Max 在所有 IO 引脚上使用 3.3V 逻辑级别。 此外 [，TXS0104E](http://www.ti.com/product/txs0104e) 级别移位器缓冲所有引脚，电源和地引脚除外。
这些级别移位器显示为具有 **10K**&#x2126;的打开收集器输出，并且无论 IO 设置为输入还是输出，都会存在下拉。
 
水平移位器的开放收集器性质意味着引脚可以强输出"0"，但只能弱输出"1"。 在附加设备时，必须记住这一点，这些设备从引脚（如 LED (）) 。 有关将 LED 与 MinnowBoard Max 连接的正确方法，请参阅 [Blinky](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) 示例。

## <a name="gpio-pins"></a>GPIO 引脚

可通过 API 访问以下 GPIO 引脚：

> | GPIO# | 标头引脚         |
> |-------|--------------------|
> | 0     | 21                 |
> | 1     | 23                 |
> | 2     | 25                 |
> | 3     | 14                 |
> | 4     | 16                 |
> | 5     | 18                 |
> | 6     | 20                 |
> | 7     | 22                 |
> | 8     | 24                 |
> | 9     | 26                 |

**注意**：MINnowBoard Max 使用 **GPIO 4** 和 **GPIO 5** 作为 BIOS 的启动配置引脚。
请确保附加的设备在启动期间不会使这些 GPIO 较低，因为这样做可能会阻止 MBM 启动。
在 MBM 启动通过 BIOS 后，可以正常使用这些 GPIO。
     
## <a name="gpio-sample"></a>GPIO 示例

例如，以下代码将 **GPIO 5** 作为输出打开，在引脚上写出数字 **"1"：**
         
```C#
using Windows.Devices.Gpio;
         
public void GPIO()
{
    GpioController Controller = GpioController.GetDefault(); /* Get the default GPIO controller on the system */

    GpioPin Pin = Controller.OpenPin(5);        /* Open GPIO 5                      */
    Pin.SetDriveMode(GpioPinDriveMode.Output);  /* Set the IO direction as output   */
    Pin.Write(GpioPinValue.High);               /* Output a digital '1'             */
}
```

## <a name="serial-uart"></a>串行 UART

MBM 上提供两个串行 **UARTS：UART1** 和 **UART2**

**UART1** 具有标准 **UART1 TX** 和 **UART1 RX** 行，以及流控制信号 **UART1 CTS** 和 **UART1 RTS。**

* 引脚 6 - **UART1 TX**
* 引脚 8 - **UART1 RX**
* 引脚 10 - **UART1 CTS**
* 引脚 12 - **UART1 RTS**

从内部版本 10240 开始，UART1 不工作。 请使用 UART2 或 USB-Serial转换器。

**UART2** 仅包括 **UART2 TX 和** **UART2 RX** 行。

* 引脚 17 - **UART2 TX**
* 引脚 19 - **UART2 RX**

UART2 不支持流控制，因此访问 SerialDevice 的以下属性可能会导致引发异常：

 * BreakSignalState
 * IsDataTerminalReadyEnabled
 * IsRequestToSendEnabled
 * 握手 - 仅支持 SerialHandshake.None

下面的示例初始化 **UART2 并执行** 写入，然后执行读取：

```C#
using Windows.Storage.Streams;
using Windows.Devices.Enumeration;
using Windows.Devices.SerialCommunication;

public async void Serial()
{
    string aqs = SerialDevice.GetDeviceSelector("UART2");                   /* Find the selector string for the serial device   */
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

请注意，必须将以下功能添加到 UWP 项目中 **的 Package.appxmanifest** 文件，以运行串行 UART 代码：

Visual Studio 2017 在清单设计器中 (appxmanifest 文件的可视化编辑器中) 影响串行通信功能。  如果 appxmanifest 添加了串行通信功能，则使用设计器修改 appxmanifest 将损坏 appxmanifest (设备 xml 子级将丢失) 。  可以通过手动编辑 appxmanifest 来解决此问题，方法是右键单击 appxmanifest，然后从上下文菜单中选择"查看代码"。

```
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

在引脚标头上公开了一个 **I2C 控制器 I2C5，** 包含两行 **SDA 和** **SCL**。 这些&#x2126;已有 10，000 个内部向上拉取器。

* 引脚 15 - **I2C5 SDA**
* 引脚 13 - **I2C5 SCL**

### <a name="i2c-sample"></a>I2C 示例

以下示例初始化 **I2C5，将数据** 写入地址为 的 I2C **0x40：**

```C#
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

### <a name="i2c-issues"></a>I2C 问题

MinnowBoard Max 具有 I2C 总线的已知问题，这导致某些 I2C 设备的通信问题。 通常，I2C 设备将在总线请求期间确认其地址。
但是，在某些情况下，此确认无法通过级别移位器传播回 MBM，因此 CPU 认为设备未响应并取消总线事务。
此问题似乎与 IO 引脚上的 [TXS0104E](http://www.ti.com/product/txs0104e) 级别移位器有关，由于线路上的电压峰值，可能会提前触发。
当前解决方法是，使用 I2C SCK 线在系列中插入 100-ohm 的电流，这有助于抑制峰值。 并非所有设备都受到影响，因此只有在获取总线响应时遇到问题，才需要此解决方法。 已知需要此解决方法的设备是 HTU21D。

## <a name="spi-bus"></a>SPI 总线

让我们看看此设备上提供的 SPI 总线。

### <a name="spi-overview"></a>SPI 概述

MBM 上提供了一个 SPI 控制器 **SPI0：**

* 引脚 9 - **SPI0 MOSI**
* 引脚 7 - **SPI0 MISO**
* 引脚 11 - **SPI0 SCLK**
* 引脚 5 - **SPI0 CS0**


### <a name="spi-sample"></a>SPI 示例

下面显示了有关如何在总线上执行 SPI 写入的示例 **SPI0** ：

```C#
using Windows.Devices.Enumeration;
using Windows.Devices.Spi;

public async void SPI()
{
    // Use chip select line CS0
    var settings = new SpiConnectionSettings(0);
    // Set clock to 10MHz
    settings.ClockFrequency = 10000000;

    // Create an SpiDevice with the specified Spi settings
    var controller = await SpiController.GetDefaultAsync();

    using (SpiDevice device = controller.GetDevice(settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```

