---
title: 蓝牙支持
ms.date: 08/28/2017
ms.topic: article
description: 了解如何利用适用于运行 Windows 10 IoT Core 的设备的蓝牙。
keywords: windows iot，蓝牙，蓝牙支持，设备，设备门户
ms.openlocfilehash: e9159e6488ddcd078f5d73b0dafd08082e295cde
ms.sourcegitcommit: d84ba83c412d5c245e89880a4fca6155d98c8f52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2019
ms.locfileid: "72918369"
---
# <a name="bluetooth-support"></a><span data-ttu-id="98009-104">蓝牙支持</span><span class="sxs-lookup"><span data-stu-id="98009-104">Bluetooth Support</span></span>
<span data-ttu-id="98009-105">Windows 10 IoT Core 支持蓝牙4.0。</span><span class="sxs-lookup"><span data-stu-id="98009-105">Windows 10 IoT Core supports Bluetooth 4.0.</span></span> <span data-ttu-id="98009-106">可以在[硬件兼容性列表](../learn-about-hardware/HardwareCompatList.md)中找到受支持的蓝牙连接器列表。</span><span class="sxs-lookup"><span data-stu-id="98009-106">A list of supported Bluetooth dongles can be found in the [Hardware Compatibility List](../learn-about-hardware/HardwareCompatList.md).</span></span>

## <a name="about-bluetooth"></a><span data-ttu-id="98009-107">关于蓝牙</span><span class="sxs-lookup"><span data-stu-id="98009-107">About Bluetooth</span></span>
<span data-ttu-id="98009-108">你可以选择两种不同的蓝牙技术来在应用程序中实现：</span><span class="sxs-lookup"><span data-stu-id="98009-108">There are two different bluetooth technologies that you can choose to implement in your app:</span></span>

* <span data-ttu-id="98009-109">经典蓝牙（RFCOMM）在蓝牙 LE 之前，设备通常使用此协议通过蓝牙进行通信。</span><span class="sxs-lookup"><span data-stu-id="98009-109">Classic Bluetooth (RFCOMM) Before Bluetooth LE, devices commonly used this protocol to communicate using Bluetooth.</span></span> <span data-ttu-id="98009-110">此协议十分简单，可用于设备到设备的通信而无需节能。</span><span class="sxs-lookup"><span data-stu-id="98009-110">This protocol is simple and useful for device-to-device communication without the need of energy savings.</span></span> <span data-ttu-id="98009-111">连接要求配对。</span><span class="sxs-lookup"><span data-stu-id="98009-111">Connectivity requires pairing.</span></span>

* <span data-ttu-id="98009-112">蓝牙低能耗（BLE/LE）蓝牙低能耗（LE）是一个规范，用于定义在具有有效能源使用要求的设备之间的发现和通信协议。</span><span class="sxs-lookup"><span data-stu-id="98009-112">Bluetooth Low-Energy (BLE/LE) Bluetooth Low Energy (LE) is a specification that defines protocols for discovery and communication between devices that have an efficient energy usage requirement.</span></span> <span data-ttu-id="98009-113">如需更多详细信息（包括代码示例），则设备无需配对即可连接到 BLE 设备。</span><span class="sxs-lookup"><span data-stu-id="98009-113">For more information including code samples, As per recent builds, a device can connect to a BLE device without pairing.</span></span>

## <a name="supported-bluetooth-profiles"></a><span data-ttu-id="98009-114">受支持的蓝牙配置文件</span><span class="sxs-lookup"><span data-stu-id="98009-114">Supported Bluetooth Profiles</span></span>
<span data-ttu-id="98009-115">Windows 10 IoT Core 支持以下蓝牙配置文件：</span><span class="sxs-lookup"><span data-stu-id="98009-115">Windows 10 IoT Core supports the following Bluetooth profiles:</span></span>

1.  <span data-ttu-id="98009-116">**人体学接口设备配置文件概念（HID）** HID 设备从用户那里获取输入，并为人类 consumpation 提供输出。</span><span class="sxs-lookup"><span data-stu-id="98009-116">**Human Interface Device Profiles Concepts (HID)** An HID device takes input from a human and presents output for human consumpation.</span></span> <span data-ttu-id="98009-117">例如键盘、鼠标、游戏控制器、条形码读取器、LED 和字母数字显示。</span><span class="sxs-lookup"><span data-stu-id="98009-117">Examples are keyboard, mouse, game controller, barcode reader, LED, and alphanumeric display.</span></span> <span data-ttu-id="98009-118">Windows 10 IoT Core 设备可以通过蓝牙连接到 HID 设备。</span><span class="sxs-lookup"><span data-stu-id="98009-118">A Windows 10 IoT Core device can connect to an HID device over Bluetooth.</span></span> <span data-ttu-id="98009-119">请参阅 Windows 上下文： [Hid 概念简介](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts)中的有关 hid 的常规主题。</span><span class="sxs-lookup"><span data-stu-id="98009-119">See the general topic about HID in the Windows context: [Introduction to HID Concepts](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts).</span></span> 

