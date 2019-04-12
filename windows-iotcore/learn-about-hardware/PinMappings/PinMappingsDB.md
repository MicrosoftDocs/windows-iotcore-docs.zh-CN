---
title: DragonBoard 引脚映射
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解 Dragonboard 引脚映射的功能。
keywords: windows iot，Dragonboard，引脚映射 GPIO
ms.openlocfilehash: f6df962c6d05aa912013f8f0819c0789bfc393ce
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59511027"
---
# <a name="dragonboard-pin-mappings"></a><span data-ttu-id="ef857-104">DragonBoard 引脚映射</span><span class="sxs-lookup"><span data-stu-id="ef857-104">Dragonboard Pin Mappings</span></span>

![Dragonboard Pin 标头](../../media/PinMappingsDB/DB_Pinout.png)

<span data-ttu-id="ef857-106">Dragonboard 的硬件接口通过开发板上的 40 排针公开。</span><span class="sxs-lookup"><span data-stu-id="ef857-106">Hardware interfaces for the Dragonboard are exposed through the 40-pin header on the board.</span></span> <span data-ttu-id="ef857-107">功能包括：</span><span class="sxs-lookup"><span data-stu-id="ef857-107">Functionality includes:</span></span>

* <span data-ttu-id="ef857-108">**11x** - GPIO 引脚</span><span class="sxs-lookup"><span data-stu-id="ef857-108">**11x** - GPIO pins</span></span>
* <span data-ttu-id="ef857-109">**2x** - 串行 UART</span><span class="sxs-lookup"><span data-stu-id="ef857-109">**2x** - Serial UARTs</span></span>
* <span data-ttu-id="ef857-110">**1x** - SPI 总线</span><span class="sxs-lookup"><span data-stu-id="ef857-110">**1x** - SPI bus</span></span>
* <span data-ttu-id="ef857-111">**2x** - I2C 总线</span><span class="sxs-lookup"><span data-stu-id="ef857-111">**2x** - I2C bus</span></span>
* <span data-ttu-id="ef857-112">**1x** - 5V 电源引脚</span><span class="sxs-lookup"><span data-stu-id="ef857-112">**1x** - 5V power pin</span></span>
* <span data-ttu-id="ef857-113">**1x** - 1.8V 电源引脚</span><span class="sxs-lookup"><span data-stu-id="ef857-113">**1x** - 1.8V power pin</span></span>
* <span data-ttu-id="ef857-114">**4x** - 接地引脚</span><span class="sxs-lookup"><span data-stu-id="ef857-114">**4x** - Ground pins</span></span>

<span data-ttu-id="ef857-115">请注意，Dragonboard 使用 1.8 v 逻辑级别上所有 IO 引脚。</span><span class="sxs-lookup"><span data-stu-id="ef857-115">Note that the Dragonboard uses 1.8V logic levels on all IO pins.</span></span> 

## <a name="gpio-pins"></a><span data-ttu-id="ef857-116">GPIO 插针</span><span class="sxs-lookup"><span data-stu-id="ef857-116">GPIO Pins</span></span>

<span data-ttu-id="ef857-117">让我们看一下 GPIO 此设备上可用。</span><span class="sxs-lookup"><span data-stu-id="ef857-117">Let's look at the GPIO available on this device.</span></span>

### <a name="gpio-pin-table"></a><span data-ttu-id="ef857-118">GPIO Pin 表</span><span class="sxs-lookup"><span data-stu-id="ef857-118">GPIO Pin Table</span></span>

