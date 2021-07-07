---
title: Raspberry Pi 2 & 3 引脚映射
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解 Raspberry Pi 2 和 3 的引脚映射功能。
keywords: windows iot， Rasperry Pi 2， Raspberry Pi 3， 引脚映射， GPIO
ms.openlocfilehash: 6abad2dbebf192c377e17ce840d7a728011d259d
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229594"
---
# <a name="raspberry-pi-2--3-pin-mappings"></a><span data-ttu-id="c04c1-104">Raspberry Pi 2 & 3 引脚映射</span><span class="sxs-lookup"><span data-stu-id="c04c1-104">Raspberry Pi 2 & 3 Pin Mappings</span></span>

![Raspberry Pi 2 & 3 引脚标头](../../media/PinMappingsRPI/RP2_Pinout.png)

<span data-ttu-id="c04c1-106">Raspberry Pi 2 和 Raspberry Pi 3 的硬件接口通过板上的 40 引脚标头 **J8** 公开。</span><span class="sxs-lookup"><span data-stu-id="c04c1-106">Hardware interfaces for the Raspberry Pi 2 and Raspberry Pi 3 are exposed through the 40-pin header **J8** on the board.</span></span> <span data-ttu-id="c04c1-107">功能包括：</span><span class="sxs-lookup"><span data-stu-id="c04c1-107">Functionality includes:</span></span>

* <span data-ttu-id="c04c1-108">**24x** - GPIO 引脚</span><span class="sxs-lookup"><span data-stu-id="c04c1-108">**24x** - GPIO pins</span></span>
* <span data-ttu-id="c04c1-109">**1x** - RPi3 (UART 仅包含微型 UART) </span><span class="sxs-lookup"><span data-stu-id="c04c1-109">**1x** - Serial UARTs (RPi3 only includes mini UART)</span></span>
* <span data-ttu-id="c04c1-110">**2x** - SPI 总线</span><span class="sxs-lookup"><span data-stu-id="c04c1-110">**2x** - SPI bus</span></span>
* <span data-ttu-id="c04c1-111">**1x** - I2C 总线</span><span class="sxs-lookup"><span data-stu-id="c04c1-111">**1x** - I2C bus</span></span>
* <span data-ttu-id="c04c1-112">**2x** - 5V 电源引脚</span><span class="sxs-lookup"><span data-stu-id="c04c1-112">**2x** - 5V power pins</span></span>
* <span data-ttu-id="c04c1-113">**2x** - 3.3V 电源引脚</span><span class="sxs-lookup"><span data-stu-id="c04c1-113">**2x** - 3.3V power pins</span></span>
* <span data-ttu-id="c04c1-114">**8x** - 地引脚</span><span class="sxs-lookup"><span data-stu-id="c04c1-114">**8x** - Ground pins</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="c04c1-115">GPIO 引脚</span><span class="sxs-lookup"><span data-stu-id="c04c1-115">GPIO Pins</span></span>

<span data-ttu-id="c04c1-116">让我们看看此设备上提供的 GPIO。</span><span class="sxs-lookup"><span data-stu-id="c04c1-116">Let's look at the GPIO available on this device.</span></span>

### <a name="gpio-pin-overview"></a><span data-ttu-id="c04c1-117">GPIO 引脚概述</span><span class="sxs-lookup"><span data-stu-id="c04c1-117">GPIO Pin Overview</span></span>

