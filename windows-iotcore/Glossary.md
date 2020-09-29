---
title: Windows IoT 术语表
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: IoT
description: 通过文档了解与 Windows IoT 核心版相关的各种术语。
keywords: windows iot, 术语表, 术语, 定义
ms.openlocfilehash: 199bb379c806652758c93c4dcefdf4424a2e26bd
ms.sourcegitcommit: 2d04dae9cb26f9aa6e1da2056be5d04dcfab317d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2020
ms.locfileid: "90782729"
---
# <a name="glossary-for-windows-iot"></a>Windows IoT 术语表

**高级配置和电源接口 (ACPI)** ACPI（高级配置和电源接口）是由 Hewlett-Packard、Intel、Microsoft、Phoenix 和 Toshiba 联合开发的开放行业规范。  ACPI 所建立的行业标准接口支持操作系统定向配置、电源管理以及移动、桌面和服务器平台的热管理。

**基本输入/输出系统 (BIOS)** 基本软件例程集，用于在启动时测试硬件、启动操作系统并支持在硬件设备之间传输数据。

**商业化** 开发和制造设备的目的是以商业方式将其推向公众。

**通用输入/输出 (GPIO)** GPIO 是集成电路上的通用引脚，用户可在运行时控制其行为（包括它是输入引脚还是输出引脚）。  可以在应用中使用 Windows.Devices.Gpio 命名空间，以便在开发板上操作 GPIO 引脚。

**有外设** Windows IoT 核心版可处于有外设模式下，也可处于无外设模式下。 这两种模式之间的区别在于是否存在任何形式的 UI。 默认情况下，Windows 10 IoT 核心版处于有外设模式下，并显示计算机名称和 IP 地址等系统信息。

**无外设** 在无外设模式下，不存在可用的 UI 堆栈并且应用不可交互。 可将无外设模式应用视为服务。

**内部集成电路 (I2C)** 内部集成电路控制的简单的双向两线式串行数据 (SDA) 和串行时钟 (SCL) 总线。  可以在应用中使用 Windows.Devices.I2c 命名空间，以便通过 I2C 与设备进行通信。

**发光二极管 (LED)** LED 是双引线半导体光源。 它是 PN 结二极管，可在激活时发光。

**Microsoft Windows 内核模式驱动程序框架 (KMDF)** Microsoft 开发框架，允许驱动程序开发人员在内核模式下公开驱动程序功能，从而使驱动程序可以访问系统内存和硬件。

**原型制作** 开发一个比你希望创建的最终设备版本更原始的版本。 强烈建议进行原型制作，即使这在制造过程中不是一项必要的步骤。 应该将此阶段用于测试你希望用于设备最终版本的任何以及所有功能。

**串行外设接口总线 (SPI)** SPI 总线是用于近距离通信的同步串行通信接口规范，主要用于嵌入系统。  可以在应用中使用 Windows.Devices.Spi 命名空间，以便通过 SPI 与设备进行通信。

**通用异步收发器 (UART)** UART 是计算机硬件的一部分，用于接收字节数据，然后以串行方式传输各个位。

**通用 Windows 平台 (UWP)** 通用 Windows 平台提供跨设备且有保证的核心 API 层。  你可以创建可安装在各种设备上的单个应用包。

**虚拟机 (VM)**<br/>
充当编译器二进制代码与实际执行程序指令的微处理器之间的接口的软件。  在 Windows 中，可以使用 Hyper-V 管理器来管理虚拟机。

**Windows 设备控制台 (Devcon.exe)** DevCon (Devcon.exe)（即设备控制台）是一个命令行工具，用于显示有关运行 Windows 的计算机上设备的详细信息。 可以使用 DevCon 启用、禁用、安装、配置以及删除设备。  此工具主要用于手动安装和删除驱动程序。
