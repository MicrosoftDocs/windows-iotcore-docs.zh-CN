---
title: Dragonboard Pin 映射
ms.date: 08/28/2017
ms.topic: article
description: 了解 Dragonboard 的 pin 映射功能，包括 GPIO、串行 UART、I2C 总线和 SPI 总线。
keywords: windows iot，Dragonboard，pin 映射，GPIO
ms.openlocfilehash: 9a74e8256da8ed7a58343d8606eedbf58550d6b1
ms.sourcegitcommit: 05278f1a522ed498900ce15b98bdd4389b5dde55
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/11/2020
ms.locfileid: "88081472"
---
# <a name="dragonboard-pin-mappings"></a><span data-ttu-id="1fe04-104">Dragonboard Pin 映射</span><span class="sxs-lookup"><span data-stu-id="1fe04-104">Dragonboard Pin Mappings</span></span>

![Dragonboard 针标头](../../media/PinMappingsDB/DB_Pinout.png)

<span data-ttu-id="1fe04-106">Dragonboard 的硬件接口通过板上的40针标头公开。</span><span class="sxs-lookup"><span data-stu-id="1fe04-106">Hardware interfaces for the Dragonboard are exposed through the 40-pin header on the board.</span></span> <span data-ttu-id="1fe04-107">功能包括：</span><span class="sxs-lookup"><span data-stu-id="1fe04-107">Functionality includes:</span></span>

* <span data-ttu-id="1fe04-108">**11x** -GPIO 引脚</span><span class="sxs-lookup"><span data-stu-id="1fe04-108">**11x** - GPIO pins</span></span>
* <span data-ttu-id="1fe04-109">**2x** -串行 UARTs</span><span class="sxs-lookup"><span data-stu-id="1fe04-109">**2x** - Serial UARTs</span></span>
* <span data-ttu-id="1fe04-110">**1x** -SPI 总线</span><span class="sxs-lookup"><span data-stu-id="1fe04-110">**1x** - SPI bus</span></span>
* <span data-ttu-id="1fe04-111">**2x** -I2C 总线</span><span class="sxs-lookup"><span data-stu-id="1fe04-111">**2x** - I2C bus</span></span>
* <span data-ttu-id="1fe04-112">**1x** -5v 电源</span><span class="sxs-lookup"><span data-stu-id="1fe04-112">**1x** - 5V power pin</span></span>
* <span data-ttu-id="1fe04-113">**1x** -1.8 v 电源固定</span><span class="sxs-lookup"><span data-stu-id="1fe04-113">**1x** - 1.8V power pin</span></span>
* <span data-ttu-id="1fe04-114">**4x**</span><span class="sxs-lookup"><span data-stu-id="1fe04-114">**4x** - Ground pins</span></span>

<span data-ttu-id="1fe04-115">请注意，Dragonboard 在所有 IO 引脚上使用 1.8 V 逻辑级别。</span><span class="sxs-lookup"><span data-stu-id="1fe04-115">Note that the Dragonboard uses 1.8V logic levels on all IO pins.</span></span> 

## <a name="gpio-pins"></a><span data-ttu-id="1fe04-116">GPIO Pin</span><span class="sxs-lookup"><span data-stu-id="1fe04-116">GPIO Pins</span></span>

<span data-ttu-id="1fe04-117">让我们看看此设备上的 GPIO 可用。</span><span class="sxs-lookup"><span data-stu-id="1fe04-117">Let's look at the GPIO available on this device.</span></span>

### <a name="gpio-pin-table"></a><span data-ttu-id="1fe04-118">GPIO 固定表</span><span class="sxs-lookup"><span data-stu-id="1fe04-118">GPIO Pin Table</span></span>

