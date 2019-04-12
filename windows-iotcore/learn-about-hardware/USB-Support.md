---
title: 有关 USB 支持和 Windows 10 IoT core 的双角色概述
author: saraclay
ms.author: saclayt
ms.date: 10/11/2017
ms.topic: article
description: 了解有关 USB 支持以及双角色新增功能以及如何进行此自定义适用于 Windows 10 IoT Core 设备。
keywords: windows iot、 USB 支持、 双重角色、 USB
ms.openlocfilehash: be1ba523975a0a39414537242ca3b14b680d9799
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510757"
---
# <a name="overview-of-usb-support-and-dual-role"></a><span data-ttu-id="d0c80-104">USB 支持和双角色概述</span><span class="sxs-lookup"><span data-stu-id="d0c80-104">Overview of USB Support and Dual Role</span></span>

<span data-ttu-id="d0c80-105">通用串行总线 (USB) 提供了可展开，热插拔插串行接口，可确保键盘、 鼠标、 游戏杆、 打印机、 扫描仪、 存储设备、 调制解调器和视频之类的外设的标准、 低成本的连接会议摄像机。</span><span class="sxs-lookup"><span data-stu-id="d0c80-105">A Universal Serial Bus (USB) provides an expandable, hot-pluggable Plug and Play serial interface that ensures a standard, low-cost connection for peripheral devices such as keyboards, mice, joysticks, printers, scanners, storage devices, modems, and video conferencing cameras.</span></span>  
<span data-ttu-id="d0c80-106">当我们谈及 USB 设备时，USB 函数堆栈是指一组枚举并由插管理器中，加载驱动程序和复合的 USB 设备可以支持一种配置中的多个接口。</span><span class="sxs-lookup"><span data-stu-id="d0c80-106">When we talk about USB devices, the USB function stack refers to a group of drivers that are enumerated and loaded by the Plug and Play Manager, and a composite USB device can support multiple interfaces in a single configuration.</span></span> <span data-ttu-id="d0c80-107">尽管大部分什么我们讨论有关在此文章的 USB 2.0 与双角色通常称为 USB 在外出时随时或 USB OTG 或 OTG，该技术还有助于了解有关 USB 3.0 和它区别 USB 2.0。</span><span class="sxs-lookup"><span data-stu-id="d0c80-107">While most of what we talk about in this article relates to the dual role for USB 2.0, more commonly known as USB On-The-Go or USB OTG or OTG, it is also helpful to know about USB 3.0 and how it differs from USB 2.0.</span></span> <span data-ttu-id="d0c80-108">USB OTG 定义适用于设备的两个角色：OTG 的设备和 OTG B 设备，指定哪一侧提供链接，它最初是在主机的电源。</span><span class="sxs-lookup"><span data-stu-id="d0c80-108">The USB OTG defines two roles for devices: OTG A-device and OTG B-device, specifying which side supplies power to the link and which is the host initially.</span></span> <span data-ttu-id="d0c80-109">由于每个 OTG 控制器支持这两个角色，它们通常称为"双角色"控制器而不是"OTG 控制器"。</span><span class="sxs-lookup"><span data-stu-id="d0c80-109">Since every OTG controller supports both roles, they are often called "Dual-Role" controllers rather than "OTG controllers."</span></span> <span data-ttu-id="d0c80-110">USB 3.0，另一方面，可以使设备成为主机或外围设备。</span><span class="sxs-lookup"><span data-stu-id="d0c80-110">USB 3.0, on the other hand, can make devices into either hosts or peripherals.</span></span> <span data-ttu-id="d0c80-111">某些设备可能需要根据哪种类型的另一端上检测到任一角色。</span><span class="sxs-lookup"><span data-stu-id="d0c80-111">Some devices can take either role depending on what kind is detected on the other end.</span></span> <span data-ttu-id="d0c80-112">这些类型的端口称为双角色数据 (DRD)。</span><span class="sxs-lookup"><span data-stu-id="d0c80-112">These types of ports are called Dual-Role-Data (DRD).</span></span> <span data-ttu-id="d0c80-113">两个此类设备连接时，会随机分配角色，但可以从任何一端命令交换。</span><span class="sxs-lookup"><span data-stu-id="d0c80-113">When two such devices are connected, the roles are randomly assigned but a swap can be commanded from either end.</span></span> 

