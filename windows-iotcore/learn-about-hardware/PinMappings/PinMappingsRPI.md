---
title: Raspberry Pi 2 & 3 针映射
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解 Raspberry Pi 2 和3的 pin 映射功能。
keywords: windows iot，Rasperry Pi 2，Raspberry Pi 3，固定映射，GPIO
ms.openlocfilehash: cbb2ce0cda197a0a9520a837fc1a0877430c6bcc
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655703"
---
# <a name="raspberry-pi-2--3-pin-mappings"></a><span data-ttu-id="aba0f-104">Raspberry Pi 2 & 3 针映射</span><span class="sxs-lookup"><span data-stu-id="aba0f-104">Raspberry Pi 2 & 3 Pin Mappings</span></span>

![Raspberry Pi 2 & 3 针标题](../../media/PinMappingsRPI/RP2_Pinout.png)

<span data-ttu-id="aba0f-106">Raspberry Pi 2 和 Raspberry Pi 3 的硬件接口通过板上的40针标头 **J8** 公开。</span><span class="sxs-lookup"><span data-stu-id="aba0f-106">Hardware interfaces for the Raspberry Pi 2 and Raspberry Pi 3 are exposed through the 40-pin header **J8** on the board.</span></span> <span data-ttu-id="aba0f-107">功能包括：</span><span class="sxs-lookup"><span data-stu-id="aba0f-107">Functionality includes:</span></span>

* <span data-ttu-id="aba0f-108">**24x** -GPIO 引脚</span><span class="sxs-lookup"><span data-stu-id="aba0f-108">**24x** - GPIO pins</span></span>
* <span data-ttu-id="aba0f-109">**1x** -串行 UARTs (RPi3 仅包含微型 UART) </span><span class="sxs-lookup"><span data-stu-id="aba0f-109">**1x** - Serial UARTs (RPi3 only includes mini UART)</span></span>
* <span data-ttu-id="aba0f-110">**2x** -SPI 总线</span><span class="sxs-lookup"><span data-stu-id="aba0f-110">**2x** - SPI bus</span></span>
* <span data-ttu-id="aba0f-111">**1x** -I2C 总线</span><span class="sxs-lookup"><span data-stu-id="aba0f-111">**1x** - I2C bus</span></span>
* <span data-ttu-id="aba0f-112">**2x** -5v 电源</span><span class="sxs-lookup"><span data-stu-id="aba0f-112">**2x** - 5V power pins</span></span>
* <span data-ttu-id="aba0f-113">**2x** -3.3 v 电源针脚</span><span class="sxs-lookup"><span data-stu-id="aba0f-113">**2x** - 3.3V power pins</span></span>
* <span data-ttu-id="aba0f-114">**8x** -地面针脚</span><span class="sxs-lookup"><span data-stu-id="aba0f-114">**8x** - Ground pins</span></span>

## <a name="gpio-pins"></a><span data-ttu-id="aba0f-115">GPIO Pin</span><span class="sxs-lookup"><span data-stu-id="aba0f-115">GPIO Pins</span></span>

<span data-ttu-id="aba0f-116">让我们看看此设备上的 GPIO 可用。</span><span class="sxs-lookup"><span data-stu-id="aba0f-116">Let's look at the GPIO available on this device.</span></span>

### <a name="gpio-pin-overview"></a><span data-ttu-id="aba0f-117">GPIO Pin 概述</span><span class="sxs-lookup"><span data-stu-id="aba0f-117">GPIO Pin Overview</span></span>

<span data-ttu-id="aba0f-118">以下 GPIO pin 可通过 Api 访问：</span><span class="sxs-lookup"><span data-stu-id="aba0f-118">The following GPIO pins are accessible through APIs:</span></span>

