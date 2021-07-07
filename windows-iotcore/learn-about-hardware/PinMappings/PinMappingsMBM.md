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
# <a name="minnowboard-max-pin-mappings"></a><span data-ttu-id="0975e-106">MinnowBoard 最大引脚映射</span><span class="sxs-lookup"><span data-stu-id="0975e-106">MinnowBoard Max Pin Mappings</span></span>

> [!NOTE] 
> <span data-ttu-id="0975e-107">若要将此引脚映射与较新版本的 Minnowboard 进行比较，请访问此处 [的文档](https://minnowboard.org/minnowboard-turbot/documentation)。</span><span class="sxs-lookup"><span data-stu-id="0975e-107">To compare this pin mapping to newer versions of the Minnowboard, please visit documentation [here](https://minnowboard.org/minnowboard-turbot/documentation).</span></span>

## <a name="overview"></a><span data-ttu-id="0975e-108">概述</span><span class="sxs-lookup"><span data-stu-id="0975e-108">Overview</span></span>

![MinnowBoard 最大引脚标头](../../media/PinMappingsMBM/MBM_Pinout.png)

<span data-ttu-id="0975e-110">MinnowBoard Max 的硬件接口通过板上的 26 引脚标头 **JP1** 公开。</span><span class="sxs-lookup"><span data-stu-id="0975e-110">Hardware interfaces for the MinnowBoard Max are exposed through the 26-pin header **JP1** on the board.</span></span> <span data-ttu-id="0975e-111">功能包括：</span><span class="sxs-lookup"><span data-stu-id="0975e-111">Functionality includes:</span></span>

* <span data-ttu-id="0975e-112">**10x** - GPIO 引脚</span><span class="sxs-lookup"><span data-stu-id="0975e-112">**10x** - GPIO pins</span></span>
* <span data-ttu-id="0975e-113">**2x** - 串行 UART</span><span class="sxs-lookup"><span data-stu-id="0975e-113">**2x** - Serial UARTs</span></span>
* <span data-ttu-id="0975e-114">**1x** - SPI 总线</span><span class="sxs-lookup"><span data-stu-id="0975e-114">**1x** - SPI bus</span></span>
* <span data-ttu-id="0975e-115">**1x** - I2C 总线</span><span class="sxs-lookup"><span data-stu-id="0975e-115">**1x** - I2C bus</span></span>
* <span data-ttu-id="0975e-116">**1x** - 5V 电源引脚</span><span class="sxs-lookup"><span data-stu-id="0975e-116">**1x** - 5V power pin</span></span>
* <span data-ttu-id="0975e-117">**1x** - 3.3V 电源引脚</span><span class="sxs-lookup"><span data-stu-id="0975e-117">**1x** - 3.3V power pin</span></span>
* <span data-ttu-id="0975e-118">**2x** - 地引脚</span><span class="sxs-lookup"><span data-stu-id="0975e-118">**2x** - Ground pins</span></span>

<span data-ttu-id="0975e-119">MinnowBoard Max 在所有 IO 引脚上使用 3.3V 逻辑级别。</span><span class="sxs-lookup"><span data-stu-id="0975e-119">The MinnowBoard Max uses 3.3V logic levels on all IO pins.</span></span> <span data-ttu-id="0975e-120">此外 [，TXS0104E](http://www.ti.com/product/txs0104e) 级别移位器缓冲所有引脚，电源和地引脚除外。</span><span class="sxs-lookup"><span data-stu-id="0975e-120">In addition all the pins are buffered by [TXS0104E](http://www.ti.com/product/txs0104e) level shifters, with the exception of power and ground pins.</span></span>
<span data-ttu-id="0975e-121">这些级别移位器显示为具有 **10K**&#x2126;的打开收集器输出，并且无论 IO 设置为输入还是输出，都会存在下拉。</span><span class="sxs-lookup"><span data-stu-id="0975e-121">These level shifters appear as open collector outputs with a **10K&#x2126; resistive pull-up, and the pull-up is present regardless of whether the IO is set to input or output.**</span></span>
 
<span data-ttu-id="0975e-122">水平移位器的开放收集器性质意味着引脚可以强输出"0"，但只能弱输出"1"。</span><span class="sxs-lookup"><span data-stu-id="0975e-122">The open-collector nature of the level shifters means is that the pins can output a '0' strongly, but only weakly output a '1'.</span></span> <span data-ttu-id="0975e-123">在附加设备时，必须记住这一点，这些设备从引脚（如 LED (）) 。</span><span class="sxs-lookup"><span data-stu-id="0975e-123">This is important to keep in mind when attaching devices which draw current from the pins (such as an LED).</span></span> <span data-ttu-id="0975e-124">有关将 LED 与 MinnowBoard Max 连接的正确方法，请参阅 [Blinky](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) 示例。</span><span class="sxs-lookup"><span data-stu-id="0975e-124">See the [Blinky Sample](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) for the correct way to interface an LED to the MinnowBoard Max.</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="0975e-125">GPIO 引脚</span><span class="sxs-lookup"><span data-stu-id="0975e-125">GPIO Pins</span></span>

<span data-ttu-id="0975e-126">可通过 API 访问以下 GPIO 引脚：</span><span class="sxs-lookup"><span data-stu-id="0975e-126">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="0975e-127">GPIO#</span><span class="sxs-lookup"><span data-stu-id="0975e-127">GPIO#</span></span> | <span data-ttu-id="0975e-128">标头引脚</span><span class="sxs-lookup"><span data-stu-id="0975e-128">Header Pin</span></span>         |
> |-------|--------------------|
> | <span data-ttu-id="0975e-129">0</span><span class="sxs-lookup"><span data-stu-id="0975e-129">0</span></span>     | <span data-ttu-id="0975e-130">21</span><span class="sxs-lookup"><span data-stu-id="0975e-130">21</span></span>                 |
> | <span data-ttu-id="0975e-131">1</span><span class="sxs-lookup"><span data-stu-id="0975e-131">1</span></span>     | <span data-ttu-id="0975e-132">23</span><span class="sxs-lookup"><span data-stu-id="0975e-132">23</span></span>                 |
> | <span data-ttu-id="0975e-133">2</span><span class="sxs-lookup"><span data-stu-id="0975e-133">2</span></span>     | <span data-ttu-id="0975e-134">25</span><span class="sxs-lookup"><span data-stu-id="0975e-134">25</span></span>                 |
> | <span data-ttu-id="0975e-135">3</span><span class="sxs-lookup"><span data-stu-id="0975e-135">3</span></span>     | <span data-ttu-id="0975e-136">14</span><span class="sxs-lookup"><span data-stu-id="0975e-136">14</span></span>                 |
> | <span data-ttu-id="0975e-137">4</span><span class="sxs-lookup"><span data-stu-id="0975e-137">4</span></span>     | <span data-ttu-id="0975e-138">16</span><span class="sxs-lookup"><span data-stu-id="0975e-138">16</span></span>                 |
> | <span data-ttu-id="0975e-139">5</span><span class="sxs-lookup"><span data-stu-id="0975e-139">5</span></span>     | <span data-ttu-id="0975e-140">18</span><span class="sxs-lookup"><span data-stu-id="0975e-140">18</span></span>                 |
> | <span data-ttu-id="0975e-141">6</span><span class="sxs-lookup"><span data-stu-id="0975e-141">6</span></span>     | <span data-ttu-id="0975e-142">20</span><span class="sxs-lookup"><span data-stu-id="0975e-142">20</span></span>                 |
> | <span data-ttu-id="0975e-143">7</span><span class="sxs-lookup"><span data-stu-id="0975e-143">7</span></span>     | <span data-ttu-id="0975e-144">22</span><span class="sxs-lookup"><span data-stu-id="0975e-144">22</span></span>                 |
> | <span data-ttu-id="0975e-145">8</span><span class="sxs-lookup"><span data-stu-id="0975e-145">8</span></span>     | <span data-ttu-id="0975e-146">24</span><span class="sxs-lookup"><span data-stu-id="0975e-146">24</span></span>                 |
> | <span data-ttu-id="0975e-147">9</span><span class="sxs-lookup"><span data-stu-id="0975e-147">9</span></span>     | <span data-ttu-id="0975e-148">26</span><span class="sxs-lookup"><span data-stu-id="0975e-148">26</span></span>                 |

<span data-ttu-id="0975e-149">**注意**：MINnowBoard Max 使用 **GPIO 4** 和 **GPIO 5** 作为 BIOS 的启动配置引脚。</span><span class="sxs-lookup"><span data-stu-id="0975e-149">**Note:** **GPIO 4** and **GPIO 5** are used by the MinnowBoard Max as bootstrap configuration pins for the BIOS.</span></span>
<span data-ttu-id="0975e-150">请确保附加的设备在启动期间不会使这些 GPIO 较低，因为这样做可能会阻止 MBM 启动。</span><span class="sxs-lookup"><span data-stu-id="0975e-150">Make sure that attached devices do not drive these GPIO low during boot, as this could prevent the MBM from booting.</span></span>
<span data-ttu-id="0975e-151">在 MBM 启动通过 BIOS 后，可以正常使用这些 GPIO。</span><span class="sxs-lookup"><span data-stu-id="0975e-151">After the MBM has booted past the BIOS, these GPIO can be used normally.</span></span>
     
## <a name="gpio-sample"></a><span data-ttu-id="0975e-152">GPIO 示例</span><span class="sxs-lookup"><span data-stu-id="0975e-152">GPIO Sample</span></span>

<span data-ttu-id="0975e-153">例如，以下代码将 **GPIO 5** 作为输出打开，在引脚上写出数字 **"1"：**</span><span class="sxs-lookup"><span data-stu-id="0975e-153">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>
         
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

## <a name="serial-uart"></a><span data-ttu-id="0975e-154">串行 UART</span><span class="sxs-lookup"><span data-stu-id="0975e-154">Serial UART</span></span>

<span data-ttu-id="0975e-155">MBM 上提供两个串行 **UARTS：UART1** 和 **UART2**</span><span class="sxs-lookup"><span data-stu-id="0975e-155">There are two Serial UARTS available on the MBM: **UART1** and **UART2**</span></span>

<span data-ttu-id="0975e-156">**UART1** 具有标准 **UART1 TX** 和 **UART1 RX** 行，以及流控制信号 **UART1 CTS** 和 **UART1 RTS。**</span><span class="sxs-lookup"><span data-stu-id="0975e-156">**UART1** has the standard **UART1 TX** and **UART1 RX** lines, along with flow control signals **UART1 CTS** and **UART1 RTS**.</span></span>

* <span data-ttu-id="0975e-157">引脚 6 - **UART1 TX**</span><span class="sxs-lookup"><span data-stu-id="0975e-157">Pin 6  - **UART1 TX**</span></span>
* <span data-ttu-id="0975e-158">引脚 8 - **UART1 RX**</span><span class="sxs-lookup"><span data-stu-id="0975e-158">Pin 8  - **UART1 RX**</span></span>
* <span data-ttu-id="0975e-159">引脚 10 - **UART1 CTS**</span><span class="sxs-lookup"><span data-stu-id="0975e-159">Pin 10 - **UART1 CTS**</span></span>
* <span data-ttu-id="0975e-160">引脚 12 - **UART1 RTS**</span><span class="sxs-lookup"><span data-stu-id="0975e-160">Pin 12 - **UART1 RTS**</span></span>

<span data-ttu-id="0975e-161">从内部版本 10240 开始，UART1 不工作。</span><span class="sxs-lookup"><span data-stu-id="0975e-161">UART1 is not working as of build 10240.</span></span> <span data-ttu-id="0975e-162">请使用 UART2 或 USB-Serial转换器。</span><span class="sxs-lookup"><span data-stu-id="0975e-162">Please use UART2 or a USB-Serial converter.</span></span>

<span data-ttu-id="0975e-163">**UART2** 仅包括 **UART2 TX 和** **UART2 RX** 行。</span><span class="sxs-lookup"><span data-stu-id="0975e-163">**UART2** includes just the **UART2 TX** and **UART2 RX** lines.</span></span>

* <span data-ttu-id="0975e-164">引脚 17 - **UART2 TX**</span><span class="sxs-lookup"><span data-stu-id="0975e-164">Pin 17  - **UART2 TX**</span></span>
* <span data-ttu-id="0975e-165">引脚 19 - **UART2 RX**</span><span class="sxs-lookup"><span data-stu-id="0975e-165">Pin 19  - **UART2 RX**</span></span>

<span data-ttu-id="0975e-166">UART2 不支持流控制，因此访问 SerialDevice 的以下属性可能会导致引发异常：</span><span class="sxs-lookup"><span data-stu-id="0975e-166">UART2 does not support flow control, so accessing the following properties of SerialDevice can result in an exception being thrown:</span></span>

 * <span data-ttu-id="0975e-167">BreakSignalState</span><span class="sxs-lookup"><span data-stu-id="0975e-167">BreakSignalState</span></span>
 * <span data-ttu-id="0975e-168">IsDataTerminalReadyEnabled</span><span class="sxs-lookup"><span data-stu-id="0975e-168">IsDataTerminalReadyEnabled</span></span>
 * <span data-ttu-id="0975e-169">IsRequestToSendEnabled</span><span class="sxs-lookup"><span data-stu-id="0975e-169">IsRequestToSendEnabled</span></span>
 * <span data-ttu-id="0975e-170">握手 - 仅支持 SerialHandshake.None</span><span class="sxs-lookup"><span data-stu-id="0975e-170">Handshake - only SerialHandshake.None is supported</span></span>

<span data-ttu-id="0975e-171">下面的示例初始化 **UART2 并执行** 写入，然后执行读取：</span><span class="sxs-lookup"><span data-stu-id="0975e-171">The example below initializes **UART2** and performs a write followed by a read:</span></span>

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

<span data-ttu-id="0975e-172">请注意，必须将以下功能添加到 UWP 项目中 **的 Package.appxmanifest** 文件，以运行串行 UART 代码：</span><span class="sxs-lookup"><span data-stu-id="0975e-172">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="0975e-173">Visual Studio 2017 在清单设计器中 (appxmanifest 文件的可视化编辑器中) 影响串行通信功能。</span><span class="sxs-lookup"><span data-stu-id="0975e-173">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="0975e-174">如果 appxmanifest 添加了串行通信功能，则使用设计器修改 appxmanifest 将损坏 appxmanifest (设备 xml 子级将丢失) 。</span><span class="sxs-lookup"><span data-stu-id="0975e-174">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="0975e-175">可以通过手动编辑 appxmanifest 来解决此问题，方法是右键单击 appxmanifest，然后从上下文菜单中选择"查看代码"。</span><span class="sxs-lookup"><span data-stu-id="0975e-175">You can work around this problem by hand editing the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="0975e-176">I2C 总线</span><span class="sxs-lookup"><span data-stu-id="0975e-176">I2C Bus</span></span>

<span data-ttu-id="0975e-177">让我们看看此设备上提供的 I2C 总线。</span><span class="sxs-lookup"><span data-stu-id="0975e-177">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="0975e-178">I2C 概述</span><span class="sxs-lookup"><span data-stu-id="0975e-178">I2C Overview</span></span>

<span data-ttu-id="0975e-179">在引脚标头上公开了一个 **I2C 控制器 I2C5，** 包含两行 **SDA 和** **SCL**。</span><span class="sxs-lookup"><span data-stu-id="0975e-179">There is one I2C controller **I2C5** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="0975e-180">这些&#x2126;已有 10，000 个内部向上拉取器。</span><span class="sxs-lookup"><span data-stu-id="0975e-180">10K&#x2126; internal pull-up resistors are already present on these lines.</span></span>

* <span data-ttu-id="0975e-181">引脚 15 - **I2C5 SDA**</span><span class="sxs-lookup"><span data-stu-id="0975e-181">Pin 15 - **I2C5 SDA**</span></span>
* <span data-ttu-id="0975e-182">引脚 13 - **I2C5 SCL**</span><span class="sxs-lookup"><span data-stu-id="0975e-182">Pin 13 - **I2C5 SCL**</span></span>

### <a name="i2c-sample"></a><span data-ttu-id="0975e-183">I2C 示例</span><span class="sxs-lookup"><span data-stu-id="0975e-183">I2C Sample</span></span>

<span data-ttu-id="0975e-184">以下示例初始化 **I2C5，将数据** 写入地址为 的 I2C **0x40：**</span><span class="sxs-lookup"><span data-stu-id="0975e-184">The example below initializes **I2C5** and writes data to an I2C device with address **0x40**:</span></span>

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

### <a name="i2c-issues"></a><span data-ttu-id="0975e-185">I2C 问题</span><span class="sxs-lookup"><span data-stu-id="0975e-185">I2C Issues</span></span>

<span data-ttu-id="0975e-186">MinnowBoard Max 具有 I2C 总线的已知问题，这导致某些 I2C 设备的通信问题。</span><span class="sxs-lookup"><span data-stu-id="0975e-186">The MinnowBoard Max has a known issue with the I2C bus, which causes communication problems with certain I2C devices.</span></span> <span data-ttu-id="0975e-187">通常，I2C 设备将在总线请求期间确认其地址。</span><span class="sxs-lookup"><span data-stu-id="0975e-187">Normally, an I2C device will acknowledge its address during a bus request.</span></span>
<span data-ttu-id="0975e-188">但是，在某些情况下，此确认无法通过级别移位器传播回 MBM，因此 CPU 认为设备未响应并取消总线事务。</span><span class="sxs-lookup"><span data-stu-id="0975e-188">However, under certain conditions this acknowledge fails to propagate back through the level shifters to the MBM, and as a result the CPU thinks the device did not respond and cancels the bus transaction.</span></span>
<span data-ttu-id="0975e-189">此问题似乎与 IO 引脚上的 [TXS0104E](http://www.ti.com/product/txs0104e) 级别移位器有关，由于线路上的电压峰值，可能会提前触发。</span><span class="sxs-lookup"><span data-stu-id="0975e-189">The issue seems to be related to the [TXS0104E](http://www.ti.com/product/txs0104e) level shifters on the IO pins, which can trigger prematurely due to voltage spikes on the line.</span></span>
<span data-ttu-id="0975e-190">当前解决方法是，使用 I2C SCK 线在系列中插入 100-ohm 的电流，这有助于抑制峰值。</span><span class="sxs-lookup"><span data-stu-id="0975e-190">The current workaround is to insert a 100-ohm resistor in series with the I2C SCK line, which helps suppress spikes.</span></span> <span data-ttu-id="0975e-191">并非所有设备都受到影响，因此只有在获取总线响应时遇到问题，才需要此解决方法。</span><span class="sxs-lookup"><span data-stu-id="0975e-191">Not all devices are affected, so this workaround is only required if you are having trouble getting a bus response.</span></span> <span data-ttu-id="0975e-192">已知需要此解决方法的设备是 HTU21D。</span><span class="sxs-lookup"><span data-stu-id="0975e-192">One device that is known to require this workaround is the HTU21D.</span></span>

## <a name="spi-bus"></a><span data-ttu-id="0975e-193">SPI 总线</span><span class="sxs-lookup"><span data-stu-id="0975e-193">SPI Bus</span></span>

<span data-ttu-id="0975e-194">让我们看看此设备上提供的 SPI 总线。</span><span class="sxs-lookup"><span data-stu-id="0975e-194">Let's look at the SPI bus available on this device.</span></span>

### <a name="spi-overview"></a><span data-ttu-id="0975e-195">SPI 概述</span><span class="sxs-lookup"><span data-stu-id="0975e-195">SPI Overview</span></span>

<span data-ttu-id="0975e-196">MBM 上提供了一个 SPI 控制器 **SPI0：**</span><span class="sxs-lookup"><span data-stu-id="0975e-196">There is one SPI controller **SPI0** available on the MBM:</span></span>

* <span data-ttu-id="0975e-197">引脚 9 - **SPI0 MOSI**</span><span class="sxs-lookup"><span data-stu-id="0975e-197">Pin 9 - **SPI0 MOSI**</span></span>
* <span data-ttu-id="0975e-198">引脚 7 - **SPI0 MISO**</span><span class="sxs-lookup"><span data-stu-id="0975e-198">Pin 7 - **SPI0 MISO**</span></span>
* <span data-ttu-id="0975e-199">引脚 11 - **SPI0 SCLK**</span><span class="sxs-lookup"><span data-stu-id="0975e-199">Pin 11 - **SPI0 SCLK**</span></span>
* <span data-ttu-id="0975e-200">引脚 5 - **SPI0 CS0**</span><span class="sxs-lookup"><span data-stu-id="0975e-200">Pin 5 - **SPI0 CS0**</span></span>


### <a name="spi-sample"></a><span data-ttu-id="0975e-201">SPI 示例</span><span class="sxs-lookup"><span data-stu-id="0975e-201">SPI Sample</span></span>

<span data-ttu-id="0975e-202">下面显示了有关如何在总线上执行 SPI 写入的示例 **SPI0** ：</span><span class="sxs-lookup"><span data-stu-id="0975e-202">An example on how to perform a SPI write on bus **SPI0** is shown below:</span></span>

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

