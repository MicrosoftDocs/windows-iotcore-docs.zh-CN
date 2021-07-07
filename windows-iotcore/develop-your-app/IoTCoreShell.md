---
title: IoT 外壳概述
ms.date: 08/28/2017
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: 了解如何利用 IoT Shell 在设备上的导航之间导航。
keywords: windows iot，IoT core shell，应用程序，前台应用程序，后台应用程序
ms.openlocfilehash: 38a55e3545116bbddb77c2ec6a7f4de14efc1d0a
ms.sourcegitcommit: 938c83c2823304341ce6022d12eeed037c119112
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2021
ms.locfileid: "113229844"
---
# <a name="iot-shell-overview"></a>IoT 外壳概述

本文档介绍 IoT Shell、前台和后台应用程序，以及如何在设备上的这些应用程序之间导航。

## <a name="iot-shell-foreground-and-background-apps"></a>IoT Shell、前台和后台应用

IoT 核心设备运行 IoT Shell。 它具有许多责任，但其主要任务是确保已启动注册的启动应用程序。 它有两种模式：头和无外设。 在头模式下，IoT Shell 将启动一个已注册的启动应用程序，该应用程序将以全屏方式显示其 UI (也称为应用) 。 向模式假设已连接屏幕并显示 UI。 在无外设模式下 (稍后会详细 [介绍) ，](../learn-about-hardware/HeadlessMode.md) 无 UI;IoT Shell 仅启动后台应用程序。

前台和后台应用程序的主要区别如下：

- **前台应用程序** 有一个 UI。 当设备处于头部模式时，将在启动时启动其中的一个。 所有前台应用都注册到设备上，用户可以在设备操作过程中在前台应用之间切换。

- **后台应用程序** 没有 ui，因此可以通过关闭 UI 堆栈来保存设备资源。 后台应用程序通常在启动时连续运行，并经常用于监视设备。

## <a name="switching-between-apps-with-a-home-app"></a>使用 Home 应用在应用之间切换

目前，启动应用程序允许您为 Windows 10 IoT 核心版创建 home 应用程序，使您可以在不同的前台应用程序之间切换。 

**IoT 启动应用** ([示例](https://github.com/microsoft/Windows-iotcore-samples/tree/master/Samples/IoTStartApp)表示一个简单的启动应用程序，该应用程序在设备上列出已安装的应用，然后使用 PackageManager api 启动一个应用。

## <a name="switching-between-apps-with-hid-injection-keys"></a>在具有 HID 注入密钥的应用之间切换

以下说明介绍了如何通过注册表项打开热键支持。 如果你正在构建自己的映像，并且想要支持以下热键 (Home、previous 应用和下一应用) 无需访问注册表，你可以包含一个可选功能包来处理这些步骤。

要查找的功能包称为： **Microsoft-OneCore-IoTUAP-Shell-HotKeys-Feature-Package.cab** ，该功能 **IOT_SHELL_HOTKEY_SUPPORT**。 请参阅[设置。示例的热键示例包](https://github.com/ms-iot/iot-adk-addonkit/tree/master/Workspace/Common/Packages/Settings.HotKey/Settings.HotKey.pkg.xml)。

本文档的其余部分介绍了如何手动实现此功能。

### <a name="return-home"></a>返回主页

使用 Windows 10 iot 周年更新 (1607) ，iot Shell 支持在运行另一个应用程序时将默认应用程序窗口设置为前台，方法是将设置为键盘上的 Windows 按钮的版本。 如果 IoT 设备上没有键盘，并且需要通过 [HID 注入](https://developer.microsoft.com/en-us/windows/iot/samples/hidinjection)注入低级键盘事件，或者只是想要在应用程序中将 "中转 HOME" 功能重新映射到其他密钥，则可以在注册表中调整密钥值。 例如，若要启用 (0x1B) 中按 ESC 键，请在注册表中输入以下命令：

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys” “HOME” QWORD    0x0000000 0000001B  
``

作为 REG 文件，如下所示：

``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Home"=hex(b):1B,00,00,00,00,00,00,00
``

### <a name="switch-between-apps"></a>在应用之间切换

或者，如果你想要在前台应用之间切换，则可以通过在注册表中输入以下命令来设置 Alt-Tab (下一个应用) 和移动-Alt-Tab (上一个应用) 功能。

``
“HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys”
“PREV” QWORD 0x00010000 00010009 
“NEXT” QWORD 0x00020000 00050009 
``

作为 REG 文件，如下所示： ``
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\IoTShellExtension\HotKeys]
"Prev"=hex(b):09,00,01,00,00,00,01,00
"Next"=hex(b):09,00,05,00,00,00,02,00
``

### <a name="bit-translation"></a>位转换

上述 REG 文件项从左向右解码，如下所示：

- Bits 0-15：对于转义) ，虚拟键代码 (例如1B、00。 有关关键代码值的完整列表，请参阅[虚拟键代码](https://msdn.microsoft.com/library/windows/desktop/dd375731(v=vs.85).aspx)
- Bits 16-19：修改键。 0x0 = No 修饰符，0x1 = ALT，0x2 = CTRL，0x4 = SHIFT。 组合键将值相加 (即 ALT + SHIFT 为 0x5) 
- Bits 20-47：保留供将来使用;必须为0
- Bits 48-62：操作
    - 0 = Home
    - 1 = 上一个视图 (在未来版本中可能不起作用) 
    - 2 = 下一个视图 (在未来版本中可能不起作用) 
- 位63：保留;必须为0