<span data-ttu-id="c04c1-118">可通过 API 访问以下 GPIO 引脚：</span><span class="sxs-lookup"><span data-stu-id="c04c1-118">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="c04c1-119">GPIO#</span><span class="sxs-lookup"><span data-stu-id="c04c1-119">GPIO#</span></span> | <span data-ttu-id="c04c1-120">打开电源拉取</span><span class="sxs-lookup"><span data-stu-id="c04c1-120">Power-on Pull</span></span> | <span data-ttu-id="c04c1-121">备用函数</span><span class="sxs-lookup"><span data-stu-id="c04c1-121">Alternate Functions</span></span> | <span data-ttu-id="c04c1-122">标头引脚</span><span class="sxs-lookup"><span data-stu-id="c04c1-122">Header Pin</span></span>         |
> |-------|---------------|---------------------|--------------------|
> | <span data-ttu-id="c04c1-123">2</span><span class="sxs-lookup"><span data-stu-id="c04c1-123">2</span></span>     | <span data-ttu-id="c04c1-124">PullUp</span><span class="sxs-lookup"><span data-stu-id="c04c1-124">PullUp</span></span>        | <span data-ttu-id="c04c1-125">I2C1 SDA</span><span class="sxs-lookup"><span data-stu-id="c04c1-125">I2C1 SDA</span></span>            | <span data-ttu-id="c04c1-126">3</span><span class="sxs-lookup"><span data-stu-id="c04c1-126">3</span></span>                  |
> | <span data-ttu-id="c04c1-127">3</span><span class="sxs-lookup"><span data-stu-id="c04c1-127">3</span></span>     | <span data-ttu-id="c04c1-128">PullUp</span><span class="sxs-lookup"><span data-stu-id="c04c1-128">PullUp</span></span>        | <span data-ttu-id="c04c1-129">I2C1 SCL</span><span class="sxs-lookup"><span data-stu-id="c04c1-129">I2C1 SCL</span></span>            | <span data-ttu-id="c04c1-130">5</span><span class="sxs-lookup"><span data-stu-id="c04c1-130">5</span></span>                  |
> | <span data-ttu-id="c04c1-131">4</span><span class="sxs-lookup"><span data-stu-id="c04c1-131">4</span></span>     | <span data-ttu-id="c04c1-132">PullUp</span><span class="sxs-lookup"><span data-stu-id="c04c1-132">PullUp</span></span>        |                     | <span data-ttu-id="c04c1-133">7</span><span class="sxs-lookup"><span data-stu-id="c04c1-133">7</span></span>                  |
> | <span data-ttu-id="c04c1-134">5</span><span class="sxs-lookup"><span data-stu-id="c04c1-134">5</span></span>     | <span data-ttu-id="c04c1-135">PullUp</span><span class="sxs-lookup"><span data-stu-id="c04c1-135">PullUp</span></span>        |                     | <span data-ttu-id="c04c1-136">29</span><span class="sxs-lookup"><span data-stu-id="c04c1-136">29</span></span>                 |
> | <span data-ttu-id="c04c1-137">6</span><span class="sxs-lookup"><span data-stu-id="c04c1-137">6</span></span>     | <span data-ttu-id="c04c1-138">PullUp</span><span class="sxs-lookup"><span data-stu-id="c04c1-138">PullUp</span></span>        |                     | <span data-ttu-id="c04c1-139">31</span><span class="sxs-lookup"><span data-stu-id="c04c1-139">31</span></span>                 |
> | <span data-ttu-id="c04c1-140">7</span><span class="sxs-lookup"><span data-stu-id="c04c1-140">7</span></span>     | <span data-ttu-id="c04c1-141">PullUp</span><span class="sxs-lookup"><span data-stu-id="c04c1-141">PullUp</span></span>        | <span data-ttu-id="c04c1-142">SPI0 CS1</span><span class="sxs-lookup"><span data-stu-id="c04c1-142">SPI0 CS1</span></span>            | <span data-ttu-id="c04c1-143">26</span><span class="sxs-lookup"><span data-stu-id="c04c1-143">26</span></span>                 |
> | <span data-ttu-id="c04c1-144">8</span><span class="sxs-lookup"><span data-stu-id="c04c1-144">8</span></span>     | <span data-ttu-id="c04c1-145">PullUp</span><span class="sxs-lookup"><span data-stu-id="c04c1-145">PullUp</span></span>        | <span data-ttu-id="c04c1-146">SPI0 CS0</span><span class="sxs-lookup"><span data-stu-id="c04c1-146">SPI0 CS0</span></span>            | <span data-ttu-id="c04c1-147">24</span><span class="sxs-lookup"><span data-stu-id="c04c1-147">24</span></span>                 |
> | <span data-ttu-id="c04c1-148">9</span><span class="sxs-lookup"><span data-stu-id="c04c1-148">9</span></span>     | <span data-ttu-id="c04c1-149">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-149">PullDown</span></span>      | <span data-ttu-id="c04c1-150">SPI0 MISO</span><span class="sxs-lookup"><span data-stu-id="c04c1-150">SPI0 MISO</span></span>           | <span data-ttu-id="c04c1-151">21</span><span class="sxs-lookup"><span data-stu-id="c04c1-151">21</span></span>                 |
> | <span data-ttu-id="c04c1-152">10</span><span class="sxs-lookup"><span data-stu-id="c04c1-152">10</span></span>    | <span data-ttu-id="c04c1-153">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-153">PullDown</span></span>      | <span data-ttu-id="c04c1-154">SPI0 MOSI</span><span class="sxs-lookup"><span data-stu-id="c04c1-154">SPI0 MOSI</span></span>           | <span data-ttu-id="c04c1-155">19</span><span class="sxs-lookup"><span data-stu-id="c04c1-155">19</span></span>                 |
> | <span data-ttu-id="c04c1-156">11</span><span class="sxs-lookup"><span data-stu-id="c04c1-156">11</span></span>    | <span data-ttu-id="c04c1-157">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-157">PullDown</span></span>      | <span data-ttu-id="c04c1-158">SPI0 SCLK</span><span class="sxs-lookup"><span data-stu-id="c04c1-158">SPI0 SCLK</span></span>           | <span data-ttu-id="c04c1-159">23</span><span class="sxs-lookup"><span data-stu-id="c04c1-159">23</span></span>                 |
> | <span data-ttu-id="c04c1-160">12</span><span class="sxs-lookup"><span data-stu-id="c04c1-160">12</span></span>    | <span data-ttu-id="c04c1-161">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-161">PullDown</span></span>      |                     | <span data-ttu-id="c04c1-162">32</span><span class="sxs-lookup"><span data-stu-id="c04c1-162">32</span></span>                 |
> | <span data-ttu-id="c04c1-163">13</span><span class="sxs-lookup"><span data-stu-id="c04c1-163">13</span></span>    | <span data-ttu-id="c04c1-164">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-164">PullDown</span></span>      |                     | <span data-ttu-id="c04c1-165">33</span><span class="sxs-lookup"><span data-stu-id="c04c1-165">33</span></span>                 |
> | <span data-ttu-id="c04c1-166">16</span><span class="sxs-lookup"><span data-stu-id="c04c1-166">16</span></span>    | <span data-ttu-id="c04c1-167">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-167">PullDown</span></span>      | <span data-ttu-id="c04c1-168">SPI1 CS0</span><span class="sxs-lookup"><span data-stu-id="c04c1-168">SPI1 CS0</span></span>            | <span data-ttu-id="c04c1-169">36</span><span class="sxs-lookup"><span data-stu-id="c04c1-169">36</span></span>                 |
> | <span data-ttu-id="c04c1-170">17</span><span class="sxs-lookup"><span data-stu-id="c04c1-170">17</span></span>    | <span data-ttu-id="c04c1-171">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-171">PullDown</span></span>      |                     | <span data-ttu-id="c04c1-172">11</span><span class="sxs-lookup"><span data-stu-id="c04c1-172">11</span></span>                 |
> | <span data-ttu-id="c04c1-173">18</span><span class="sxs-lookup"><span data-stu-id="c04c1-173">18</span></span>    | <span data-ttu-id="c04c1-174">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-174">PullDown</span></span>      |                     | <span data-ttu-id="c04c1-175">12</span><span class="sxs-lookup"><span data-stu-id="c04c1-175">12</span></span>                 |
> | <span data-ttu-id="c04c1-176">19</span><span class="sxs-lookup"><span data-stu-id="c04c1-176">19</span></span>    | <span data-ttu-id="c04c1-177">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-177">PullDown</span></span>      | <span data-ttu-id="c04c1-178">SPI1 MISO</span><span class="sxs-lookup"><span data-stu-id="c04c1-178">SPI1 MISO</span></span>           | <span data-ttu-id="c04c1-179">35</span><span class="sxs-lookup"><span data-stu-id="c04c1-179">35</span></span>                 |
> | <span data-ttu-id="c04c1-180">20</span><span class="sxs-lookup"><span data-stu-id="c04c1-180">20</span></span>    | <span data-ttu-id="c04c1-181">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-181">PullDown</span></span>      | <span data-ttu-id="c04c1-182">SPI1 MOSI</span><span class="sxs-lookup"><span data-stu-id="c04c1-182">SPI1 MOSI</span></span>           | <span data-ttu-id="c04c1-183">38</span><span class="sxs-lookup"><span data-stu-id="c04c1-183">38</span></span>                 |
> | <span data-ttu-id="c04c1-184">21</span><span class="sxs-lookup"><span data-stu-id="c04c1-184">21</span></span>    | <span data-ttu-id="c04c1-185">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-185">PullDown</span></span>      | <span data-ttu-id="c04c1-186">SPI1 SCLK</span><span class="sxs-lookup"><span data-stu-id="c04c1-186">SPI1 SCLK</span></span>           | <span data-ttu-id="c04c1-187">40</span><span class="sxs-lookup"><span data-stu-id="c04c1-187">40</span></span>                 |
> | <span data-ttu-id="c04c1-188">22</span><span class="sxs-lookup"><span data-stu-id="c04c1-188">22</span></span>    | <span data-ttu-id="c04c1-189">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-189">PullDown</span></span>      |                     | <span data-ttu-id="c04c1-190">15</span><span class="sxs-lookup"><span data-stu-id="c04c1-190">15</span></span>                 |
> | <span data-ttu-id="c04c1-191">23</span><span class="sxs-lookup"><span data-stu-id="c04c1-191">23</span></span>    | <span data-ttu-id="c04c1-192">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-192">PullDown</span></span>      |                     | <span data-ttu-id="c04c1-193">16</span><span class="sxs-lookup"><span data-stu-id="c04c1-193">16</span></span>                 |
> | <span data-ttu-id="c04c1-194">24</span><span class="sxs-lookup"><span data-stu-id="c04c1-194">24</span></span>    | <span data-ttu-id="c04c1-195">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-195">PullDown</span></span>      |                     | <span data-ttu-id="c04c1-196">18</span><span class="sxs-lookup"><span data-stu-id="c04c1-196">18</span></span>                 |
> | <span data-ttu-id="c04c1-197">25</span><span class="sxs-lookup"><span data-stu-id="c04c1-197">25</span></span>    | <span data-ttu-id="c04c1-198">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-198">PullDown</span></span>      |                     | <span data-ttu-id="c04c1-199">22</span><span class="sxs-lookup"><span data-stu-id="c04c1-199">22</span></span>                 |
> | <span data-ttu-id="c04c1-200">26</span><span class="sxs-lookup"><span data-stu-id="c04c1-200">26</span></span>    | <span data-ttu-id="c04c1-201">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-201">PullDown</span></span>      |                     | <span data-ttu-id="c04c1-202">37</span><span class="sxs-lookup"><span data-stu-id="c04c1-202">37</span></span>                 |
> | <span data-ttu-id="c04c1-203">27</span><span class="sxs-lookup"><span data-stu-id="c04c1-203">27</span></span>    | <span data-ttu-id="c04c1-204">PullDown</span><span class="sxs-lookup"><span data-stu-id="c04c1-204">PullDown</span></span>      |                     | <span data-ttu-id="c04c1-205">13</span><span class="sxs-lookup"><span data-stu-id="c04c1-205">13</span></span>                 |
> | <span data-ttu-id="c04c1-206">35\*</span><span class="sxs-lookup"><span data-stu-id="c04c1-206">35\*</span></span>   | <span data-ttu-id="c04c1-207">PullUp</span><span class="sxs-lookup"><span data-stu-id="c04c1-207">PullUp</span></span>        |                     | <span data-ttu-id="c04c1-208">红色电源 LED</span><span class="sxs-lookup"><span data-stu-id="c04c1-208">Red Power LED</span></span>      |
> | <span data-ttu-id="c04c1-209">47\*</span><span class="sxs-lookup"><span data-stu-id="c04c1-209">47\*</span></span>   | <span data-ttu-id="c04c1-210">PullUp</span><span class="sxs-lookup"><span data-stu-id="c04c1-210">PullUp</span></span>        |                     | <span data-ttu-id="c04c1-211">绿色活动 LED</span><span class="sxs-lookup"><span data-stu-id="c04c1-211">Green Activity LED</span></span> |