<span data-ttu-id="1fe04-119">以下 GPIO pin 可通过 Api 访问：</span><span class="sxs-lookup"><span data-stu-id="1fe04-119">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="1fe04-120">GPIO#</span><span class="sxs-lookup"><span data-stu-id="1fe04-120">GPIO#</span></span> | <span data-ttu-id="1fe04-121">标头 Pin</span><span class="sxs-lookup"><span data-stu-id="1fe04-121">Header Pin</span></span>         |
> |-------|--------------------|
> | <span data-ttu-id="1fe04-122">36</span><span class="sxs-lookup"><span data-stu-id="1fe04-122">36</span></span>    | <span data-ttu-id="1fe04-123">23</span><span class="sxs-lookup"><span data-stu-id="1fe04-123">23</span></span>                 |
> | <span data-ttu-id="1fe04-124">12</span><span class="sxs-lookup"><span data-stu-id="1fe04-124">12</span></span>    | <span data-ttu-id="1fe04-125">24</span><span class="sxs-lookup"><span data-stu-id="1fe04-125">24</span></span>                 |
> | <span data-ttu-id="1fe04-126">13</span><span class="sxs-lookup"><span data-stu-id="1fe04-126">13</span></span>    | <span data-ttu-id="1fe04-127">25</span><span class="sxs-lookup"><span data-stu-id="1fe04-127">25</span></span>                 |
> | <span data-ttu-id="1fe04-128">69</span><span class="sxs-lookup"><span data-stu-id="1fe04-128">69</span></span>    | <span data-ttu-id="1fe04-129">26</span><span class="sxs-lookup"><span data-stu-id="1fe04-129">26</span></span>                 |
> | <span data-ttu-id="1fe04-130">115</span><span class="sxs-lookup"><span data-stu-id="1fe04-130">115</span></span>   | <span data-ttu-id="1fe04-131">27</span><span class="sxs-lookup"><span data-stu-id="1fe04-131">27</span></span>                 |
> | <span data-ttu-id="1fe04-132">24</span><span class="sxs-lookup"><span data-stu-id="1fe04-132">24</span></span>    | <span data-ttu-id="1fe04-133">29</span><span class="sxs-lookup"><span data-stu-id="1fe04-133">29</span></span>                 |
> | <span data-ttu-id="1fe04-134">25</span><span class="sxs-lookup"><span data-stu-id="1fe04-134">25</span></span>    | <span data-ttu-id="1fe04-135">30</span><span class="sxs-lookup"><span data-stu-id="1fe04-135">30</span></span>                 |
> | <span data-ttu-id="1fe04-136">35</span><span class="sxs-lookup"><span data-stu-id="1fe04-136">35</span></span>    | <span data-ttu-id="1fe04-137">31</span><span class="sxs-lookup"><span data-stu-id="1fe04-137">31</span></span>                 |
> | <span data-ttu-id="1fe04-138">34</span><span class="sxs-lookup"><span data-stu-id="1fe04-138">34</span></span>    | <span data-ttu-id="1fe04-139">32</span><span class="sxs-lookup"><span data-stu-id="1fe04-139">32</span></span>                 |
> | <span data-ttu-id="1fe04-140">28</span><span class="sxs-lookup"><span data-stu-id="1fe04-140">28</span></span>    | <span data-ttu-id="1fe04-141">33</span><span class="sxs-lookup"><span data-stu-id="1fe04-141">33</span></span>                 |
> | <span data-ttu-id="1fe04-142">33</span><span class="sxs-lookup"><span data-stu-id="1fe04-142">33</span></span>    | <span data-ttu-id="1fe04-143">34</span><span class="sxs-lookup"><span data-stu-id="1fe04-143">34</span></span>                 |
> | <span data-ttu-id="1fe04-144">21</span><span class="sxs-lookup"><span data-stu-id="1fe04-144">21</span></span>    | <span data-ttu-id="1fe04-145">用户 LED 1</span><span class="sxs-lookup"><span data-stu-id="1fe04-145">User LED 1</span></span>         | 
> | <span data-ttu-id="1fe04-146">120</span><span class="sxs-lookup"><span data-stu-id="1fe04-146">120</span></span>   | <span data-ttu-id="1fe04-147">用户 LED 2</span><span class="sxs-lookup"><span data-stu-id="1fe04-147">User LED 2</span></span>         |         


<span data-ttu-id="1fe04-148">例如，以下代码将**GPIO 35**打开为输出，并在 pin 上写入数字 "**1**"：</span><span class="sxs-lookup"><span data-stu-id="1fe04-148">As an example, the following code opens **GPIO 35** as an output and writes a digital '**1**' out on the pin:</span></span>
         
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

### <a name="gpio-issues"></a><span data-ttu-id="1fe04-149">GPIO 问题</span><span class="sxs-lookup"><span data-stu-id="1fe04-149">GPIO Issues</span></span>

* <span data-ttu-id="1fe04-150">输出在 GPIO 24 上不起作用。</span><span class="sxs-lookup"><span data-stu-id="1fe04-150">Output doesn't work on GPIO 24.</span></span> <span data-ttu-id="1fe04-151">输入工作正常。</span><span class="sxs-lookup"><span data-stu-id="1fe04-151">Input works fine.</span></span>
* <span data-ttu-id="1fe04-152">在启动时，pin 配置为 InputPullDown，但在首次打开时，将更改为 "输入 (" 浮动) </span><span class="sxs-lookup"><span data-stu-id="1fe04-152">Pins are configured as InputPullDown at boot, but will change to Input (floating) the first time they are opened</span></span>
* <span data-ttu-id="1fe04-153">Pin 在关闭时不会恢复为其默认状态</span><span class="sxs-lookup"><span data-stu-id="1fe04-153">Pins do not revert to their default state when closed</span></span>
* <span data-ttu-id="1fe04-154">如果对多个 pin 启用了中断，可能会出现虚假中断</span><span class="sxs-lookup"><span data-stu-id="1fe04-154">Spurious interrupts may be seen when interrupts are enabled on multiple pins</span></span>


