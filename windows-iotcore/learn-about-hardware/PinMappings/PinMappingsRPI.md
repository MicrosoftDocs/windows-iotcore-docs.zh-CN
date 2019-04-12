---
title: Raspberry Pi 2 和 3 引脚映射
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解 Raspberry Pi 2 和 3 引脚映射的功能。
keywords: windows iot，Rasperry Pi 2，Raspberry Pi 3，固定映射，GPIO
ms.openlocfilehash: 86e641bdcc6b4895161c6509ca7529b0dd55fad9
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510762"
---
# <a name="raspberry-pi-2--3-pin-mappings"></a><span data-ttu-id="9831c-104">Raspberry Pi 2 和 3 引脚映射</span><span class="sxs-lookup"><span data-stu-id="9831c-104">Raspberry Pi 2 & 3 Pin Mappings</span></span>

![Raspberry Pi 2 和 3 Pin 标头](../../media/PinMappingsRPI/RP2_Pinout.png)

<span data-ttu-id="9831c-106">Raspberry Pi 2 和 Raspberry Pi 3 的硬件接口通过开发板上的 40 排针 **J8** 公开。</span><span class="sxs-lookup"><span data-stu-id="9831c-106">Hardware interfaces for the Raspberry Pi 2 and Raspberry Pi 3 are exposed through the 40-pin header **J8** on the board.</span></span> <span data-ttu-id="9831c-107">功能包括：</span><span class="sxs-lookup"><span data-stu-id="9831c-107">Functionality includes:</span></span>

* <span data-ttu-id="9831c-108">**24 x**的 GPIO 插针</span><span class="sxs-lookup"><span data-stu-id="9831c-108">**24x** - GPIO pins</span></span>
* <span data-ttu-id="9831c-109">**1 x** -串行 UARTs （RPi3 仅包括最小 UART）</span><span class="sxs-lookup"><span data-stu-id="9831c-109">**1x** - Serial UARTs (RPi3 only includes mini UART)</span></span>
* <span data-ttu-id="9831c-110">**2 x** -SPI 总线</span><span class="sxs-lookup"><span data-stu-id="9831c-110">**2x** - SPI bus</span></span>
* <span data-ttu-id="9831c-111">**1x** - I2C 总线</span><span class="sxs-lookup"><span data-stu-id="9831c-111">**1x** - I2C bus</span></span>
* <span data-ttu-id="9831c-112">**2x** - 5V 电源引脚</span><span class="sxs-lookup"><span data-stu-id="9831c-112">**2x** - 5V power pins</span></span>
* <span data-ttu-id="9831c-113">**2x** - 3.3V 电源引脚</span><span class="sxs-lookup"><span data-stu-id="9831c-113">**2x** - 3.3V power pins</span></span>
* <span data-ttu-id="9831c-114">**8x** - 接地引脚</span><span class="sxs-lookup"><span data-stu-id="9831c-114">**8x** - Ground pins</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="9831c-115">GPIO 插针</span><span class="sxs-lookup"><span data-stu-id="9831c-115">GPIO Pins</span></span>

<span data-ttu-id="9831c-116">让我们看一下 GPIO 此设备上可用。</span><span class="sxs-lookup"><span data-stu-id="9831c-116">Let's look at the GPIO available on this device.</span></span>

### <a name="gpio-pin-overview"></a><span data-ttu-id="9831c-117">GPIO Pin 概述</span><span class="sxs-lookup"><span data-stu-id="9831c-117">GPIO Pin Overview</span></span>