<span data-ttu-id="c04c1-212">\* = Raspberry Pi 2 ONLY。</span><span class="sxs-lookup"><span data-stu-id="c04c1-212">\* = Raspberry Pi 2 ONLY.</span></span> <span data-ttu-id="c04c1-213">GPIO 35 & 47 在 Raspberry Pi 3 上不可用。</span><span class="sxs-lookup"><span data-stu-id="c04c1-213">GPIO 35 & 47 are not available on Raspberry Pi 3.</span></span>

### <a name="gpio-sample"></a><span data-ttu-id="c04c1-214">GPIO 示例</span><span class="sxs-lookup"><span data-stu-id="c04c1-214">GPIO Sample</span></span>

<span data-ttu-id="c04c1-215">例如，以下代码将 **GPIO 5** 作为输出打开，在引脚上写出数字 **"1"：**</span><span class="sxs-lookup"><span data-stu-id="c04c1-215">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>

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

<span data-ttu-id="c04c1-216">打开引脚时，它将位于其打开状态，可能包括拉取器。</span><span class="sxs-lookup"><span data-stu-id="c04c1-216">When you open a pin, it will be in its power-on state, which may include a pull resistor.</span></span> <span data-ttu-id="c04c1-217">若要断开拉取器并获取高抗抗性输入，将驱动器模式设置为 GpioPinDriveMode.Input：</span><span class="sxs-lookup"><span data-stu-id="c04c1-217">To disconnect the pull resistors and get a high-impedance input, set the drive mode to GpioPinDriveMode.Input:</span></span>
```
    pin.SetDriveMode(GpioPinDriveMode.Input);
```
<span data-ttu-id="c04c1-218">当引脚关闭时，它将还原为其打开状态。</span><span class="sxs-lookup"><span data-stu-id="c04c1-218">When a pin is closed, it reverts to its power-on state.</span></span>