## <a name="serial-uart"></a><span data-ttu-id="1fe04-155">串行 UART</span><span class="sxs-lookup"><span data-stu-id="1fe04-155">Serial UART</span></span>

<span data-ttu-id="1fe04-156">Dragonboard **UART0**和**UART1**上提供了两个串行 UARTS</span><span class="sxs-lookup"><span data-stu-id="1fe04-156">There are two Serial UARTS available on the Dragonboard **UART0** and **UART1**</span></span>

<span data-ttu-id="1fe04-157">**UART0**具有标准的**UART0 TX**和**UART0 RX**线路，以及流控制信号**UART0 CTS**和**UART0 RTS**。</span><span class="sxs-lookup"><span data-stu-id="1fe04-157">**UART0** has the standard **UART0 TX** and **UART0 RX** lines, along with flow control signals **UART0 CTS** and **UART0 RTS**.</span></span>

* <span data-ttu-id="1fe04-158">Pin 5- **UART0 TX**</span><span class="sxs-lookup"><span data-stu-id="1fe04-158">Pin 5  - **UART0 TX**</span></span>
* <span data-ttu-id="1fe04-159">引脚 7- **UART0 RX**</span><span class="sxs-lookup"><span data-stu-id="1fe04-159">Pin 7  - **UART0 RX**</span></span>
* <span data-ttu-id="1fe04-160">Pin 3- **UART0 CTS**</span><span class="sxs-lookup"><span data-stu-id="1fe04-160">Pin 3 - **UART0 CTS**</span></span>
* <span data-ttu-id="1fe04-161">Pin 9- **UART0 RTS**</span><span class="sxs-lookup"><span data-stu-id="1fe04-161">Pin 9 - **UART0 RTS**</span></span>


<span data-ttu-id="1fe04-162">**UART1**仅包括**UART1 TX**和**UART1 RX**行。</span><span class="sxs-lookup"><span data-stu-id="1fe04-162">**UART1** includes just the **UART1 TX** and **UART1 RX** lines.</span></span>

* <span data-ttu-id="1fe04-163">Pin 11- **UART1 TX**</span><span class="sxs-lookup"><span data-stu-id="1fe04-163">Pin 11  - **UART1 TX**</span></span>
* <span data-ttu-id="1fe04-164">Pin 13- **UART1 RX**</span><span class="sxs-lookup"><span data-stu-id="1fe04-164">Pin 13  - **UART1 RX**</span></span>

<span data-ttu-id="1fe04-165">下面的示例初始化**UART1**并执行写操作，后跟读取：</span><span class="sxs-lookup"><span data-stu-id="1fe04-165">The example below initializes **UART1** and performs a write followed by a read:</span></span>

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
> <span data-ttu-id="1fe04-166">Visual Studio 2017 在清单设计器中有一个已知 bug， (用于 appxmanifest.xml 文件的可视化编辑器) 会影响 serialcommunication 功能。</span><span class="sxs-lookup"><span data-stu-id="1fe04-166">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="1fe04-167">如果你的 appxmanifest.xml 添加 serialcommunication 功能，则通过设计器修改 appxmanifest.xml 将损坏 appxmanifest.xml (设备 xml 子级将丢失) 。</span><span class="sxs-lookup"><span data-stu-id="1fe04-167">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="1fe04-168">若要解决此问题，请右键单击 appxmanifest.xml，然后从上下文菜单中选择 "查看代码"，手动编辑 appxmanifest.xml。</span><span class="sxs-lookup"><span data-stu-id="1fe04-168">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

<span data-ttu-id="1fe04-169">必须将以下功能添加到 UWP 项目中的**appxmanifest.xml**文件，才能运行串行 UART 代码：</span><span class="sxs-lookup"><span data-stu-id="1fe04-169">You must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="1fe04-170">I2C 总线</span><span class="sxs-lookup"><span data-stu-id="1fe04-170">I2C Bus</span></span>

<span data-ttu-id="1fe04-171">让我们看看此设备上提供的 I2C 总线。</span><span class="sxs-lookup"><span data-stu-id="1fe04-171">Let's look at the I2C busses available on this device.</span></span>

### <a name="i2c-pins"></a><span data-ttu-id="1fe04-172">I2C 引脚</span><span class="sxs-lookup"><span data-stu-id="1fe04-172">I2C Pins</span></span>

