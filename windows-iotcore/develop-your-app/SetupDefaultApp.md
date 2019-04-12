---
title: 安装默认应用程序
author: bfjelds
ms.author: bfjelds
ms.date: 09/05/17
ms.topic: article
description: 了解如何设置使用 Windows Device Portal 或命令行程序的默认应用程序。
keywords: windows iot，默认应用程序中，PowerShell iot
ms.openlocfilehash: f3f7a5194491250a8a0b49e81e073282c8f5660b
ms.sourcegitcommit: ef85ccba54b1118d49554e88768240020ff514b0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/11/2019
ms.locfileid: "59510874"
---
# <a name="setup-a-default-app"></a>安装默认应用程序
此处，您将学习如何将你的应用程序设置为默认应用程序。 默认应用程序是在系统启动时启动的。  

> [!NOTE]
> 部署到 RS5 时，visual Studio 将生成一个含义模糊的错误 （或使用 OpenSSH RS4 启用） IoT 图像，除非已从 RS4 或更高版本的 SDK 安装 Visual Studio 可以访问。

## <a name="runtime-options"></a>运行时选项

在开发期间 / 实验阶段，您可以通过以下方式更改默认的应用。

### <a name="using-windows-device-portal"></a>使用 Windows Device Portal

你可以单击**启动**列对应于应用程序。
![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)

### <a name="using-the-shell"></a>使用命令行程序

使用命令行程序将默认应用程序设置的步骤 

1. 连接到通过设备[Powershell](../connect-your-device/PowerShell.md)

2. 列出使用安装的应用程序 `iotstartup list`

3. 请注意你想要使为默认值并将其使用设置的应用程序的 appid `iotstartup add headed <appid>`。 对于无外设的应用程序，应使用`iotstartup add headless <appid>`。


## <a name="build-time-option"></a>生成时间选项

对于大型部署，您可以实现此目的使用预配包

预配包创建期间，可以指定在 WCD StartupApp/默认设置。
![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)

请参阅[Appx.IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml)作为示例。 可以获取应用程序用户模型 ID (AUMID) 使用 appx [GetAppxInfo 工具](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe)。

## <a name="how-to-configure-home-key"></a>如何配置"Home"键

Windows 10 IoT 周年更新 (1607) 对于将默认应用程序窗口带到前台，另一个应用程序当前正在运行时提供命令行程序支持。

若要查看如何启用"Home"键，请访问我们[IoT Shell 页](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)