### <a name="pin-muxing"></a><span data-ttu-id="c04c1-219">固定多路复用</span><span class="sxs-lookup"><span data-stu-id="c04c1-219">Pin Muxing</span></span>

<span data-ttu-id="c04c1-220">某些 GPIO 引脚可以执行多个功能。</span><span class="sxs-lookup"><span data-stu-id="c04c1-220">Some GPIO pins can perform multiple functions.</span></span> <span data-ttu-id="c04c1-221">默认情况下，引脚配置为 GPIO 输入。</span><span class="sxs-lookup"><span data-stu-id="c04c1-221">By default, pins are configured as GPIO inputs.</span></span> <span data-ttu-id="c04c1-222">通过调用 或 打开备用函数时，该函数所需的引脚 `I2cDevice.FromIdAsync()` `SpiDevice.FromIdAsync()` ("muxed") 切换到正确的函数。</span><span class="sxs-lookup"><span data-stu-id="c04c1-222">When you open an alternate function by calling `I2cDevice.FromIdAsync()` or `SpiDevice.FromIdAsync()` , the pins required by the function are automatically switched ("muxed") to the correct function.</span></span> <span data-ttu-id="c04c1-223">通过调用 或 关闭设备 `I2cDevice.Dispose()` 时 `SpiDevice.Dispose()` ，引脚将恢复为默认功能。</span><span class="sxs-lookup"><span data-stu-id="c04c1-223">When the device is closed by calling `I2cDevice.Dispose()` or `SpiDevice.Dispose()`, the pins revert back to their default function.</span></span> <span data-ttu-id="c04c1-224">如果尝试同时对两个不同的函数使用 pin，则当你尝试打开冲突函数时，将引发异常。</span><span class="sxs-lookup"><span data-stu-id="c04c1-224">If you try to use a pin for two different functions at once, an exception will be thrown when you try to open the conflicting function.</span></span> <span data-ttu-id="c04c1-225">例如，</span><span class="sxs-lookup"><span data-stu-id="c04c1-225">For example,</span></span>

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