2.  <span data-ttu-id="98009-120">**射频通信（RFCOMM）** RFCOMMM 是经典蓝牙的基础串行通信。</span><span class="sxs-lookup"><span data-stu-id="98009-120">**Radio Frequency Communication (RFCOMM)** RFCOMMM is the underlying serial communications for Classic Bluetooth.</span></span> <span data-ttu-id="98009-121">对于 UWP 应用，支持以下 RFCOMM 服务：</span><span class="sxs-lookup"><span data-stu-id="98009-121">With UWP apps, the following RFCOMM services are supported:</span></span>

* <span data-ttu-id="98009-122">serialPort</span><span class="sxs-lookup"><span data-stu-id="98009-122">serialPort</span></span>
* <span data-ttu-id="98009-123">obexObjectPush</span><span class="sxs-lookup"><span data-stu-id="98009-123">obexObjectPush</span></span>
* <span data-ttu-id="98009-124">obexFileTransfer</span><span class="sxs-lookup"><span data-stu-id="98009-124">obexFileTransfer</span></span>
* <span data-ttu-id="98009-125">phoneBookAccessPce</span><span class="sxs-lookup"><span data-stu-id="98009-125">phoneBookAccessPce</span></span>
* <span data-ttu-id="98009-126">phoneBookAccessPse</span><span class="sxs-lookup"><span data-stu-id="98009-126">phoneBookAccessPse</span></span>
* <span data-ttu-id="98009-127">genericFileTransfer</span><span class="sxs-lookup"><span data-stu-id="98009-127">genericFileTransfer</span></span>

3. <span data-ttu-id="98009-128">**泛型属性配置文件（GATT）** 请参阅[UWP-蓝牙低能耗](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview)主题。</span><span class="sxs-lookup"><span data-stu-id="98009-128">**Generic Attribute Profile (GATT)** See the [UWP-Bluetooth Low Energy](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview) topic.</span></span> 

> [!NOTE]
> <span data-ttu-id="98009-129">你将需要在 AppManifest 中手动指定 RFCOMM 服务。</span><span class="sxs-lookup"><span data-stu-id="98009-129">You will need to manually specify the RFCOMM services in the AppManifest.</span></span>  <span data-ttu-id="98009-130">请参阅[UWP-蓝牙 RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm)主题。</span><span class="sxs-lookup"><span data-stu-id="98009-130">See the [UWP-Bluetooth RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm) topic.</span></span> <span data-ttu-id="98009-131">另请参阅[UWP-蓝牙 Rfcomm Chat 示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat)主题。</span><span class="sxs-lookup"><span data-stu-id="98009-131">Also see the [UWP-Bluetooth Rfcomm Chat Sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) topic.</span></span>

## <a name="connecting-bluetooth-devices-using-the-device-portal"></a><span data-ttu-id="98009-132">使用设备门户连接蓝牙设备</span><span class="sxs-lookup"><span data-stu-id="98009-132">Connecting Bluetooth devices using the device portal</span></span>
<span data-ttu-id="98009-133">使用[windows 10 IoT Core 版本映像](https://developer.microsoft.com/en-us/windows/iot/downloads)时，可以使用设备门户将蓝牙设备与 Windows IoT core 设备配对。</span><span class="sxs-lookup"><span data-stu-id="98009-133">When using one of the [Windows 10 IoT Core Release Image](https://developer.microsoft.com/en-us/windows/iot/downloads) Bluetooth devices can be paired with the Windows IoT Core device using the device portal.</span></span> <span data-ttu-id="98009-134">导航到 "蓝牙" 选项卡时，设备将查找蓝牙设备，还会被其他蓝牙设备发现。</span><span class="sxs-lookup"><span data-stu-id="98009-134">When navigating to the Bluetooth tab the device will look for Bluetooth devices and will also be discoverable to other Bluetooth devices.</span></span> <span data-ttu-id="98009-135">下图显示了传入配对请求。</span><span class="sxs-lookup"><span data-stu-id="98009-135">The picture below shows an incoming pairing request.</span></span> 

![蓝牙传入配对](../media/Bluetooth/Portal_BT_2.png)

<span data-ttu-id="98009-137">成功配对设备后，它将在 "配对设备" 部分下列出</span><span class="sxs-lookup"><span data-stu-id="98009-137">After the device is successfully paired it will be listed under the paired device section</span></span> 

![蓝牙传入配对](../media/Bluetooth/Portal_BT_3.png)