<span data-ttu-id="9831c-118">以下 GPIO 引脚可通过 API 访问：</span><span class="sxs-lookup"><span data-stu-id="9831c-118">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="9831c-119">GPIO#</span><span class="sxs-lookup"><span data-stu-id="9831c-119">GPIO#</span></span> | <span data-ttu-id="9831c-120">通电拉</span><span class="sxs-lookup"><span data-stu-id="9831c-120">Power-on Pull</span></span> | <span data-ttu-id="9831c-121">备用函数</span><span class="sxs-lookup"><span data-stu-id="9831c-121">Alternate Functions</span></span> | <span data-ttu-id="9831c-122">排针</span><span class="sxs-lookup"><span data-stu-id="9831c-122">Header Pin</span></span>         |
> |-------|---------------|---------------------|--------------------|
> | <span data-ttu-id="9831c-123">2</span><span class="sxs-lookup"><span data-stu-id="9831c-123">2</span></span>     | <span data-ttu-id="9831c-124">上拉</span><span class="sxs-lookup"><span data-stu-id="9831c-124">PullUp</span></span>        | <span data-ttu-id="9831c-125">I2C1 SDA</span><span class="sxs-lookup"><span data-stu-id="9831c-125">I2C1 SDA</span></span>            | <span data-ttu-id="9831c-126">3</span><span class="sxs-lookup"><span data-stu-id="9831c-126">3</span></span>                  |
> | <span data-ttu-id="9831c-127">3</span><span class="sxs-lookup"><span data-stu-id="9831c-127">3</span></span>     | <span data-ttu-id="9831c-128">上拉</span><span class="sxs-lookup"><span data-stu-id="9831c-128">PullUp</span></span>        | <span data-ttu-id="9831c-129">I2C1 SCL</span><span class="sxs-lookup"><span data-stu-id="9831c-129">I2C1 SCL</span></span>            | <span data-ttu-id="9831c-130">5</span><span class="sxs-lookup"><span data-stu-id="9831c-130">5</span></span>                  |
> | <span data-ttu-id="9831c-131">4</span><span class="sxs-lookup"><span data-stu-id="9831c-131">4</span></span>     | <span data-ttu-id="9831c-132">上拉</span><span class="sxs-lookup"><span data-stu-id="9831c-132">PullUp</span></span>        |                     | <span data-ttu-id="9831c-133">7</span><span class="sxs-lookup"><span data-stu-id="9831c-133">7</span></span>                  |
> | <span data-ttu-id="9831c-134">5</span><span class="sxs-lookup"><span data-stu-id="9831c-134">5</span></span>     | <span data-ttu-id="9831c-135">上拉</span><span class="sxs-lookup"><span data-stu-id="9831c-135">PullUp</span></span>        |                     | <span data-ttu-id="9831c-136">29</span><span class="sxs-lookup"><span data-stu-id="9831c-136">29</span></span>                 |
> | <span data-ttu-id="9831c-137">6</span><span class="sxs-lookup"><span data-stu-id="9831c-137">6</span></span>     | <span data-ttu-id="9831c-138">上拉</span><span class="sxs-lookup"><span data-stu-id="9831c-138">PullUp</span></span>        |                     | <span data-ttu-id="9831c-139">31</span><span class="sxs-lookup"><span data-stu-id="9831c-139">31</span></span>                 |
> | <span data-ttu-id="9831c-140">7</span><span class="sxs-lookup"><span data-stu-id="9831c-140">7</span></span>     | <span data-ttu-id="9831c-141">上拉</span><span class="sxs-lookup"><span data-stu-id="9831c-141">PullUp</span></span>        | <span data-ttu-id="9831c-142">SPI0 CS1</span><span class="sxs-lookup"><span data-stu-id="9831c-142">SPI0 CS1</span></span>            | <span data-ttu-id="9831c-143">26</span><span class="sxs-lookup"><span data-stu-id="9831c-143">26</span></span>                 |
> | <span data-ttu-id="9831c-144">8</span><span class="sxs-lookup"><span data-stu-id="9831c-144">8</span></span>     | <span data-ttu-id="9831c-145">上拉</span><span class="sxs-lookup"><span data-stu-id="9831c-145">PullUp</span></span>        | <span data-ttu-id="9831c-146">SPI0 CS0</span><span class="sxs-lookup"><span data-stu-id="9831c-146">SPI0 CS0</span></span>            | <span data-ttu-id="9831c-147">24</span><span class="sxs-lookup"><span data-stu-id="9831c-147">24</span></span>                 |
> | <span data-ttu-id="9831c-148">9</span><span class="sxs-lookup"><span data-stu-id="9831c-148">9</span></span>     | <span data-ttu-id="9831c-149">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-149">PullDown</span></span>      | <span data-ttu-id="9831c-150">SPI0 MISO</span><span class="sxs-lookup"><span data-stu-id="9831c-150">SPI0 MISO</span></span>           | <span data-ttu-id="9831c-151">21</span><span class="sxs-lookup"><span data-stu-id="9831c-151">21</span></span>                 |
> | <span data-ttu-id="9831c-152">10</span><span class="sxs-lookup"><span data-stu-id="9831c-152">10</span></span>    | <span data-ttu-id="9831c-153">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-153">PullDown</span></span>      | <span data-ttu-id="9831c-154">SPI0 MOSI</span><span class="sxs-lookup"><span data-stu-id="9831c-154">SPI0 MOSI</span></span>           | <span data-ttu-id="9831c-155">19</span><span class="sxs-lookup"><span data-stu-id="9831c-155">19</span></span>                 |
> | <span data-ttu-id="9831c-156">11</span><span class="sxs-lookup"><span data-stu-id="9831c-156">11</span></span>    | <span data-ttu-id="9831c-157">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-157">PullDown</span></span>      | <span data-ttu-id="9831c-158">SPI0 SCLK</span><span class="sxs-lookup"><span data-stu-id="9831c-158">SPI0 SCLK</span></span>           | <span data-ttu-id="9831c-159">23</span><span class="sxs-lookup"><span data-stu-id="9831c-159">23</span></span>                 |
> | <span data-ttu-id="9831c-160">12</span><span class="sxs-lookup"><span data-stu-id="9831c-160">12</span></span>    | <span data-ttu-id="9831c-161">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-161">PullDown</span></span>      |                     | <span data-ttu-id="9831c-162">32</span><span class="sxs-lookup"><span data-stu-id="9831c-162">32</span></span>                 |
> | <span data-ttu-id="9831c-163">13</span><span class="sxs-lookup"><span data-stu-id="9831c-163">13</span></span>    | <span data-ttu-id="9831c-164">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-164">PullDown</span></span>      |                     | <span data-ttu-id="9831c-165">33</span><span class="sxs-lookup"><span data-stu-id="9831c-165">33</span></span>                 |
> | <span data-ttu-id="9831c-166">16</span><span class="sxs-lookup"><span data-stu-id="9831c-166">16</span></span>    | <span data-ttu-id="9831c-167">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-167">PullDown</span></span>      | <span data-ttu-id="9831c-168">SPI1 CS0</span><span class="sxs-lookup"><span data-stu-id="9831c-168">SPI1 CS0</span></span>            | <span data-ttu-id="9831c-169">36</span><span class="sxs-lookup"><span data-stu-id="9831c-169">36</span></span>                 |
> | <span data-ttu-id="9831c-170">17</span><span class="sxs-lookup"><span data-stu-id="9831c-170">17</span></span>    | <span data-ttu-id="9831c-171">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-171">PullDown</span></span>      |                     | <span data-ttu-id="9831c-172">11</span><span class="sxs-lookup"><span data-stu-id="9831c-172">11</span></span>                 |
> | <span data-ttu-id="9831c-173">18</span><span class="sxs-lookup"><span data-stu-id="9831c-173">18</span></span>    | <span data-ttu-id="9831c-174">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-174">PullDown</span></span>      |                     | <span data-ttu-id="9831c-175">12</span><span class="sxs-lookup"><span data-stu-id="9831c-175">12</span></span>                 |
> | <span data-ttu-id="9831c-176">19</span><span class="sxs-lookup"><span data-stu-id="9831c-176">19</span></span>    | <span data-ttu-id="9831c-177">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-177">PullDown</span></span>      | <span data-ttu-id="9831c-178">SPI1 MISO</span><span class="sxs-lookup"><span data-stu-id="9831c-178">SPI1 MISO</span></span>           | <span data-ttu-id="9831c-179">35</span><span class="sxs-lookup"><span data-stu-id="9831c-179">35</span></span>                 |
> | <span data-ttu-id="9831c-180">20</span><span class="sxs-lookup"><span data-stu-id="9831c-180">20</span></span>    | <span data-ttu-id="9831c-181">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-181">PullDown</span></span>      | <span data-ttu-id="9831c-182">SPI1 MOSI</span><span class="sxs-lookup"><span data-stu-id="9831c-182">SPI1 MOSI</span></span>           | <span data-ttu-id="9831c-183">38</span><span class="sxs-lookup"><span data-stu-id="9831c-183">38</span></span>                 |
> | <span data-ttu-id="9831c-184">21</span><span class="sxs-lookup"><span data-stu-id="9831c-184">21</span></span>    | <span data-ttu-id="9831c-185">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-185">PullDown</span></span>      | <span data-ttu-id="9831c-186">SPI1 SCLK</span><span class="sxs-lookup"><span data-stu-id="9831c-186">SPI1 SCLK</span></span>           | <span data-ttu-id="9831c-187">40</span><span class="sxs-lookup"><span data-stu-id="9831c-187">40</span></span>                 |
> | <span data-ttu-id="9831c-188">22</span><span class="sxs-lookup"><span data-stu-id="9831c-188">22</span></span>    | <span data-ttu-id="9831c-189">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-189">PullDown</span></span>      |                     | <span data-ttu-id="9831c-190">15</span><span class="sxs-lookup"><span data-stu-id="9831c-190">15</span></span>                 |
> | <span data-ttu-id="9831c-191">23</span><span class="sxs-lookup"><span data-stu-id="9831c-191">23</span></span>    | <span data-ttu-id="9831c-192">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-192">PullDown</span></span>      |                     | <span data-ttu-id="9831c-193">16</span><span class="sxs-lookup"><span data-stu-id="9831c-193">16</span></span>                 |
> | <span data-ttu-id="9831c-194">24</span><span class="sxs-lookup"><span data-stu-id="9831c-194">24</span></span>    | <span data-ttu-id="9831c-195">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-195">PullDown</span></span>      |                     | <span data-ttu-id="9831c-196">18</span><span class="sxs-lookup"><span data-stu-id="9831c-196">18</span></span>                 |
> | <span data-ttu-id="9831c-197">25</span><span class="sxs-lookup"><span data-stu-id="9831c-197">25</span></span>    | <span data-ttu-id="9831c-198">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-198">PullDown</span></span>      |                     | <span data-ttu-id="9831c-199">22</span><span class="sxs-lookup"><span data-stu-id="9831c-199">22</span></span>                 |
> | <span data-ttu-id="9831c-200">26</span><span class="sxs-lookup"><span data-stu-id="9831c-200">26</span></span>    | <span data-ttu-id="9831c-201">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-201">PullDown</span></span>      |                     | <span data-ttu-id="9831c-202">37</span><span class="sxs-lookup"><span data-stu-id="9831c-202">37</span></span>                 |
> | <span data-ttu-id="9831c-203">27</span><span class="sxs-lookup"><span data-stu-id="9831c-203">27</span></span>    | <span data-ttu-id="9831c-204">下拉</span><span class="sxs-lookup"><span data-stu-id="9831c-204">PullDown</span></span>      |                     | <span data-ttu-id="9831c-205">13</span><span class="sxs-lookup"><span data-stu-id="9831c-205">13</span></span>                 |
> | <span data-ttu-id="9831c-206">35\*</span><span class="sxs-lookup"><span data-stu-id="9831c-206">35\*</span></span>   | <span data-ttu-id="9831c-207">上拉</span><span class="sxs-lookup"><span data-stu-id="9831c-207">PullUp</span></span>        |                     | <span data-ttu-id="9831c-208">红色电源 LED</span><span class="sxs-lookup"><span data-stu-id="9831c-208">Red Power LED</span></span>      |
> | <span data-ttu-id="9831c-209">47\*</span><span class="sxs-lookup"><span data-stu-id="9831c-209">47\*</span></span>   | <span data-ttu-id="9831c-210">上拉</span><span class="sxs-lookup"><span data-stu-id="9831c-210">PullUp</span></span>        |                     | <span data-ttu-id="9831c-211">绿色活动 LED</span><span class="sxs-lookup"><span data-stu-id="9831c-211">Green Activity LED</span></span> |

