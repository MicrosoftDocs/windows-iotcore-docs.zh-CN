---
title: Windows 10 IoT 核心版API 移植工具
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 Windows 10 IoT 核心版 API 移植工具估算移植成本。
keywords: windows iot， API 移植工具， API 移植， 二进制文件
ms.openlocfilehash: 0b6631c3ee0afe5c60a972bcf69999e39f0d60dc
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229634"
---
# <a name="windows-10-iot-core-api-porting-tool"></a>Windows 10 IoT 核心版API 移植工具

Windows 10 IoT 核心版仅支持各种早期版本的 Windows 上提供的 Win32 和 .NET API 图面Windows。 此工具将扫描二进制文件，并报告这些二进制文件使用的不可用 API，并针对可能的替换提供建议。 这两种方法都有助于估算 IoT 核心的端口成本，还有助于你完成这一步。


## <a name="usage"></a>使用情况

可以在Windows 10 IoT 核心版的[ms-iot/iot-utilities](https://github.com/ms-iot/iot-utilities) GitHub工具。  下载 [存储库 zip，](https://github.com/ms-iot/iot-utilities/archive/master.zip) 将 IoTAPIPortingTool 文件夹复制到本地计算机。  在 2017 Visual Studio打开 **IoTAPIPortingTool.sln** 并生成项目。  这将生成 `IotAPIPortingTool.exe`。

可以通过运行 来使用该工具 `IoTAPIPortingTool.exe <Application path> [-os]` 。

*  `<Application path>` 用于移植工具的应用程序的 exe

*  `-os` 如果打算使用 UWP，应指定 。  默认情况下，该工具根据 UWP 平台Windows二进制文件。

> [!NOTE]
> IoTAPIPortingTool.exe必须运行自 Visual Studio 开发人员命令提示。 需要导航到包含该文件夹IotAPIPortingTool.exe。
```
        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os
```
## <a name="output"></a>输出

该工具将在包含 的同 (csv) 文件中生成逗号分隔值 `IotAPIPortingTool.exe` 。 该文件名为 (，或者，如果 `IoTAPIPortingTool.csv` 指定了 `IoTAPIPortingToolOS.csv` -os) 则摘要将位于命令行上。 打开 `.csv` 文件Excel以分析完整输出。