## <a name="architecture-of-usb-function-in-windows-10-iot-core"></a><span data-ttu-id="d0c80-114">USB 函数在 Windows 10 IoT 核心版中的体系结构</span><span class="sxs-lookup"><span data-stu-id="d0c80-114">Architecture of USB Function in Windows 10 IoT Core</span></span>

<span data-ttu-id="d0c80-115">当在 Windows 10 IoT 平台充当 USB 设备时，它将使用几种配置之一。</span><span class="sxs-lookup"><span data-stu-id="d0c80-115">When the Windows 10 IoT platform acts as USB device, it will use one of several configurations.</span></span> <span data-ttu-id="d0c80-116">每个配置了一个或多个 USB 接口。</span><span class="sxs-lookup"><span data-stu-id="d0c80-116">Each configuration has one or more USB interfaces.</span></span> <span data-ttu-id="d0c80-117">若要正确地在 Windows 10 IoT 上支持 USB OTG，需要注意几件事情。</span><span class="sxs-lookup"><span data-stu-id="d0c80-117">To properly support USB OTG on Windows 10 IoT, several things need to be taken care of.</span></span>  

## <a name="components-oems-have-to-supply"></a><span data-ttu-id="d0c80-118">组件 Oem 必须提供</span><span class="sxs-lookup"><span data-stu-id="d0c80-118">Components OEMs have to supply</span></span>

<span data-ttu-id="d0c80-119">Oem 需要提供两面 – USB 设备端以及可能是 USB 主机端上的组件。</span><span class="sxs-lookup"><span data-stu-id="d0c80-119">OEMs need to supply components on both sides – for the USB device-side and possibly for the USB host-side.</span></span>  

![组件 OEM 提供，数量](../media/USB-Support/OEM-Components.png)

### <a name="oems-support-for-both-sides"></a><span data-ttu-id="d0c80-121">双方的 Oem 支持</span><span class="sxs-lookup"><span data-stu-id="d0c80-121">OEMs support for both sides</span></span>