> | <span data-ttu-id="aba0f-119">GPIO#</span><span class="sxs-lookup"><span data-stu-id="aba0f-119">GPIO#</span></span> | <span data-ttu-id="aba0f-120">开机请求</span><span class="sxs-lookup"><span data-stu-id="aba0f-120">Power-on Pull</span></span> | <span data-ttu-id="aba0f-121">备用函数</span><span class="sxs-lookup"><span data-stu-id="aba0f-121">Alternate Functions</span></span> | <span data-ttu-id="aba0f-122">标头 Pin</span><span class="sxs-lookup"><span data-stu-id="aba0f-122">Header Pin</span></span>         |
> |-------|---------------|---------------------|--------------------|
> | <span data-ttu-id="aba0f-123">2</span><span class="sxs-lookup"><span data-stu-id="aba0f-123">2</span></span>     | <span data-ttu-id="aba0f-124">PullUp</span><span class="sxs-lookup"><span data-stu-id="aba0f-124">PullUp</span></span>        | <span data-ttu-id="aba0f-125">I2C1 SDA</span><span class="sxs-lookup"><span data-stu-id="aba0f-125">I2C1 SDA</span></span>            | <span data-ttu-id="aba0f-126">3</span><span class="sxs-lookup"><span data-stu-id="aba0f-126">3</span></span>                  |
> | <span data-ttu-id="aba0f-127">3</span><span class="sxs-lookup"><span data-stu-id="aba0f-127">3</span></span>     | <span data-ttu-id="aba0f-128">PullUp</span><span class="sxs-lookup"><span data-stu-id="aba0f-128">PullUp</span></span>        | <span data-ttu-id="aba0f-129">I2C1 SCL</span><span class="sxs-lookup"><span data-stu-id="aba0f-129">I2C1 SCL</span></span>            | <span data-ttu-id="aba0f-130">5</span><span class="sxs-lookup"><span data-stu-id="aba0f-130">5</span></span>                  |
> | <span data-ttu-id="aba0f-131">4</span><span class="sxs-lookup"><span data-stu-id="aba0f-131">4</span></span>     | <span data-ttu-id="aba0f-132">PullUp</span><span class="sxs-lookup"><span data-stu-id="aba0f-132">PullUp</span></span>        |                     | <span data-ttu-id="aba0f-133">7</span><span class="sxs-lookup"><span data-stu-id="aba0f-133">7</span></span>                  |
> | <span data-ttu-id="aba0f-134">5</span><span class="sxs-lookup"><span data-stu-id="aba0f-134">5</span></span>     | <span data-ttu-id="aba0f-135">PullUp</span><span class="sxs-lookup"><span data-stu-id="aba0f-135">PullUp</span></span>        |                     | <span data-ttu-id="aba0f-136">29</span><span class="sxs-lookup"><span data-stu-id="aba0f-136">29</span></span>                 |
> | <span data-ttu-id="aba0f-137">6</span><span class="sxs-lookup"><span data-stu-id="aba0f-137">6</span></span>     | <span data-ttu-id="aba0f-138">PullUp</span><span class="sxs-lookup"><span data-stu-id="aba0f-138">PullUp</span></span>        |                     | <span data-ttu-id="aba0f-139">31</span><span class="sxs-lookup"><span data-stu-id="aba0f-139">31</span></span>                 |
> | <span data-ttu-id="aba0f-140">7</span><span class="sxs-lookup"><span data-stu-id="aba0f-140">7</span></span>     | <span data-ttu-id="aba0f-141">PullUp</span><span class="sxs-lookup"><span data-stu-id="aba0f-141">PullUp</span></span>        | <span data-ttu-id="aba0f-142">SPI0 CS1</span><span class="sxs-lookup"><span data-stu-id="aba0f-142">SPI0 CS1</span></span>            | <span data-ttu-id="aba0f-143">26</span><span class="sxs-lookup"><span data-stu-id="aba0f-143">26</span></span>                 |
> | <span data-ttu-id="aba0f-144">8</span><span class="sxs-lookup"><span data-stu-id="aba0f-144">8</span></span>     | <span data-ttu-id="aba0f-145">PullUp</span><span class="sxs-lookup"><span data-stu-id="aba0f-145">PullUp</span></span>        | <span data-ttu-id="aba0f-146">SPI0 CS0</span><span class="sxs-lookup"><span data-stu-id="aba0f-146">SPI0 CS0</span></span>            | <span data-ttu-id="aba0f-147">24</span><span class="sxs-lookup"><span data-stu-id="aba0f-147">24</span></span>                 |
> | <span data-ttu-id="aba0f-148">9</span><span class="sxs-lookup"><span data-stu-id="aba0f-148">9</span></span>     | <span data-ttu-id="aba0f-149">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-149">PullDown</span></span>      | <span data-ttu-id="aba0f-150">SPI0 MISO</span><span class="sxs-lookup"><span data-stu-id="aba0f-150">SPI0 MISO</span></span>           | <span data-ttu-id="aba0f-151">21</span><span class="sxs-lookup"><span data-stu-id="aba0f-151">21</span></span>                 |
> | <span data-ttu-id="aba0f-152">10</span><span class="sxs-lookup"><span data-stu-id="aba0f-152">10</span></span>    | <span data-ttu-id="aba0f-153">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-153">PullDown</span></span>      | <span data-ttu-id="aba0f-154">SPI0 MOSI</span><span class="sxs-lookup"><span data-stu-id="aba0f-154">SPI0 MOSI</span></span>           | <span data-ttu-id="aba0f-155">19</span><span class="sxs-lookup"><span data-stu-id="aba0f-155">19</span></span>                 |
> | <span data-ttu-id="aba0f-156">11</span><span class="sxs-lookup"><span data-stu-id="aba0f-156">11</span></span>    | <span data-ttu-id="aba0f-157">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-157">PullDown</span></span>      | <span data-ttu-id="aba0f-158">SPI0 SCLK</span><span class="sxs-lookup"><span data-stu-id="aba0f-158">SPI0 SCLK</span></span>           | <span data-ttu-id="aba0f-159">23</span><span class="sxs-lookup"><span data-stu-id="aba0f-159">23</span></span>                 |
> | <span data-ttu-id="aba0f-160">12</span><span class="sxs-lookup"><span data-stu-id="aba0f-160">12</span></span>    | <span data-ttu-id="aba0f-161">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-161">PullDown</span></span>      |                     | <span data-ttu-id="aba0f-162">32</span><span class="sxs-lookup"><span data-stu-id="aba0f-162">32</span></span>                 |
> | <span data-ttu-id="aba0f-163">13</span><span class="sxs-lookup"><span data-stu-id="aba0f-163">13</span></span>    | <span data-ttu-id="aba0f-164">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-164">PullDown</span></span>      |                     | <span data-ttu-id="aba0f-165">33</span><span class="sxs-lookup"><span data-stu-id="aba0f-165">33</span></span>                 |
> | <span data-ttu-id="aba0f-166">16</span><span class="sxs-lookup"><span data-stu-id="aba0f-166">16</span></span>    | <span data-ttu-id="aba0f-167">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-167">PullDown</span></span>      | <span data-ttu-id="aba0f-168">SPI1 CS0</span><span class="sxs-lookup"><span data-stu-id="aba0f-168">SPI1 CS0</span></span>            | <span data-ttu-id="aba0f-169">36</span><span class="sxs-lookup"><span data-stu-id="aba0f-169">36</span></span>                 |
> | <span data-ttu-id="aba0f-170">17</span><span class="sxs-lookup"><span data-stu-id="aba0f-170">17</span></span>    | <span data-ttu-id="aba0f-171">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-171">PullDown</span></span>      |                     | <span data-ttu-id="aba0f-172">11</span><span class="sxs-lookup"><span data-stu-id="aba0f-172">11</span></span>                 |
> | <span data-ttu-id="aba0f-173">18</span><span class="sxs-lookup"><span data-stu-id="aba0f-173">18</span></span>    | <span data-ttu-id="aba0f-174">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-174">PullDown</span></span>      |                     | <span data-ttu-id="aba0f-175">12</span><span class="sxs-lookup"><span data-stu-id="aba0f-175">12</span></span>                 |
> | <span data-ttu-id="aba0f-176">19</span><span class="sxs-lookup"><span data-stu-id="aba0f-176">19</span></span>    | <span data-ttu-id="aba0f-177">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-177">PullDown</span></span>      | <span data-ttu-id="aba0f-178">SPI1 MISO</span><span class="sxs-lookup"><span data-stu-id="aba0f-178">SPI1 MISO</span></span>           | <span data-ttu-id="aba0f-179">35</span><span class="sxs-lookup"><span data-stu-id="aba0f-179">35</span></span>                 |
> | <span data-ttu-id="aba0f-180">20</span><span class="sxs-lookup"><span data-stu-id="aba0f-180">20</span></span>    | <span data-ttu-id="aba0f-181">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-181">PullDown</span></span>      | <span data-ttu-id="aba0f-182">SPI1 MOSI</span><span class="sxs-lookup"><span data-stu-id="aba0f-182">SPI1 MOSI</span></span>           | <span data-ttu-id="aba0f-183">38</span><span class="sxs-lookup"><span data-stu-id="aba0f-183">38</span></span>                 |
> | <span data-ttu-id="aba0f-184">21</span><span class="sxs-lookup"><span data-stu-id="aba0f-184">21</span></span>    | <span data-ttu-id="aba0f-185">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-185">PullDown</span></span>      | <span data-ttu-id="aba0f-186">SPI1 SCLK</span><span class="sxs-lookup"><span data-stu-id="aba0f-186">SPI1 SCLK</span></span>           | <span data-ttu-id="aba0f-187">40</span><span class="sxs-lookup"><span data-stu-id="aba0f-187">40</span></span>                 |
> | <span data-ttu-id="aba0f-188">22</span><span class="sxs-lookup"><span data-stu-id="aba0f-188">22</span></span>    | <span data-ttu-id="aba0f-189">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-189">PullDown</span></span>      |                     | <span data-ttu-id="aba0f-190">15</span><span class="sxs-lookup"><span data-stu-id="aba0f-190">15</span></span>                 |
> | <span data-ttu-id="aba0f-191">23</span><span class="sxs-lookup"><span data-stu-id="aba0f-191">23</span></span>    | <span data-ttu-id="aba0f-192">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-192">PullDown</span></span>      |                     | <span data-ttu-id="aba0f-193">16</span><span class="sxs-lookup"><span data-stu-id="aba0f-193">16</span></span>                 |
> | <span data-ttu-id="aba0f-194">24</span><span class="sxs-lookup"><span data-stu-id="aba0f-194">24</span></span>    | <span data-ttu-id="aba0f-195">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-195">PullDown</span></span>      |                     | <span data-ttu-id="aba0f-196">18</span><span class="sxs-lookup"><span data-stu-id="aba0f-196">18</span></span>                 |
> | <span data-ttu-id="aba0f-197">25</span><span class="sxs-lookup"><span data-stu-id="aba0f-197">25</span></span>    | <span data-ttu-id="aba0f-198">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-198">PullDown</span></span>      |                     | <span data-ttu-id="aba0f-199">22</span><span class="sxs-lookup"><span data-stu-id="aba0f-199">22</span></span>                 |
> | <span data-ttu-id="aba0f-200">26</span><span class="sxs-lookup"><span data-stu-id="aba0f-200">26</span></span>    | <span data-ttu-id="aba0f-201">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-201">PullDown</span></span>      |                     | <span data-ttu-id="aba0f-202">37</span><span class="sxs-lookup"><span data-stu-id="aba0f-202">37</span></span>                 |
> | <span data-ttu-id="aba0f-203">27</span><span class="sxs-lookup"><span data-stu-id="aba0f-203">27</span></span>    | <span data-ttu-id="aba0f-204">下拉菜单</span><span class="sxs-lookup"><span data-stu-id="aba0f-204">PullDown</span></span>      |                     | <span data-ttu-id="aba0f-205">13</span><span class="sxs-lookup"><span data-stu-id="aba0f-205">13</span></span>                 |
> | <span data-ttu-id="aba0f-206">35 \*</span><span class="sxs-lookup"><span data-stu-id="aba0f-206">35\*</span></span>   | <span data-ttu-id="aba0f-207">PullUp</span><span class="sxs-lookup"><span data-stu-id="aba0f-207">PullUp</span></span>        |                     | <span data-ttu-id="aba0f-208">红色电源 LED</span><span class="sxs-lookup"><span data-stu-id="aba0f-208">Red Power LED</span></span>      |
> | <span data-ttu-id="aba0f-209">47 \*</span><span class="sxs-lookup"><span data-stu-id="aba0f-209">47\*</span></span>   | <span data-ttu-id="aba0f-210">PullUp</span><span class="sxs-lookup"><span data-stu-id="aba0f-210">PullUp</span></span>        |                     | <span data-ttu-id="aba0f-211">绿色活动 LED</span><span class="sxs-lookup"><span data-stu-id="aba0f-211">Green Activity LED</span></span> |