<span data-ttu-id="ef857-119">以下 GPIO 引脚可通过 API 访问：</span><span class="sxs-lookup"><span data-stu-id="ef857-119">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="ef857-120">GPIO#</span><span class="sxs-lookup"><span data-stu-id="ef857-120">GPIO#</span></span> | <span data-ttu-id="ef857-121">排针</span><span class="sxs-lookup"><span data-stu-id="ef857-121">Header Pin</span></span>         |
> |-------|--------------------|
> | <span data-ttu-id="ef857-122">36</span><span class="sxs-lookup"><span data-stu-id="ef857-122">36</span></span>    | <span data-ttu-id="ef857-123">23</span><span class="sxs-lookup"><span data-stu-id="ef857-123">23</span></span>                 |
> | <span data-ttu-id="ef857-124">12</span><span class="sxs-lookup"><span data-stu-id="ef857-124">12</span></span>    | <span data-ttu-id="ef857-125">24</span><span class="sxs-lookup"><span data-stu-id="ef857-125">24</span></span>                 |
> | <span data-ttu-id="ef857-126">13</span><span class="sxs-lookup"><span data-stu-id="ef857-126">13</span></span>    | <span data-ttu-id="ef857-127">25</span><span class="sxs-lookup"><span data-stu-id="ef857-127">25</span></span>                 |
> | <span data-ttu-id="ef857-128">69</span><span class="sxs-lookup"><span data-stu-id="ef857-128">69</span></span>    | <span data-ttu-id="ef857-129">26</span><span class="sxs-lookup"><span data-stu-id="ef857-129">26</span></span>                 |
> | <span data-ttu-id="ef857-130">115</span><span class="sxs-lookup"><span data-stu-id="ef857-130">115</span></span>   | <span data-ttu-id="ef857-131">27</span><span class="sxs-lookup"><span data-stu-id="ef857-131">27</span></span>                 |
> | <span data-ttu-id="ef857-132">24</span><span class="sxs-lookup"><span data-stu-id="ef857-132">24</span></span>    | <span data-ttu-id="ef857-133">29</span><span class="sxs-lookup"><span data-stu-id="ef857-133">29</span></span>                 |
> | <span data-ttu-id="ef857-134">25</span><span class="sxs-lookup"><span data-stu-id="ef857-134">25</span></span>    | <span data-ttu-id="ef857-135">30</span><span class="sxs-lookup"><span data-stu-id="ef857-135">30</span></span>                 |
> | <span data-ttu-id="ef857-136">35</span><span class="sxs-lookup"><span data-stu-id="ef857-136">35</span></span>    | <span data-ttu-id="ef857-137">31</span><span class="sxs-lookup"><span data-stu-id="ef857-137">31</span></span>                 |
> | <span data-ttu-id="ef857-138">34</span><span class="sxs-lookup"><span data-stu-id="ef857-138">34</span></span>    | <span data-ttu-id="ef857-139">32</span><span class="sxs-lookup"><span data-stu-id="ef857-139">32</span></span>                 |
> | <span data-ttu-id="ef857-140">28</span><span class="sxs-lookup"><span data-stu-id="ef857-140">28</span></span>    | <span data-ttu-id="ef857-141">33</span><span class="sxs-lookup"><span data-stu-id="ef857-141">33</span></span>                 |
> | <span data-ttu-id="ef857-142">33</span><span class="sxs-lookup"><span data-stu-id="ef857-142">33</span></span>    | <span data-ttu-id="ef857-143">34</span><span class="sxs-lookup"><span data-stu-id="ef857-143">34</span></span>                 |
> | <span data-ttu-id="ef857-144">21</span><span class="sxs-lookup"><span data-stu-id="ef857-144">21</span></span>    | <span data-ttu-id="ef857-145">用户 LED 1</span><span class="sxs-lookup"><span data-stu-id="ef857-145">User LED 1</span></span>         | 
> | <span data-ttu-id="ef857-146">120</span><span class="sxs-lookup"><span data-stu-id="ef857-146">120</span></span>   | <span data-ttu-id="ef857-147">用户 LED 2</span><span class="sxs-lookup"><span data-stu-id="ef857-147">User LED 2</span></span>         |         


<span data-ttu-id="ef857-148">例如，下面的代码打开**GPIO 35**作为输出，并将写入数字**1**的插针的扩展：</span><span class="sxs-lookup"><span data-stu-id="ef857-148">As an example, the following code opens **GPIO 35** as an output and writes a digital '**1**' out on the pin:</span></span>
         
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

### <a name="gpio-issues"></a><span data-ttu-id="ef857-149">GPIO 问题</span><span class="sxs-lookup"><span data-stu-id="ef857-149">GPIO Issues</span></span>

* <span data-ttu-id="ef857-150">GPIO 24 输出不起作用。</span><span class="sxs-lookup"><span data-stu-id="ef857-150">Output doesn't work on GPIO 24.</span></span> <span data-ttu-id="ef857-151">输入工作正常。</span><span class="sxs-lookup"><span data-stu-id="ef857-151">Input works fine.</span></span>
* <span data-ttu-id="ef857-152">引脚会在启动时配置为 InputPullDown，但在首次打开时将更改为 Input (floating)</span><span class="sxs-lookup"><span data-stu-id="ef857-152">Pins are configured as InputPullDown at boot, but will change to Input (floating) the first time they are opened</span></span>
* <span data-ttu-id="ef857-153">关闭时，引脚不会还原为默认状态</span><span class="sxs-lookup"><span data-stu-id="ef857-153">Pins do not revert to their default state when closed</span></span>
* <span data-ttu-id="ef857-154">当多个引脚上启用了中断时，可能会看到假中断</span><span class="sxs-lookup"><span data-stu-id="ef857-154">Spurious interrupts may be seen when interrupts are enabled on multiple pins</span></span>


