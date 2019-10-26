---
title: Arduino 接线移植指南
ms.date: 08/28/2017
ms.topic: article
description: 了解部署 Arduino 接线图项目时出现的修改和常见问题。
keywords: windows iot，Arduino，布线，Visual Studio，移植
ms.openlocfilehash: 7f3f70101fb28fab001dbd38d3159a7a10fa5586
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918136"
---
# <a name="arduino-wiring-porting-guide"></a><span data-ttu-id="3d657-104">Arduino 接线移植指南</span><span class="sxs-lookup"><span data-stu-id="3d657-104">Arduino Wiring Porting Guide</span></span>

<span data-ttu-id="3d657-105">Arduino 接线草图和库可在 Visual Studio 内复制/粘贴到 Arduino 接线项目，并在 Raspberry Pi 2、Raspberry Pi 3 或 Minnowboard Max 上运行。</span><span class="sxs-lookup"><span data-stu-id="3d657-105">Arduino Wiring sketches and libraries can be copy/pasted into an Arduino Wiring project inside Visual Studio and run on Raspberry Pi 2, Raspberry Pi 3 or Minnowboard Max.</span></span> <span data-ttu-id="3d657-106">有时需要对这些文件稍作修改，以便使它们与 Windows 环境或你正在使用的板更兼容。</span><span class="sxs-lookup"><span data-stu-id="3d657-106">Sometimes there are slight modifications that need to be made to these files in order to make them more compatible with the Windows environment, or the board you are working with.</span></span> <span data-ttu-id="3d657-107">本指南将介绍这些修改以及部署 Arduino 布线项目时可能遇到的常见问题。</span><span class="sxs-lookup"><span data-stu-id="3d657-107">This guide will cover those modifications as well as common issues that you may run into when deploying Arduino Wiring projects.</span></span>

## <a name="porting"></a><span data-ttu-id="3d657-108">移植</span><span class="sxs-lookup"><span data-stu-id="3d657-108">Porting</span></span>

### <a name="updating-pins"></a><span data-ttu-id="3d657-109">更新引脚</span><span class="sxs-lookup"><span data-stu-id="3d657-109">Updating Pins</span></span>

<span data-ttu-id="3d657-110">不言而喻，许多草图和库（尤其是用于 Arduino 防护的草图和库）可能包含对 Arduino 设备的特定连接器引脚的引用。</span><span class="sxs-lookup"><span data-stu-id="3d657-110">It might go without saying, but many sketches and libraries (especially those for arduino shields) may contain references to specific connector pins for Arduino devices.</span></span> <span data-ttu-id="3d657-111">你将要自定义你的草图来针对你正在处理的设备和你正在使用的配置使用相应的连接器引脚。</span><span class="sxs-lookup"><span data-stu-id="3d657-111">You'll want to customize your sketches to use the appropriate connector pins for the device you are working on and the configuration you are using.</span></span>

<span data-ttu-id="3d657-112">Arduino 接线最终需要引用“引脚”的任何函数的物理连接器引脚编号。</span><span class="sxs-lookup"><span data-stu-id="3d657-112">Arduino Wiring ultimately requires a physical connector pin number for any functions that refer to 'pins'.</span></span> <span data-ttu-id="3d657-113">你可以直接使用这些编号，不过我们还提供了一些对应于特定板上的连接器引脚的预定义引脚名称。</span><span class="sxs-lookup"><span data-stu-id="3d657-113">You can use these numbers directly, but we've also provided some pre-defined pin names which correspond to connector pins on specific boards.</span></span>

<span data-ttu-id="3d657-114">例如，Raspberry Pi 2 和 3 上的物理连接器引脚 29 也称为 `GPIO5`。</span><span class="sxs-lookup"><span data-stu-id="3d657-114">For example, the physical connector pin 29 on a Raspberry Pi 2 and 3 is also known as `GPIO5`.</span></span> <span data-ttu-id="3d657-115">你可以通过使用以下任一命令在 Raspberry Pi 2 和 3 上将 GPIO 引脚 5 设置为 HIGH 状态：</span><span class="sxs-lookup"><span data-stu-id="3d657-115">You may set GPIO pin 5 to a HIGH state on a Raspberry Pi 2 and 3 by using either of the following commands:</span></span>
```
pinMode( 29, OUTPUT );
digitalWrite( 29, HIGH );
```

<span data-ttu-id="3d657-116">或</span><span class="sxs-lookup"><span data-stu-id="3d657-116">or</span></span>

```
pinMode( GPIO5, OUTPUT );
digitalWrite( GPIO5, HIGH );
```