<span data-ttu-id="9831c-212">\* = 仅 raspberry Pi 2。</span><span class="sxs-lookup"><span data-stu-id="9831c-212">\* = Raspberry Pi 2 ONLY.</span></span> <span data-ttu-id="9831c-213">Raspberry Pi 3 上未提供 GPIO 35 和 47。</span><span class="sxs-lookup"><span data-stu-id="9831c-213">GPIO 35 & 47 are not available on Raspberry Pi 3.</span></span>

### <a name="gpio-sample"></a><span data-ttu-id="9831c-214">GPIO 示例</span><span class="sxs-lookup"><span data-stu-id="9831c-214">GPIO Sample</span></span>

<span data-ttu-id="9831c-215">例如，以下代码将 **GPIO 5** 作为输出打开，并在该引脚上写入数字“**1**”：</span><span class="sxs-lookup"><span data-stu-id="9831c-215">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>

```csharp
using Windows.Devices.Gpio;

public void GPIO()
{
    // Get the default GPIO controller on the system
    GpioController gpio = GpioController.GetDefault();
    if (gpio == null)
        return; // GPIO not available on this system

    // Open GPIO 5
    using (GpioPin pin = gpio.OpenPin(5))
    {
        // Latch HIGH value first. This ensures a default value when the pin is set as output
        pin.Write(GpioPinValue.High);

        // Set the IO direction as output
        pin.SetDriveMode(GpioPinDriveMode.Output);

    } // Close pin - will revert to its power-on state
}
```