<span data-ttu-id="aba0f-212">\* = Raspberry Pi 2。</span><span class="sxs-lookup"><span data-stu-id="aba0f-212">\* = Raspberry Pi 2 ONLY.</span></span> <span data-ttu-id="aba0f-213">在 Raspberry Pi 3 上，GPIO 35 & 47 不可用。</span><span class="sxs-lookup"><span data-stu-id="aba0f-213">GPIO 35 & 47 are not available on Raspberry Pi 3.</span></span>

### <a name="gpio-sample"></a><span data-ttu-id="aba0f-214">GPIO 示例</span><span class="sxs-lookup"><span data-stu-id="aba0f-214">GPIO Sample</span></span>

<span data-ttu-id="aba0f-215">例如，以下代码将 **GPIO 5** 打开为输出，并在 pin 上写入数字 "**1**"：</span><span class="sxs-lookup"><span data-stu-id="aba0f-215">As an example, the following code opens **GPIO 5** as an output and writes a digital '**1**' out on the pin:</span></span>

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

<span data-ttu-id="aba0f-216">打开 pin 时，它将处于其开机状态，其中可能包括拉取电阻器。</span><span class="sxs-lookup"><span data-stu-id="aba0f-216">When you open a pin, it will be in its power-on state, which may include a pull resistor.</span></span> <span data-ttu-id="aba0f-217">若要断开拉取电阻并获得高频输入，请将驱动器模式设置为 GpioPinDriveMode：</span><span class="sxs-lookup"><span data-stu-id="aba0f-217">To disconnect the pull resistors and get a high-impedance input, set the drive mode to GpioPinDriveMode.Input:</span></span>
```
    pin.SetDriveMode(GpioPinDriveMode.Input);
```
<span data-ttu-id="aba0f-218">关闭 pin 后，它会恢复到其开机状态。</span><span class="sxs-lookup"><span data-stu-id="aba0f-218">When a pin is closed, it reverts to its power-on state.</span></span>

