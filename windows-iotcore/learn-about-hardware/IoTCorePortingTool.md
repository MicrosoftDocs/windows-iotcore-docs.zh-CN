---
title: Windows 10 IoT Core API 移植工具
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Windows 10 IoT Core API 移植工具来估算迁移成本。
keywords: windows iot, API 移植工具, API 移植, 二进制文件
ms.openlocfilehash: 56ca0d57752f000bf9e908fd32f514c3ae3264e5
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "60169625"
---
# <a name="windows-10-iot-core-api-porting-tool"></a>Windows 10 IoT Core API 移植工具

Windows 10 IoT Core 仅支持 Windows 的各种早期版本中提供的 Win32 和 .Net API 外围应用的子集。 此工具将扫描您的二进制文件, 并向您提供这些二进制文件使用的 Api 的报告, 并提供可能的替换建议。 这既有助于估计到 IoT 核心的端口成本, 也有助于你的工作方式。


## <a name="usage"></a>用法

Windows 10 IoT 核心版 API 移植工具可在 [ms-iot/iot-utilities](https://github.com/ms-iot/iot-utilities) github 存储库中找到。  下载[存储库 zip](https://github.com/ms-iot/iot-utilities/archive/master.zip) , 并将 IoTAPIPortingTool 文件夹复制到本地计算机。  在 Visual Studio 2017 中打开**IoTAPIPortingTool**并生成项目。  这将生成 `IotAPIPortingTool.exe`。

可通过运行 `IoTAPIPortingTool.exe <Application path> [-os]` 使用该工具。

*  `<Application path>`用于迁移工具的应用程序的 exe

*  如果你不计划使用 UWP，应指定 `-os`。  默认情况下，该工具针对 WindowsUWP 平台验证你的二进制文件。

> [!NOTE] 
> 必须从 Visual Studio 开发人员命令提示中运行 IoTAPIPortingTool。 需要导航到包含 IotAPIPortingTool 的文件夹。 

        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os 

## <a name="output"></a>Output

此工具将在包含的`IotAPIPortingTool.exe`同一文件夹中生成一个逗号分隔值 (csv) 文件。 该文件的名称`IoTAPIPortingTool.csv`为 (或者`IoTAPIPortingToolOS.csv` , 如果指定了-os), 并在命令行上有一个摘要。 在 Excel 中打开 `.csv` 文件来分析完整输出。