<span data-ttu-id="3d657-117">可以在[pins_arduino](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h)中找到预定义的 pin 名称，并将其包含在每个 arduino 布线项目中，但由于要为构建的硬件设置，提供了不同的物理连接器 pin，因此我们还提供了一个表此处说明每个设备的可用 pin 名称。</span><span class="sxs-lookup"><span data-stu-id="3d657-117">The pre-defined pin names can be found in [pins_arduino.h](https://github.com/ms-iot/lightning/blob/develop/source/pins_arduino.h) and included in every Arduino Wiring project, but since there will be different physical connector pins available depending on the hardware setup you are building for, we've also included a table here to describe which pin names are available for each device.</span></span>

#### <a name="raspberry-pi-2-and-3"></a><span data-ttu-id="3d657-118">Raspberry Pi 2 和 3</span><span class="sxs-lookup"><span data-stu-id="3d657-118">Raspberry Pi 2 and 3</span></span>

![引线关系图](../media/ArduinoWiringPortingGuide/RP2_Pinout.png)

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="3d657-120">引脚定义</span><span class="sxs-lookup"><span data-stu-id="3d657-120">Pin Define</span></span> | <span data-ttu-id="3d657-121">相应的引脚编号</span><span class="sxs-lookup"><span data-stu-id="3d657-121">Corresponding Pin Number</span></span>|
> |-------------|----------|
> | <span data-ttu-id="3d657-122">LED_BUILTIN</span><span class="sxs-lookup"><span data-stu-id="3d657-122">LED_BUILTIN</span></span> | <span data-ttu-id="3d657-123">*板载 LED*</span><span class="sxs-lookup"><span data-stu-id="3d657-123">*onboard LED*</span></span> |
> | <span data-ttu-id="3d657-124">GPIO \* _where \* 指 [0，27]_</span><span class="sxs-lookup"><span data-stu-id="3d657-124">GPIO\* _where \* refers to [0, 27]_</span></span> | <span data-ttu-id="3d657-125">*请参考引出线图*</span><span class="sxs-lookup"><span data-stu-id="3d657-125">*refer to pinout diagram*</span></span> |
> | <span data-ttu-id="3d657-126">GCLK</span><span class="sxs-lookup"><span data-stu-id="3d657-126">GCLK</span></span> | <span data-ttu-id="3d657-127">7</span><span class="sxs-lookup"><span data-stu-id="3d657-127">7</span></span> |
> | <span data-ttu-id="3d657-128">GEN \* _where \* 指 [0，5]_</span><span class="sxs-lookup"><span data-stu-id="3d657-128">GEN\* _where \* refers to [0, 5]_</span></span> | <span data-ttu-id="3d657-129">\* 参阅引线关系图</span><span class="sxs-lookup"><span data-stu-id="3d657-129">\*refer to pinout diagram</span></span> |
> | <span data-ttu-id="3d657-130">SCL1</span><span class="sxs-lookup"><span data-stu-id="3d657-130">SCL1</span></span> | <span data-ttu-id="3d657-131">5</span><span class="sxs-lookup"><span data-stu-id="3d657-131">5</span></span> |
> | <span data-ttu-id="3d657-132">SDA1</span><span class="sxs-lookup"><span data-stu-id="3d657-132">SDA1</span></span> | <span data-ttu-id="3d657-133">3</span><span class="sxs-lookup"><span data-stu-id="3d657-133">3</span></span> |
> | <span data-ttu-id="3d657-134">CS0 （或 CE0 或 SS）</span><span class="sxs-lookup"><span data-stu-id="3d657-134">CS0 (or CE0 or SS)</span></span> | <span data-ttu-id="3d657-135">24</span><span class="sxs-lookup"><span data-stu-id="3d657-135">24</span></span> |
> | <span data-ttu-id="3d657-136">CS1 （或 CE1）</span><span class="sxs-lookup"><span data-stu-id="3d657-136">CS1 (or CE1)</span></span> | <span data-ttu-id="3d657-137">26</span><span class="sxs-lookup"><span data-stu-id="3d657-137">26</span></span> |
> | <span data-ttu-id="3d657-138">SCLK （或 SCK）</span><span class="sxs-lookup"><span data-stu-id="3d657-138">SCLK (or SCK)</span></span> | <span data-ttu-id="3d657-139">23</span><span class="sxs-lookup"><span data-stu-id="3d657-139">23</span></span> |
> | <span data-ttu-id="3d657-140">MISO</span><span class="sxs-lookup"><span data-stu-id="3d657-140">MISO</span></span> | <span data-ttu-id="3d657-141">21</span><span class="sxs-lookup"><span data-stu-id="3d657-141">21</span></span> |
> | <span data-ttu-id="3d657-142">MOSI</span><span class="sxs-lookup"><span data-stu-id="3d657-142">MOSI</span></span> | <span data-ttu-id="3d657-143">19</span><span class="sxs-lookup"><span data-stu-id="3d657-143">19</span></span> |
> | <span data-ttu-id="3d657-144">RXD</span><span class="sxs-lookup"><span data-stu-id="3d657-144">RXD</span></span> | <span data-ttu-id="3d657-145">10</span><span class="sxs-lookup"><span data-stu-id="3d657-145">10</span></span> |
> | <span data-ttu-id="3d657-146">TXD</span><span class="sxs-lookup"><span data-stu-id="3d657-146">TXD</span></span> | <span data-ttu-id="3d657-147">8</span><span class="sxs-lookup"><span data-stu-id="3d657-147">8</span></span> |

#### <a name="minnowboard-max"></a><span data-ttu-id="3d657-148">Minnowboard Max</span><span class="sxs-lookup"><span data-stu-id="3d657-148">Minnowboard Max</span></span>

![引线关系图](../media/ArduinoWiringPortingGuide/MBM_Pinout.png)
> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="3d657-150">引脚定义</span><span class="sxs-lookup"><span data-stu-id="3d657-150">Pin Define</span></span> | <span data-ttu-id="3d657-151">相应的引脚编号</span><span class="sxs-lookup"><span data-stu-id="3d657-151">Corresponding Pin Number</span></span>|
> |-------------|----------|
> | <span data-ttu-id="3d657-152">GPIO \* _where \* 指 [0，9]_</span><span class="sxs-lookup"><span data-stu-id="3d657-152">GPIO\* _where \* refers to [0, 9]_</span></span>  | <span data-ttu-id="3d657-153">*请参考引出线图*</span><span class="sxs-lookup"><span data-stu-id="3d657-153">*refer to pinout diagram*</span></span> |
> | <span data-ttu-id="3d657-154">SCL</span><span class="sxs-lookup"><span data-stu-id="3d657-154">SCL</span></span> | <span data-ttu-id="3d657-155">13</span><span class="sxs-lookup"><span data-stu-id="3d657-155">13</span></span> |
> | <span data-ttu-id="3d657-156">SDA</span><span class="sxs-lookup"><span data-stu-id="3d657-156">SDA</span></span> | <span data-ttu-id="3d657-157">15</span><span class="sxs-lookup"><span data-stu-id="3d657-157">15</span></span> |
> | <span data-ttu-id="3d657-158">CS0 （或 CE0 或 SS）</span><span class="sxs-lookup"><span data-stu-id="3d657-158">CS0 (or CE0 or SS)</span></span> | <span data-ttu-id="3d657-159">5</span><span class="sxs-lookup"><span data-stu-id="3d657-159">5</span></span> |
> | <span data-ttu-id="3d657-160">SCLK （或 SCK）</span><span class="sxs-lookup"><span data-stu-id="3d657-160">SCLK  (or SCK)</span></span>| <span data-ttu-id="3d657-161">11</span><span class="sxs-lookup"><span data-stu-id="3d657-161">11</span></span> |
> | <span data-ttu-id="3d657-162">MISO</span><span class="sxs-lookup"><span data-stu-id="3d657-162">MISO</span></span> |<span data-ttu-id="3d657-163">7</span><span class="sxs-lookup"><span data-stu-id="3d657-163">7</span></span> |
> | <span data-ttu-id="3d657-164">MOSI</span><span class="sxs-lookup"><span data-stu-id="3d657-164">MOSI</span></span> | <span data-ttu-id="3d657-165">9</span><span class="sxs-lookup"><span data-stu-id="3d657-165">9</span></span> |
> | <span data-ttu-id="3d657-166">CTS1</span><span class="sxs-lookup"><span data-stu-id="3d657-166">CTS1</span></span> | <span data-ttu-id="3d657-167">10</span><span class="sxs-lookup"><span data-stu-id="3d657-167">10</span></span> |
> | <span data-ttu-id="3d657-168">RTS1</span><span class="sxs-lookup"><span data-stu-id="3d657-168">RTS1</span></span> | <span data-ttu-id="3d657-169">12</span><span class="sxs-lookup"><span data-stu-id="3d657-169">12</span></span> |
> | <span data-ttu-id="3d657-170">RX1</span><span class="sxs-lookup"><span data-stu-id="3d657-170">RX1</span></span> | <span data-ttu-id="3d657-171">8</span><span class="sxs-lookup"><span data-stu-id="3d657-171">8</span></span> |
> | <span data-ttu-id="3d657-172">TX1</span><span class="sxs-lookup"><span data-stu-id="3d657-172">TX1</span></span> | <span data-ttu-id="3d657-173">6</span><span class="sxs-lookup"><span data-stu-id="3d657-173">6</span></span> |
> | <span data-ttu-id="3d657-174">RX2</span><span class="sxs-lookup"><span data-stu-id="3d657-174">RX2</span></span> | <span data-ttu-id="3d657-175">19</span><span class="sxs-lookup"><span data-stu-id="3d657-175">19</span></span> |
> | <span data-ttu-id="3d657-176">TX2</span><span class="sxs-lookup"><span data-stu-id="3d657-176">TX2</span></span> | <span data-ttu-id="3d657-177">17</span><span class="sxs-lookup"><span data-stu-id="3d657-177">17</span></span> |


## <a name="common-problems"></a><span data-ttu-id="3d657-178">常见问题</span><span class="sxs-lookup"><span data-stu-id="3d657-178">Common Problems</span></span>

### <a name="cant-find-arduino-wiring-application-visual-c-project-template-in-visual-studio"></a><span data-ttu-id="3d657-179">在 Visual Studio 中找不到“Arduino 接线应用程序”Visual C++ 项目模板</span><span class="sxs-lookup"><span data-stu-id="3d657-179">Can't find "Arduino Wiring Application" Visual C++ project template in Visual Studio</span></span>

<span data-ttu-id="3d657-180">**原因**： 未安装适用于 Visual Studio 的 Windows IoT 项目模板扩展。</span><span class="sxs-lookup"><span data-stu-id="3d657-180">**Cause**: The Windows IoT Project Templates extension for Visual Studio is not installed.</span></span>

<span data-ttu-id="3d657-181">**解决方案**： 你必须先安装适用于 Windows IoT 项目模板的 Visual Studio 扩展才能在 Visual Studio 中创建 Arduino 接线项目。</span><span class="sxs-lookup"><span data-stu-id="3d657-181">**Solution**: You must install the Visual Studio Extension for Windows IoT Project Templates before you can create Arduino Wiring projects in Visual Studio.</span></span> <span data-ttu-id="3d657-182">转到 [Windows IoT 核心版项目模板扩展页面](https://go.microsoft.com/fwlink/?linkid=847472)来从 Visual Studio 库下载该扩展！</span><span class="sxs-lookup"><span data-stu-id="3d657-182">Head over to [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to download the extension from the Visual Studio Gallery!</span></span>

### <a name="error-identifier-not-found-when-calling-a-function"></a><span data-ttu-id="3d657-183">错误：在调用某个函数时“找不到标识符”</span><span class="sxs-lookup"><span data-stu-id="3d657-183">ERROR: "identifier not found" when calling a function</span></span>

<span data-ttu-id="3d657-184">**原因**： 当调用尚未在文档中声明的函数时，在链接器过程中会发生此错误。</span><span class="sxs-lookup"><span data-stu-id="3d657-184">**Cause**: This error occurs during the linker process when a function is invoked that has not yet been declared in the document.</span></span>

<span data-ttu-id="3d657-185">**解决方案**： 在 C++ 中，所有函数都必须在调用前进行声明。</span><span class="sxs-lookup"><span data-stu-id="3d657-185">**Solution**: In C++, all functions must be declared before they are invoked.</span></span> <span data-ttu-id="3d657-186">如果你已在草图文件中定义了新函数，该函数的声明或完整实现必须在任何调用它的尝试上方（通常在文档顶部）。</span><span class="sxs-lookup"><span data-stu-id="3d657-186">If you have defined a new function in your sketch file, either the declaration or the entire implementation of the function must be above any attempts to invoke it (typically at the top of the document).</span></span>

<span data-ttu-id="3d657-187">**示例**：</span><span class="sxs-lookup"><span data-stu-id="3d657-187">**Example**:</span></span>

<span data-ttu-id="3d657-188">以下代码块将引发错误“‘myFunction’：找不到标识符”</span><span class="sxs-lookup"><span data-stu-id="3d657-188">The following block of code will raise the error "'myFunction': identifier not found"</span></span>

```
void setup()
{

}

void loop()
{
    myFunction();
}

void myFunction()
{
    //do something
}
```

<span data-ttu-id="3d657-189">有两种解决方案。</span><span class="sxs-lookup"><span data-stu-id="3d657-189">There are two solutions.</span></span> <span data-ttu-id="3d657-190">首先，你可以在任何调用上方声明该函数。</span><span class="sxs-lookup"><span data-stu-id="3d657-190">First, you may declare the function above any invocations.</span></span> <span data-ttu-id="3d657-191">通常，此声明在文件顶部完成。</span><span class="sxs-lookup"><span data-stu-id="3d657-191">Typically, this declaration is done at the top of the file.</span></span>

```C++
// Declare function here
void myFunction();

void setup()
{

}

void loop()
{
    myFunction();
}

// And, define the function here
void myFunction()
{
    //do something
}
```

<span data-ttu-id="3d657-192">或者，您可以将函数的整个实现移动到任何调用的上面。</span><span class="sxs-lookup"><span data-stu-id="3d657-192">Alternatively, you can move the entire implementation of the function above any invocations.</span></span> <span data-ttu-id="3d657-193">这会导致同时声明和定义该函数。</span><span class="sxs-lookup"><span data-stu-id="3d657-193">This has the effect of both declaring and defining the function at the same time.</span></span>

```C++
void setup()
{
}

void myFunction()
{
    //do something
}

void loop()
{
    myFunction();
}
```

### <a name="my-solution-hangs-infinitely-when-being-initialized"></a><span data-ttu-id="3d657-194">我的解决方案在初始化时无限期挂起</span><span class="sxs-lookup"><span data-stu-id="3d657-194">My solution hangs infinitely when being initialized</span></span>

<span data-ttu-id="3d657-195">存在可能导致 C++ 解决方案在初始化时无限期挂起（死锁）的已知问题。</span><span class="sxs-lookup"><span data-stu-id="3d657-195">There is a known issue which can cause a C++ solution to hang infinitely (deadlock) when being initialized.</span></span> <span data-ttu-id="3d657-196">如果你发现你的解决方案看起来永久挂起，并且你无法使用调试器“闯入”Arduino 接线应用程序的 setup() 或 loop() 部分中的任何声明，则可能遇到此类型的问题。</span><span class="sxs-lookup"><span data-stu-id="3d657-196">You may be experiencing this type of issue if you find that your solution appears to hang forever and you are unable to use the debugger to 'break in' to any statement in the setup() or loop() sections of your Arduino Wiring application.</span></span>

<span data-ttu-id="3d657-197">**原因**： 在解决方案完成初始化前创建了某个对象或调用了某个函数，从而导致异步操作。</span><span class="sxs-lookup"><span data-stu-id="3d657-197">**Cause**: An object is being created or a function is being called which leads to an asyncronous action before the solution has finished initializing.</span></span> <span data-ttu-id="3d657-198">这可能由对象的构造函数调用 `pinMode` 等 API 函数所导致。</span><span class="sxs-lookup"><span data-stu-id="3d657-198">It is likely caused from an object's constructor calling an API function like `pinMode`.</span></span>

<span data-ttu-id="3d657-199">**解决方案**： 将任何对象构造函数和函数调用从代码的初始化部分中移开，并移到 `setup()` 块中。</span><span class="sxs-lookup"><span data-stu-id="3d657-199">**Solution**: Move any object constructors and function calls away from the initialization section of code and into the `setup()` block.</span></span>

<span data-ttu-id="3d657-200">**示例 1**：</span><span class="sxs-lookup"><span data-stu-id="3d657-200">**Example 1**:</span></span>

<span data-ttu-id="3d657-201">在解决方案本身完成初始化前，此草图的执行会调用称为 `setPinModes()` 的函数。</span><span class="sxs-lookup"><span data-stu-id="3d657-201">The execution of this sketch calls a function called `setPinModes()` before the solution itself has been initialized.</span></span> <span data-ttu-id="3d657-202">解决方案将显示为执行，但会无限期挂起。</span><span class="sxs-lookup"><span data-stu-id="3d657-202">The solution will appear to execute but will hang infinitely.</span></span>

```C++
bool setPinModes();

int pin = GPIO5;
bool initialized = setPinModes();

void setup()
{

}

void loop()
{
    if( initialized )
    {
        //do something
    }
}

bool setPinModes()
{
    if( pin < 0 ) return false;
    pinMode( pin, OUTPUT );
    return true;
}
```

<span data-ttu-id="3d657-203">解决方案如下，我们仅仅将 `setPinModes()` 的执行移到 `setup()` 函数：</span><span class="sxs-lookup"><span data-stu-id="3d657-203">The solution is below, we've simply moved the execution of `setPinModes()` to the `setup()` function:</span></span>

```C++
bool setPinModes();

int pin = GPIO5;
bool initialized;

void setup()
{
    initialized = setPinModes();
}

void loop()
{
    if( initialized )
    {
        //do something
    }
}

bool setPinModes()
{
    if( pin < 0 ) return false;
    pinMode( pin, OUTPUT );
    return true;
}
```

<span data-ttu-id="3d657-204">**示例 2**：</span><span class="sxs-lookup"><span data-stu-id="3d657-204">**Example 2**:</span></span>

<span data-ttu-id="3d657-205">在调用 `setup()` 前，此草图的执行会在堆栈上创建一个对象。</span><span class="sxs-lookup"><span data-stu-id="3d657-205">The execution of this sketch creates an object on the stack before `setup()` has been called.</span></span> <span data-ttu-id="3d657-206">由于对象在其构造函数中调用 `pinMode`，这还会导致死锁。</span><span class="sxs-lookup"><span data-stu-id="3d657-206">Since the object calls `pinMode` in its constructor, this will also cause a deadlock.</span></span> <span data-ttu-id="3d657-207">这不是常见问题，但可能在来自某些库（如 Arduino `LiquidCrystal` 库）的对象上发生。</span><span class="sxs-lookup"><span data-stu-id="3d657-207">This is an uncommon issue, but may occur with objects from certain libraries (like the Arduino `LiquidCrystal` library).</span></span>

```C++
class MyObject
{
public:
    MyObject()
    {
        pinMode( GPIO5, OUTPUT );
    }

    void doSomething()
    {
        //... 
    }
};

MyObject myObject;

void setup()
{
}

void loop()
{
    myObject.doSomething();
}
```

<span data-ttu-id="3d657-208">解决方案如下。</span><span class="sxs-lookup"><span data-stu-id="3d657-208">The solution is below.</span></span> <span data-ttu-id="3d657-209">我们已将对象更改为对象指针，并将对象的初始化移到了 `setup()`。</span><span class="sxs-lookup"><span data-stu-id="3d657-209">We've changed the object to an object pointer and moved the initialization of the object to `setup()`.</span></span>

```C++
class MyObject
{
public:
    MyObject()
    {
        pinMode( GPIO5, OUTPUT );
    }

    void doSomething()
    {
        //... 
    }
};

MyObject *myObject;

void setup()
{
    myObject = new MyObject();
}

void loop()
{
    myObject->doSomething();
}
```

### <a name="using-serialprint-and-serialprintln"></a><span data-ttu-id="3d657-210">使用 `Serial.print()` 和 `Serial.println()`</span><span class="sxs-lookup"><span data-stu-id="3d657-210">Using `Serial.print()` and `Serial.println()`</span></span>

<span data-ttu-id="3d657-211">许多 Arduino 草图使用 `Serial` 将数据打印到串行控制台（如果打开）或写入串行线（USB 或 tx/rx）。</span><span class="sxs-lookup"><span data-stu-id="3d657-211">Many Arduino sketches use `Serial` to print data to the serial console (if opened) or to write to the serial lines (USB or tx/rx).</span></span> <span data-ttu-id="3d657-212">在早期版本的闪电 SDK 中，不包括硬件 `Serial` 支持，因此我们提供了一个 `Log()` 函数，该函数将打印到 Visual Studio 中的 "调试器输出" 窗口。</span><span class="sxs-lookup"><span data-stu-id="3d657-212">In prior versions of the Lightning SDK, Hardware `Serial` support wasn't included, so we provided a `Log()` function which will print to the debugger output window in Visual Studio.</span></span> <span data-ttu-id="3d657-213">必须删除 `Serial.print*()` 或 `Serial.write()`。</span><span class="sxs-lookup"><span data-stu-id="3d657-213">`Serial.print*()` or `Serial.write()` had to be removed.</span></span>

<span data-ttu-id="3d657-214">但从_闪电 SDK v 1.1.0_开始，我们添加了 `Hardware Serial` 支持，并完全支持 `Serial.print*()` 或 `Serial.write()` 函数。</span><span class="sxs-lookup"><span data-stu-id="3d657-214">However, starting with _Lightning SDK v1.1.0_, we've added `Hardware Serial` support and both `Serial.print*()` or `Serial.write()` functions are fully supported.</span></span> <span data-ttu-id="3d657-215">因此，如果您要复制为 Arduino 生成的草绘，则不需要替换该草图的 Windows IoT 版本中的任何这些序列引用。</span><span class="sxs-lookup"><span data-stu-id="3d657-215">So, if you are copying a sketch built for an Arduino, you won't need to replace any of these Serial references in the Windows IoT version of the sketch.</span></span>

<span data-ttu-id="3d657-216">此外，我们还扩展了 `Serial.print()` 和 `Serial.println()`的功能，在附加调试器的情况下输出到调试器窗口-除了写入硬件串行 pin 外。</span><span class="sxs-lookup"><span data-stu-id="3d657-216">Furthermore, we've extended the functionality of `Serial.print()` and `Serial.println()`, to output to the debugger window when a debugger is attached - in addition to writing to the hardware serial pins.</span></span>
<span data-ttu-id="3d657-217">调试输出打印设置为默认值，因为在读取输出后，大多数用户都需要该输出。</span><span class="sxs-lookup"><span data-stu-id="3d657-217">The debug output printing is set as the default since reading that output is what most users would want when running their sketches.</span></span> <span data-ttu-id="3d657-218">但是，也可以禁用该功能;例如，若要提高性能，只需调用 `Serial.enablePrintDebugOutput(false);` 以在草绘中禁用它。</span><span class="sxs-lookup"><span data-stu-id="3d657-218">However, that functionality can be disabled as well; e.g. to improve performance, simply call `Serial.enablePrintDebugOutput(false);` to disable it in your sketch.</span></span> <span data-ttu-id="3d657-219">若要重新启用，请调用 `Serial.enablePrintDebugOutput(true);`。</span><span class="sxs-lookup"><span data-stu-id="3d657-219">To re-enable it, call `Serial.enablePrintDebugOutput(true);`.</span></span> <span data-ttu-id="3d657-220">写入硬件串行端口不受这些调用的影响。</span><span class="sxs-lookup"><span data-stu-id="3d657-220">Writing to the hardware serial pins is not affected by those calls.</span></span>

<span data-ttu-id="3d657-221">请注意，不需要将任何外围设备连接到串行 pin （如 FTDI），即可获取发送到调试器窗口的输出。</span><span class="sxs-lookup"><span data-stu-id="3d657-221">Note, you do NOT need to attach any peripheral to your serial pins such as an FTDI, to get output sent to the debugger window.</span></span> <span data-ttu-id="3d657-222">但是，你需要确保在调试你的应用程序时调试器窗口处于打开状态。</span><span class="sxs-lookup"><span data-stu-id="3d657-222">However, you'll need to make sure the debugger window is open while your application is being debugged.</span></span>

![调试器输出](../media/ArduinoWiringPortingGuide/debugger_output.png)

<span data-ttu-id="3d657-224">已在[Windows IoT Core 项目模板扩展页面](https://go.microsoft.com/fwlink/?linkid=847472)上更新项目模板，以允许使用现成的硬件 `Serial`。</span><span class="sxs-lookup"><span data-stu-id="3d657-224">The project templates have been updated on the [Windows IoT Core Project Templates extension page](https://go.microsoft.com/fwlink/?linkid=847472) to enable using Hardware `Serial` out of the box.</span></span> <span data-ttu-id="3d657-225">但是，如果你的 Arduino 配应用程序已使用较旧的项目模板版本创建，则需要1）将项目升级到最新的闪电 SDK，v 1.1.0 或更高版本，并2）将所需的硬件串行设备功能添加到你的Appxmanifest.xml 可以使用 `Serial`。</span><span class="sxs-lookup"><span data-stu-id="3d657-225">However, if your Arduino Wiring application has already been created using an older project template version, you'll need to 1) Upgrade your project to the latest Lightning SDK, v1.1.0 or later, and 2) add the required Hardware Serial device capability to your AppxManifest to be able to use `Serial`.</span></span>

### <a name="hardware-serial-device-capability-requirements"></a><span data-ttu-id="3d657-226">硬件串行设备功能要求</span><span class="sxs-lookup"><span data-stu-id="3d657-226">Hardware Serial device capability requirements</span></span>

<span data-ttu-id="3d657-227">Windows 10 IoT Core 中的硬件串行功能要求向 AppX 清单添加设备功能声明。</span><span class="sxs-lookup"><span data-stu-id="3d657-227">Hardware Serial functionality in Windows 10 IoT Core requires device capability declarations added to the AppX manifest.</span></span>

<span data-ttu-id="3d657-228">在 "解决方案资源管理器" 中键入文件名，查找项目中的文件 `Package.appxmanifest`。</span><span class="sxs-lookup"><span data-stu-id="3d657-228">Find the file `Package.appxmanifest` in your project, by typing the file name in the solution explorer.</span></span> <span data-ttu-id="3d657-229">然后，右键单击该文件，然后选择 "打开方式 ..."。</span><span class="sxs-lookup"><span data-stu-id="3d657-229">Then, right click the file and choose 'Open With...'.</span></span> <span data-ttu-id="3d657-230">选择 "XML （文本）编辑器"，然后单击 "确定"。</span><span class="sxs-lookup"><span data-stu-id="3d657-230">Choose 'XML (Text) Editor' and click 'OK'.</span></span>

![正在更新包。 appxmanifest.xml](../media/ArduinoWiringPortingGuide/appxmanifest_search.png)

<span data-ttu-id="3d657-232">在 appx 清单文件编辑器中，将 `serialcommunication` DeviceCapability 添加到您的项目中，如以下 XML 代码片段所示：</span><span class="sxs-lookup"><span data-stu-id="3d657-232">In the appx manifest file editor, add the `serialcommunication` DeviceCapability to your project as in the following XML snippet:</span></span>

```xml
<Capabilities>
  <Capability Name="internetClient" />

  <!-- General Arduino Wiring required capabilities -->
  <iot:Capability Name="lowLevelDevices" />
  <DeviceCapability Name="109b86ad-f53d-4b76-aa5f-821e2ddf2141"/>

  <!-- The serialcommunication capability is required to access Hardware Serial. --> 
  <DeviceCapability Name="serialcommunication">
    <Device Id="any">
      <Function Type="name:serialPort"/>
    </Device>
  </DeviceCapability>

</Capabilities>
```

### <a name="upgrade-your-project-to-the-latest-lightning-sdk"></a><span data-ttu-id="3d657-233">将项目升级到最新的闪电 SDK</span><span class="sxs-lookup"><span data-stu-id="3d657-233">Upgrade your project to the latest Lightning SDK</span></span>

<span data-ttu-id="3d657-234">Arduino 布线项目依赖于[闪电 SDK Nuget 包](https://www.nuget.org/packages/Microsoft.IoT.Lightning/)来实现所需的 Arduino 布线功能和声明，并与闪电驱动程序建立接口。</span><span class="sxs-lookup"><span data-stu-id="3d657-234">The Arduino Wiring projects depend on the [Lightning SDK Nuget package](https://www.nuget.org/packages/Microsoft.IoT.Lightning/) to implement the required Arduino Wiring functions and declarations as well as interface with the Lightning driver.</span></span> <span data-ttu-id="3d657-235">最新的闪电 SDK 将包含最新的改进和 bug 修复。</span><span class="sxs-lookup"><span data-stu-id="3d657-235">The latest Lightning SDK will contain the latest improvements and bug fixes.</span></span> <span data-ttu-id="3d657-236">若要升级到最新的闪电 SDK，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="3d657-236">To upgrade to the latest Lightning SDK, follow these steps:</span></span>

- <span data-ttu-id="3d657-237">在解决方案资源管理器中，右键单击你的项目，然后单击 "管理 Nuget 包 ..."</span><span class="sxs-lookup"><span data-stu-id="3d657-237">In the Solution Explorer, right click on your project and click 'Manage Nuget Packages...'</span></span>
- <span data-ttu-id="3d657-238">在 NuGet 包管理器中，切换到 "已安装" 选项卡。应会看到已安装的 ""</span><span class="sxs-lookup"><span data-stu-id="3d657-238">In the NuGet Package Manager, go to the 'Installed' tab. You should see the Microsoft.IoT.Lightning package installed</span></span>
- <span data-ttu-id="3d657-239">可用版本将在 "版本" combobox 内列出。</span><span class="sxs-lookup"><span data-stu-id="3d657-239">Available versions will be listed inside the 'Version' combobox.</span></span>
- <span data-ttu-id="3d657-240">选择最新版本，并单击 "更新" 更新您的包。</span><span class="sxs-lookup"><span data-stu-id="3d657-240">Choose the latest version, and click 'Update' to update your package.</span></span>
- <span data-ttu-id="3d657-241">请注意，若要升级到预发布版本，请务必选中 "包括预发行版" 复选框。</span><span class="sxs-lookup"><span data-stu-id="3d657-241">Notice, to upgrade to a prerelease version, make sure to check the 'Include prerelease' checkbox as well.</span></span>

![NuGet 包管理器](../media/ArduinoWiringPortingGuide/Nuget_PackageManager.png)
