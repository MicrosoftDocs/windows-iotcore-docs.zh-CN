---
title: 快如闪电性能测试
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 了解如何针对不同平台和语言的 Windows IoT 闪电般的功能和切换频率。
keywords: windows iot、 闪电般的性能、 快如闪电的功能，GPIO
ms.openlocfilehash: 65f6732dd945b199902bb7eb4a9e0cc41aac2131
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510940"
---
# <a name="windows-iot-lightning-performance-testing"></a>Windows IoT Lightning 性能测试

GPIO 性能进行了测试使用一个简单的 GPIO 切换应用程序，Windows IoT 闪电功能[可从以下站点](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite)。 通过以尽可能快的速度切换 0 和 1 之间的 GPIO 5 来执行测试。 每个用例的切换频率已使用 Tektronix TP 2024 Oscilloscope 测量。

通过分析得出以下结果：

> | 测试平台                     | 语言        | 频率     |
> | ----------------------------------- | --------------- | ------------- |
> | Arduino Uno                         | Arduino 草图  | 75.06 kHz     |
> | Windows 10 IoT 核心版本机堆栈    | C#              | 239 KHz       |
> | Windows 10 IoT 核心版本机堆栈    | C++/CX          | 278 kHz       |
> | Windows 10 IoT 核心版本机堆栈    | WinJS           | 34 kHz        |
> | Windows 10 IoT 核心版 Arduino 布线  | Arduino 接线  | **7.36 MHz**  |
> | Windows 10 IoT 核心版 DMAP 堆栈      | C#              | **1.76 MHz**  |
> | Windows 10 IoT 核心版 DMAP 堆栈      | C++/CX          | **3.78 MHz**  |
> | Windows 10 IoT 核心版 DMAP 堆栈      | WinJS           | 42 kHz        |

Windows 10 IoT 核心版测试已在使用 Windows 10 IoT Core Insider Preview 构建 15026 (codename Redstone 2) Raspberry Pi 3 上运行，并使用 Microsoft IoT 闪电 SDK 1.1.0 生成。
