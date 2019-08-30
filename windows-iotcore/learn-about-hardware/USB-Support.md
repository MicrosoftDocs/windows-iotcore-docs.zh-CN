---
title: 适用于 Windows 10 IoT Core 的 USB 支持和双重角色概述
author: saraclay
ms.author: saclayt
ms.date: 10/11/2017
ms.topic: article
description: 了解什么是 USB 支持和双角色, 以及如何为 Windows 10 IoT Core 设备自定义此功能。
keywords: windows iot, USB 支持, 双角色, USB
ms.openlocfilehash: be1ba523975a0a39414537242ca3b14b680d9799
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167596"
---
# <a name="overview-of-usb-support-and-dual-role"></a><span data-ttu-id="e2ce2-104">USB 支持和双重角色概述</span><span class="sxs-lookup"><span data-stu-id="e2ce2-104">Overview of USB Support and Dual Role</span></span>

<span data-ttu-id="e2ce2-105">通用串行总线 (USB) 提供可扩展的热插拔即插即用串行接口, 可确保外围设备 (例如键盘、鼠标、游戏杆、打印机、扫描仪、存储设备、调制解调器和视频) 的标准低成本连接。会议摄像机。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-105">A Universal Serial Bus (USB) provides an expandable, hot-pluggable Plug and Play serial interface that ensures a standard, low-cost connection for peripheral devices such as keyboards, mice, joysticks, printers, scanners, storage devices, modems, and video conferencing cameras.</span></span>  
<span data-ttu-id="e2ce2-106">当我们谈到 USB 设备时, USB 函数堆栈是指由即插即用 Manager 枚举和加载的一组驱动程序, 复合 USB 设备可以在单个配置中支持多个接口。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-106">When we talk about USB devices, the USB function stack refers to a group of drivers that are enumerated and loaded by the Plug and Play Manager, and a composite USB device can support multiple interfaces in a single configuration.</span></span> <span data-ttu-id="e2ce2-107">尽管本文中所述的大部分内容都与用于 USB 2.0 的双重角色相关, 但更常见的是 usb 即用或 USB OTG 或 OTG, 但知道 USB 3.0 以及它与 USB 2.0 有何不同。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-107">While most of what we talk about in this article relates to the dual role for USB 2.0, more commonly known as USB On-The-Go or USB OTG or OTG, it is also helpful to know about USB 3.0 and how it differs from USB 2.0.</span></span> <span data-ttu-id="e2ce2-108">USB OTG 为设备定义了两个角色:OTG A-设备和 OTG B-设备, 指定哪一端提供链接电源, 后者最初为主机。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-108">The USB OTG defines two roles for devices: OTG A-device and OTG B-device, specifying which side supplies power to the link and which is the host initially.</span></span> <span data-ttu-id="e2ce2-109">由于每个 OTG 控制器都支持这两个角色, 因此它们通常称为 "双角色" 控制器而不是 "OTG 控制器"。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-109">Since every OTG controller supports both roles, they are often called "Dual-Role" controllers rather than "OTG controllers."</span></span> <span data-ttu-id="e2ce2-110">另一方面, USB 3.0 可以使设备进入主机或外围设备。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-110">USB 3.0, on the other hand, can make devices into either hosts or peripherals.</span></span> <span data-ttu-id="e2ce2-111">某些设备可以采用这两种角色, 具体取决于在另一端上检测到的类型。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-111">Some devices can take either role depending on what kind is detected on the other end.</span></span> <span data-ttu-id="e2ce2-112">这类端口称为 "双角色数据" (DRD)。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-112">These types of ports are called Dual-Role-Data (DRD).</span></span> <span data-ttu-id="e2ce2-113">连接两个此类设备时, 将随机分配角色, 但可以从任一端发出交换。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-113">When two such devices are connected, the roles are randomly assigned but a swap can be commanded from either end.</span></span> 