<span data-ttu-id="9831c-216">当打开 pin 时，它将在其电源的状态，其中可能包括拉取电阻器。</span><span class="sxs-lookup"><span data-stu-id="9831c-216">When you open a pin, it will be in its power-on state, which may include a pull resistor.</span></span> <span data-ttu-id="9831c-217">若要断开拉电阻的连接并获取高阻抗输入，请将驱动程序模式设置为 GpioPinDriveMode.Input：</span><span class="sxs-lookup"><span data-stu-id="9831c-217">To disconnect the pull resistors and get a high-impedance input, set the drive mode to GpioPinDriveMode.Input:</span></span>

    pin.SetDriveMode(GpioPinDriveMode.Input);

<span data-ttu-id="9831c-218">当关闭引脚时，它将还原到其通电状态。</span><span class="sxs-lookup"><span data-stu-id="9831c-218">When a pin is closed, it reverts to its power-on state.</span></span>

### <a name="pin-muxing"></a><span data-ttu-id="9831c-219">Pin Muxing</span><span class="sxs-lookup"><span data-stu-id="9831c-219">Pin Muxing</span></span>

<span data-ttu-id="9831c-220">某些 GPIO 插针可以执行多个功能。</span><span class="sxs-lookup"><span data-stu-id="9831c-220">Some GPIO pins can perform multiple functions.</span></span> <span data-ttu-id="9831c-221">默认情况下，pin 配置为 GPIO 输入。</span><span class="sxs-lookup"><span data-stu-id="9831c-221">By default, pins are configured as GPIO inputs.</span></span> <span data-ttu-id="9831c-222">当您打开一个备用函数通过调用`I2cDevice.FromIdAsync()`或`SpiDevice.FromIdAsync()`，针函数所需的自动交换 ("muxed") 到正确的函数。</span><span class="sxs-lookup"><span data-stu-id="9831c-222">When you open an alternate function by calling `I2cDevice.FromIdAsync()` or `SpiDevice.FromIdAsync()` , the pins required by the function are automatically switched ("muxed") to the correct function.</span></span> <span data-ttu-id="9831c-223">通过调用关闭设备时`I2cDevice.Dispose()`或`SpiDevice.Dispose()`，球瓶还原为其默认函数。</span><span class="sxs-lookup"><span data-stu-id="9831c-223">When the device is closed by calling `I2cDevice.Dispose()` or `SpiDevice.Dispose()`, the pins revert back to their default function.</span></span> <span data-ttu-id="9831c-224">如果你尝试为两个不同的功能一次使用 pin，当您尝试打开冲突函数时将引发异常。</span><span class="sxs-lookup"><span data-stu-id="9831c-224">If you try to use a pin for two different functions at once, an exception will be thrown when you try to open the conflicting function.</span></span> <span data-ttu-id="9831c-225">例如，</span><span class="sxs-lookup"><span data-stu-id="9831c-225">For example,</span></span>