## <a name="serial-uart"></a><span data-ttu-id="c04c1-226">串行 UART</span><span class="sxs-lookup"><span data-stu-id="c04c1-226">Serial UART</span></span>

<span data-ttu-id="c04c1-227">RPi2/3 上提供了一个串行 **UART：UART0**</span><span class="sxs-lookup"><span data-stu-id="c04c1-227">There is one Serial UART available on the RPi2/3: **UART0**</span></span>

* <span data-ttu-id="c04c1-228">引脚 8 - **UART0 TX**</span><span class="sxs-lookup"><span data-stu-id="c04c1-228">Pin 8  - **UART0 TX**</span></span>
* <span data-ttu-id="c04c1-229">引脚 10 - **UART0 RX**</span><span class="sxs-lookup"><span data-stu-id="c04c1-229">Pin 10  - **UART0 RX**</span></span>

<span data-ttu-id="c04c1-230">下面的示例初始化 **UART0** 并执行写入，然后执行读取：</span><span class="sxs-lookup"><span data-stu-id="c04c1-230">The example below initializes **UART0** and performs a write followed by a read:</span></span>


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

<span data-ttu-id="c04c1-231">请注意，必须将以下功能添加到 UWP 项目中 **的 Package.appxmanifest** 文件，以运行串行 UART 代码：</span><span class="sxs-lookup"><span data-stu-id="c04c1-231">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="c04c1-232">Visual Studio 2017 在清单设计器中 (appxmanifest 文件的可视化编辑器中) 影响串行通信功能。</span><span class="sxs-lookup"><span data-stu-id="c04c1-232">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="c04c1-233">如果 appxmanifest 添加了串行通信功能，则使用设计器修改 appxmanifest 将损坏 appxmanifest (设备 xml 子级将丢失) 。</span><span class="sxs-lookup"><span data-stu-id="c04c1-233">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="c04c1-234">可以通过手动编辑 appxmanifest 来解决此问题，方法是右键单击 appxmanifest，然后从上下文菜单中选择"查看代码"。</span><span class="sxs-lookup"><span data-stu-id="c04c1-234">You can work around this problem by hand editing the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="c04c1-235">I2C 总线</span><span class="sxs-lookup"><span data-stu-id="c04c1-235">I2C Bus</span></span>