### <a name="pin-muxing"></a><span data-ttu-id="aba0f-219">固定 Muxing</span><span class="sxs-lookup"><span data-stu-id="aba0f-219">Pin Muxing</span></span>

<span data-ttu-id="aba0f-220">某些 GPIO pin 可以执行多个功能。</span><span class="sxs-lookup"><span data-stu-id="aba0f-220">Some GPIO pins can perform multiple functions.</span></span> <span data-ttu-id="aba0f-221">默认情况下，pin 配置为 GPIO 输入。</span><span class="sxs-lookup"><span data-stu-id="aba0f-221">By default, pins are configured as GPIO inputs.</span></span> <span data-ttu-id="aba0f-222">当通过调用或打开替代函数时 `I2cDevice.FromIdAsync()` `SpiDevice.FromIdAsync()` ，该函数所需的 pin 会自动切换 ( "muxed" ) 转换为正确的函数。</span><span class="sxs-lookup"><span data-stu-id="aba0f-222">When you open an alternate function by calling `I2cDevice.FromIdAsync()` or `SpiDevice.FromIdAsync()` , the pins required by the function are automatically switched ("muxed") to the correct function.</span></span> <span data-ttu-id="aba0f-223">当通过调用或关闭设备时 `I2cDevice.Dispose()` `SpiDevice.Dispose()` ，pin 会恢复为其默认功能。</span><span class="sxs-lookup"><span data-stu-id="aba0f-223">When the device is closed by calling `I2cDevice.Dispose()` or `SpiDevice.Dispose()`, the pins revert back to their default function.</span></span> <span data-ttu-id="aba0f-224">如果尝试同时对两个不同的函数使用 pin，则在尝试打开冲突的函数时会引发异常。</span><span class="sxs-lookup"><span data-stu-id="aba0f-224">If you try to use a pin for two different functions at once, an exception will be thrown when you try to open the conflicting function.</span></span> <span data-ttu-id="aba0f-225">例如，</span><span class="sxs-lookup"><span data-stu-id="aba0f-225">For example,</span></span>

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