## <a name="architecture-of-usb-function-in-windows-10-iot-core"></a><span data-ttu-id="e2ce2-114">Windows 10 IoT Core 中的 USB 功能的体系结构</span><span class="sxs-lookup"><span data-stu-id="e2ce2-114">Architecture of USB Function in Windows 10 IoT Core</span></span>

<span data-ttu-id="e2ce2-115">当 Windows 10 IoT 平台充当 USB 设备时, 它将使用几种配置中的一种。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-115">When the Windows 10 IoT platform acts as USB device, it will use one of several configurations.</span></span> <span data-ttu-id="e2ce2-116">每个配置都有一个或多个 USB 接口。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-116">Each configuration has one or more USB interfaces.</span></span> <span data-ttu-id="e2ce2-117">若要在 Windows 10 IoT 上正确支持 USB OTG, 需要注意以下几件事。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-117">To properly support USB OTG on Windows 10 IoT, several things need to be taken care of.</span></span>  

## <a name="components-oems-have-to-supply"></a><span data-ttu-id="e2ce2-118">Oem 必须提供的组件</span><span class="sxs-lookup"><span data-stu-id="e2ce2-118">Components OEMs have to supply</span></span>

<span data-ttu-id="e2ce2-119">Oem 需要为 USB 设备端和 USB 主机端提供两端的组件。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-119">OEMs need to supply components on both sides – for the USB device-side and possibly for the USB host-side.</span></span>  

![OEM 供应的组件](../media/USB-Support/OEM-Components.png)

### <a name="oems-support-for-both-sides"></a><span data-ttu-id="e2ce2-121">Oem 支持两侧</span><span class="sxs-lookup"><span data-stu-id="e2ce2-121">OEMs support for both sides</span></span>

<span data-ttu-id="e2ce2-122">每个 USB 设备都具有唯一的 VID 和 PID, 用于识别它。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-122">Every USB device has unique VID and PID, which identify it.</span></span> <span data-ttu-id="e2ce2-123">作为基于 Windows IoT 的 USB 设备的制造商, OEM 需要提供这些。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-123">An OEM, as the manufacturer of a Windows IoT-based USB device, needs to supply those.</span></span>  <span data-ttu-id="e2ce2-124">Oem 可应用于 USB 联盟, 并获取其公司 VID (如果尚未安装), 然后选择对该产品唯一的 PID。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-124">OEMs can apply to the USB Consortium and obtain their company VID (if they don't have one already) and then choose a PID that will be unique for that product.</span></span> <span data-ttu-id="e2ce2-125">当带有 USBFN 功能的 Windows 10 IoT 连接到电脑时, 它将充当 USB 设备 (在 myUSBFN 中选择的任何功能), 其中包含 "VID_nnn" 和 "PID_NNN"。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-125">When Windows 10 IoT with USBFN functionality is connected to a PC it will act as USB device (of whatever functionality to choose as set in myUSBFN.sys), with those "VID_nnn" and "PID_NNN".</span></span> <span data-ttu-id="e2ce2-126">宿主 PC 将使用此 VID 和 PID 组合查找适当的驱动程序以进行加载 (myUSB)。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-126">This VID and PID combination is then used by the host PC to find the appropriate drivers to load (myUSB.sys).</span></span> 

![USB 函数如何结合在一起](../media/USB-Support/OEM-supplies.png)

### <a name="supporting-from-the-device-side"></a><span data-ttu-id="e2ce2-128">从设备端支持</span><span class="sxs-lookup"><span data-stu-id="e2ce2-128">Supporting from the device side</span></span>