<span data-ttu-id="c04c1-236">让我们看看此设备上提供的 I2C 总线。</span><span class="sxs-lookup"><span data-stu-id="c04c1-236">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="c04c1-237">I2C 概述</span><span class="sxs-lookup"><span data-stu-id="c04c1-237">I2C Overview</span></span>

<span data-ttu-id="c04c1-238">在引脚标头上公开了一个 **I2C 控制器 I2C1，** 包含两行 **SDA 和** **SCL**。</span><span class="sxs-lookup"><span data-stu-id="c04c1-238">There is one I2C controller **I2C1** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="c04c1-239">此总线&#x2126;板中已安装 1.8K 个内部拉取开关。</span><span class="sxs-lookup"><span data-stu-id="c04c1-239">1.8K&#x2126; internal pull-up resistors are already installed on the board for this bus.</span></span>

> | <span data-ttu-id="c04c1-240">信号名称</span><span class="sxs-lookup"><span data-stu-id="c04c1-240">Signal Name</span></span> | <span data-ttu-id="c04c1-241">标头引脚编号</span><span class="sxs-lookup"><span data-stu-id="c04c1-241">Header Pin Number</span></span> | <span data-ttu-id="c04c1-242">Gpio 编号</span><span class="sxs-lookup"><span data-stu-id="c04c1-242">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="c04c1-243">Sda</span><span class="sxs-lookup"><span data-stu-id="c04c1-243">SDA</span></span>         | <span data-ttu-id="c04c1-244">3</span><span class="sxs-lookup"><span data-stu-id="c04c1-244">3</span></span>                 | <span data-ttu-id="c04c1-245">2</span><span class="sxs-lookup"><span data-stu-id="c04c1-245">2</span></span>           |
> | <span data-ttu-id="c04c1-246">SCL</span><span class="sxs-lookup"><span data-stu-id="c04c1-246">SCL</span></span>         | <span data-ttu-id="c04c1-247">5</span><span class="sxs-lookup"><span data-stu-id="c04c1-247">5</span></span>                 | <span data-ttu-id="c04c1-248">3</span><span class="sxs-lookup"><span data-stu-id="c04c1-248">3</span></span>           |