## <a name="serial-uart"></a><span data-ttu-id="ef857-155">串行 UART</span><span class="sxs-lookup"><span data-stu-id="ef857-155">Serial UART</span></span>

<span data-ttu-id="ef857-156">Dragonboard 上提供了两个串行 UART：**UART0** 和 **UART1**</span><span class="sxs-lookup"><span data-stu-id="ef857-156">There are two Serial UARTS available on the Dragonboard **UART0** and **UART1**</span></span>

<span data-ttu-id="ef857-157">**UART0** 具有标准 **UART0 TX** 和 **UART0 RX** 线以及流控制信号 **UART0 CTS** 和 **UART0 RTS**。</span><span class="sxs-lookup"><span data-stu-id="ef857-157">**UART0** has the standard **UART0 TX** and **UART0 RX** lines, along with flow control signals **UART0 CTS** and **UART0 RTS**.</span></span>

* <span data-ttu-id="ef857-158">固定 5- **UART0 TX**</span><span class="sxs-lookup"><span data-stu-id="ef857-158">Pin 5  - **UART0 TX**</span></span>
* <span data-ttu-id="ef857-159">将固定 7- **UART0 RX**</span><span class="sxs-lookup"><span data-stu-id="ef857-159">Pin 7  - **UART0 RX**</span></span>
* <span data-ttu-id="ef857-160">固定 3- **UART0 CTS**</span><span class="sxs-lookup"><span data-stu-id="ef857-160">Pin 3 - **UART0 CTS**</span></span>
* <span data-ttu-id="ef857-161">将固定 9- **UART0 RTS**</span><span class="sxs-lookup"><span data-stu-id="ef857-161">Pin 9 - **UART0 RTS**</span></span>


<span data-ttu-id="ef857-162">**UART1** 仅包含 **UART1 TX** 和 **UART1 RX** 线。</span><span class="sxs-lookup"><span data-stu-id="ef857-162">**UART1** includes just the **UART1 TX** and **UART1 RX** lines.</span></span>

* <span data-ttu-id="ef857-163">将固定 11- **UART1 TX**</span><span class="sxs-lookup"><span data-stu-id="ef857-163">Pin 11  - **UART1 TX**</span></span>
* <span data-ttu-id="ef857-164">将固定 13- **UART1 RX**</span><span class="sxs-lookup"><span data-stu-id="ef857-164">Pin 13  - **UART1 RX**</span></span>

<span data-ttu-id="ef857-165">以下示例初始化 **UART1** 并依次执行写入和读取操作：</span><span class="sxs-lookup"><span data-stu-id="ef857-165">The example below initializes **UART1** and performs a write followed by a read:</span></span>

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
> <span data-ttu-id="ef857-166">Visual Studio 2017 在清单设计器 （appxmanifest 文件的可视编辑器） 的影响 serialcommunication 功能中有一个已知的 bug。</span><span class="sxs-lookup"><span data-stu-id="ef857-166">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="ef857-167">如果你 appxmanifest 添加 serialcommunication 功能，修改与设计器在 appxmanifest 将损坏你 appxmanifest （设备 xml 子将会丢失）。</span><span class="sxs-lookup"><span data-stu-id="ef857-167">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="ef857-168">可以解决此问题通过手动编辑 appxmanifest 通过右键单击你的 appxmanifest 并从上下文菜单中选择查看代码。</span><span class="sxs-lookup"><span data-stu-id="ef857-168">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

<span data-ttu-id="ef857-169">必须将添加到了以下功能**Package.appxmanifest** UWP 项目运行串行 UART 代码文件中：</span><span class="sxs-lookup"><span data-stu-id="ef857-169">You must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="ef857-170">I2C 总线</span><span class="sxs-lookup"><span data-stu-id="ef857-170">I2C Bus</span></span>

<span data-ttu-id="ef857-171">让我们看一下此设备上的可用 I2C 总线。</span><span class="sxs-lookup"><span data-stu-id="ef857-171">Let's look at the I2C busses available on this device.</span></span>

### <a name="i2c-pins"></a><span data-ttu-id="ef857-172">I2C Pin</span><span class="sxs-lookup"><span data-stu-id="ef857-172">I2C Pins</span></span>

<span data-ttu-id="ef857-173">在排针上公开的 **I2C0**，带有 **SDA** 和 **SCL** 两条线</span><span class="sxs-lookup"><span data-stu-id="ef857-173">**I2C0** exposed on the pin header with two lines **SDA** and **SCL**</span></span>