<span data-ttu-id="e2ce2-129">_要在 FFU 中包含的用于启用 USBFN 的映像生成的功能_</span><span class="sxs-lookup"><span data-stu-id="e2ce2-129">_Features to include in FFU for image generation with USBFN enabled_</span></span>
* <span data-ttu-id="e2ce2-130">IoT 映像必须包含其中所需的包, 即 ufx01000 和 usbfnclx。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-130">The IoT image must have the necessary packages in it, namely ufx01000.sys and usbfnclx.sys.</span></span> <span data-ttu-id="e2ce2-131">它们都附带了以下程序包`Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-131">They both come with the following package `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`.</span></span> <span data-ttu-id="e2ce2-132">Oem 必须在其 XML 文件中使用正确的 "feature" 标记, 其中列出了 FFU 中包含的所有功能。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-132">OEMs must use a proper "feature" tag in their XML file, which lists all features included in the FFU.</span></span> <span data-ttu-id="e2ce2-133">例如, 在 BoardTestOEMInput 文件中, " <Microsoft>功能" 部分中将包含以下项<Feature>IOT_USBFN_CLASS_EXTENSION</Feature> 。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-133">For example, in the BoardTestOEMInput.xml file there will be the following entry <Feature>IOT_USBFN_CLASS_EXTENSION</Feature>  included under <Microsoft> features section.</span></span> 

<span data-ttu-id="e2ce2-134">_USB 角色切换驱动程序_</span><span class="sxs-lookup"><span data-stu-id="e2ce2-134">_USB Role Switching driver_</span></span>
* <span data-ttu-id="e2ce2-135">对于 USB OTG, Oem 必须为 USB 角色切换驱动程序和驱动程序本身 (\* myURS) 提供正确的 ACPI 表条目 (*myOTGacpi*)。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-135">For the USB OTG, OEMs have to supply the correct ACPI table entry (*myOTGacpi*) for the USB role-switching driver and the driver itself (\*myURS.sys).</span></span>

<span data-ttu-id="e2ce2-136">_USB 函数控制器驱动程序_</span><span class="sxs-lookup"><span data-stu-id="e2ce2-136">_USB Function Controller Driver_</span></span>
* <span data-ttu-id="e2ce2-137">这取决于 Oem 使用的硬件。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-137">This depends on the hardware used by OEMs.</span></span> <span data-ttu-id="e2ce2-138">Microsoft 为两个常见 USB OTG 芯片集提供 USB 函数控制器驱动程序-Synopsys 和 ChipIdea。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-138">Microsoft supplies USB Function Controller drivers for two popular USB OTG chipsets - Synopsys and ChipIdea.</span></span>
* <span data-ttu-id="e2ce2-139">如果 OEM 选择使用另一个 USB OTG 芯片, 则 OEM 必须提供其自己的 USB 函数控制器硬件 (*myfunctioncontroller*)。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-139">If an OEM chooses to use another USB OTG chipset, then the OEM must supply their own USB function controller hardware (*myfunctioncontroller.sys*).</span></span>

<span data-ttu-id="e2ce2-140">_USB 函数类驱动程序_</span><span class="sxs-lookup"><span data-stu-id="e2ce2-140">_USB Function Class drivers_</span></span>
* <span data-ttu-id="e2ce2-141">必须至少提供一个 USB 函数类驱动程序。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-141">At least one USB function class driver must be supplied.</span></span>
* <span data-ttu-id="e2ce2-142">此驱动程序实现特定的 USB 设备功能。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-142">This driver implements specific USB device functionality.</span></span> <span data-ttu-id="e2ce2-143">它确定设备将在主机端显示的内容以及它将会执行的操作。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-143">It determines what the device will appear as on the host side as well as what it will do.</span></span>
<span data-ttu-id="e2ce2-144">例如, 它可能显示为串行通信设备或大容量存储设备或完全自定义类型的设备 (*myUSBFN*)。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-144">For example, it may appear as a serial communications device or as a mass storage device or a completely custom type device (*myUSBFN.sys*).</span></span>

<span data-ttu-id="e2ce2-145">_正在配置 USB 函数设备_</span><span class="sxs-lookup"><span data-stu-id="e2ce2-145">_Configuring USB Function Device_</span></span>
* <span data-ttu-id="e2ce2-146">当 IoT 平台处于 USB 设备模式时, 它可以在一个或多个配置下运行。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-146">When the IoT platform is in USB device mode, it can operate under one or more configurations.</span></span> <span data-ttu-id="e2ce2-147">必须添加每个使用中的配置, 并指定其属性。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-147">Each configuration in use must be added and have its properties specified.</span></span>

