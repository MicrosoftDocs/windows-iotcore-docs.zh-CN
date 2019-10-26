---
title: Minnowboard 最大 Pin 映射
ms.date: 08/28/2017
ms.topic: article
description: 了解 Minnowboard Max 的 pin 映射功能。
keywords: windows iot，Minnowboard Max，pin 映射，GPIO
ms.openlocfilehash: c97147357bbe17c13f2e69e9878b2630a6d12097
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72917957"
---
# <a name="minnowboard-max-pin-mappings"></a><span data-ttu-id="75b70-104">MinnowBoard Max 引脚映射</span><span class="sxs-lookup"><span data-stu-id="75b70-104">MinnowBoard Max Pin Mappings</span></span>

> [!NOTE] 
> <span data-ttu-id="75b70-105">若要将此 pin 映射与较新版本的 Minnowboard 进行比较，请访问[此处](https://minnowboard.org/minnowboard-turbot/documentation)的文档。</span><span class="sxs-lookup"><span data-stu-id="75b70-105">To compare this pin mapping to newer versions of the Minnowboard, please visit documentation [here](https://minnowboard.org/minnowboard-turbot/documentation).</span></span>

## <a name="overview"></a><span data-ttu-id="75b70-106">概述</span><span class="sxs-lookup"><span data-stu-id="75b70-106">Overview</span></span>

![MinnowBoard Max 排针](../../media/PinMappingsMBM/MBM_Pinout.png)

<span data-ttu-id="75b70-108">MinnowBoard Max 的硬件接口通过开发板上的 26 排针 **JP1** 公开。</span><span class="sxs-lookup"><span data-stu-id="75b70-108">Hardware interfaces for the MinnowBoard Max are exposed through the 26-pin header **JP1** on the board.</span></span> <span data-ttu-id="75b70-109">功能包括：</span><span class="sxs-lookup"><span data-stu-id="75b70-109">Functionality includes:</span></span>

* <span data-ttu-id="75b70-110">**10x** - GPIO 引脚</span><span class="sxs-lookup"><span data-stu-id="75b70-110">**10x** - GPIO pins</span></span>
* <span data-ttu-id="75b70-111">**2x** - 串行 UART</span><span class="sxs-lookup"><span data-stu-id="75b70-111">**2x** - Serial UARTs</span></span>
* <span data-ttu-id="75b70-112">**1x** - SPI 总线</span><span class="sxs-lookup"><span data-stu-id="75b70-112">**1x** - SPI bus</span></span>
* <span data-ttu-id="75b70-113">**1x** - I2C 总线</span><span class="sxs-lookup"><span data-stu-id="75b70-113">**1x** - I2C bus</span></span>
* <span data-ttu-id="75b70-114">**1x** - 5V 电源引脚</span><span class="sxs-lookup"><span data-stu-id="75b70-114">**1x** - 5V power pin</span></span>
* <span data-ttu-id="75b70-115">**1x** - 3.3V 电源引脚</span><span class="sxs-lookup"><span data-stu-id="75b70-115">**1x** - 3.3V power pin</span></span>
* <span data-ttu-id="75b70-116">**2x** - 接地引脚</span><span class="sxs-lookup"><span data-stu-id="75b70-116">**2x** - Ground pins</span></span>

<span data-ttu-id="75b70-117">MinnowBoard Max 在所有 IO 引脚上使用 3.3 V 逻辑级别。</span><span class="sxs-lookup"><span data-stu-id="75b70-117">The MinnowBoard Max uses 3.3V logic levels on all IO pins.</span></span> <span data-ttu-id="75b70-118">此外所有引脚由 [TXS0104E](http://www.ti.com/product/txs0104e) 电平转换器缓冲，电源和接地引脚除外。</span><span class="sxs-lookup"><span data-stu-id="75b70-118">In addition all the pins are buffered by [TXS0104E](http://www.ti.com/product/txs0104e) level shifters, with the exception of power and ground pins.</span></span>
<span data-ttu-id="75b70-119">这些电平转换器显示为开放收集器输出，并带有 **10K&#x2126; 电阻式上拉，无论 IO 设置为输入还是输出该上拉都存在。**</span><span class="sxs-lookup"><span data-stu-id="75b70-119">These level shifters appear as open collector outputs with a **10K&#x2126; resistive pull-up, and the pull-up is present regardless of whether the IO is set to input or output.**</span></span>
 
<span data-ttu-id="75b70-120">电平转换器的开放收集器性质意味着引脚可以强输出“０”，但只能弱输出“１”。</span><span class="sxs-lookup"><span data-stu-id="75b70-120">The open-collector nature of the level shifters means is that the pins can output a '0' strongly, but only weakly output a '1'.</span></span> <span data-ttu-id="75b70-121">在连接从引脚（例如 LED）消耗电流的设备时记住这一点很重要。</span><span class="sxs-lookup"><span data-stu-id="75b70-121">This is important to keep in mind when attaching devices which draw current from the pins (such as an LED).</span></span> <span data-ttu-id="75b70-122">有关将 LED 接入到 MinnowBoard Max 的正确方法，请参阅 [Blinky 示例](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky)。</span><span class="sxs-lookup"><span data-stu-id="75b70-122">See the [Blinky Sample](https://developer.microsoft.com/en-us/windows/iot/samples/helloblinky) for the correct way to interface an LED to the MinnowBoard Max.</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="75b70-123">GPIO Pin</span><span class="sxs-lookup"><span data-stu-id="75b70-123">GPIO Pins</span></span>

<span data-ttu-id="75b70-124">以下 GPIO 引脚可通过 API 访问：</span><span class="sxs-lookup"><span data-stu-id="75b70-124">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="75b70-125">GPIO#</span><span class="sxs-lookup"><span data-stu-id="75b70-125">GPIO#</span></span> | <span data-ttu-id="75b70-126">排针</span><span class="sxs-lookup"><span data-stu-id="75b70-126">Header Pin</span></span>         |
> |-------|--------------------|
> | <span data-ttu-id="75b70-127">0</span><span class="sxs-lookup"><span data-stu-id="75b70-127">0</span></span>     | <span data-ttu-id="75b70-128">21</span><span class="sxs-lookup"><span data-stu-id="75b70-128">21</span></span>                 |
> | <span data-ttu-id="75b70-129">1</span><span class="sxs-lookup"><span data-stu-id="75b70-129">1</span></span>     | <span data-ttu-id="75b70-130">23</span><span class="sxs-lookup"><span data-stu-id="75b70-130">23</span></span>                 |
> | <span data-ttu-id="75b70-131">2</span><span class="sxs-lookup"><span data-stu-id="75b70-131">2</span></span>     | <span data-ttu-id="75b70-132">25</span><span class="sxs-lookup"><span data-stu-id="75b70-132">25</span></span>                 |
> | <span data-ttu-id="75b70-133">3</span><span class="sxs-lookup"><span data-stu-id="75b70-133">3</span></span>     | <span data-ttu-id="75b70-134">14</span><span class="sxs-lookup"><span data-stu-id="75b70-134">14</span></span>                 |
> | <span data-ttu-id="75b70-135">4</span><span class="sxs-lookup"><span data-stu-id="75b70-135">4</span></span>     | <span data-ttu-id="75b70-136">16</span><span class="sxs-lookup"><span data-stu-id="75b70-136">16</span></span>                 |
> | <span data-ttu-id="75b70-137">5</span><span class="sxs-lookup"><span data-stu-id="75b70-137">5</span></span>     | <span data-ttu-id="75b70-138">18</span><span class="sxs-lookup"><span data-stu-id="75b70-138">18</span></span>                 |
> | <span data-ttu-id="75b70-139">6</span><span class="sxs-lookup"><span data-stu-id="75b70-139">6</span></span>     | <span data-ttu-id="75b70-140">20</span><span class="sxs-lookup"><span data-stu-id="75b70-140">20</span></span>                 |
> | <span data-ttu-id="75b70-141">7</span><span class="sxs-lookup"><span data-stu-id="75b70-141">7</span></span>     | <span data-ttu-id="75b70-142">22</span><span class="sxs-lookup"><span data-stu-id="75b70-142">22</span></span>                 |
> | <span data-ttu-id="75b70-143">8</span><span class="sxs-lookup"><span data-stu-id="75b70-143">8</span></span>     | <span data-ttu-id="75b70-144">24</span><span class="sxs-lookup"><span data-stu-id="75b70-144">24</span></span>                 |
> | <span data-ttu-id="75b70-145">9</span><span class="sxs-lookup"><span data-stu-id="75b70-145">9</span></span>     | <span data-ttu-id="75b70-146">26</span><span class="sxs-lookup"><span data-stu-id="75b70-146">26</span></span>                 |

<span data-ttu-id="75b70-147">**注意：** 对于 BIOS， **Gpio 4**和**gpio 5**被 MinnowBoard Max 用作启动配置的 pin。</span><span class="sxs-lookup"><span data-stu-id="75b70-147">**Note:** **GPIO 4** and **GPIO 5** are used by the MinnowBoard Max as bootstrap configuration pins for the BIOS.</span></span>
<span data-ttu-id="75b70-148">确保连接的设备不会在启动时将 GPIO 电平降低，因为这会阻止 MBM 启动。</span><span class="sxs-lookup"><span data-stu-id="75b70-148">Make sure that attached devices do not drive these GPIO low during boot, as this could prevent the MBM from booting.</span></span>
<span data-ttu-id="75b70-149">在 MBM 晚于 BIOS 启动后，这些 GPIO 可正常使用。</span><span class="sxs-lookup"><span data-stu-id="75b70-149">After the MBM has booted past the BIOS, these GPIO can be used normally.</span></span>
     
## <a name="gpio-sample"></a><span data-ttu-id="75b70-150">GPIO 示例</span><span class="sxs-lookup"><span data-stu-id="75b70-150">GPIO Sample</span></span>

<span data-ttu-id="75b70-151">例如，以下代码将 **GPIO 5** 作为输出打开，并在该引脚上写入数字“**1**”：</span><span class="sxs-lookup"><span data-stu-id="75b70-151">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>
         
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

## <a name="serial-uart"></a><span data-ttu-id="75b70-152">串行 UART</span><span class="sxs-lookup"><span data-stu-id="75b70-152">Serial UART</span></span>

<span data-ttu-id="75b70-153">MBM 上提供两个串行 UART： **UART1** 和 **UART2**</span><span class="sxs-lookup"><span data-stu-id="75b70-153">There are two Serial UARTS available on the MBM: **UART1** and **UART2**</span></span>

<span data-ttu-id="75b70-154">**UART1** 具有标准 **UART1 TX** 和 **UART1 RX** 线，以及流控制信号 **UART1 CTS** 和 **UART1 RTS**。</span><span class="sxs-lookup"><span data-stu-id="75b70-154">**UART1** has the standard **UART1 TX** and **UART1 RX** lines, along with flow control signals **UART1 CTS** and **UART1 RTS**.</span></span>

* <span data-ttu-id="75b70-155">Pin 6- **UART1 TX**</span><span class="sxs-lookup"><span data-stu-id="75b70-155">Pin 6  - **UART1 TX**</span></span>
* <span data-ttu-id="75b70-156">Pin 8- **UART1 RX**</span><span class="sxs-lookup"><span data-stu-id="75b70-156">Pin 8  - **UART1 RX**</span></span>
* <span data-ttu-id="75b70-157">引脚 10- **UART1 CTS**</span><span class="sxs-lookup"><span data-stu-id="75b70-157">Pin 10 - **UART1 CTS**</span></span>
* <span data-ttu-id="75b70-158">引脚 12- **UART1 RTS**</span><span class="sxs-lookup"><span data-stu-id="75b70-158">Pin 12 - **UART1 RTS**</span></span>

<span data-ttu-id="75b70-159">从版本 10240 开始，UART1 不再工作。</span><span class="sxs-lookup"><span data-stu-id="75b70-159">UART1 is not working as of build 10240.</span></span> <span data-ttu-id="75b70-160">请使用 UART2 或 USB 串行转换器。</span><span class="sxs-lookup"><span data-stu-id="75b70-160">Please use UART2 or a USB-Serial converter.</span></span>

<span data-ttu-id="75b70-161">**UART2** 仅包括 **UART2 TX** 和 **UART2 RX** 线。</span><span class="sxs-lookup"><span data-stu-id="75b70-161">**UART2** includes just the **UART2 TX** and **UART2 RX** lines.</span></span>

* <span data-ttu-id="75b70-162">固定 17- **UART2 TX**</span><span class="sxs-lookup"><span data-stu-id="75b70-162">Pin 17  - **UART2 TX**</span></span>
* <span data-ttu-id="75b70-163">Pin 19- **UART2 RX**</span><span class="sxs-lookup"><span data-stu-id="75b70-163">Pin 19  - **UART2 RX**</span></span>

<span data-ttu-id="75b70-164">UART2 不支持流控制，因此访问 SerialDevice 的以下属性可能会导致引发异常：</span><span class="sxs-lookup"><span data-stu-id="75b70-164">UART2 does not support flow control, so accessing the following properties of SerialDevice can result in an exception being thrown:</span></span>

 * <span data-ttu-id="75b70-165">BreakSignalState</span><span class="sxs-lookup"><span data-stu-id="75b70-165">BreakSignalState</span></span>
 * <span data-ttu-id="75b70-166">IsDataTerminalReadyEnabled</span><span class="sxs-lookup"><span data-stu-id="75b70-166">IsDataTerminalReadyEnabled</span></span>
 * <span data-ttu-id="75b70-167">IsRequestToSendEnabled</span><span class="sxs-lookup"><span data-stu-id="75b70-167">IsRequestToSendEnabled</span></span>
 * <span data-ttu-id="75b70-168">握手 - 仅支持 SerialHandshake.None</span><span class="sxs-lookup"><span data-stu-id="75b70-168">Handshake - only SerialHandshake.None is supported</span></span>

<span data-ttu-id="75b70-169">以下示例初始化 **UART2** 并依次执行写入和读取操作：</span><span class="sxs-lookup"><span data-stu-id="75b70-169">The example below initializes **UART2** and performs a write followed by a read:</span></span>

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

<span data-ttu-id="75b70-170">请注意，必须将以下功能添加到 UWP 项目中的 **Package.appxmanifest** 文件，才能运行串行 UART 代码：</span><span class="sxs-lookup"><span data-stu-id="75b70-170">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="75b70-171">Visual Studio 2017 在清单设计器（appxmanifest.xml 文件的可视化编辑器）中有一个已知 bug，该 bug 会影响 serialcommunication 功能。</span><span class="sxs-lookup"><span data-stu-id="75b70-171">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="75b70-172">如果 appxmanifest.xml 添加 serialcommunication 功能，则在设计器中修改 appxmanifest.xml 将损坏 appxmanifest.xml （设备 xml 子级将丢失）。</span><span class="sxs-lookup"><span data-stu-id="75b70-172">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="75b70-173">若要解决此问题，请右键单击 appxmanifest.xml，然后从上下文菜单中选择 "查看代码"，手动编辑 appxmanifest.xml。</span><span class="sxs-lookup"><span data-stu-id="75b70-173">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="75b70-174">I2C 总线</span><span class="sxs-lookup"><span data-stu-id="75b70-174">I2C Bus</span></span>

<span data-ttu-id="75b70-175">让我们看看此设备上提供的 I2C 总线。</span><span class="sxs-lookup"><span data-stu-id="75b70-175">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="75b70-176">I2C 概述</span><span class="sxs-lookup"><span data-stu-id="75b70-176">I2C Overview</span></span>

<span data-ttu-id="75b70-177">排针上公开了一个 I2C 控制器 **I2C5**，带有 **SDA** 和 **SCL** 两条线。</span><span class="sxs-lookup"><span data-stu-id="75b70-177">There is one I2C controller **I2C5** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="75b70-178">10K&#x2126; 内部上拉电阻已存在于这些线上。</span><span class="sxs-lookup"><span data-stu-id="75b70-178">10K&#x2126; internal pull-up resistors are already present on these lines.</span></span>

* <span data-ttu-id="75b70-179">引脚 15 - **I2C5 SDA**</span><span class="sxs-lookup"><span data-stu-id="75b70-179">Pin 15 - **I2C5 SDA**</span></span>
* <span data-ttu-id="75b70-180">引脚 13 - **I2C5 SCL**</span><span class="sxs-lookup"><span data-stu-id="75b70-180">Pin 13 - **I2C5 SCL**</span></span>

### <a name="i2c-sample"></a><span data-ttu-id="75b70-181">I2C 示例</span><span class="sxs-lookup"><span data-stu-id="75b70-181">I2C Sample</span></span>

<span data-ttu-id="75b70-182">以下示例初始化 **I2C5** 并将数据写入带有地址 **0x40** 的 I2C 设备：</span><span class="sxs-lookup"><span data-stu-id="75b70-182">The example below initializes **I2C5** and writes data to an I2C device with address **0x40**:</span></span>

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

### <a name="i2c-issues"></a><span data-ttu-id="75b70-183">I2C 问题</span><span class="sxs-lookup"><span data-stu-id="75b70-183">I2C Issues</span></span>

<span data-ttu-id="75b70-184">MinnowBoard Max 具有已知的 I2C 总线问题，可导致某些 I2C 设备发生通信问题。</span><span class="sxs-lookup"><span data-stu-id="75b70-184">The MinnowBoard Max has a known issue with the I2C bus which causes communication problems with certain I2C devices.</span></span> <span data-ttu-id="75b70-185">通常，I2C 设备将在总线请求期间确认其地址。</span><span class="sxs-lookup"><span data-stu-id="75b70-185">Normally, an I2C device will acknowledge its address during a bus request.</span></span>
<span data-ttu-id="75b70-186">但是，在某些条件下，此确认无法通过电平转换器传播回 MBM，因此 CPU 认为设备未响应并取消总线事务。</span><span class="sxs-lookup"><span data-stu-id="75b70-186">However, under certain conditions this acknowledge fails to propagate back through the level shifters to the MBM, and as a result the CPU thinks the device did not respond and cancels the bus transaction.</span></span>
<span data-ttu-id="75b70-187">该问题似乎与 IO 引脚上 [TXS0104E](http://www.ti.com/product/txs0104e) 水平转换器相关，这可能由于线上的电压尖脉冲而过早触发。</span><span class="sxs-lookup"><span data-stu-id="75b70-187">The issue seems to be related to the [TXS0104E](http://www.ti.com/product/txs0104e) level shifters on the IO pins, which can trigger prematurely due to voltage spikes on the line.</span></span>
<span data-ttu-id="75b70-188">当前的解决方案是插入一个与 I2C SCK 线串联的 100 欧姆电阻，这有助于消除尖脉冲。</span><span class="sxs-lookup"><span data-stu-id="75b70-188">The current workaround is to insert a 100 ohm resistor in series with the I2C SCK line, which helps suppress spikes.</span></span> <span data-ttu-id="75b70-189">并非所有设备都会受影响，因此只在你无法顺利获取总线响应时需要此解决方法。</span><span class="sxs-lookup"><span data-stu-id="75b70-189">Not all devices are affected, so this workaround is only required if you are having trouble getting a bus response.</span></span> <span data-ttu-id="75b70-190">已知需要此解决方案的一台设备是 HTU21D。</span><span class="sxs-lookup"><span data-stu-id="75b70-190">One device that is known to require this workaround is the HTU21D.</span></span>

## <a name="spi-bus"></a><span data-ttu-id="75b70-191">SPI 总线</span><span class="sxs-lookup"><span data-stu-id="75b70-191">SPI Bus</span></span>

<span data-ttu-id="75b70-192">让我们看看此设备上可用的 SPI 总线。</span><span class="sxs-lookup"><span data-stu-id="75b70-192">Let's look at the SPI bus available on this device.</span></span>

### <a name="spi-overview"></a><span data-ttu-id="75b70-193">SPI 概述</span><span class="sxs-lookup"><span data-stu-id="75b70-193">SPI Overview</span></span>

<span data-ttu-id="75b70-194">MBM 上提供一个 SPI 控制器 **SPI0**：</span><span class="sxs-lookup"><span data-stu-id="75b70-194">There is one SPI controller **SPI0** available on the MBM:</span></span>

* <span data-ttu-id="75b70-195">引脚 9 - **SPI0 MOSI**</span><span class="sxs-lookup"><span data-stu-id="75b70-195">Pin 9 - **SPI0 MOSI**</span></span>
* <span data-ttu-id="75b70-196">引脚 7 - **SPI0 MISO**</span><span class="sxs-lookup"><span data-stu-id="75b70-196">Pin 7 - **SPI0 MISO**</span></span>
* <span data-ttu-id="75b70-197">引脚 11 - **SPI0 SCLK**</span><span class="sxs-lookup"><span data-stu-id="75b70-197">Pin 11 - **SPI0 SCLK**</span></span>
* <span data-ttu-id="75b70-198">引脚 5 - **SPI0 CS0**</span><span class="sxs-lookup"><span data-stu-id="75b70-198">Pin 5 - **SPI0 CS0**</span></span>


### <a name="spi-sample"></a><span data-ttu-id="75b70-199">SPI 示例</span><span class="sxs-lookup"><span data-stu-id="75b70-199">SPI Sample</span></span>

<span data-ttu-id="75b70-200">有关如何在总线 **SPI0** 上执行 SPI 写入的示例如下所示：</span><span class="sxs-lookup"><span data-stu-id="75b70-200">An example on how to perform a SPI write on bus **SPI0** is shown below:</span></span>

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