## <a name="serial-uart"></a><span data-ttu-id="aba0f-226">串行 UART</span><span class="sxs-lookup"><span data-stu-id="aba0f-226">Serial UART</span></span>

<span data-ttu-id="aba0f-227">RPi2/3： **UART0**上提供了一个串行 UART：</span><span class="sxs-lookup"><span data-stu-id="aba0f-227">There is one Serial UART available on the RPi2/3: **UART0**</span></span>

* <span data-ttu-id="aba0f-228">Pin 8- **UART0 TX**</span><span class="sxs-lookup"><span data-stu-id="aba0f-228">Pin 8  - **UART0 TX**</span></span>
* <span data-ttu-id="aba0f-229">引脚 10- **UART0 RX**</span><span class="sxs-lookup"><span data-stu-id="aba0f-229">Pin 10  - **UART0 RX**</span></span>

<span data-ttu-id="aba0f-230">下面的示例初始化 **UART0** 并执行写操作，后跟读取：</span><span class="sxs-lookup"><span data-stu-id="aba0f-230">The example below initializes **UART0** and performs a write followed by a read:</span></span>


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

<span data-ttu-id="aba0f-231">请注意，必须将以下功能添加到 UWP 项目中的 **appxmanifest.xml** 文件，才能运行串行 UART 代码：</span><span class="sxs-lookup"><span data-stu-id="aba0f-231">Note that you must add the following capability to the **Package.appxmanifest** file in your UWP project to run Serial UART code:</span></span>

