---
title: Windows 10 IoT Core API 移植工具
author: saraclay
ms.author: saclayt
ms.date: 08/28/2017
ms.topic: article
description: 了解如何使用 Windows 10 IoT Core API 移植工具来估计迁移成本。
keywords: windows iot，API 移植工具、 API 移植、 二进制文件
ms.openlocfilehash: 56ca0d57752f000bf9e908fd32f514c3ae3264e5
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510795"
---
# <a name="windows-10-iot-core-api-porting-tool"></a>Windows 10 IoT Core API 移植工具

Windows 10 IoT 核心版仅支持在各种以前版本的 Windows 上的 Win32 和.Net API 表面区域的子集。 此工具将扫描您的二进制文件，并为您提供的 Api 使用这些二进制文件不可用，并且提供有关可能的替换建议的报告。 这将同时帮助估算成本 IoT 核心版的端口，以及帮助你在此过程。


## <a name="usage"></a>用法

Windows 10 IoT 核心版 API 移植工具可在 [ms-iot/iot-utilities](https://github.com/ms-iot/iot-utilities) github 存储库中找到。  下载[存储库 zip](https://github.com/ms-iot/iot-utilities/archive/master.zip)将 IoTAPIPortingTool 文件夹复制到本地计算机。  打开**IoTAPIPortingTool.sln**在 Visual Studio 2017 并生成项目。  这将生成 `IotAPIPortingTool.exe`。

可通过运行 `IoTAPIPortingTool.exe <Application path> [-os]` 使用该工具。

*  `<Application path>` 迁移工具用于应用程序的 exe

*  `-os` 应指定是否您不打算使用 UWP。  默认情况下，该工具针对 WindowsUWP 平台验证你的二进制文件。

> [!NOTE] 
> 必须从 Visual Studio 开发人员命令提示运行 IoTAPIPortingTool.exe。 您需要导航到包含 IotAPIPortingTool.exe 的文件夹。 

        Sample command: C:\IoTAPIPortingTool\bin\Debug>IoTAPIPortingTool.exe C:\Sample\Sample.exe -os 

## <a name="output"></a>输出

此工具将在包含的相同文件夹中生成逗号分隔的值 (csv) 文件`IotAPIPortingTool.exe`。 将该文件命名`IoTAPIPortingTool.csv`(或者，`IoTAPIPortingToolOS.csv`如果指定-os) 和摘要将在命令行上。 在 Excel 中打开 `.csv` 文件来分析完整输出。
