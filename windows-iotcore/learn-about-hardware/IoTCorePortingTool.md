---
title: Windows 10 IoT Core API 移植工具
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 Windows 10 IoT Core API 移植工具来估算迁移成本。
keywords: windows iot，API 移植工具，API 移植，二进制文件
ms.openlocfilehash: 5d7ffa00fb6ac9739b69227d5ed3248d7c466b7b
ms.sourcegitcommit: c57cebdf4d083079f41ec92ef65d897fd3c0faf8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/02/2020
ms.locfileid: "91655785"
---
# <a name="windows-10-iot-core-api-porting-tool"></a>Windows 10 IoT Core API 移植工具

Windows 10 IoT Core 仅支持 Windows 的各种早期版本中提供的 Win32 和 .NET API 外围应用的子集。 此工具将扫描您的二进制文件，并向您提供这些二进制文件使用的 Api 的报告，并提供可能的替换建议。 这既有助于估计到 IoT 核心的端口成本，也有助于你的工作方式。


## <a name="usage"></a>使用情况

Windows 10 IoT Core API 移植工具可在 " [ms-iot-实用程序](https://github.com/ms-iot/iot-utilities) " GitHub 存储库中找到。  下载 [存储库 zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) ，并将 IoTAPIPortingTool 文件夹复制到本地计算机。  在 Visual Studio 2017 中打开 **IoTAPIPortingTool** 并生成项目。  这将生成 `IotAPIPortingTool.exe`。

可以通过运行来使用该工具 `IoTAPIPortingTool.exe <Application path> [-os]` 。

*  `<Application path>` 用于迁移工具的应用程序的 exe

*  `-os` 如果你不打算使用 UWP，则应该指定。  默认情况下，该工具会针对 Windows UWP 平台验证你的二进制文件。

> [!NOTE]
> 必须从 Visual Studio 开发人员命令提示运行 IoTAPIPortingTool.exe。 需要导航到包含该 IotAPIPortingTool.exe 的文件夹。
```
        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os
```
## <a name="output"></a>输出

此工具将在包含的同一文件夹中 (csv) 文件生成逗号分隔值 `IotAPIPortingTool.exe` 。 该文件的名称为 `IoTAPIPortingTool.csv` (或者， `IoTAPIPortingToolOS.csv` 如果指定了-os) ，则在命令行上有一个摘要。 `.csv`在 Excel 中打开文件以分析完整的输出。
