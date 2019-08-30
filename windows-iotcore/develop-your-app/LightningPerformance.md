---
title: 闪电性能测试
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
description: 了解适用于不同平台和语言的 Windows IoT 闪电功能和切换频率。
keywords: windows iot, 闪电性能, 闪电功能, GPIO
ms.openlocfilehash: e7d57f72f6db85fbb8e453943c87e8ee31ef8a40
ms.sourcegitcommit: cbea9d713986fbe8b85e1bba1561a000188bd91c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64744778"
---
# <a name="windows-iot-lightning-performance-testing"></a>Windows IoT Lightning 性能测试

> [!IMPORTANT]
> Windows 10 IoT 团队不再主动支持 Arduino。

使用简单的 GPIO 切换应用 ([此处提供](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite)了) 对 Windows IoT 闪电功能测试了 GPIO 性能。 通过以尽可能快的速度切换 0 和 1 之间的 GPIO 5 来执行测试。 每个事例的切换频率均使用 Tektronix TPS 2024 Oscilloscope 进行度量。

通过分析得出以下结果：

> | 测试平台                     | 语言        | 频率     |
> | ----------------------------------- | --------------- | ------------- |
> | Arduino Uno                         | Arduino 草图  | 75.06 kHz     |
> | Windows 10 IoT 核心本机堆栈    | C#              | 239 KHz       |
> | Windows 10 IoT 核心本机堆栈    | C++/CX          | 278 kHz       |
> | Windows 10 IoT 核心本机堆栈    | WinJS           | 34 kHz        |
> | Windows 10 IoT Core Arduino 布线  | Arduino 接线  | **7.36 MHz**  |
> | Windows 10 IoT Core DMAP Stack      | C#              | **1.76 MHz**  |
> | Windows 10 IoT Core DMAP Stack      | C++/CX          | **3.78 MHz**  |
> | Windows 10 IoT Core DMAP Stack      | WinJS           | 42 kHz        |

Windows 10 IoT 核心测试使用 Windows 10 IoT Core 有问必答 Preview Build 15026 (codename Redstone 2) 在 Raspberry Pi 3 上运行, 并使用 Microsoft IoT 闪电 SDK 1.1.0 构建。
