---
title: 闪电性能测试
author: msalehmsft
ms.author: msaleh
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解不同平台和语言的 Windows IoT 闪电功能和切换频率。
keywords: windows iot，闪电性能，闪电功能，GPIO
ms.openlocfilehash: e833b9614a648276067d55c61688f1c2d213810c
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229013"
---
# <a name="windows-iot-lightning-performance-testing"></a>WindowsIoT 闪电性能测试

> [!IMPORTANT]
> Windows 10 IoT 团队不再主动支持 Arduino。

使用简单的 gpio 切换应用（[可从此处获取](https://github.com/ms-iot/lightning/tree/develop/PerformanceTestSuite)）为 Windows IoT 闪电功能测试了 GPIO 性能。 这些测试是通过在0和1之间切换，以最快的速度来执行的。 每个事例的切换频率均使用 Tektronix TPS 2024 Oscilloscope 进行度量。

以下结果是从分析获得的：

> | 已测试平台                     | 语言        | 频率     |
> | ----------------------------------- | --------------- | ------------- |
> | Arduino Uno                         | Arduino 草图  | 75.06 kHz     |
> | Windows 10 IoT 核心版本机堆栈    | C#              | 239 KHz       |
> | Windows 10 IoT 核心版本机堆栈    | C++/CX          | 278 kHz       |
> | Windows 10 IoT 核心版本机堆栈    | WinJS           | 34 kHz        |
> | Windows 10 IoT 核心版Arduino 布线  | Arduino 布线  | **7.36 MHz**  |
> | Windows 10 IoT 核心版DMAP 堆栈      | C#              | **1.76 MHz**  |
> | Windows 10 IoT 核心版DMAP 堆栈      | C++/CX          | **3.78 MHz**  |
> | Windows 10 IoT 核心版DMAP 堆栈      | WinJS           | 42 kHz        |

使用 Windows 10 IoT 核心版有问必答 preview Build 15026 (codename Redstone 2) 并使用 Microsoft IoT 闪电 SDK 1.1.0 构建 Windows 10 IoT 核心版测试在 Raspberry Pi 3 上运行。