<span data-ttu-id="1fe04-173">**I2C0**在 pin 标头上公开，并带有两行**SDA**和**SCL**</span><span class="sxs-lookup"><span data-stu-id="1fe04-173">**I2C0** exposed on the pin header with two lines **SDA** and **SCL**</span></span>

* <span data-ttu-id="1fe04-174">Pin 17- **I2C0 SDA**</span><span class="sxs-lookup"><span data-stu-id="1fe04-174">Pin 17 - **I2C0 SDA**</span></span>
* <span data-ttu-id="1fe04-175">固定 15- **I2C0 SCL**</span><span class="sxs-lookup"><span data-stu-id="1fe04-175">Pin 15 - **I2C0 SCL**</span></span>

<span data-ttu-id="1fe04-176">**I2C1**在 pin 标头上公开，并带有两行**SDA**和**SCL**</span><span class="sxs-lookup"><span data-stu-id="1fe04-176">**I2C1** exposed on the pin header with two lines **SDA** and **SCL**</span></span>

* <span data-ttu-id="1fe04-177">Pin 21- **I2C1 SDA**</span><span class="sxs-lookup"><span data-stu-id="1fe04-177">Pin 21 - **I2C1 SDA**</span></span>
* <span data-ttu-id="1fe04-178">固定 19- **I2C1 SCL**</span><span class="sxs-lookup"><span data-stu-id="1fe04-178">Pin 19 - **I2C1 SCL**</span></span>

### <a name="i2c-sample"></a><span data-ttu-id="1fe04-179">I2C 示例</span><span class="sxs-lookup"><span data-stu-id="1fe04-179">I2C Sample</span></span>

<span data-ttu-id="1fe04-180">下面的示例使用 address **0x40**初始化**I2C0**并将数据写入 I2C 设备：</span><span class="sxs-lookup"><span data-stu-id="1fe04-180">The example below initializes **I2C0** and writes data to an I2C device with address **0x40**:</span></span>

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


## <a name="spi-bus"></a><span data-ttu-id="1fe04-181">SPI 总线</span><span class="sxs-lookup"><span data-stu-id="1fe04-181">SPI Bus</span></span>

<span data-ttu-id="1fe04-182">让我们看看此设备上可用的 SPI 总线。</span><span class="sxs-lookup"><span data-stu-id="1fe04-182">Let's look at the SPI bus available on this device.</span></span>

### <a name="spi-pins"></a><span data-ttu-id="1fe04-183">SPI Pin</span><span class="sxs-lookup"><span data-stu-id="1fe04-183">SPI Pins</span></span>

<span data-ttu-id="1fe04-184">数据库上有一个 SPI 控制器**SPI0**可用</span><span class="sxs-lookup"><span data-stu-id="1fe04-184">There is one SPI controller **SPI0** available on the DB</span></span>

* <span data-ttu-id="1fe04-185">Pin 10- **SPI0 MISO**</span><span class="sxs-lookup"><span data-stu-id="1fe04-185">Pin 10 - **SPI0 MISO**</span></span>
* <span data-ttu-id="1fe04-186">Pin 14- **SPI0 MOSI**</span><span class="sxs-lookup"><span data-stu-id="1fe04-186">Pin 14 - **SPI0 MOSI**</span></span>
* <span data-ttu-id="1fe04-187">Pin 8- **SPI0 SCLK**</span><span class="sxs-lookup"><span data-stu-id="1fe04-187">Pin 8 - **SPI0 SCLK**</span></span>
* <span data-ttu-id="1fe04-188">Pin 12- **SPI0 CS0**</span><span class="sxs-lookup"><span data-stu-id="1fe04-188">Pin 12 - **SPI0 CS0**</span></span>

### <a name="spi-issues"></a><span data-ttu-id="1fe04-189">SPI 问题</span><span class="sxs-lookup"><span data-stu-id="1fe04-189">SPI Issues</span></span>

<span data-ttu-id="1fe04-190">SPI 时钟固定在 4.8 mhz。</span><span class="sxs-lookup"><span data-stu-id="1fe04-190">The SPI clock is fixed at 4.8mhz.</span></span> <span data-ttu-id="1fe04-191">请求的 SPI 时钟将被忽略。</span><span class="sxs-lookup"><span data-stu-id="1fe04-191">The requested SPI clock will be ignored.</span></span> 


### <a name="spi-sample"></a><span data-ttu-id="1fe04-192">SPI 示例</span><span class="sxs-lookup"><span data-stu-id="1fe04-192">SPI Sample</span></span>

<span data-ttu-id="1fe04-193">下面显示了有关如何在总线上执行 SPI 写入的示例**SPI0** ：</span><span class="sxs-lookup"><span data-stu-id="1fe04-193">An example on how to perform a SPI write on bus **SPI0** is shown below:</span></span>

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