<span data-ttu-id="e2ce2-148">_通用属性_</span><span class="sxs-lookup"><span data-stu-id="e2ce2-148">_Common Properties_</span></span>
* <span data-ttu-id="e2ce2-149">IoT 平台的所有 USB 功能配置都有常见的属性。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-149">There are common properties for all USB function configurations of the IoT platform.</span></span> <span data-ttu-id="e2ce2-150">最终, OEM 需要指定标准 USB 描述符条目, 例如 VID、PID、DeviceClass、DeviceProtocol、Manufacturerer 字符串、序列号等。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-150">It is ultimately up to the OEM to specify standard USB descriptor entries such as VID, PID, DeviceClass, DeviceProtocol, Manufacturerer string, serial number, etc.</span></span>
* <span data-ttu-id="e2ce2-151">在注册表中的以下位置设置这些通用属性:`HKLM\System\ControlSet001\Control\USBFN\default`</span><span class="sxs-lookup"><span data-stu-id="e2ce2-151">These common properties are set in registry in the following location: `HKLM\System\ControlSet001\Control\USBFN\default`</span></span>

```
BcdDevice=0x1 
bDeviceClass=0x0 
bDeviceProtocol=0x0 
bDeviceSubClass= 0x0 
idProduct= 0xc0c0 
idVendor=0x045e 
iManufacturer=1 
iSerialNumber=3 
ManufacturerString=OEMname 
ProductString="Windows IOT" 
SerialNumberString=0x123 
```
> [!IMPORTANT]
> <span data-ttu-id="e2ce2-152">上述值仅用于演示目的, 不能用于任何产品。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-152">The values above are for demonstration purposes only and cannot be used in any product.</span></span> <span data-ttu-id="e2ce2-153">OEM 必须将这些占位符字段替换为上述每个条目中的*实际值*。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-153">The OEM must replace these placeholder fields with *actual values* in each entry above.</span></span>

<span data-ttu-id="e2ce2-154">_按配置属性_</span><span class="sxs-lookup"><span data-stu-id="e2ce2-154">_Per configuration properties_</span></span>

<span data-ttu-id="e2ce2-155">配置存储在注册表中的以下项下面:`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`</span><span class="sxs-lookup"><span data-stu-id="e2ce2-155">Configurations are stored in a registry under the following key: `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`</span></span>

<span data-ttu-id="e2ce2-156">默认情况下, FFU 中包含空的默认 USB 函数配置, 如中所述:`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`</span><span class="sxs-lookup"><span data-stu-id="e2ce2-156">By default, there is an empty default USB function configuration included in the FFU, as set in: `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`</span></span>

<span data-ttu-id="e2ce2-157">此空的默认配置会导致 IoT 平台显示为在其上未安装主机端驱动程序的 Windows IoT 设备。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-157">This empty default configuration results in the IoT platform appearing as a Windows IoT device for which there is no driver on the host side installed.</span></span>

![USBFN 的配置](../media/USB-Support/config-screenshot.png)

<span data-ttu-id="e2ce2-159">每个配置必须指定特定的属性, 如 Interface List。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-159">Each configuration must specify certain properties, such as the Interface List.</span></span> <span data-ttu-id="e2ce2-160">IoT 平台可以作为带有不同配置的 USB 设备运行, 这些配置 h 由从 USB 设备向 USB 主机公开的 USB 接口定义。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-160">The IoT platform can operate as a USB device with different configurations, whic hare defined by USB interfaces that are exposed from USB device to USB host.</span></span>

`HKLM\System\CurrentControlSet\Control\USBFN\Configurations\Default`

```
bmAttributes=0xC0
bMaxPower=0xFA
InterfaceList =
InterfaceDescriptor =
InterfaceGUIDE =
```