<span data-ttu-id="c04c1-249">以下示例初始化 **I2C1，** 将数据写入地址为 的 I2C **0x40：**</span><span class="sxs-lookup"><span data-stu-id="c04c1-249">The example below initializes **I2C1** and writes data to an I2C device with address **0x40**:</span></span>

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

## <a name="spi-bus"></a><span data-ttu-id="c04c1-250">SPI 总线</span><span class="sxs-lookup"><span data-stu-id="c04c1-250">SPI Bus</span></span>

<span data-ttu-id="c04c1-251">RPi2/3 上提供两个 SPI 总线控制器。</span><span class="sxs-lookup"><span data-stu-id="c04c1-251">There are two SPI bus controllers available on the RPi2/3.</span></span>

### <a name="spi0"></a><span data-ttu-id="c04c1-252">SPI0</span><span class="sxs-lookup"><span data-stu-id="c04c1-252">SPI0</span></span>

> | <span data-ttu-id="c04c1-253">信号名称</span><span class="sxs-lookup"><span data-stu-id="c04c1-253">Signal Name</span></span> | <span data-ttu-id="c04c1-254">标头引脚编号</span><span class="sxs-lookup"><span data-stu-id="c04c1-254">Header Pin Number</span></span> | <span data-ttu-id="c04c1-255">Gpio 编号</span><span class="sxs-lookup"><span data-stu-id="c04c1-255">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="c04c1-256">MOSI</span><span class="sxs-lookup"><span data-stu-id="c04c1-256">MOSI</span></span>        | <span data-ttu-id="c04c1-257">19</span><span class="sxs-lookup"><span data-stu-id="c04c1-257">19</span></span>                | <span data-ttu-id="c04c1-258">10</span><span class="sxs-lookup"><span data-stu-id="c04c1-258">10</span></span>          |
> | <span data-ttu-id="c04c1-259">酱</span><span class="sxs-lookup"><span data-stu-id="c04c1-259">MISO</span></span>        | <span data-ttu-id="c04c1-260">21</span><span class="sxs-lookup"><span data-stu-id="c04c1-260">21</span></span>                | <span data-ttu-id="c04c1-261">9</span><span class="sxs-lookup"><span data-stu-id="c04c1-261">9</span></span>           |
> | <span data-ttu-id="c04c1-262">SCLK</span><span class="sxs-lookup"><span data-stu-id="c04c1-262">SCLK</span></span>        | <span data-ttu-id="c04c1-263">23</span><span class="sxs-lookup"><span data-stu-id="c04c1-263">23</span></span>                | <span data-ttu-id="c04c1-264">11</span><span class="sxs-lookup"><span data-stu-id="c04c1-264">11</span></span>          |
> | <span data-ttu-id="c04c1-265">CS0</span><span class="sxs-lookup"><span data-stu-id="c04c1-265">CS0</span></span>         | <span data-ttu-id="c04c1-266">24</span><span class="sxs-lookup"><span data-stu-id="c04c1-266">24</span></span>                | <span data-ttu-id="c04c1-267">8</span><span class="sxs-lookup"><span data-stu-id="c04c1-267">8</span></span>           |
> | <span data-ttu-id="c04c1-268">CS1</span><span class="sxs-lookup"><span data-stu-id="c04c1-268">CS1</span></span>         | <span data-ttu-id="c04c1-269">26</span><span class="sxs-lookup"><span data-stu-id="c04c1-269">26</span></span>                | <span data-ttu-id="c04c1-270">7</span><span class="sxs-lookup"><span data-stu-id="c04c1-270">7</span></span>           |