* <span data-ttu-id="ef857-174">引脚 17 - **I2C0 SDA**</span><span class="sxs-lookup"><span data-stu-id="ef857-174">Pin 17 - **I2C0 SDA**</span></span>
* <span data-ttu-id="ef857-175">引脚 15 - **I2C0 SCL**</span><span class="sxs-lookup"><span data-stu-id="ef857-175">Pin 15 - **I2C0 SCL**</span></span>

<span data-ttu-id="ef857-176">在排针上公开的 **I2C1**，带有 **SDA** 和 **SCL** 两条线</span><span class="sxs-lookup"><span data-stu-id="ef857-176">**I2C1** exposed on the pin header with two lines **SDA** and **SCL**</span></span>

* <span data-ttu-id="ef857-177">引脚 21 - **I2C1 SDA**</span><span class="sxs-lookup"><span data-stu-id="ef857-177">Pin 21 - **I2C1 SDA**</span></span>
* <span data-ttu-id="ef857-178">引脚 19 - **I2C1 SCL**</span><span class="sxs-lookup"><span data-stu-id="ef857-178">Pin 19 - **I2C1 SCL**</span></span>

### <a name="i2c-sample"></a><span data-ttu-id="ef857-179">I2C 示例</span><span class="sxs-lookup"><span data-stu-id="ef857-179">I2C Sample</span></span>

<span data-ttu-id="ef857-180">以下示例将初始化 **I2C0** 并将数据写入地址为 **0x40** 的 I2C 设备：</span><span class="sxs-lookup"><span data-stu-id="ef857-180">The example below initializes **I2C0** and writes data to an I2C device with address **0x40**:</span></span>

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


## <a name="spi-bus"></a><span data-ttu-id="ef857-181">SPI 总线</span><span class="sxs-lookup"><span data-stu-id="ef857-181">SPI Bus</span></span>

<span data-ttu-id="ef857-182">让我们看一下此设备上的可用 SPI 总线。</span><span class="sxs-lookup"><span data-stu-id="ef857-182">Let's look at the SPI bus available on this device.</span></span>

### <a name="spi-pins"></a><span data-ttu-id="ef857-183">SPI Pin</span><span class="sxs-lookup"><span data-stu-id="ef857-183">SPI Pins</span></span>

<span data-ttu-id="ef857-184">DB 上提供一个 SPI 控制器 **SPI0**</span><span class="sxs-lookup"><span data-stu-id="ef857-184">There is one SPI controller **SPI0** available on the DB</span></span>

* <span data-ttu-id="ef857-185">将固定 10- **SPI0 MISO**</span><span class="sxs-lookup"><span data-stu-id="ef857-185">Pin 10 - **SPI0 MISO**</span></span>
* <span data-ttu-id="ef857-186">将固定 14- **SPI0 MOSI**</span><span class="sxs-lookup"><span data-stu-id="ef857-186">Pin 14 - **SPI0 MOSI**</span></span>
* <span data-ttu-id="ef857-187">引脚 8 - **SPI0 SCLK**</span><span class="sxs-lookup"><span data-stu-id="ef857-187">Pin 8 - **SPI0 SCLK**</span></span>
* <span data-ttu-id="ef857-188">引脚 12 - **SPI0 CS0**</span><span class="sxs-lookup"><span data-stu-id="ef857-188">Pin 12 - **SPI0 CS0**</span></span>

### <a name="spi-issues"></a><span data-ttu-id="ef857-189">SPI 问题</span><span class="sxs-lookup"><span data-stu-id="ef857-189">SPI Issues</span></span>

<span data-ttu-id="ef857-190">SPI 时钟固定在 4.8mhz。</span><span class="sxs-lookup"><span data-stu-id="ef857-190">The SPI clock is fixed at 4.8mhz.</span></span> <span data-ttu-id="ef857-191">请求的 SPI 时钟将被忽略。</span><span class="sxs-lookup"><span data-stu-id="ef857-191">The requested SPI clock will be ignored.</span></span> 


### <a name="spi-sample"></a><span data-ttu-id="ef857-192">SPI 示例</span><span class="sxs-lookup"><span data-stu-id="ef857-192">SPI Sample</span></span>

<span data-ttu-id="ef857-193">有关如何在总线 **SPI0** 上执行 SPI 写入的示例如下所示：</span><span class="sxs-lookup"><span data-stu-id="ef857-193">An example on how to perform a SPI write on bus **SPI0** is shown below:</span></span>

```C3
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