<span data-ttu-id="aba0f-232">Visual Studio 2017 在清单设计器中有一个已知 bug， (用于 appxmanifest.xml 文件的可视化编辑器) 会影响 serialcommunication 功能。</span><span class="sxs-lookup"><span data-stu-id="aba0f-232">Visual Studio 2017 has a known bug in the Manifest Designer (the visual editor for appxmanifest files) that affects the serialcommunication capability.</span></span>  <span data-ttu-id="aba0f-233">如果你的 appxmanifest.xml 添加 serialcommunication 功能，则通过设计器修改 appxmanifest.xml 将损坏 appxmanifest.xml (设备 xml 子级将丢失) 。</span><span class="sxs-lookup"><span data-stu-id="aba0f-233">If your appxmanifest adds the serialcommunication capability, modifying your appxmanifest with the designer will corrupt your appxmanifest (the Device xml child will be lost).</span></span>  <span data-ttu-id="aba0f-234">若要解决此问题，可以手动编辑 appxmanifest.xml，方法是右键单击 appxmanifest.xml，然后从上下文菜单中选择 "查看代码"。</span><span class="sxs-lookup"><span data-stu-id="aba0f-234">You can work around this problem by hand editing the appxmanifest by right-clicking your appxmanifest and selecting View Code from the context menu.</span></span>

```xml
  <Capabilities>
    <DeviceCapability Name="serialcommunication">
      <Device Id="any">
        <Function Type="name:serialPort" />
      </Device>
    </DeviceCapability>
  </Capabilities>
```

## <a name="i2c-bus"></a><span data-ttu-id="aba0f-235">I2C 总线</span><span class="sxs-lookup"><span data-stu-id="aba0f-235">I2C Bus</span></span>

<span data-ttu-id="aba0f-236">让我们看看此设备上提供的 I2C 总线。</span><span class="sxs-lookup"><span data-stu-id="aba0f-236">Let's look at the I2C bus available on this device.</span></span>

### <a name="i2c-overview"></a><span data-ttu-id="aba0f-237">I2C 概述</span><span class="sxs-lookup"><span data-stu-id="aba0f-237">I2C Overview</span></span>

