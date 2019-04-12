---
title: 蓝牙支持
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何利用运行 Windows 10 IoT 核心版的设备的蓝牙。
keywords: windows iot、 蓝牙、 蓝牙的支持、 设备、 设备门户
ms.openlocfilehash: f24b50b65b192ed6bd9309eeda30dbadfedf5bc2
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510858"
---
# <a name="bluetooth-support"></a><span data-ttu-id="c234f-104">蓝牙支持</span><span class="sxs-lookup"><span data-stu-id="c234f-104">Bluetooth Support</span></span>
<span data-ttu-id="c234f-105">Windows 10 IoT Core 支持蓝牙 4.0。</span><span class="sxs-lookup"><span data-stu-id="c234f-105">Windows 10 IoT Core supports Bluetooth 4.0.</span></span> <span data-ttu-id="c234f-106">可以在找到的受支持蓝牙连接器列表[硬件兼容性列表](../learn-about-hardware/HardwareCompatList.md)。</span><span class="sxs-lookup"><span data-stu-id="c234f-106">A list of supported Bluetooth dongles can be found in the [Hardware Compatibility List](../learn-about-hardware/HardwareCompatList.md).</span></span>

## <a name="about-bluetooth"></a><span data-ttu-id="c234f-107">有关 Bluetooth</span><span class="sxs-lookup"><span data-stu-id="c234f-107">About Bluetooth</span></span>
<span data-ttu-id="c234f-108">有两个不同的蓝牙技术，您可以选择在应用中实现：</span><span class="sxs-lookup"><span data-stu-id="c234f-108">There are two different bluetooth technologies that you can choose to implement in your app:</span></span>

* <span data-ttu-id="c234f-109">经典蓝牙 (RFCOMM) 之前蓝牙 LE、 设备通常用于此协议使用蓝牙进行通信。</span><span class="sxs-lookup"><span data-stu-id="c234f-109">Classic Bluetooth (RFCOMM) Before Bluetooth LE, devices commonly used this protocol to communicate using Bluetooth.</span></span> <span data-ttu-id="c234f-110">此协议十分简单，可用于设备到设备的通信而无需节能。</span><span class="sxs-lookup"><span data-stu-id="c234f-110">This protocol is simple and useful for device-to-device communication without the need of energy savings.</span></span> <span data-ttu-id="c234f-111">连接需要配对。</span><span class="sxs-lookup"><span data-stu-id="c234f-111">Connectivity requires pairing.</span></span>

* <span data-ttu-id="c234f-112">低耗电 Bluetooth (BLE/LE) 蓝牙低能耗 (LE) 是一种规范，用于定义用于发现和具有有效的能源使用情况要求的设备之间的通信协议。</span><span class="sxs-lookup"><span data-stu-id="c234f-112">Bluetooth Low-Energy (BLE/LE) Bluetooth Low Energy (LE) is a specification that defines protocols for discovery and communication between devices that have an efficient energy usage requirement.</span></span> <span data-ttu-id="c234f-113">有关详细信息包括根据最新生成的代码示例，可以连接到 BLE 设备而无需配对设备。</span><span class="sxs-lookup"><span data-stu-id="c234f-113">For more information including code samples, As per recent builds, a device can connect to a BLE device without pairing.</span></span>

## <a name="supported-bluetooth-profiles"></a><span data-ttu-id="c234f-114">受支持的蓝牙配置文件</span><span class="sxs-lookup"><span data-stu-id="c234f-114">Supported Bluetooth Profiles</span></span>
<span data-ttu-id="c234f-115">Windows 10 IoT Core 支持以下蓝牙配置文件：</span><span class="sxs-lookup"><span data-stu-id="c234f-115">Windows 10 IoT Core supports the following Bluetooth profiles:</span></span>

