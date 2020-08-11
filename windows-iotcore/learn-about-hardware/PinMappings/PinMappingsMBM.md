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
# <a name="minnowboard-max-pin-mappings"></a><span data-ttu-id="6b510-106">MinnowBoard 最大 Pin 映射</span><span class="sxs-lookup"><span data-stu-id="6b510-106">MinnowBoard Max Pin Mappings</span></span>

> [!NOTE] 
> <span data-ttu-id="6b510-107">若要将此 pin 映射与较新版本的 Minnowboard 进行比较，请访问[此处](https://minnowboard.org/minnowboard-turbot/documentation)的文档。</span><span class="sxs-lookup"><span data-stu-id="6b510-107">To compare this pin mapping to newer versions of the Minnowboard, please visit documentation [here](https://minnowboard.org/minnowboard-turbot/documentation).</span></span>

## <a name="overview"></a><span data-ttu-id="6b510-108">概述</span><span class="sxs-lookup"><span data-stu-id="6b510-108">Overview</span></span>

![MinnowBoard 最大 Pin 标头](../../media/PinMappingsMBM/MBM_Pinout.png)

<span data-ttu-id="6b510-110">MinnowBoard 最大值的硬件接口通过板上的26针标头**JP1**公开。</span><span class="sxs-lookup"><span data-stu-id="6b510-110">Hardware interfaces for the MinnowBoard Max are exposed through the 26-pin header **JP1** on the board.</span></span> <span data-ttu-id="6b510-111">功能包括：</span><span class="sxs-lookup"><span data-stu-id="6b510-111">Functionality includes:</span></span>

* <span data-ttu-id="6b510-112">**10 倍**-GPIO pin</span><span class="sxs-lookup"><span data-stu-id="6b510-112">**10x** - GPIO pins</span></span>
* <span data-ttu-id="6b510-113">**2x** -串行 UARTs</span><span class="sxs-lookup"><span data-stu-id="6b510-113">**2x** - Serial UARTs</span></span>
* <span data-ttu-id="6b510-114">**1x** -SPI 总线</span><span class="sxs-lookup"><span data-stu-id="6b510-114">**1x** - SPI bus</span></span>
* <span data-ttu-id="6b510-115">**1x** -I2C 总线</span><span class="sxs-lookup"><span data-stu-id="6b510-115">**1x** - I2C bus</span></span>
* <span data-ttu-id="6b510-116">**1x** -5v 电源</span><span class="sxs-lookup"><span data-stu-id="6b510-116">**1x** - 5V power pin</span></span>
* <span data-ttu-id="6b510-117">**1x** -3.3 v 电源固定</span><span class="sxs-lookup"><span data-stu-id="6b510-117">**1x** - 3.3V power pin</span></span>
* <span data-ttu-id="6b510-118">**2x** -地面针脚</span><span class="sxs-lookup"><span data-stu-id="6b510-118">**2x** - Ground pins</span></span>

<span data-ttu-id="6b510-119">MinnowBoard Max 在所有 IO 引脚上使用 3.3 V 逻辑级别。</span><span class="sxs-lookup"><span data-stu-id="6b510-119">The MinnowBoard Max uses 3.3V logic levels on all IO pins.</span></span> <span data-ttu-id="6b510-120">此外，所有针脚都由[TXS0104E](http://www.ti.com/product/txs0104e) level shifters 缓冲，但电源和接地引脚除外。</span><span class="sxs-lookup"><span data-stu-id="6b510-120">In addition all the pins are buffered by [TXS0104E](http://www.ti.com/product/txs0104e) level shifters, with the exception of power and ground pins.</span></span>
<span data-ttu-id="6b510-121">这些级别的 shifters 显示为具有 10K&#x2126; 电阻式的开放收集器输出 **，而无论 IO 设置为输入还是输出，都将显示该下拉。**</span><span class="sxs-lookup"><span data-stu-id="6b510-121">These level shifters appear as open collector outputs with a **10K&#x2126; resistive pull-up, and the pull-up is present regardless of whether the IO is set to input or output.**</span></span>
 
<span data-ttu-id="6b510-122">级别 shifters 的开放收集器特性意味着 pin 可以强输出 "0"，但只会有弱输出 "1"。</span><span class="sxs-lookup"><span data-stu-id="6b510-122">The open-collector nature of the level shifters means is that the pins can output a '0' strongly, but only weakly output a '1'.</span></span> <span data-ttu-id="6b510-123">在附加从引脚中抽取电流 (例如 LED) 的设备时，必须记住这一点。</span><span class="sxs-lookup"><span data-stu-id="6b510-123">This is important to keep in mind when attaching devices which draw current from the pins (such as an LED).</span></span> <span data-ttu-id="6b510-124">请参阅[Blinky 示例](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)，了解如何正确地将 LED MinnowBoard 最大。</span><span class="sxs-lookup"><span data-stu-id="6b510-124">See the [Blinky Sample](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) for the correct way to interface an LED to the MinnowBoard Max.</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="6b510-125">GPIO Pin</span><span class="sxs-lookup"><span data-stu-id="6b510-125">GPIO Pins</span></span>

<span data-ttu-id="6b510-126">以下 GPIO pin 可通过 Api 访问：</span><span class="sxs-lookup"><span data-stu-id="6b510-126">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="6b510-127">GPIO#</span><span class="sxs-lookup"><span data-stu-id="6b510-127">GPIO#</span></span> | <span data-ttu-id="6b510-128">标头 Pin</span><span class="sxs-lookup"><span data-stu-id="6b510-128">Header Pin</span></span>         |
> |-------|--------------------|
> | <span data-ttu-id="6b510-129">0</span><span class="sxs-lookup"><span data-stu-id="6b510-129">0</span></span>     | <span data-ttu-id="6b510-130">21</span><span class="sxs-lookup"><span data-stu-id="6b510-130">21</span></span>                 |
> | <span data-ttu-id="6b510-131">1</span><span class="sxs-lookup"><span data-stu-id="6b510-131">1</span></span>     | <span data-ttu-id="6b510-132">23</span><span class="sxs-lookup"><span data-stu-id="6b510-132">23</span></span>                 |
> | <span data-ttu-id="6b510-133">2</span><span class="sxs-lookup"><span data-stu-id="6b510-133">2</span></span>     | <span data-ttu-id="6b510-134">25</span><span class="sxs-lookup"><span data-stu-id="6b510-134">25</span></span>                 |
> | <span data-ttu-id="6b510-135">3</span><span class="sxs-lookup"><span data-stu-id="6b510-135">3</span></span>     | <span data-ttu-id="6b510-136">14</span><span class="sxs-lookup"><span data-stu-id="6b510-136">14</span></span>                 |
> | <span data-ttu-id="6b510-137">4</span><span class="sxs-lookup"><span data-stu-id="6b510-137">4</span></span>     | <span data-ttu-id="6b510-138">16</span><span class="sxs-lookup"><span data-stu-id="6b510-138">16</span></span>                 |
> | <span data-ttu-id="6b510-139">5</span><span class="sxs-lookup"><span data-stu-id="6b510-139">5</span></span>     | <span data-ttu-id="6b510-140">18</span><span class="sxs-lookup"><span data-stu-id="6b510-140">18</span></span>                 |
> | <span data-ttu-id="6b510-141">6</span><span class="sxs-lookup"><span data-stu-id="6b510-141">6</span></span>     | <span data-ttu-id="6b510-142">20</span><span class="sxs-lookup"><span data-stu-id="6b510-142">20</span></span>                 |
> | <span data-ttu-id="6b510-143">7</span><span class="sxs-lookup"><span data-stu-id="6b510-143">7</span></span>     | <span data-ttu-id="6b510-144">22</span><span class="sxs-lookup"><span data-stu-id="6b510-144">22</span></span>                 |
> | <span data-ttu-id="6b510-145">8</span><span class="sxs-lookup"><span data-stu-id="6b510-145">8</span></span>     | <span data-ttu-id="6b510-146">24</span><span class="sxs-lookup"><span data-stu-id="6b510-146">24</span></span>                 |
> | <span data-ttu-id="6b510-147">9</span><span class="sxs-lookup"><span data-stu-id="6b510-147">9</span></span>     | <span data-ttu-id="6b510-148">26</span><span class="sxs-lookup"><span data-stu-id="6b510-148">26</span></span>                 |

<span data-ttu-id="6b510-149">**注意：** 对于 BIOS， **Gpio 4**和**gpio 5**被 MinnowBoard Max 用作启动配置的 pin。</span><span class="sxs-lookup"><span data-stu-id="6b510-149">**Note:** **GPIO 4** and **GPIO 5** are used by the MinnowBoard Max as bootstrap configuration pins for the BIOS.</span></span>
<span data-ttu-id="6b510-150">请确保在启动过程中连接的设备不会驱动这些 GPIO，因为这样可能会阻止 MBM 启动。</span><span class="sxs-lookup"><span data-stu-id="6b510-150">Make sure that attached devices do not drive these GPIO low during boot, as this could prevent the MBM from booting.</span></span>
<span data-ttu-id="6b510-151">MBM 在 BIOS 之后启动后，可以正常使用这些 GPIO。</span><span class="sxs-lookup"><span data-stu-id="6b510-151">After the MBM has booted past the BIOS, these GPIO can be used normally.</span></span>
     
## <a name="gpio-sample"></a><span data-ttu-id="6b510-152">GPIO 示例</span><span class="sxs-lookup"><span data-stu-id="6b510-152">GPIO Sample</span></span>

<span data-ttu-id="6b510-153">例如，以下代码将**GPIO 5**打开为输出，并在 pin 上写入数字 "**1**"：</span><span class="sxs-lookup"><span data-stu-id="6b510-153">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>
         
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

## <a name="serial-uart"></a><span data-ttu-id="6b510-154">串行 UART</span><span class="sxs-lookup"><span data-stu-id="6b510-154">Serial UART</span></span>

<span data-ttu-id="6b510-155">MBM 上提供了两个串行 UARTS： **UART1**和**UART2**</span><span class="sxs-lookup"><span data-stu-id="6b510-155">There are two Serial UARTS available on the MBM: **UART1** and **UART2**</span></span>

<span data-ttu-id="6b510-156">**UART1**具有标准的**UART1 TX**和**UART1 RX**线路，以及流控制信号**UART1 CTS**和**UART1 RTS**。</span><span class="sxs-lookup"><span data-stu-id="6b510-156">**UART1** has the standard **UART1 TX** and **UART1 RX** lines, along with flow control signals **UART1 CTS** and **UART1 RTS**.</span></span>

* <span data-ttu-id="6b510-157">Pin 6- **UART1 TX**</span><span class="sxs-lookup"><span data-stu-id="6b510-157">Pin 6  - **UART1 TX**</span></span>
* <span data-ttu-id="6b510-158">Pin 8- **UART1 RX**</span><span class="sxs-lookup"><span data-stu-id="6b510-158">Pin 8  - **UART1 RX**</span></span>
* <span data-ttu-id="6b510-159">Pin 10- **UART1 CTS**</span><span class="sxs-lookup"><span data-stu-id="6b510-159">Pin 10 - **UART1 CTS**</span></span>
* <span data-ttu-id="6b510-160">Pin 12- **UART1 RTS**</span><span class="sxs-lookup"><span data-stu-id="6b510-160">Pin 12 - **UART1 RTS**</span></span>

<span data-ttu-id="6b510-161">UART1 在版本10240中不起作用。</span><span class="sxs-lookup"><span data-stu-id="6b510-161">UART1 is not working as of build 10240.</span></span> <span data-ttu-id="6b510-162">请使用 UART2 或 USB 串行转换器。</span><span class="sxs-lookup"><span data-stu-id="6b510-162">Please use UART2 or a USB-Serial converter.</span></span>

<span data-ttu-id="6b510-163">**UART2**仅包括**UART2 TX**和**UART2 RX**行。</span><span class="sxs-lookup"><span data-stu-id="6b510-163">**UART2** includes just the **UART2 TX** and **UART2 RX** lines.</span></span>

* <span data-ttu-id="6b510-164">固定 17- **UART2 TX**</span><span class="sxs-lookup"><span data-stu-id="6b510-164">Pin 17  - **UART2 TX**</span></span>
* <span data-ttu-id="6b510-165">Pin 19- **UART2 RX**</span><span class="sxs-lookup"><span data-stu-id="6b510-165">Pin 19  - **UART2 RX**</span></span>

<span data-ttu-id="6b510-166">UART2 不支持流控制，因此访问 SerialDevice 的以下属性可能会导致引发异常：</span><span class="sxs-lookup"><span data-stu-id="6b510-166">UART2 does not support flow control, so accessing the following properties of SerialDevice can result in an exception being thrown:</span></span>

 * <span data-ttu-id="6b510-167">BreakSignalState</span><span class="sxs-lookup"><span data-stu-id="6b510-167">BreakSignalState</span></span>
 * <span data-ttu-id="6b510-168">IsDataTerminalReadyEnabled</span><span class="sxs-lookup"><span data-stu-id="6b510-168">IsDataTerminalReadyEnabled</span></span>
 * <span data-ttu-id="6b510-169">IsRequestToSendEnabled</span><span class="sxs-lookup"><span data-stu-id="6b510-169">IsRequestToSendEnabled</span></span>
 * <span data-ttu-id="6b510-170">仅握手 SerialHandshake 受支持</span><span class="sxs-lookup"><span data-stu-id="6b510-170">Handshake - only SerialHandshake.None is supported</span></span>

<span data-ttu-id="6b510-171">下面的示例初始化**UART2**并执行写操作，后跟读取：</span><span class="sxs-lookup"><span data-stu-id="6b510-171">The example below initializes **UART2** and performs a write followed by a read:</span></span>

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

<span data-ttu-id="6b510-172">请注意，必须将以下功能添加到 UWP 项目中的**appxmanifest.xml**文件，才能运行串行 UART 代码：</span><span class="sxs-lookup"><span data-stu-id="6b510-172">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="6b510-173">Visual Studio 2017 在清单设计器中有一个已知 bug， (用于 appxmanifest.xml 文件的可视化编辑器) 会影响 serialcommunication 功能。</span><span class="sxs-lookup"><span data-stu-id="6b510-173">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="6b510-174">如果你的 appxmanifest.xml 添加 serialcommunication 功能，则通过设计器修改 appxmanifest.xml 将损坏 appxmanifest.xml (设备 xml 子级将丢失) 。</span><span class="sxs-lookup"><span data-stu-id="6b510-174">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="6b510-175">若要解决此问题，请右键单击 appxmanifest.xml，然后从上下文菜单中选择 "查看代码"，手动编辑 appxmanifest.xml。</span><span class="sxs-lookup"><span data-stu-id="6b510-175">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="6b510-176">I2C 总线</span><span class="sxs-lookup"><span data-stu-id="6b510-176">I2C Bus</span></span>

<span data-ttu-id="6b510-177">让我们看看此设备上提供的 I2C 总线。</span><span class="sxs-lookup"><span data-stu-id="6b510-177">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="6b510-178">I2C 概述</span><span class="sxs-lookup"><span data-stu-id="6b510-178">I2C Overview</span></span>

<span data-ttu-id="6b510-179">Pin 标头上有一个 I2C 控制器**I2C5** ，其中包含两行**SDA**和**SCL**。</span><span class="sxs-lookup"><span data-stu-id="6b510-179">There is one I2C controller **I2C5** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="6b510-180">10K&#x2126; 这些线路上已存在内部拉取电阻。</span><span class="sxs-lookup"><span data-stu-id="6b510-180">10K&#x2126; internal pull-up resistors are already present on these lines.</span></span>

* <span data-ttu-id="6b510-181">Pin 15- **I2C5 SDA**</span><span class="sxs-lookup"><span data-stu-id="6b510-181">Pin 15 - **I2C5 SDA**</span></span>
* <span data-ttu-id="6b510-182">Pin 13- **I2C5 SCL**</span><span class="sxs-lookup"><span data-stu-id="6b510-182">Pin 13 - **I2C5 SCL**</span></span>

### <a name="i2c-sample"></a><span data-ttu-id="6b510-183">I2C 示例</span><span class="sxs-lookup"><span data-stu-id="6b510-183">I2C Sample</span></span>

<span data-ttu-id="6b510-184">下面的示例使用 address **0x40**初始化**I2C5**并将数据写入 I2C 设备：</span><span class="sxs-lookup"><span data-stu-id="6b510-184">The example below initializes **I2C5** and writes data to an I2C device with address **0x40**:</span></span>

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

### <a name="i2c-issues"></a><span data-ttu-id="6b510-185">I2C 问题</span><span class="sxs-lookup"><span data-stu-id="6b510-185">I2C Issues</span></span>

<span data-ttu-id="6b510-186">MinnowBoard Max 具有与 I2C 总线相关的已知问题，导致某些 I2C 设备发生通信问题。</span><span class="sxs-lookup"><span data-stu-id="6b510-186">The MinnowBoard Max has a known issue with the I2C bus which causes communication problems with certain I2C devices.</span></span> <span data-ttu-id="6b510-187">通常，I2C 设备会在总线请求期间确认其地址。</span><span class="sxs-lookup"><span data-stu-id="6b510-187">Normally, an I2C device will acknowledge its address during a bus request.</span></span>
<span data-ttu-id="6b510-188">但是，在某些情况下，此确认无法在 shifters 到 MBM 的情况下向后传播，因此 CPU 认为设备没有响应并取消总线事务。</span><span class="sxs-lookup"><span data-stu-id="6b510-188">However, under certain conditions this acknowledge fails to propagate back through the level shifters to the MBM, and as a result the CPU thinks the device did not respond and cancels the bus transaction.</span></span>
<span data-ttu-id="6b510-189">此问题似乎与 IO 引脚上的[TXS0104E](http://www.ti.com/product/txs0104e) level shifters 相关，这会由于线路上出现电压峰值而提前触发。</span><span class="sxs-lookup"><span data-stu-id="6b510-189">The issue seems to be related to the [TXS0104E](http://www.ti.com/product/txs0104e) level shifters on the IO pins, which can trigger prematurely due to voltage spikes on the line.</span></span>
<span data-ttu-id="6b510-190">当前的解决方法是使用 I2C SCK line 在系列中插入100欧姆电阻器，这有助于抑制峰值。</span><span class="sxs-lookup"><span data-stu-id="6b510-190">The current workaround is to insert a 100 ohm resistor in series with the I2C SCK line, which helps suppress spikes.</span></span> <span data-ttu-id="6b510-191">并非所有设备都受影响，因此，仅当遇到总线响应问题时才需要此解决方法。</span><span class="sxs-lookup"><span data-stu-id="6b510-191">Not all devices are affected, so this workaround is only required if you are having trouble getting a bus response.</span></span> <span data-ttu-id="6b510-192">已知需要此解决方法的一个设备是 HTU21D。</span><span class="sxs-lookup"><span data-stu-id="6b510-192">One device that is known to require this workaround is the HTU21D.</span></span>

## <a name="spi-bus"></a><span data-ttu-id="6b510-193">SPI 总线</span><span class="sxs-lookup"><span data-stu-id="6b510-193">SPI Bus</span></span>

<span data-ttu-id="6b510-194">让我们看看此设备上可用的 SPI 总线。</span><span class="sxs-lookup"><span data-stu-id="6b510-194">Let's look at the SPI bus available on this device.</span></span>

### <a name="spi-overview"></a><span data-ttu-id="6b510-195">SPI 概述</span><span class="sxs-lookup"><span data-stu-id="6b510-195">SPI Overview</span></span>

<span data-ttu-id="6b510-196">MBM 上提供了一个 SPI 控制器**SPI0** ：</span><span class="sxs-lookup"><span data-stu-id="6b510-196">There is one SPI controller **SPI0** available on the MBM:</span></span>

* <span data-ttu-id="6b510-197">Pin 9- **SPI0 MOSI**</span><span class="sxs-lookup"><span data-stu-id="6b510-197">Pin 9 - **SPI0 MOSI**</span></span>
* <span data-ttu-id="6b510-198">引脚 7- **SPI0 MISO**</span><span class="sxs-lookup"><span data-stu-id="6b510-198">Pin 7 - **SPI0 MISO**</span></span>
* <span data-ttu-id="6b510-199">引脚 11- **SPI0 SCLK**</span><span class="sxs-lookup"><span data-stu-id="6b510-199">Pin 11 - **SPI0 SCLK**</span></span>
* <span data-ttu-id="6b510-200">Pin 5- **SPI0 CS0**</span><span class="sxs-lookup"><span data-stu-id="6b510-200">Pin 5 - **SPI0 CS0**</span></span>


### <a name="spi-sample"></a><span data-ttu-id="6b510-201">SPI 示例</span><span class="sxs-lookup"><span data-stu-id="6b510-201">SPI Sample</span></span>

<span data-ttu-id="6b510-202">下面显示了有关如何在总线上执行 SPI 写入的示例**SPI0** ：</span><span class="sxs-lookup"><span data-stu-id="6b510-202">An example on how to perform a SPI write on bus **SPI0** is shown below:</span></span>

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