<span data-ttu-id="aba0f-238">Pin 标头上有一个 I2C 控制器 **I2C1** ，其中包含两行 **SDA** 和 **SCL**。</span><span class="sxs-lookup"><span data-stu-id="aba0f-238">There is one I2C controller **I2C1** exposed on the pin header with two lines **SDA** and **SCL**.</span></span> <span data-ttu-id="aba0f-239">1.8 k&#x2126; 在此总线的板上已经安装了内部下拉电阻。</span><span class="sxs-lookup"><span data-stu-id="aba0f-239">1.8K&#x2126; internal pull-up resistors are already installed on the board for this bus.</span></span>

> | <span data-ttu-id="aba0f-240">信号名称</span><span class="sxs-lookup"><span data-stu-id="aba0f-240">Signal Name</span></span> | <span data-ttu-id="aba0f-241">标头 Pin 号</span><span class="sxs-lookup"><span data-stu-id="aba0f-241">Header Pin Number</span></span> | <span data-ttu-id="aba0f-242">Gpio 编号</span><span class="sxs-lookup"><span data-stu-id="aba0f-242">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="aba0f-243">SDA</span><span class="sxs-lookup"><span data-stu-id="aba0f-243">SDA</span></span>         | <span data-ttu-id="aba0f-244">3</span><span class="sxs-lookup"><span data-stu-id="aba0f-244">3</span></span>                 | <span data-ttu-id="aba0f-245">2</span><span class="sxs-lookup"><span data-stu-id="aba0f-245">2</span></span>           |
> | <span data-ttu-id="aba0f-246">SCL</span><span class="sxs-lookup"><span data-stu-id="aba0f-246">SCL</span></span>         | <span data-ttu-id="aba0f-247">5</span><span class="sxs-lookup"><span data-stu-id="aba0f-247">5</span></span>                 | <span data-ttu-id="aba0f-248">3</span><span class="sxs-lookup"><span data-stu-id="aba0f-248">3</span></span>           |

<span data-ttu-id="aba0f-249">下面的示例使用 address **0x40**初始化**I2C1**并将数据写入 I2C 设备：</span><span class="sxs-lookup"><span data-stu-id="aba0f-249">The example below initializes **I2C1** and writes data to an I2C device with address **0x40**:</span></span>

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

## <a name="spi-bus"></a><span data-ttu-id="aba0f-250">SPI 总线</span><span class="sxs-lookup"><span data-stu-id="aba0f-250">SPI Bus</span></span>

<span data-ttu-id="aba0f-251">RPi2/3 提供了两个 SPI 总线控制器。</span><span class="sxs-lookup"><span data-stu-id="aba0f-251">There are two SPI bus controllers available on the RPi2/3.</span></span>

### <a name="spi0"></a><span data-ttu-id="aba0f-252">SPI0</span><span class="sxs-lookup"><span data-stu-id="aba0f-252">SPI0</span></span>

> | <span data-ttu-id="aba0f-253">信号名称</span><span class="sxs-lookup"><span data-stu-id="aba0f-253">Signal Name</span></span> | <span data-ttu-id="aba0f-254">标头 Pin 号</span><span class="sxs-lookup"><span data-stu-id="aba0f-254">Header Pin Number</span></span> | <span data-ttu-id="aba0f-255">Gpio 编号</span><span class="sxs-lookup"><span data-stu-id="aba0f-255">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="aba0f-256">MOSI</span><span class="sxs-lookup"><span data-stu-id="aba0f-256">MOSI</span></span>        | <span data-ttu-id="aba0f-257">19</span><span class="sxs-lookup"><span data-stu-id="aba0f-257">19</span></span>                | <span data-ttu-id="aba0f-258">10</span><span class="sxs-lookup"><span data-stu-id="aba0f-258">10</span></span>          |
> | <span data-ttu-id="aba0f-259">MISO</span><span class="sxs-lookup"><span data-stu-id="aba0f-259">MISO</span></span>        | <span data-ttu-id="aba0f-260">21</span><span class="sxs-lookup"><span data-stu-id="aba0f-260">21</span></span>                | <span data-ttu-id="aba0f-261">9</span><span class="sxs-lookup"><span data-stu-id="aba0f-261">9</span></span>           |
> | <span data-ttu-id="aba0f-262">SCLK</span><span class="sxs-lookup"><span data-stu-id="aba0f-262">SCLK</span></span>        | <span data-ttu-id="aba0f-263">23</span><span class="sxs-lookup"><span data-stu-id="aba0f-263">23</span></span>                | <span data-ttu-id="aba0f-264">11</span><span class="sxs-lookup"><span data-stu-id="aba0f-264">11</span></span>          |
> | <span data-ttu-id="aba0f-265">CS0</span><span class="sxs-lookup"><span data-stu-id="aba0f-265">CS0</span></span>         | <span data-ttu-id="aba0f-266">24</span><span class="sxs-lookup"><span data-stu-id="aba0f-266">24</span></span>                | <span data-ttu-id="aba0f-267">8</span><span class="sxs-lookup"><span data-stu-id="aba0f-267">8</span></span>           |
> | <span data-ttu-id="aba0f-268">CS1</span><span class="sxs-lookup"><span data-stu-id="aba0f-268">CS1</span></span>         | <span data-ttu-id="aba0f-269">26</span><span class="sxs-lookup"><span data-stu-id="aba0f-269">26</span></span>                | <span data-ttu-id="aba0f-270">7</span><span class="sxs-lookup"><span data-stu-id="aba0f-270">7</span></span>           |