```csharp
var controller = GpioController.GetDefault();
var gpio2 = controller.OpenPin(2);      // open GPIO2, shared with I2C1 SDA

var dis = await DeviceInformation.FindAllAsync(I2cDevice.GetDeviceSelector());
var i2cDevice = await I2cDevice.FromIdAsync(dis[0].Id, new I2cConnectionSettings(0x55)); // exception thrown because GPIO2 is open

gpio2.Dispose(); // close GPIO2
var i2cDevice = await I2cDevice.FromIdAsync(dis[0].Id, new I2cConnectionSettings(0x55)); // succeeds because gpio2 is now available

var gpio2 = controller.OpenPin(2); // throws exception because GPIO2 is in use as SDA1

i2cDevice.Dispose(); // release I2C device
var gpio2 = controller.OpenPin(2); // succeeds now that GPIO2 is available
```

## <a name="serial-uart"></a><span data-ttu-id="9831c-226">串行 UART</span><span class="sxs-lookup"><span data-stu-id="9831c-226">Serial UART</span></span>

<span data-ttu-id="9831c-227">RPi2/3 上有一个串行 UART：**UART0**</span><span class="sxs-lookup"><span data-stu-id="9831c-227">There is one Serial UART available on the RPi2/3: **UART0**</span></span>