<span data-ttu-id="d0c80-122">每个 USB 设备具有唯一 VID 和 PID，以便将其标记。</span><span class="sxs-lookup"><span data-stu-id="d0c80-122">Every USB device has unique VID and PID, which identify it.</span></span> <span data-ttu-id="d0c80-123">OEM，为基于 Windows IoT 的 USB 设备制造商需要提供这些。</span><span class="sxs-lookup"><span data-stu-id="d0c80-123">An OEM, as the manufacturer of a Windows IoT-based USB device, needs to supply those.</span></span>  <span data-ttu-id="d0c80-124">Oem 可以将应用于 USB 联盟并获取其公司 VID （如果它们尚未拥有的话），然后选择将是该产品的唯一的 PID。</span><span class="sxs-lookup"><span data-stu-id="d0c80-124">OEMs can apply to the USB Consortium and obtain their company VID (if they don't have one already) and then choose a PID that will be unique for that product.</span></span> <span data-ttu-id="d0c80-125">USBFN 功能的 Windows 10 IoT 连接到 PC 时它将使用这些"VID_nnn"和"PID_NNN"充当 USB 设备 （用于选择作为任何功能集的 myUSBFN.sys 中）。</span><span class="sxs-lookup"><span data-stu-id="d0c80-125">When Windows 10 IoT with USBFN functionality is connected to a PC it will act as USB device (of whatever functionality to choose as set in myUSBFN.sys), with those "VID_nnn" and "PID_NNN".</span></span> <span data-ttu-id="d0c80-126">宿主 PC 然后使用此 VID 和 PID 组合以查找相应的驱动程序加载 (myUSB.sys)。</span><span class="sxs-lookup"><span data-stu-id="d0c80-126">This VID and PID combination is then used by the host PC to find the appropriate drivers to load (myUSB.sys).</span></span> 

![USB 函数如何组合在一起](../media/USB-Support/OEM-supplies.png)

### <a name="supporting-from-the-device-side"></a><span data-ttu-id="d0c80-128">从设备端支持</span><span class="sxs-lookup"><span data-stu-id="d0c80-128">Supporting from the device side</span></span>

_<span data-ttu-id="d0c80-129">要包括在 FFU 映像生成了 USBFN 启用的功能</span><span class="sxs-lookup"><span data-stu-id="d0c80-129">Features to include in FFU for image generation with USBFN enabled</span></span>_
* <span data-ttu-id="d0c80-130">IoT 映像必须包含所需的包，即 ufx01000.sys 和 usbfnclx.sys。</span><span class="sxs-lookup"><span data-stu-id="d0c80-130">The IoT image must have the necessary packages in it, namely ufx01000.sys and usbfnclx.sys.</span></span> <span data-ttu-id="d0c80-131">这两个都具有以下包`Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`。</span><span class="sxs-lookup"><span data-stu-id="d0c80-131">They both come with the following package `Microsoft-IoTUAP-USBFN-Class-Extension-Package.cab`.</span></span> <span data-ttu-id="d0c80-132">在其 XML 文件中，其中列出了在 FFU 中包含的所有功能，Oem 必须使用正确的"功能"标记。</span><span class="sxs-lookup"><span data-stu-id="d0c80-132">OEMs must use a proper "feature" tag in their XML file, which lists all features included in the FFU.</span></span> <span data-ttu-id="d0c80-133">例如，在 BoardTestOEMInput.xml 文件中将有以下条目<Feature>IOT_USBFN_CLASS_EXTENSION</Feature>将其纳入<Microsoft>功能部分。</span><span class="sxs-lookup"><span data-stu-id="d0c80-133">For example, in the BoardTestOEMInput.xml file there will be the following entry <Feature>IOT_USBFN_CLASS_EXTENSION</Feature>  included under <Microsoft> features section.</span></span> 

_<span data-ttu-id="d0c80-134">角色切换中 USB 驱动程序</span><span class="sxs-lookup"><span data-stu-id="d0c80-134">USB Role Switching driver</span></span>_
* <span data-ttu-id="d0c80-135">有关 USB OTG，Oem 必须提供正确的 ACPI 表条目 (*myOTGacpi*) USB 角色切换驱动程序和驱动程序本身 (\* myURS.sys)。</span><span class="sxs-lookup"><span data-stu-id="d0c80-135">For the USB OTG, OEMs have to supply the correct ACPI table entry (*myOTGacpi*) for the USB role-switching driver and the driver itself (\*myURS.sys).</span></span>

_<span data-ttu-id="d0c80-136">USB 函数控制器驱动程序</span><span class="sxs-lookup"><span data-stu-id="d0c80-136">USB Function Controller Driver</span></span>_
* <span data-ttu-id="d0c80-137">这取决于由 Oem 硬件。</span><span class="sxs-lookup"><span data-stu-id="d0c80-137">This depends on the hardware used by OEMs.</span></span> <span data-ttu-id="d0c80-138">Microsoft 提供了用于两个常用 USB OTG 芯片集-Synopsys 和 ChipIdea USB 函数控制器驱动程序。</span><span class="sxs-lookup"><span data-stu-id="d0c80-138">Microsoft supplies USB Function Controller drivers for two popular USB OTG chipsets - Synopsys and ChipIdea.</span></span>
* <span data-ttu-id="d0c80-139">如果 OEM 选择使用另一个 USB OTG 芯片组，则 OEM 必须提供其自己的 USB 函数控制器硬件 (*myfunctioncontroller.sys*)。</span><span class="sxs-lookup"><span data-stu-id="d0c80-139">If an OEM chooses to use another USB OTG chipset, then the OEM must supply their own USB function controller hardware (*myfunctioncontroller.sys*).</span></span>

_<span data-ttu-id="d0c80-140">USB 函数类驱动程序</span><span class="sxs-lookup"><span data-stu-id="d0c80-140">USB Function Class drivers</span></span>_
* <span data-ttu-id="d0c80-141">必须提供至少一个 USB 函数类驱动程序。</span><span class="sxs-lookup"><span data-stu-id="d0c80-141">At least one USB function class driver must be supplied.</span></span>
* <span data-ttu-id="d0c80-142">此驱动程序实现特定 USB 设备的功能。</span><span class="sxs-lookup"><span data-stu-id="d0c80-142">This driver implements specific USB device functionality.</span></span> <span data-ttu-id="d0c80-143">它确定该设备将显示为在主机端也为 it 将执行操作。</span><span class="sxs-lookup"><span data-stu-id="d0c80-143">It determines what the device will appear as on the host side as well as what it will do.</span></span>
<span data-ttu-id="d0c80-144">例如，它可能显示为串行通信的设备或作为大容量存储设备或完全自定义类型设备 (*myUSBFN.sys*)。</span><span class="sxs-lookup"><span data-stu-id="d0c80-144">For example, it may appear as a serial communications device or as a mass storage device or a completely custom type device (*myUSBFN.sys*).</span></span>

_<span data-ttu-id="d0c80-145">配置函数的 USB 设备</span><span class="sxs-lookup"><span data-stu-id="d0c80-145">Configuring USB Function Device</span></span>_
* <span data-ttu-id="d0c80-146">在 USB 设备模式下的 IoT 平台时，它可以在一个或多个配置下进行操作。</span><span class="sxs-lookup"><span data-stu-id="d0c80-146">When the IoT platform is in USB device mode, it can operate under one or more configurations.</span></span> <span data-ttu-id="d0c80-147">必须添加在使用每个配置，并指定其属性。</span><span class="sxs-lookup"><span data-stu-id="d0c80-147">Each configuration in use must be added and have its properties specified.</span></span>

_<span data-ttu-id="d0c80-148">通用属性</span><span class="sxs-lookup"><span data-stu-id="d0c80-148">Common Properties</span></span>_
* <span data-ttu-id="d0c80-149">没有为所有 USB 函数配置 IoT 平台的常见属性。</span><span class="sxs-lookup"><span data-stu-id="d0c80-149">There are common properties for all USB function configurations of the IoT platform.</span></span> <span data-ttu-id="d0c80-150">最终将由最多 OEM 用来指定标准 USB 描述符条目，例如视频、 PID、 DeviceClass、 DeviceProtocol，Manufacturerer 字符串、 序列号，等等。</span><span class="sxs-lookup"><span data-stu-id="d0c80-150">It is ultimately up to the OEM to specify standard USB descriptor entries such as VID, PID, DeviceClass, DeviceProtocol, Manufacturerer string, serial number, etc.</span></span>
* <span data-ttu-id="d0c80-151">在以下位置的注册表中设置这些通用属性：</span><span class="sxs-lookup"><span data-stu-id="d0c80-151">These common properties are set in registry in the following location:</span></span> `HKLM\System\ControlSet001\Control\USBFN\default`

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
> <span data-ttu-id="d0c80-152">上面的值是仅用于演示目的并不能在任何产品中使用。</span><span class="sxs-lookup"><span data-stu-id="d0c80-152">The values above are for demonstration purposes only and cannot be used in any product.</span></span> <span data-ttu-id="d0c80-153">OEM 必须替换这些占位符字段*实际值*上述每个条目中。</span><span class="sxs-lookup"><span data-stu-id="d0c80-153">The OEM must replace these placeholder fields with *actual values* in each entry above.</span></span>

_<span data-ttu-id="d0c80-154">每个配置属性</span><span class="sxs-lookup"><span data-stu-id="d0c80-154">Per configuration properties</span></span>_

<span data-ttu-id="d0c80-155">配置存储在注册表中的以下项：</span><span class="sxs-lookup"><span data-stu-id="d0c80-155">Configurations are stored in a registry under the following key:</span></span> `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations`

<span data-ttu-id="d0c80-156">默认情况下，没有包含在 FFU，按照中的一个空的默认 USB 函数配置：</span><span class="sxs-lookup"><span data-stu-id="d0c80-156">By default, there is an empty default USB function configuration included in the FFU, as set in:</span></span> `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`

<span data-ttu-id="d0c80-157">此空的默认配置会导致 Windows IoT 设备与为其在此处显示的 IoT 平台是在主机端安装任何驱动程序。</span><span class="sxs-lookup"><span data-stu-id="d0c80-157">This empty default configuration results in the IoT platform appearing as a Windows IoT device for which there is no driver on the host side installed.</span></span>

![USBFN 的配置](../media/USB-Support/config-screenshot.png)

<span data-ttu-id="d0c80-159">每个配置必须指定某些属性，例如接口列表。</span><span class="sxs-lookup"><span data-stu-id="d0c80-159">Each configuration must specify certain properties, such as the Interface List.</span></span> <span data-ttu-id="d0c80-160">IoT 平台可以充当具有不同的配置，一起共享到 USB 主机公开从 USB 设备的 USB 接口定义的 USB 设备。</span><span class="sxs-lookup"><span data-stu-id="d0c80-160">The IoT platform can operate as a USB device with different configurations, whic hare defined by USB interfaces that are exposed from USB device to USB host.</span></span>

`HKLM\System\CurrentControlSet\Control\USBFN\Configurations\Default`

```
bmAttributes=0xC0
bMaxPower=0xFA
InterfaceList =
InterfaceDescriptor =
InterfaceGUIDE =
```

<span data-ttu-id="d0c80-161">目前，所选的配置是将连接到 USB 热时实际上是一个：</span><span class="sxs-lookup"><span data-stu-id="d0c80-161">Currently, the selected configuration is the one that will be in effect when connecting to the USB hot:</span></span> `HKLM\SYSTEM\ControlSet001\Control\USBFN`

_<span data-ttu-id="d0c80-162">配置示例</span><span class="sxs-lookup"><span data-stu-id="d0c80-162">Examples of configurations</span></span>_

1. <span data-ttu-id="d0c80-163">单个配置</span><span class="sxs-lookup"><span data-stu-id="d0c80-163">Single configuration</span></span>
   1. <span data-ttu-id="d0c80-164">必须包含至少一个接口</span><span class="sxs-lookup"><span data-stu-id="d0c80-164">Must contain at least one interface</span></span>
   2. <span data-ttu-id="d0c80-165">可以是默认配置</span><span class="sxs-lookup"><span data-stu-id="d0c80-165">Can be a default configuration</span></span>
   3. <span data-ttu-id="d0c80-166">当连接到 PC 时，IoT 平台将显示为该类型的 USB 设备 （例如调制解调器或存储）。</span><span class="sxs-lookup"><span data-stu-id="d0c80-166">When connected to a PC, the IoT platform will appear as that type of USB device (e.g. modem or storage).</span></span>
   4. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\default`<span data-ttu-id="d0c80-167">，</span><span class="sxs-lookup"><span data-stu-id="d0c80-167">,</span></span> `InterfaceList = "MODEM\0MTP"`

2. <span data-ttu-id="d0c80-168">复合配置</span><span class="sxs-lookup"><span data-stu-id="d0c80-168">Composite configuration</span></span>
   1. <span data-ttu-id="d0c80-169">包含一系列具有其他参数的接口</span><span class="sxs-lookup"><span data-stu-id="d0c80-169">Contains a list of interfaces with additional parameters</span></span>
   2. <span data-ttu-id="d0c80-170">当连接到 PC 时，IoT 平台会作为具有多个单元中 （即 MTP 设备、 串行设备、 自定义设备） 的复合 USB 设备。</span><span class="sxs-lookup"><span data-stu-id="d0c80-170">When connected to a PC, the IoT platform will appear as a composite USB device with multiple units in it (i.e. MTP device, serial device, custom device).</span></span>
   3. `HKLM\SYSTEM\ControlSet001\Control\USBFN\Configurations\mycfg`<span data-ttu-id="d0c80-171">，</span><span class="sxs-lookup"><span data-stu-id="d0c80-171">,</span></span> `InterfaceList = "MODEM\0MTP"`

<span data-ttu-id="d0c80-172">USBFN 接口枚举注册表中的以下项下：</span><span class="sxs-lookup"><span data-stu-id="d0c80-172">USBFN Interfaces are enumerated in registry under the following key:</span></span>
`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\USBFN\Interfaces`

<span data-ttu-id="d0c80-173">USB 接口的每个条目必须包含一个接口描述符值和接口的 GUID。</span><span class="sxs-lookup"><span data-stu-id="d0c80-173">Each USB interface entry must contain an interface descriptor value and an interface GUID.</span></span>

### <a name="supporting-from-the-host-side"></a><span data-ttu-id="d0c80-174">从宿主端支持</span><span class="sxs-lookup"><span data-stu-id="d0c80-174">Supporting from the host side</span></span>

<span data-ttu-id="d0c80-175">如果 OEM 选择实现任何标准的 USB 接口 （例如 大容量存储） 在设备端，然后宿主 PC 可以使用现成的 Windows 驱动程序为该类型的 USB 设备。</span><span class="sxs-lookup"><span data-stu-id="d0c80-175">If an OEM chooses to implement any standard USB interface (e.g.  mass storage) on the device side, then a host PC can use in-box Windows drivers for that type of USB device.</span></span> <span data-ttu-id="d0c80-176">如果 OEM 在设备端实现任何自定义的 USB 接口，则有必要 oem 用来开发的自定义的函数 USB 设备的 Windows 主机驱动程序。</span><span class="sxs-lookup"><span data-stu-id="d0c80-176">If an OEM implements any custom USB interface on device side, then it is necessary for the OEM to develop a Windows host driver for that custom USB Function device.</span></span> 
