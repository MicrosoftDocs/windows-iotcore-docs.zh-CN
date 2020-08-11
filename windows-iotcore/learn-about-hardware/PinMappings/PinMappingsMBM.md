---
title: Minnowboard 最大 Pin 映射
ms.date: 08/28/2017
ms.topic: article
description: 了解 Minnowboard Max 的 pin 映射功能。 获取有关串行 UART、I2C 总线和 SPI 总线的信息。 阅读 GPIO 代码示例。
keywords: windows iot，Minnowboard Max，pin 映射，GPIO
ms.openlocfilehash: 720d900873bd39d3f867920bb6316319c114fdd5
ms.sourcegitcommit: 05278f1a522ed498900ce15b98bdd4389b5dde55
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88081332"
---
# <a name="minnowboard-max-pin-mappings"></a>MinnowBoard 最大 Pin 映射

> [!NOTE] 
> 若要将此 pin 映射与较新版本的 Minnowboard 进行比较，请访问[此处](https://minnowboard.org/minnowboard-turbot/documentation)的文档。

## <a name="overview"></a>概述

![MinnowBoard 最大 Pin 标头](../../media/PinMappingsMBM/MBM_Pinout.png)

MinnowBoard 最大值的硬件接口通过板上的26针标头**JP1**公开。 功能包括：

* **10 倍**-GPIO pin
* **2x** -串行 UARTs
* **1x** -SPI 总线
* **1x** -I2C 总线
* **1x** -5v 电源
* **1x** -3.3 v 电源固定
* **2x** -地面针脚

MinnowBoard Max 在所有 IO 引脚上使用 3.3 V 逻辑级别。 此外，所有针脚都由[TXS0104E](http://www.ti.com/product/txs0104e) level shifters 缓冲，但电源和接地引脚除外。
这些级别的 shifters 显示为具有 10K&#x2126; 电阻式的开放收集器输出 **，而无论 IO 设置为输入还是输出，都将显示该下拉。**
 
级别 shifters 的开放收集器特性意味着 pin 可以强输出 "0"，但只会有弱输出 "1"。 在附加从引脚中抽取电流 (例如 LED) 的设备时，必须记住这一点。 请参阅[Blinky 示例](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)，了解如何正确地将 LED MinnowBoard 最大。

## <a name="gpio-pins"></a>GPIO Pin

以下 GPIO pin 可通过 Api 访问：

> | GPIO# | 标头 Pin         |
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

**注意：** 对于 BIOS， **Gpio 4**和**gpio 5**被 MinnowBoard Max 用作启动配置的 pin。
请确保在启动过程中连接的设备不会驱动这些 GPIO，因为这样可能会阻止 MBM 启动。
MBM 在 BIOS 之后启动后，可以正常使用这些 GPIO。
     
## <a name="gpio-sample"></a>GPIO 示例

例如，以下代码将**GPIO 5**打开为输出，并在 pin 上写入数字 "**1**"：
         
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

MBM 上提供了两个串行 UARTS： **UART1**和**UART2**

**UART1**具有标准的**UART1 TX**和**UART1 RX**线路，以及流控制信号**UART1 CTS**和**UART1 RTS**。

* Pin 6- **UART1 TX**
* Pin 8- **UART1 RX**
* Pin 10- **UART1 CTS**
* Pin 12- **UART1 RTS**

UART1 在版本10240中不起作用。 请使用 UART2 或 USB 串行转换器。

**UART2**仅包括**UART2 TX**和**UART2 RX**行。

* 固定 17- **UART2 TX**
* Pin 19- **UART2 RX**

UART2 不支持流控制，因此访问 SerialDevice 的以下属性可能会导致引发异常：

 * BreakSignalState
 * IsDataTerminalReadyEnabled
 * IsRequestToSendEnabled
 * 仅握手 SerialHandshake 受支持

下面的示例初始化**UART2**并执行写操作，后跟读取：

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

请注意，必须将以下功能添加到 UWP 项目中的**appxmanifest.xml**文件，才能运行串行 UART 代码：

Visual Studio 2017 在清单设计器中有一个已知 bug， (用于 appxmanifest.xml 文件的可视化编辑器) 会影响 serialcommunication 功能。  如果你的 appxmanifest.xml 添加 serialcommunication 功能，则通过设计器修改 appxmanifest.xml 将损坏 appxmanifest.xml (设备 xml 子级将丢失) 。  若要解决此问题，请右键单击 appxmanifest.xml，然后从上下文菜单中选择 "查看代码"，手动编辑 appxmanifest.xml。

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

Pin 标头上有一个 I2C 控制器**I2C5** ，其中包含两行**SDA**和**SCL**。 10K&#x2126; 这些线路上已存在内部拉取电阻。

* Pin 15- **I2C5 SDA**
* Pin 13- **I2C5 SCL**

### <a name="i2c-sample"></a>I2C 示例

下面的示例使用 address **0x40**初始化**I2C5**并将数据写入 I2C 设备：

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

MinnowBoard Max 具有与 I2C 总线相关的已知问题，导致某些 I2C 设备发生通信问题。 通常，I2C 设备会在总线请求期间确认其地址。
但是，在某些情况下，此确认无法在 shifters 到 MBM 的情况下向后传播，因此 CPU 认为设备没有响应并取消总线事务。
此问题似乎与 IO 引脚上的[TXS0104E](http://www.ti.com/product/txs0104e) level shifters 相关，这会由于线路上出现电压峰值而提前触发。
当前的解决方法是使用 I2C SCK line 在系列中插入100欧姆电阻器，这有助于抑制峰值。 并非所有设备都受影响，因此，仅当遇到总线响应问题时才需要此解决方法。 已知需要此解决方法的一个设备是 HTU21D。

## <a name="spi-bus"></a>SPI 总线

让我们看看此设备上可用的 SPI 总线。

### <a name="spi-overview"></a>SPI 概述

MBM 上提供了一个 SPI 控制器**SPI0** ：

* Pin 9- **SPI0 MOSI**
* 引脚 7- **SPI0 MISO**
* 引脚 11- **SPI0 SCLK**
* Pin 5- **SPI0 CS0**


### <a name="spi-sample"></a>SPI 示例

下面显示了有关如何在总线上执行 SPI 写入的示例**SPI0** ：

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