* <span data-ttu-id="9831c-228">将固定 8- **UART0 TX**</span><span class="sxs-lookup"><span data-stu-id="9831c-228">Pin 8  - **UART0 TX**</span></span>
* <span data-ttu-id="9831c-229">将固定 10- **UART0 RX**</span><span class="sxs-lookup"><span data-stu-id="9831c-229">Pin 10  - **UART0 RX**</span></span>

<span data-ttu-id="9831c-230">以下示例初始化 **UART0** 并依次执行写入和读取操作：</span><span class="sxs-lookup"><span data-stu-id="9831c-230">The example below initializes **UART0** and performs a write followed by a read:</span></span>


```csharp
using Windows.Storage.Streams;
using Windows.Devices.Enumeration;
using Windows.Devices.SerialCommunication;

public async void Serial()
{
    string aqs = SerialDevice.GetDeviceSelector("UART0");                   /* Find the selector string for the serial device   */
    var dis = await DeviceInformation.FindAllAsync(aqs);                    /* Find the serial device with our selector string  */
    SerialDevice SerialPort = await SerialDevice.FromIdAsync(dis[0].Id);    /* Create an serial device with our selected device */

    /* Configure serial settings */
    SerialPort.WriteTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.ReadTimeout = TimeSpan.FromMilliseconds(1000);
    SerialPort.BaudRate = 9600;                                             /* mini UART: only standard baudrates */
    SerialPort.Parity = SerialParity.None;                                  /* mini UART: no parities */  
    SerialPort.StopBits = SerialStopBitCount.One;                           /* mini UART: 1 stop bit */
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

<span data-ttu-id="9831c-231">请注意，必须将以下功能添加到 UWP 项目中的 **Package.appxmanifest** 文件，才能运行串行 UART 代码：</span><span class="sxs-lookup"><span data-stu-id="9831c-231">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="9831c-232">Visual Studio 2017 在清单设计器 （appxmanifest 文件的可视编辑器） 的影响 serialcommunication 功能中有一个已知的 bug。</span><span class="sxs-lookup"><span data-stu-id="9831c-232">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="9831c-233">如果你 appxmanifest 添加 serialcommunication 功能，修改与设计器在 appxmanifest 将损坏你 appxmanifest （设备 xml 子将会丢失）。</span><span class="sxs-lookup"><span data-stu-id="9831c-233">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="9831c-234">可以解决此问题通过手动编辑 appxmanifest 通过右键单击你的 appxmanifest 并从上下文菜单中选择查看代码。</span><span class="sxs-lookup"><span data-stu-id="9831c-234">You can workaround this problem by hand editting the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="9831c-235">I2C 总线</span><span class="sxs-lookup"><span data-stu-id="9831c-235">I2C Bus</span></span>

<span data-ttu-id="9831c-236">让我们看一下此设备上可用的 I2C 总线。</span><span class="sxs-lookup"><span data-stu-id="9831c-236">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="9831c-237">I2C 概述</span><span class="sxs-lookup"><span data-stu-id="9831c-237">I2C Overview</span></span>

<span data-ttu-id="9831c-238">排针上公开了一个 I2C 控制器 **I2C1**，带有 **SDA** 和 **SCL** 两条线。</span><span class="sxs-lookup"><span data-stu-id="9831c-238">There is one I2C controller **I2C1** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="9831c-239">用于此总线的 1.8K&#x2126; 内部上拉电阻已安装在开发板上。</span><span class="sxs-lookup"><span data-stu-id="9831c-239">1.8K&#x2126; internal pull-up resistors are already installed on the board for this bus.</span></span>

> | <span data-ttu-id="9831c-240">信号名称</span><span class="sxs-lookup"><span data-stu-id="9831c-240">Signal Name</span></span> | <span data-ttu-id="9831c-241">标头的 Pin 号码</span><span class="sxs-lookup"><span data-stu-id="9831c-241">Header Pin Number</span></span> | <span data-ttu-id="9831c-242">Gpio 数</span><span class="sxs-lookup"><span data-stu-id="9831c-242">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="9831c-243">SDA</span><span class="sxs-lookup"><span data-stu-id="9831c-243">SDA</span></span>         | <span data-ttu-id="9831c-244">3</span><span class="sxs-lookup"><span data-stu-id="9831c-244">3</span></span>                 | <span data-ttu-id="9831c-245">2</span><span class="sxs-lookup"><span data-stu-id="9831c-245">2</span></span>           |
> | <span data-ttu-id="9831c-246">SCL</span><span class="sxs-lookup"><span data-stu-id="9831c-246">SCL</span></span>         | <span data-ttu-id="9831c-247">5</span><span class="sxs-lookup"><span data-stu-id="9831c-247">5</span></span>                 | <span data-ttu-id="9831c-248">3</span><span class="sxs-lookup"><span data-stu-id="9831c-248">3</span></span>           |

<span data-ttu-id="9831c-249">下面的示例将初始化 **I2C1** 并将数据写入地址为 **0x40** 的 I2C 设备：</span><span class="sxs-lookup"><span data-stu-id="9831c-249">The example below initializes **I2C1** and writes data to an I2C device with address **0x40**:</span></span>

```csharp
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