### <a name="spi1"></a><span data-ttu-id="c04c1-271">SPI1</span><span class="sxs-lookup"><span data-stu-id="c04c1-271">SPI1</span></span>

> | <span data-ttu-id="c04c1-272">信号名称</span><span class="sxs-lookup"><span data-stu-id="c04c1-272">Signal Name</span></span> | <span data-ttu-id="c04c1-273">标头引脚编号</span><span class="sxs-lookup"><span data-stu-id="c04c1-273">Header Pin Number</span></span> | <span data-ttu-id="c04c1-274">Gpio 编号</span><span class="sxs-lookup"><span data-stu-id="c04c1-274">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="c04c1-275">MOSI</span><span class="sxs-lookup"><span data-stu-id="c04c1-275">MOSI</span></span>        | <span data-ttu-id="c04c1-276">38</span><span class="sxs-lookup"><span data-stu-id="c04c1-276">38</span></span>                | <span data-ttu-id="c04c1-277">20</span><span class="sxs-lookup"><span data-stu-id="c04c1-277">20</span></span>          |
> | <span data-ttu-id="c04c1-278">酱</span><span class="sxs-lookup"><span data-stu-id="c04c1-278">MISO</span></span>        | <span data-ttu-id="c04c1-279">35</span><span class="sxs-lookup"><span data-stu-id="c04c1-279">35</span></span>                | <span data-ttu-id="c04c1-280">19</span><span class="sxs-lookup"><span data-stu-id="c04c1-280">19</span></span>          |
> | <span data-ttu-id="c04c1-281">SCLK</span><span class="sxs-lookup"><span data-stu-id="c04c1-281">SCLK</span></span>        | <span data-ttu-id="c04c1-282">40</span><span class="sxs-lookup"><span data-stu-id="c04c1-282">40</span></span>                | <span data-ttu-id="c04c1-283">21</span><span class="sxs-lookup"><span data-stu-id="c04c1-283">21</span></span>          |
> | <span data-ttu-id="c04c1-284">CS0</span><span class="sxs-lookup"><span data-stu-id="c04c1-284">CS0</span></span>         | <span data-ttu-id="c04c1-285">36</span><span class="sxs-lookup"><span data-stu-id="c04c1-285">36</span></span>                | <span data-ttu-id="c04c1-286">16</span><span class="sxs-lookup"><span data-stu-id="c04c1-286">16</span></span>          |


### <a name="spi-sample"></a><span data-ttu-id="c04c1-287">SPI 示例</span><span class="sxs-lookup"><span data-stu-id="c04c1-287">SPI Sample</span></span>

<span data-ttu-id="c04c1-288">下面显示了如何使用芯片选择 0 在总线 **SPI0** 上执行 SPI 写入的示例：</span><span class="sxs-lookup"><span data-stu-id="c04c1-288">An example of how to perform a SPI write on bus **SPI0** using chip select 0 is shown below:</span></span>

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