<span data-ttu-id="e2ce2-161">目前, 所选配置是在连接到 USB 热:`HKLM\SYSTEM\ControlSet001\Control\USBFN`</span><span class="sxs-lookup"><span data-stu-id="e2ce2-161">Currently, the selected configuration is the one that will be in effect when connecting to the USB hot: `HKLM\SYSTEM\ControlSet001\Control\USBFN`</span></span>

<span data-ttu-id="e2ce2-162">_配置示例_</span><span class="sxs-lookup"><span data-stu-id="e2ce2-162">_Examples of configurations_</span></span>

1. <span data-ttu-id="e2ce2-163">单个配置</span><span class="sxs-lookup"><span data-stu-id="e2ce2-163">Single configuration</span></span>
   1. <span data-ttu-id="e2ce2-164">必须至少包含一个接口</span><span class="sxs-lookup"><span data-stu-id="e2ce2-164">Must contain at least one interface</span></span>
   2. <span data-ttu-id="e2ce2-165">可以是默认配置</span><span class="sxs-lookup"><span data-stu-id="e2ce2-165">Can be a default configuration</span></span>
   3. <span data-ttu-id="e2ce2-166">连接到电脑时, IoT 平台将显示为该类型的 USB 设备 (例如调制解调器或存储)。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-166">When connected to a PC, the IoT platform will appear as that type of USB device (e.g. modem or storage).</span></span>
   4. <span data-ttu-id="e2ce2-167">`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`， `InterfaceList = "MODEM\0MTP"`</span><span class="sxs-lookup"><span data-stu-id="e2ce2-167">`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`, `InterfaceList = "MODEM\0MTP"`</span></span>

2. <span data-ttu-id="e2ce2-168">复合配置</span><span class="sxs-lookup"><span data-stu-id="e2ce2-168">Composite configuration</span></span>
   1. <span data-ttu-id="e2ce2-169">包含具有其他参数的接口的列表</span><span class="sxs-lookup"><span data-stu-id="e2ce2-169">Contains a list of interfaces with additional parameters</span></span>
   2. <span data-ttu-id="e2ce2-170">当连接到电脑时, IoT 平台将显示为复合 USB 设备, 其中包含多个单位 (即 MTP 设备、串行设备、自定义设备)。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-170">When connected to a PC, the IoT platform will appear as a composite USB device with multiple units in it (i.e. MTP device, serial device, custom device).</span></span>
   3. <span data-ttu-id="e2ce2-171">`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`， `InterfaceList = "MODEM\0MTP"`</span><span class="sxs-lookup"><span data-stu-id="e2ce2-171">`HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`, `InterfaceList = "MODEM\0MTP"`</span></span>

<span data-ttu-id="e2ce2-172">在注册表中的以下项下枚举 USBFN 接口:`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`</span><span class="sxs-lookup"><span data-stu-id="e2ce2-172">USBFN Interfaces are enumerated in registry under the following key: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`</span></span>

<span data-ttu-id="e2ce2-173">每个 USB 接口条目都必须包含一个接口描述符值和一个接口 GUID。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-173">Each USB interface entry must contain an interface descriptor value and an interface GUID.</span></span>

### <a name="supporting-from-the-host-side"></a><span data-ttu-id="e2ce2-174">从宿主端支持</span><span class="sxs-lookup"><span data-stu-id="e2ce2-174">Supporting from the host side</span></span>

<span data-ttu-id="e2ce2-175">如果 OEM 选择实现任何标准 USB 接口 (例如 大容量存储), 则主机 PC 可以为该类型的 USB 设备使用内置的 Windows 驱动程序。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-175">If an OEM chooses to implement any standard USB interface (e.g.  mass storage) on the device side, then a host PC can use in-box Windows drivers for that type of USB device.</span></span> <span data-ttu-id="e2ce2-176">如果 OEM 在设备端实现任何自定义 USB 接口, 则 OEM 需要为该自定义 USB 功能设备开发 Windows 主机驱动程序。</span><span class="sxs-lookup"><span data-stu-id="e2ce2-176">If an OEM implements any custom USB interface on device side, then it is necessary for the OEM to develop a Windows host driver for that custom USB Function device.</span></span> 
