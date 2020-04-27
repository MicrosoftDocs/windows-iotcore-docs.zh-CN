---
title: Windows IoT 术语表
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 通过文档了解与 Windows IoT 核心版相关的各种术语。
keywords: windows iot, 术语表, 术语, 定义
ms.openlocfilehash: 109ddbb9e9c6c163fdc5a8d0219b89dde3a2bbf2
ms.sourcegitcommit: 9fb86fb605d6a8feb5c226a391045b908117a90a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2020
ms.locfileid: "72918423"
---
# <a name="glossary-for-windows-iot"></a><span data-ttu-id="732e9-104">Windows IoT 术语表</span><span class="sxs-lookup"><span data-stu-id="732e9-104">Glossary for Windows IoT</span></span>

<span data-ttu-id="732e9-105">**高级配置和电源接口 (ACPI)** ACPI（高级配置和电源接口）是由 Hewlett-Packard、Intel、Microsoft、Phoenix 和 Toshiba 联合开发的开放行业规范。</span><span class="sxs-lookup"><span data-stu-id="732e9-105">**Advanced Configuration & Power Interface (ACPI)** ACPI (Advanced Configuration and Power Interface) is an open industry specification co-developed by Hewlett-Packard, Intel, Microsoft, Phoenix, and Toshiba.</span></span>  <span data-ttu-id="732e9-106">ACPI 所建立的行业标准接口支持操作系统定向配置、电源管理以及移动、桌面和服务器平台的热管理。</span><span class="sxs-lookup"><span data-stu-id="732e9-106">ACPI establishes industry-standard interfaces enabling OS-directed configuration, power management, and thermal management of mobile, desktop, and server platforms.</span></span>

<span data-ttu-id="732e9-107">**基本输入/输出系统 (BIOS)** 基本软件例程集，用于在启动时测试硬件、启动操作系统并支持在硬件设备之间传输数据。</span><span class="sxs-lookup"><span data-stu-id="732e9-107">**Basic Input/Output System (BIOS)** The set of essential software routines that test hardware at startup, start the operating system, and support the transfer of data among hardware devices.</span></span>

<span data-ttu-id="732e9-108">**商业化** 开发和制造设备的目的是以商业方式将其推向公众。</span><span class="sxs-lookup"><span data-stu-id="732e9-108">**Commercialize** Developing and manufacturing a device with the intention of putting it out to the public commercially.</span></span>

<span data-ttu-id="732e9-109">**通用输入/输出 (GPIO)** GPIO 是集成电路上的通用引脚，用户可在运行时控制其行为（包括它是输入引脚还是输出引脚）。</span><span class="sxs-lookup"><span data-stu-id="732e9-109">**General-Purpose Input/Output (GPIO)** GPIO is a generic pin on an integrated circuit whose behavior, including whether it is an input or output pin, can be controlled by the user at run time.</span></span>  <span data-ttu-id="732e9-110">可以在应用中使用 Windows.Devices.Gpio 命名空间，以便在开发板上操作 GPIO 引脚。</span><span class="sxs-lookup"><span data-stu-id="732e9-110">You can use the Windows.Devices.Gpio namespace in your app to manipulate the GPIO pins on your board.</span></span>

<span data-ttu-id="732e9-111">**有外设** Windows IoT 核心版可处于有外设模式下，也可处于无外设模式下。</span><span class="sxs-lookup"><span data-stu-id="732e9-111">**Headed** Windows IoT Core can either be in headed or headless mode.</span></span> <span data-ttu-id="732e9-112">这两种模式之间的区别在于是否存在任何形式的 UI。</span><span class="sxs-lookup"><span data-stu-id="732e9-112">The difference between these two modes is the presence or absence of any form of UI.</span></span> <span data-ttu-id="732e9-113">默认情况下，Windows 10 IoT 核心版处于有外设模式下，并显示计算机名称和 IP 地址等系统信息。</span><span class="sxs-lookup"><span data-stu-id="732e9-113">By default, Windows 10 IoT Core is in headed mode and displays system information like the computer name and IP address.</span></span>

<span data-ttu-id="732e9-114">**无外设** 在无外设模式下，不存在可用的 UI 堆栈并且应用不可交互。</span><span class="sxs-lookup"><span data-stu-id="732e9-114">**Headless** In headless mode, there is no UI stack available and apps are not interactive.</span></span> <span data-ttu-id="732e9-115">可将无外设模式应用视为服务。</span><span class="sxs-lookup"><span data-stu-id="732e9-115">Headless mode apps can be thought of as services.</span></span>

<span data-ttu-id="732e9-116">**内部集成电路 (I2C)** 内部集成电路控制的简单的双向两线式串行数据 (SDA) 和串行时钟 (SCL) 总线。</span><span class="sxs-lookup"><span data-stu-id="732e9-116">**Inter-Integrated Circuits (I2C)** Simple bidirectional two-wire serial data (SDA) and serial clock (SCL) buses for inter-integrated circuit control.</span></span>  <span data-ttu-id="732e9-117">可以在应用中使用 Windows.Devices.I2c 命名空间，以便通过 I2C 与设备进行通信。</span><span class="sxs-lookup"><span data-stu-id="732e9-117">You can use the Windows.Devices.I2c namespace in your app to communicate with a device over I2C.</span></span>

