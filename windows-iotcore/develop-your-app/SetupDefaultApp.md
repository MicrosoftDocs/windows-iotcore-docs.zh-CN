---
title: 设置默认应用程序
author: bfjelds
ms.author: bfjelds
ms.date: 09/05/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何使用 Windows 设备门户或 shell 设置默认应用程序。
keywords: windows iot，默认应用，PowerShell，iot
ms.openlocfilehash: 09897d19f6b6f7cea64597b94c3a000a2ea7fa06
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229003"
---
# <a name="set-up-a-default-app"></a>设置默认应用程序
在这里，你将了解将应用程序设置为默认应用程序的方式。 默认的应用程序是在系统启动时启动的应用程序。  

> [!NOTE]
> 在部署到 RS5（或启用了 OpenSSH 的 RS4）IoT 映像时，Visual Studio 会生成一条晦涩的错误，除非安装了可供 Visual Studio 访问的来自 RS4 或更高版本的 SDK。

## <a name="runtime-options"></a>运行时选项

在开发/实验阶段，可以通过以下方式更改默认应用。

### <a name="using-windows-device-portal"></a>使用 Windows 设备门户

你可以单击对应于该应用的 **启动** 列。
![SetupDefaultAppWDP](../media/SetupDefaultApp/DefaultAppWDP.png)

### <a name="using-the-shell"></a>使用 shell

使用 shell 设置默认应用程序的步骤 

1. 通过[PowerShell](../connect-your-device/PowerShell.md)将连接到设备

2. 列出使用安装的应用程序 `iotstartup list`

3. 请注意要作为默认设置的应用程序的 appid，并使用对其进行设置 `iotstartup add headed <appid>` 。 对于无外设应用，应使用 `iotstartup add headless <appid>` 。


## <a name="build-time-option"></a>生成时间选项

对于大型部署，你可以使用预配包实现此目的

可以在创建预配包的过程中，在 WCD 中指定 StartupApp/Default 设置。
![SetupDefaultAppICD](../media/SetupDefaultApp/DefaultAppICD.png)

请参阅 [IoTCoreDefaultApp](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Source-arm/Packages/Appx.IoTCoreDefaultApp/customizations.xml) 作为示例。 你可以使用 [GetAppxInfo 工具](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Tools/GetAppxInfo.exe)获取应用程序用户模型 ID (APPX 的 AUMID) 。

## <a name="how-to-configure-home-key"></a>如何配置 "Home" 键

Windows 10IoT 周年更新 (1607) 为在另一个应用程序当前运行时将默认应用程序窗口引入前台提供 shell 支持。

若要了解如何启用 "主页" 密钥，请访问 [IoT Shell 页面](https://docs.microsoft.com/windows/iot-core/develop-your-app/iotcoreshell#switching-between-apps-with-hid-injection-keys)