1.  <span data-ttu-id="c234f-116">**人体学接口设备配置文件的概念 (HID)** HID 设备将用户输入，并提供人工 consumpation 的输出。</span><span class="sxs-lookup"><span data-stu-id="c234f-116">**Human Interface Device Profiles Concepts (HID)** An HID device takes input from a human and presents output for human consumpation.</span></span> <span data-ttu-id="c234f-117">示例包括键盘、 鼠标、 游戏控制器、 条形码读取器、 LED 和字母数字显示。</span><span class="sxs-lookup"><span data-stu-id="c234f-117">Examples are keyboard, mouse, game controller, barcode reader, LED, and alphanumeric display.</span></span> <span data-ttu-id="c234f-118">Windows 10 IoT Core 设备可以连接到 HID 设备通过蓝牙。</span><span class="sxs-lookup"><span data-stu-id="c234f-118">A Windows 10 IoT Core device can connect to an HID device over Bluetooth.</span></span> <span data-ttu-id="c234f-119">请参阅有关 HID Windows 上下文中的常规主题：[HID 概念简介](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts)。</span><span class="sxs-lookup"><span data-stu-id="c234f-119">See the general topic about HID in the Windows context: [Introduction to HID Concepts](https://docs.microsoft.com/windows-hardware/drivers/hid/introduction-to-hid-concepts).</span></span> 

2.  <span data-ttu-id="c234f-120">**射频通信 (RFCOMM)** RFCOMMM 是经典蓝牙的基础串行通信。</span><span class="sxs-lookup"><span data-stu-id="c234f-120">**Radio Frequency Communication (RFCOMM)** RFCOMMM is the underlying serial communications for Classic Bluetooth.</span></span> <span data-ttu-id="c234f-121">与 UWP 应用，支持以下 RFCOMM 服务：</span><span class="sxs-lookup"><span data-stu-id="c234f-121">With UWP apps, the following RFCOMM services are supported:</span></span>

* <span data-ttu-id="c234f-122">serialPort</span><span class="sxs-lookup"><span data-stu-id="c234f-122">serialPort</span></span>
* <span data-ttu-id="c234f-123">obexObjectPush</span><span class="sxs-lookup"><span data-stu-id="c234f-123">obexObjectPush</span></span>
* <span data-ttu-id="c234f-124">obexFileTransfer</span><span class="sxs-lookup"><span data-stu-id="c234f-124">obexFileTransfer</span></span>
* <span data-ttu-id="c234f-125">phoneBookAccessPce</span><span class="sxs-lookup"><span data-stu-id="c234f-125">phoneBookAccessPce</span></span>
* <span data-ttu-id="c234f-126">phoneBookAccessPse</span><span class="sxs-lookup"><span data-stu-id="c234f-126">phoneBookAccessPse</span></span>
* <span data-ttu-id="c234f-127">genericFileTransfer</span><span class="sxs-lookup"><span data-stu-id="c234f-127">genericFileTransfer</span></span>

3. <span data-ttu-id="c234f-128">**泛型属性配置文件 (GATT)** 请参阅[UWP 蓝牙低能耗](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview)主题。</span><span class="sxs-lookup"><span data-stu-id="c234f-128">**Generic Attribute Profile (GATT)** See the [UWP-Bluetooth Low Energy](https://docs.microsoft.com/windows/uwp/devices-sensors/bluetooth-low-energy-overview) topic.</span></span> 

> [!NOTE]
> <span data-ttu-id="c234f-129">你将需要手动指定 AppManifest 中 RFCOMM 服务。</span><span class="sxs-lookup"><span data-stu-id="c234f-129">You will need to manually specify the RFCOMM services in the AppManifest.</span></span>  <span data-ttu-id="c234f-130">请参阅[UWP 蓝牙 RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm)主题。</span><span class="sxs-lookup"><span data-stu-id="c234f-130">See the [UWP-Bluetooth RFCOMM](https://docs.microsoft.com/windows/uwp/devices-sensors/send-or-receive-files-with-rfcomm) topic.</span></span> <span data-ttu-id="c234f-131">另请参阅[UWP 蓝牙 Rfcomm 聊天示例](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat)主题。</span><span class="sxs-lookup"><span data-stu-id="c234f-131">Also see the [UWP-Bluetooth Rfcomm Chat Sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/BluetoothRfcommChat) topic.</span></span>

## <a name="connecting-bluetooth-devices-using-the-device-portal"></a><span data-ttu-id="c234f-132">将蓝牙设备使用设备门户连接</span><span class="sxs-lookup"><span data-stu-id="c234f-132">Connecting Bluetooth devices using the device portal</span></span>
<span data-ttu-id="c234f-133">使用之一时[Windows 10 IoT Core 版本映像](https://developer.microsoft.com/en-us/windows/iot/downloads)可以与使用设备门户的 Windows IoT Core 设备配对的蓝牙设备。</span><span class="sxs-lookup"><span data-stu-id="c234f-133">When using one of the [Windows 10 IoT Core Release Image](https://developer.microsoft.com/en-us/windows/iot/downloads) Bluetooth devices can be paired with the Windows IoT Core device using the device portal.</span></span> <span data-ttu-id="c234f-134">导航到蓝牙选项卡时设备将寻找 Bluetooth 的设备，并还将对其他蓝牙设备发现。</span><span class="sxs-lookup"><span data-stu-id="c234f-134">When navigating to the Bluetooth tab the device will look for Bluetooth devices and will also be discoverable to other Bluetooth devices.</span></span> <span data-ttu-id="c234f-135">下图显示了配对的传入请求。</span><span class="sxs-lookup"><span data-stu-id="c234f-135">The picture below shows an incoming pairing request.</span></span> 

![配对的蓝牙传入](../media/Bluetooth/Portal_BT_2.png)

<span data-ttu-id="c234f-137">成功配对设备后它将列在配对的设备部分下</span><span class="sxs-lookup"><span data-stu-id="c234f-137">After the device is successfully paired it will be listed under the paired device section</span></span> 

![配对的蓝牙传入](../media/Bluetooth/Portal_BT_3.png)
