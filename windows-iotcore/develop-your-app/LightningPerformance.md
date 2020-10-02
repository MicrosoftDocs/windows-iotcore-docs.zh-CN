---
title: 闪电性能测试
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解适用于不同平台和语言的 Windows IoT 闪电功能和切换频率。
keywords: windows iot，闪电性能，闪电功能，GPIO
ms.openlocfilehash: ee46734ce6eff327f9f0a428cb72cac9275e88dd
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91656283"
---
# <a name="windows-iot-lightning-performance-testing"></a>Windows IoT 闪电性能测试

> [!IMPORTANT]
> Windows 10 IoT 团队不再主动支持 Arduino。

使用简单的 GPIO 切换应用（ [此处提供](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite)了）对 Windows IoT 闪电功能测试了 GPIO 性能。 这些测试是通过在0和1之间切换，以最快的速度来执行的。 每个事例的切换频率均使用 Tektronix TPS 2024 Oscilloscope 进行度量。

以下结果是从分析获得的：

> | 已测试平台                     | 语言        | 频率     |
> | ----------------------------------- | --------------- | ------------- |
> | Arduino Uno                         | Arduino 草图  | 75.06 kHz     |
> | Windows 10 IoT 核心本机堆栈    | C#              | 239 KHz       |
> | Windows 10 IoT 核心本机堆栈    | C++/CX          | 278 kHz       |
> | Windows 10 IoT 核心本机堆栈    | WinJS           | 34 kHz        |
> | Windows 10 IoT Core Arduino 布线  | Arduino 布线  | **7.36 MHz**  |
> | Windows 10 IoT Core DMAP Stack      | C#              | **1.76 MHz**  |
> | Windows 10 IoT Core DMAP Stack      | C++/CX          | **3.78 MHz**  |
> | Windows 10 IoT Core DMAP Stack      | WinJS           | 42 kHz        |

在 Raspberry Pi 3 上运行 windows 10 IoT Core 测试，使用 Windows 10 IoT Core 有问必答 Preview Build 15026 (codename Redstone 2) 并使用 Microsoft IoT 闪电 SDK 1.1.0 构建。