## <a name="spi-bus"></a><span data-ttu-id="9831c-250">SPI 总线</span><span class="sxs-lookup"><span data-stu-id="9831c-250">SPI Bus</span></span>

<span data-ttu-id="9831c-251">SPI 总线的两个控制器上有 RPi2/3。</span><span class="sxs-lookup"><span data-stu-id="9831c-251">There are two SPI bus controllers available on the RPi2/3.</span></span>

### <a name="spi0"></a><span data-ttu-id="9831c-252">SPI0</span><span class="sxs-lookup"><span data-stu-id="9831c-252">SPI0</span></span>

> | <span data-ttu-id="9831c-253">信号名称</span><span class="sxs-lookup"><span data-stu-id="9831c-253">Signal Name</span></span> | <span data-ttu-id="9831c-254">标头的 Pin 号码</span><span class="sxs-lookup"><span data-stu-id="9831c-254">Header Pin Number</span></span> | <span data-ttu-id="9831c-255">Gpio 数</span><span class="sxs-lookup"><span data-stu-id="9831c-255">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="9831c-256">MOSI</span><span class="sxs-lookup"><span data-stu-id="9831c-256">MOSI</span></span>        | <span data-ttu-id="9831c-257">19</span><span class="sxs-lookup"><span data-stu-id="9831c-257">19</span></span>                | <span data-ttu-id="9831c-258">10</span><span class="sxs-lookup"><span data-stu-id="9831c-258">10</span></span>          |
> | <span data-ttu-id="9831c-259">MISO</span><span class="sxs-lookup"><span data-stu-id="9831c-259">MISO</span></span>        | <span data-ttu-id="9831c-260">21</span><span class="sxs-lookup"><span data-stu-id="9831c-260">21</span></span>                | <span data-ttu-id="9831c-261">9</span><span class="sxs-lookup"><span data-stu-id="9831c-261">9</span></span>           |
> | <span data-ttu-id="9831c-262">SCLK</span><span class="sxs-lookup"><span data-stu-id="9831c-262">SCLK</span></span>        | <span data-ttu-id="9831c-263">23</span><span class="sxs-lookup"><span data-stu-id="9831c-263">23</span></span>                | <span data-ttu-id="9831c-264">11</span><span class="sxs-lookup"><span data-stu-id="9831c-264">11</span></span>          |
> | <span data-ttu-id="9831c-265">CS0</span><span class="sxs-lookup"><span data-stu-id="9831c-265">CS0</span></span>         | <span data-ttu-id="9831c-266">24</span><span class="sxs-lookup"><span data-stu-id="9831c-266">24</span></span>                | <span data-ttu-id="9831c-267">8</span><span class="sxs-lookup"><span data-stu-id="9831c-267">8</span></span>           |
> | <span data-ttu-id="9831c-268">CS1</span><span class="sxs-lookup"><span data-stu-id="9831c-268">CS1</span></span>         | <span data-ttu-id="9831c-269">26</span><span class="sxs-lookup"><span data-stu-id="9831c-269">26</span></span>                | <span data-ttu-id="9831c-270">7</span><span class="sxs-lookup"><span data-stu-id="9831c-270">7</span></span>           |