<span data-ttu-id="732e9-118">**发光二极管 (LED)** LED 是双引线半导体光源。</span><span class="sxs-lookup"><span data-stu-id="732e9-118">**Light-Emitting Diode (LED)** A LED is a two-lead semiconductor light source.</span></span> <span data-ttu-id="732e9-119">它是 PN 结二极管，可在激活时发光。</span><span class="sxs-lookup"><span data-stu-id="732e9-119">It is a pn-junction diode, which emits light when activated.</span></span>

<span data-ttu-id="732e9-120">**Microsoft Windows 内核模式驱动程序框架 (KMDF)** Microsoft 开发框架，允许驱动程序开发人员在内核模式下公开驱动程序功能，从而使驱动程序可以访问系统内存和硬件。</span><span class="sxs-lookup"><span data-stu-id="732e9-120">**Microsoft Windows Kernel Mode Driver Framework (KMDF)** Microsoft development framework which allows driver developers to expose driver functionality in kernel mode, giving the driver access to system memory and hardware.</span></span>

<span data-ttu-id="732e9-121">**原型制作** 开发一个比你希望创建的最终设备版本更原始的版本。</span><span class="sxs-lookup"><span data-stu-id="732e9-121">**Prototype** Developing a more raw version of a final version of a device that you're hoping to create.</span></span> <span data-ttu-id="732e9-122">强烈建议进行原型制作，即使这在制造过程中不是一项必要的步骤。</span><span class="sxs-lookup"><span data-stu-id="732e9-122">Prototyping is highly recommended, if not an obligatory step in the manufacturing process.</span></span> <span data-ttu-id="732e9-123">应该将此阶段用于测试你希望用于设备最终版本的任何以及所有功能。</span><span class="sxs-lookup"><span data-stu-id="732e9-123">This stage should be used for testing any and all features you're hoping to use for the final version of your device.</span></span>

<span data-ttu-id="732e9-124">**串行外设接口总线 (SPI)** SPI 总线是用于近距离通信的同步串行通信接口规范，主要用于嵌入系统。</span><span class="sxs-lookup"><span data-stu-id="732e9-124">**Serial Peripheral Interface Bus (SPI)** The SPI bus is a synchronous serial communication interface specification used for short distance communication, primarily in embedded systems.</span></span>  <span data-ttu-id="732e9-125">可以在应用中使用 Windows.Devices.Spi 命名空间，以便通过 SPI 与设备进行通信。</span><span class="sxs-lookup"><span data-stu-id="732e9-125">You can use the Windows.Devices.Spi namespace in your app to communicate with a device over SPI.</span></span>

<span data-ttu-id="732e9-126">**通用异步收发器 (UART)** UART 是计算机硬件的一部分，用于接收字节数据，然后以串行方式传输各个位。</span><span class="sxs-lookup"><span data-stu-id="732e9-126">**Universal Asynchronous Receiver/Transmitter (UART)** UART is a piece of computer hardware that takes bytes of data and transmits the individual bits serially.</span></span>

<span data-ttu-id="732e9-127">**通用 Windows 平台 (UWP)** 通用 Windows 平台提供跨设备且有保证的核心 API 层。</span><span class="sxs-lookup"><span data-stu-id="732e9-127">**Universal Windows Platform (UWP)** The Universal Windows Platform provides a guaranteed core API layer across devices.</span></span>  <span data-ttu-id="732e9-128">你可以创建可安装在各种设备上的单个应用包。</span><span class="sxs-lookup"><span data-stu-id="732e9-128">You can create a single app package that can be installed onto a wide range of devices.</span></span>

<span data-ttu-id="732e9-129">**虚拟机 (VM)**</span><span class="sxs-lookup"><span data-stu-id="732e9-129">**Virtual Machine (VM)**</span></span><br/>
<span data-ttu-id="732e9-130">充当编译器二进制代码与实际执行程序指令的微处理器之间的接口的软件。</span><span class="sxs-lookup"><span data-stu-id="732e9-130">Software that acts as an interface between compiler binary code and the microprocessor that actually performs the program's instructions.</span></span>  <span data-ttu-id="732e9-131">在 Windows 中，可以使用 Hyper-V 管理器来管理虚拟机。</span><span class="sxs-lookup"><span data-stu-id="732e9-131">In Windows, you can use Hyper-V Manager to manage virtual machines.</span></span>

<span data-ttu-id="732e9-132">**Windows 设备控制台 (Devcon.exe)** DevCon (Devcon.exe)（即设备控制台）是一个命令行工具，用于显示有关运行 Windows 的计算机上设备的详细信息。</span><span class="sxs-lookup"><span data-stu-id="732e9-132">**Windows Device Console (Devcon.exe)** DevCon (Devcon.exe), the Device Console, is a command-line tool that displays detailed information about devices on computers running Windows.</span></span> <span data-ttu-id="732e9-133">可以使用 DevCon 启用、禁用、安装、配置以及删除设备。</span><span class="sxs-lookup"><span data-stu-id="732e9-133">You can use DevCon to enable, disable, install, configure, and remove devices.</span></span>  <span data-ttu-id="732e9-134">此工具主要用于手动安装和删除驱动程序。</span><span class="sxs-lookup"><span data-stu-id="732e9-134">This tool is mostly used for manually installing and removing drivers.</span></span>