### <a name="spi1"></a><span data-ttu-id="aba0f-271">SPI1</span><span class="sxs-lookup"><span data-stu-id="aba0f-271">SPI1</span></span>

> | <span data-ttu-id="aba0f-272">信号名称</span><span class="sxs-lookup"><span data-stu-id="aba0f-272">Signal Name</span></span> | <span data-ttu-id="aba0f-273">标头 Pin 号</span><span class="sxs-lookup"><span data-stu-id="aba0f-273">Header Pin Number</span></span> | <span data-ttu-id="aba0f-274">Gpio 编号</span><span class="sxs-lookup"><span data-stu-id="aba0f-274">Gpio Number</span></span> |
> |-------------|-------------------|-------------|
> | <span data-ttu-id="aba0f-275">MOSI</span><span class="sxs-lookup"><span data-stu-id="aba0f-275">MOSI</span></span>        | <span data-ttu-id="aba0f-276">38</span><span class="sxs-lookup"><span data-stu-id="aba0f-276">38</span></span>                | <span data-ttu-id="aba0f-277">20</span><span class="sxs-lookup"><span data-stu-id="aba0f-277">20</span></span>          |
> | <span data-ttu-id="aba0f-278">MISO</span><span class="sxs-lookup"><span data-stu-id="aba0f-278">MISO</span></span>        | <span data-ttu-id="aba0f-279">35</span><span class="sxs-lookup"><span data-stu-id="aba0f-279">35</span></span>                | <span data-ttu-id="aba0f-280">19</span><span class="sxs-lookup"><span data-stu-id="aba0f-280">19</span></span>          |
> | <span data-ttu-id="aba0f-281">SCLK</span><span class="sxs-lookup"><span data-stu-id="aba0f-281">SCLK</span></span>        | <span data-ttu-id="aba0f-282">40</span><span class="sxs-lookup"><span data-stu-id="aba0f-282">40</span></span>                | <span data-ttu-id="aba0f-283">21</span><span class="sxs-lookup"><span data-stu-id="aba0f-283">21</span></span>          |
> | <span data-ttu-id="aba0f-284">CS0</span><span class="sxs-lookup"><span data-stu-id="aba0f-284">CS0</span></span>         | <span data-ttu-id="aba0f-285">36</span><span class="sxs-lookup"><span data-stu-id="aba0f-285">36</span></span>                | <span data-ttu-id="aba0f-286">16</span><span class="sxs-lookup"><span data-stu-id="aba0f-286">16</span></span>          |


### <a name="spi-sample"></a><span data-ttu-id="aba0f-287">SPI 示例</span><span class="sxs-lookup"><span data-stu-id="aba0f-287">SPI Sample</span></span>

<span data-ttu-id="aba0f-288">下面显示了一个示例，说明如何使用芯片 **SPI0** 在总线上执行 SPI 写入操作：</span><span class="sxs-lookup"><span data-stu-id="aba0f-288">An example of how to perform a SPI write on bus **SPI0** using chip select 0 is shown below:</span></span>

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