### <a name="spi1"></a><span data-ttu-id="9831c-271">SPI1</span><span class="sxs-lookup"><span data-stu-id="9831c-271">SPI1</span></span>

> | <span data-ttu-id="9831c-272">信号名称</span><span class="sxs-lookup"><span data-stu-id="9831c-272">Signal Name</span></span> | <span data-ttu-id="9831c-273">标头的 Pin 号码</span><span class="sxs-lookup"><span data-stu-id="9831c-273">Header Pin Number</span></span> | <span data-ttu-id="9831c-274">Gpio 数</span><span class="sxs-lookup"><span data-stu-id="9831c-274">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="9831c-275">MOSI</span><span class="sxs-lookup"><span data-stu-id="9831c-275">MOSI</span></span>        | <span data-ttu-id="9831c-276">38</span><span class="sxs-lookup"><span data-stu-id="9831c-276">38</span></span>                | <span data-ttu-id="9831c-277">20</span><span class="sxs-lookup"><span data-stu-id="9831c-277">20</span></span>          |
> | <span data-ttu-id="9831c-278">MISO</span><span class="sxs-lookup"><span data-stu-id="9831c-278">MISO</span></span>        | <span data-ttu-id="9831c-279">35</span><span class="sxs-lookup"><span data-stu-id="9831c-279">35</span></span>                | <span data-ttu-id="9831c-280">19</span><span class="sxs-lookup"><span data-stu-id="9831c-280">19</span></span>          |
> | <span data-ttu-id="9831c-281">SCLK</span><span class="sxs-lookup"><span data-stu-id="9831c-281">SCLK</span></span>        | <span data-ttu-id="9831c-282">40</span><span class="sxs-lookup"><span data-stu-id="9831c-282">40</span></span>                | <span data-ttu-id="9831c-283">21</span><span class="sxs-lookup"><span data-stu-id="9831c-283">21</span></span>          |
> | <span data-ttu-id="9831c-284">CS0</span><span class="sxs-lookup"><span data-stu-id="9831c-284">CS0</span></span>         | <span data-ttu-id="9831c-285">36</span><span class="sxs-lookup"><span data-stu-id="9831c-285">36</span></span>                | <span data-ttu-id="9831c-286">16</span><span class="sxs-lookup"><span data-stu-id="9831c-286">16</span></span>          |


### <a name="spi-sample"></a><span data-ttu-id="9831c-287">SPI 示例</span><span class="sxs-lookup"><span data-stu-id="9831c-287">SPI Sample</span></span>

<span data-ttu-id="9831c-288">举例说明如何执行 SPI 总线上编写**SPI0**使用芯片 select 0 如下所示：</span><span class="sxs-lookup"><span data-stu-id="9831c-288">An example of how to perform a SPI write on bus **SPI0** using chip select 0 is shown below:</span></span>

```csharp
using Windows.Devices.Enumeration;
using Windows.Devices.Spi;

public async void SPI()
{
    // Use chip select line CS0
    var settings = new SpiConnectionSettings(0);
    // Set clock to 10MHz 
    settings.ClockFrequency = 10000000;

    // Get a selector string that will return our wanted SPI controller
    string aqs = SpiDevice.GetDeviceSelector("SPI0");
    
    // Find the SPI bus controller devices with our selector string
    var dis = await DeviceInformation.FindAllAsync(aqs);
    
    // Create an SpiDevice with our selected bus controller and Spi settings
    using (SpiDevice device = await SpiDevice.FromIdAsync(dis[0].Id, settings))
    {
        byte[] writeBuf = { 0x01, 0x02, 0x03, 0x04 };
        device.Write(writeBuf);
    }
}
```

